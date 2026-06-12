---
title: "banshee install failed"
date: 2008-12-03
forum: Multimedia Software
---

### Post by kev380 on 2008-12-03
i just switched to linux and i have an ipod. i read that banshee is ipod compatible and im not even sure if i could get itunes running. anyway ive been trying to get it. i go to the website and i save the repository. but then in synaptic i try to install it, and i mark it to install. then it says




"the following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
banshee:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.0-1ubuntu3 is to be installed
 Depends: libboo2.0-cil (>=0.8.1.2865) but it is not installable
  Depends: libc6 (>=2.7-1) but 2.6.1-1ubuntu10 is to be installed or
 	libc6.1 (>=2.7-1) but it is not installable or
 	libc0.1 (>=2.7-1) but it is not installable
  Depends: libgconf2.0-cil (>=2.20.0) but 2.16.0-7ubuntu1 is to be installed
  Depends: libglade2.0-cil (>=2.12.1) but 2.10.2-1ubuntu2 is to be installed
  Depends: libglib2.0-cil (>=2.12.1) but 2.10.2-1ubuntu2 is to be installed
  Depends: libgnome2.0-cil (>=2.20.0) but 2.16.0-7ubuntu1 is to be installed
  Depends: libgtk2.0-cil (>=2.12.1) but 2.10.2-1ubuntu2 is to be installed
 Depends: libmono-addins-gui0.2-cil but it is not going to be installed
 Depends: libmono-addins0.2-cil but it is not going to be installed
 Depends: libmono-cairo2.0-cil but it is not going to be installed
  Depends: libmono-sqlite2.0-cil (>=1.2.6) but 1.2.4-6ubuntu6.1 is to be installed
  Depends: libmono-system-data2.0-cil (>=1.2.6) but 1.2.4-6ubuntu6.1 is to be installed
  Depends: libmono-system-web2.0-cil (>=1.9.1) but 1.2.4-6ubuntu6.1 is to be installed
  Depends: libmono-system2.0-cil (>=1.9) but 1.2.4-6ubuntu6.1 is to be installed
 Depends: libmono-zeroconf1.0-cil but it is not going to be installed
  Depends: libmono2.0-cil (>=1.9) but 1.2.4-6ubuntu6.1 is to be installed
 Depends: libmtp8  but it is not installable
  Depends: libndesk-dbus-glib1.0-cil (>=0.4.0) but 0.3-2 is to be installed
  Depends: libndesk-dbus1.0-cil (>=0.6.0) but 0.4.2-1 is to be installed
 Depends: libnotify0.4-cil (>=0.4.0~r2998) but it is not installable
 Depends: libtaglib2.0-cil but it is not going to be installed
  Depends: gstreamer0.10-plugins-good (>=0.10.8-4) but 0.10.6-0ubuntu4.1 is to be installed


i dont understand what this is and i cant find it in any forums. what do i need to do?

---

### Post by hjallen on 2008-12-08
no help here.  I have the same problem - maybe libmtp8?  it is not in the main repository

---

### Post by hjallen on 2008-12-08
figured out my problem (a silly one).  I have 2 machines, one with hardy and one with intrepid.  I added the intrepid apt line to my hardy repos rather than hardy.  Changed to hardy and worked.  Look at your apt line that you added to synaptic repos and make sure it is the correct version.  A silly mistake but at least one of us made it.:lolflag:

---

