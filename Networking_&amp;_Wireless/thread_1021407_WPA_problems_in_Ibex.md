---
title: "WPA problems in Ibex"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by tamman2000 on 2008-12-25
Hey all,
I am having wpa problems in Ibex...

I first installed ubuntu 6.04 on this machine and I have been doing the upgrade installs ever since.  I had to mess with my wpasuplicant.conf at one point and now I am not sure if that is what is causing problems or not...

Anyway, I am visiting my parents and their wifi uses wpa, and the regular network manager, prompt for password method of connecting to their net isn't working.  WPA is supposed to "just work" in ibex, right?  Any ideas why it isn't working for me?  If there is any info I can provide about this system to help, please let me know how to find the information you need (for instance, I have no idea how to tell what driver I am using if you don't tell me what command to use).

Thanks,
Tamman2000

---

### Post by negev on 2008-12-25
maybe this will help [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by negev on 2008-12-25
or use wicd [http://wicd.net](http://wicd.net) 

sudo apt-get install wicd

---

### Post by tamman2000 on 2008-12-26
I just installed wicd...

Now there is just one problem...  not too major, but still a problem...

I would really like to have a wicd tray icon, and the only instructions I have found for setting that up tell me to use /opt/wicd/tray.py which doesn't exist on my system...

Anyone know how I can set up the wicd tray icon?

[edit]
nevermind....

I found out that it is now called wicd-client and it started when I restarted gnome.

---

