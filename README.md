vagrant-Zabbix
==============

* This VagrantFile provides a Zabbix 2.4 server installed on CentOS 6.7.   
* And with grafana 2.5.0 and grafana-zabbix 2.5.1 plugin installed and configured.

<pre>
  zabbix web console  :http://192.168.33.10
  Username            :admin     (default administrator)
  Password            :zabbix

  Username            :grafana   (zabbix admins, for grafana datasource)
  Password            :grafana-ro

------------------------------------------------------------------------
  grafana web console :http://192.168.33.10:3000
  Username            :admin
  password            :admin

------------------------------------------------------------------------
  MySQL password:
  username            :root
  password            :topsecret
</pre>  

comments
=======
1. 另外我更改使用了aliyun的更新源，在国内会更新快一点。

2. 我使用微软雅黑字体，替换了zabbix网站下的默认字体，这样显示中文的时候会好一些。

3. 为了修正zabbix界面历史栏乱码问题，我把mysql的默认数据库编码设置成了utf8(同过替换my.cnf)

4. 该虚拟机内置了grafana 2.5.0 并且安装了grafana-zabbix 以让grafana 显示zabbix中的数据（zabbix数据源已经配置).


* 关于grafana-zabbix 可以参考：https://github.com/alexanderzobnin/grafana-zabbix/wiki/Usage
* 关于grafana可以参考
  * grafana screencast: https://www.youtube.com/playlist?list=PLDGkOdUX1Ujo3wHw9-z5Vo12YLqXRjzg2
  *  http://docs.grafana.org/guides/basic_concepts/


Install is based on the steps found here:
========================================
 http://bicofino.io/blog/2015/10/09/install-zabbix-2-dot-4-6-from-source-on-centos/

Some tips:
=========
* vagrant的provison script 我拆分成了多个，方便测试以及自定义。
* 如果你想只使用zabbix 可以vagrant up --provision-with setRepo,installZabbix
* 后续如果你想安装grafana 以及grafana-zabbix 插件时，可以使用 vagrant provision --provision-with installGrafana
