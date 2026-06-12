---
title: "Connect from Vista to Ubuntu printer"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by wazzle on 2009-12-29
I have been searching everywhere but have not found a fix for my problem. I am running Ubuntu 9.10 on my desktop and would like my laptop running Windows Vista to be able to print to the Ubuntu printer. The laptop connects through a router wirelessly and the desktop is connect to router with cable. I have set the Canon iP4200 up in Ubuntu with no problem and have it shared. I have typed the command in Windows "http//servername:631/printers/printername"           I have tried the word ubuntu for servername, the IP address showing up on my router for the desktop computer, the IP address showing up on ifconfig for the desktop computer and the exact printer name showing up in printers.  It won't connect to the printer no matter what I do. 

One thing I am not sure of,  my router config page shows the IP address of my desktop as the usual 192.168. .   type of address. When I ifconfig in terminal, I get an IP address of 172.27.35....  Why are these different? is this my problem.   I can ping from the laptop to the 192.168... address but not the 172.27.35... address.

---

### Post by b0b138 on 2009-12-30
Yes, the 172.x.x.x is a problem. Post the whole output of ifconfig

---

### Post by wazzle on 2009-12-30
eth0      Link encap:Ethernet  HWaddr 00:11:d8:cb:05:76  
          inet addr:172.27.35.133  Bcast:172.27.35.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fecb:576/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9691527 (9.6 MB)  TX bytes:1610757 (1.6 MB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8172 (8.1 KB)  TX bytes:8172 (8.1 KB)

---

### Post by b0b138 on 2009-12-30
If you hover the mouse over the network icon to the left of the clock, does its say "Wired network connection 'Auto eth0' active"?

---

### Post by wazzle on 2009-12-30
yes it does

---

### Post by b0b138 on 2009-12-30
post the output of ```
cat /etc/network/interfaces
```

---

### Post by b0b138 on 2009-12-30
doh...check your router settings.  172.27.x.x falls within a private ip range as does 192.168.x.x See if its giving different settings based on wired or wireless as they can give out different ranges depending on the router

---

### Post by wazzle on 2009-12-30
I may have figured out part of the problem. I had my network cable on the desktop running through my VOIP phone box as suggested by the company. I disconnected the cable from the phone and ran it right from the router and the IP address changed to the 192.168...  I have a printer showing up on my ubuntu laptop, I just need to check my windows laptop and will let you know tomorrow.  Thanks for the assistance.

---

