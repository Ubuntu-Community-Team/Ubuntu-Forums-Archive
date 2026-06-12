---
title: "NetworkManager Infrastructure Hotspot (not ad-hoc)?"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by robjoski on 2012-10-01
I've been connecting my Android phone to my desktop computer's Wifi to use a latency-sensitive music app, and until recently, I used NetworkManager's easy ad-hoc hotspot for the connection. 
Since I upgraded my phone to Jelly Bean (CyanogenMod 10) however, ad-hoc networks aren't supported anymore.

I read about one of the new features of Fedora 18 - infrastructure hotspot support for NetworkManager - and I was wondering if Ubuntu will get this in 12.10 or not.
Is this an upstream feature or is it specific to Fedora?

And if Ubuntu 12.10 doesn't support it, will there be a PPA or something? 
I'm too lazy to recompile/repackage NetworkManager, and I'm already fed up with how complicated configuring hostapd is, so an easy solution would be great ;)

---

### Post by pvfjr on 2012-10-09
I've been banging my head up against the wall with this too.  Funny thing is, in Windows 7, my wifi card is capable of connecting to a wifi router AND hosting an infrastructure network simultaneously.  I can't even get Ubuntu 12.04 to host a infrastructure network by itself.  It does ad-hoc fine, but my android can't see adhoc. :(

---

### Post by ogyct on 2012-11-11
I want to support this thread. Allowing to create an infrastructure hotspot would a really great addition

---

### Post by ogyct on 2012-11-23
found a solution
[http://forum.xda-developers.com/showthread.php?t=2009381](http://forum.xda-developers.com/showthread.php?t=2009381)

---

### Post by sbnwl on 2012-12-26
I've also searched a lot, still found nothing working. Perhaps Ubuntu 13.04 will have this feature.

---

### Post by rrich1974 on 2013-06-27
[http://forum.xda-developers.com/show....php?t=2009381]("http://forum.xda-developers.com/showthread.php?t=2009381")

that is a great guide, my only comment would be that you should use wicd instead of network-manager. 
stop the network-manager first "sudo stop network-manager", connect via wicd or maybe wvdial in case of a mobile broadband an then, run that script.

---

