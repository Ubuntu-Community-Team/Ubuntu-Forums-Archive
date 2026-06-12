---
title: "ipblock blocking local traffic?"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by mrPalomar on 2011-02-06
Hi all,

A day or two ago I was suddenly unable to access services on my Ubuntu server from other machines on my LAN.  After some trial & error, I was able to determine that stopping ipblock fixes the problem.  However, looking through the ipblock log files, I see no references to either the 192.168.xxx.xxx LAN address that the requests should be originating from, or the external IP I've been assigned by my ISP.

Does anyone have any recommendations for where to begin?  I've scoured all of the log files I can find and none give me any indication that the connection attempts are even making it to my linux machine.  

I should note that even the linux machine is unable to connect to itself, but can connect to the outside world. I've tried using ssh, http, and ping, and none work when ipblock is running. 

Thanks!
Ed

---

