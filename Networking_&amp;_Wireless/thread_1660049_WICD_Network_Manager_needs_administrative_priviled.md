---
title: "WICD Network Manager needs administrative priviledges"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by evans62 on 2011-01-04
I had to reinstall WICD to fix another problem, and now it always asks me for my admin password every time I start up.   After I enter in the password, it doesn't work.

I have tried removing WICD and reinstalling it but that didn't help.

I tried searching for a cure to this problem but none of them seemed to have been SOLVED.  One post said he solved it but he wasn't clear on HOW he solved it.

Here is the log:

wicd initializing...
2011/01/05 02:04:54 :: ---------------------------
2011/01/05 02:04:54 :: wicd is version 1.7.0 552
2011/01/05 02:04:54 :: setting backend to external
2011/01/05 02:04:54 :: trying to load backend external
2011/01/05 02:04:54 :: successfully loaded backend external
2011/01/05 02:04:54 :: trying to load backend external
2011/01/05 02:04:54 :: successfully loaded backend external
2011/01/05 02:04:54 :: Automatically detected wireless interface wlan1
2011/01/05 02:04:54 :: setting wireless interface wlan1
2011/01/05 02:04:54 :: automatically detected wired interface eth0
2011/01/05 02:04:54 :: setting wired interface eth0
2011/01/05 02:04:54 :: setting wpa driver wext
2011/01/05 02:04:54 :: setting use global dns to False
2011/01/05 02:04:54 :: setting global dns
2011/01/05 02:04:54 :: global dns servers are None None None
2011/01/05 02:04:54 :: domain is None
2011/01/05 02:04:54 :: search domain is None
2011/01/05 02:04:54 :: setting automatically reconnect when connection drops True
2011/01/05 02:04:54 :: Setting dhcp client to 0
2011/01/05 02:04:54 :: Wireless configuration file found...
2011/01/05 02:04:54 :: Wired configuration file found...
2011/01/05 02:04:54 :: dhclient.conf.template not found, copying...
2011/01/05 02:04:54 :: Traceback (most recent call last):
2011/01/05 02:04:54 ::   File "/usr/share/wicd/daemon/wicd-daemon.py", line 1843, in <module>
2011/01/05 02:04:54 ::     main(sys.argv)
2011/01/05 02:04:54 ::   File "/usr/share/wicd/daemon/wicd-daemon.py", line 1807, in main
2011/01/05 02:04:54 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2011/01/05 02:04:54 ::   File "/usr/share/wicd/daemon/wicd-daemon.py", line 115, in __init__
2011/01/05 02:04:54 ::     self.ReadConfig()
2011/01/05 02:04:54 ::   File "/usr/share/wicd/daemon/wicd-daemon.py", line 945, in ReadConfig
2011/01/05 02:04:54 ::     shutil.copy(dhclient_conf + ".default", dhclient_conf)            
2011/01/05 02:04:54 ::   File "/usr/lib/python2.6/shutil.py", line 84, in copy
2011/01/05 02:04:54 ::     copyfile(src, dst)
2011/01/05 02:04:54 ::   File "/usr/lib/python2.6/shutil.py", line 50, in copyfile
2011/01/05 02:04:54 ::     with open(src, 'rb') as fsrc:
2011/01/05 02:04:54 :: IOError: [Errno 2] No such file or directory: '/etc/wicd/dhclient.conf.template.default'

---

### Post by evans62 on 2011-01-06
Anyone?  Please??

---

