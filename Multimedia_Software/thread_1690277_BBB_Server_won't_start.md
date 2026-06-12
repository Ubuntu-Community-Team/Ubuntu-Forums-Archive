---
title: "BBB Server won't start"
date: 2011-02-18
forum: Multimedia Software
---

### Post by parkerj on 2011-02-18
I've Installed BBB according to the google code website, but I can't get it started. Below is the following info from bbb-conf -c:

BigBlueButton Server 0.71a
                    Kernel version: 2.6.32-28-generic-pae
                      Distribution: Ubuntu 10.04.2 LTS (32-bit)
                            Memory: 8055 MB

/var/www/bigbluebutton/client/conf/config.xml
  		Port test (tunnel): 127.0.0.1
                              Red5: 127.0.0.1

/etc/nginx/sites-available/bigbluebutton
                       server name: 127.0.0.1
                              port: 80
                    bbb-client dir: /var/www/bigbluebutton

/var/lib/tomcat6/webapps/bigbluebutton/WEB-INF/classes/bigbluebutton.properties (bbb-web)
                      bbb-web host: 127.0.0.1

/var/lib/tomcat6/webapps/bigbluebutton/demo/bbb_api_conf.jsp (API demos)
                  bbb-web-api host: 127.0.0.1

/usr/share/red5/webapps/bigbluebutton/WEB-INF/red5-web.xml
                  voice conference: FreeSWITCH


** Potential problems described below **
# Not Running:  Nginx

#  This server could not connect to BigBlueButton through [http://127.0.0.1/](http://127.0.0.1/)
#
#  If you are setting up BigBlueButton behind a firewall, see the FAQ
#  for steps to setup BigBlueButton behind a firewall.
#  	[http://code.google.com/p/bigbluebutton/wiki/FAQ](http://code.google.com/p/bigbluebutton/wiki/FAQ)

I am actually using a real ip address, not shown above. Any help with this is greatly appreciated.

---

