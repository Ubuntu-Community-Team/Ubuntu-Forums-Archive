---
title: "XRDP and Windows"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by mcorey on 2012-04-23
Ubuntu newbie here...

I am trying to use remote desktop to connect to my Ubuntu 11.10 machine from Windows Vista.  Unfortunately it is not working.  When I attempt to connect from Vista all I get is a black screen, no menus, no login screen, nothing. This is a new install of Ubuntu and I have installed xrdp a couple of times, but still no luck.  

I tried the information in this site, but no luck.
[http://it.rawconcept.com/2011/10/24/xrdp-ubuntu-11-10-update/](http://it.rawconcept.com/2011/10/24/xrdp-ubuntu-11-10-update/)

I even tried the steps in this example, but no luck. Now one thing did change when I tried the steps below and a Windoes 7 machine (a friend of mine's) I got a login screen and put in my credentials, but then the screen just turned to a grey screen and then remote desktop closed.
[http://scarygliders.net/2011/11/17/x11rdp-ubuntu-11-10-gnome-3-xrdp-customization-new-hotness/](http://scarygliders.net/2011/11/17/x11rdp-ubuntu-11-10-gnome-3-xrdp-customization-new-hotness/)

So Vista no luck and Windows 7 a login panel and then nothing.

Any help would be appreciated.

---

### Post by Paddy Landau on 2012-04-24
This is a big, gaping hole in Linux -- how to access Linux machines from Windows.

XRDP can be buggy, unfortunately.

Have a look at VNC, which is open-source and cross-platform -- but be aware that the connection is unencrypted. At least it will work.

---

