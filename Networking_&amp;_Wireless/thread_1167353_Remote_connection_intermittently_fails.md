---
title: "Remote connection intermittently fails"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by bernie888 on 2009-05-22
hi guys

Hopefully someone can give me some ideas on this.

So, I setup remote desktop (the built in vnc equivalent in Ubuntu 8.10) and it initially works fine. I have port forwarding setup on my router for the default vnc ports.

I connect from a Windows machine at work to my home PC (described above) using VNC Viewer. 

Here's what happens. Usually I can connect first time, it prompts for password and I'm in and can do everything normally on my Ubuntu home machine. But typically it drops the connection at some point - usually if I'm away from my desk for a while or not actively using the remote connection. And then subsequent to that it will not let me reconnect.
VNC will display the error "unable to connect to host: A socket was attempted to an unreachable host. (10065)"
The only way I can get it to work again is when I go home, reboot my PC and then the next day it will allow me to connect again, but as soon as it drops the connection (which is does every day) or times-out then I cannot get back in again.

Any idea if its the router itself or if its the Ubuntu system, specifically the built-in vnc client with some timeout value? Or is it the Ubuntu O/S sending the PC into sleep mode? 

Thanks

---

### Post by superprash2003 on 2009-05-23
in your terminal type ifconfig and post output , could be an MTU related issue..

---

### Post by bernie888 on 2009-05-24
hey superprash

here's the wlan0 section of ifconfig.
I haven't changed it from the defaults when it was originally setup.

wlan0     Link encap:Ethernet  HWaddr 00:23:54:7b:07:3e  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe7b:73e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21223397 (21.2 MB)  TX bytes:15269942 (15.2 MB)

---

### Post by superprash2003 on 2009-05-26
you could try 2 things , 
1)disable ipv6 - [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)
2)change MTU value - [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)
 
 i have a feeling it could be a MTU related issue..

---

