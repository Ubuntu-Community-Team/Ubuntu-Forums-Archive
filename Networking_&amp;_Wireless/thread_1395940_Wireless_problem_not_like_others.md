---
title: "Wireless problem not like others"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by bfever74 on 2010-02-01
Hello, I'm brand new to Ubuntu. Have installed with Vista on partitioned hard drive. Installed 9.1 and no wireless. Driver is installed, says it's active and running. Network manager never appeared in tray, so I installed wicd. It says no wireless networks are available. Used troubleshooting algorithm, with no help their either. When I input sudo lshw -c network, I don't get any of the 4 messages I am supposed to (Enabled/Disabled) Really don't know how to proceed.
 
Have a Dell Studio with a Dell 1510 Internal Card. HELP!!
Thanks

---

### Post by chaanakya_chiraag on 2010-02-01
Post the output of ```
sudo ifconfig
```

---

### Post by bfever74 on 2010-02-01
bret@novus-laptop:~$ sudo ifconfig
[sudo] password for bret: 
eth0      Link encap:Ethernet  HWaddr 00:22:19:e4:b9:92  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fee4:b992/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1232 (1.2 KB)  TX bytes:4485 (4.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

bret@novus-laptop:~$

---

### Post by chaanakya_chiraag on 2010-02-01
I think it's detecting your hardware.  Have you tried looking at the man pages for ifup and ifdown (If I were at my Ubuntu box right now, I'd tell you the command, but I don't remember it offhand)??

---

### Post by bfever74 on 2010-02-01
no I haven't; I'm not sure what that means.  I'll investigate though.  Thank You!

---

