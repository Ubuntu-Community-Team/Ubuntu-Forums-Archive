---
title: "Networking dosen't survive going down hard"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by jfb3 on 2011-05-08
Wireless networking never works again after a hard shutdown like the power plug getting pulled, or if it's frozen and only responds to a hard shutdown.

The only solution has been to reload the OS, which is not acceptable.

Specs:  
Machine: Dell e1505 laptop
OS:  Ubuntu 11.04
Wireless card:  Intel 3945ABG


rfkill shows:
Soft blocked: no
Hard blocked: no


I've looked at other threads on similar subjects and nothing works. 
In the drop down from the main menubar from the networking widget it shows the wireless device as "device not ready".

lshw -c network 
shows the device as "*-network DISABLED"

ifconfig wlan0 up returns:
"SIOCSIFFLAGS: Input/output error"

I ran gentoo on this machine for years with no problem.

Am I missing something?

---

