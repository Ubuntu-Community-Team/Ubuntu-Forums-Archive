---
title: "new to ubuntu no internet connection PLEASE HELP"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by 1bad450r on 2011-08-16
Im new to linux and decided to give ubuntu 11.04 a shot on an older laptop of mine which is a compaq f700. first big problem im having is no wired or wireless internet connection. i know it has an atheros ar242x network card but being so new to this i have no idea where to start diagnosing this problem. Any help would be awesome. Thanks. :confused::confused::confused:

---

### Post by pdc on 2011-08-16
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by 1bad450r on 2011-08-16
Compaq F700 

Atheros AR5001 ethernet controller

eth0   Link encap:Ethernet  HWaddr 00:1b:24:ef:28:8a
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:42 Base address:0x4000

lo     Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::0/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:256 errors:0 dropped:0 overruns:0 frame:0
TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:19968 (19.9 KB)  TX bytes:19968 (19.9 KB)
 
nvidia mcp67 ethernet interface

it says network disabled, not sure how to enable. 

does that help??

---

### Post by wes_lin on 2011-08-16
hi 1bad450r,

Think about how you normally connect using a cable with the computer you already use. Would you normally use DHCP to get an ip address? In that case, run the commmand: sudo  dhclient. This is the equivalent of running ipconfig /renew in windows. It will try to pull down an ip address from the DHCP server. 
If that doesnt work then you need to confirm that your old laptop is still working. Connect a patch cable between  your laptop and another computer. Set an ip address on the other computer like 192.168.1.1 255.255.255.0 or whatever. Then set an ip address on your laptop by typing in sudo ifconfig 192.168.1.2/24. Confirm it was set by running ifconfig. Then try to ping the other computer. This should get you started :-)

---

### Post by 1bad450r on 2011-08-16
ok i entered the command: sudo dhclient in the terminal, it asked for my password, i entered it and it did nothing. just went down a line for a new command. the internet worked fine when i had windows on here. its almost like the ethernet port is disabled or something.

---

### Post by pdc on 2011-08-16
try this

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by 1bad450r on 2011-08-16
i already posted some of that info. this doesn't seem like it should be a big issue for someone who knows what they're doing with this program.??

---

### Post by 1bad450r on 2011-08-16
well thanks for the suggestion wes_lin but linux just seems like a lot more trouble than its worth at this point. i think ill just go back to windows for the time being, maybe try it again later down the road when its more user friendly.

---

