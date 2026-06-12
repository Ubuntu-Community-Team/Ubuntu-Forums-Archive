---
title: "Ubuntu 9.04 wired connection problem!?"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by kemkokems on 2009-04-24
Today I did a fresh install of ubuntu 9.04 and everything went fine.But after I installed drivers for gpu via restricted driver manager and rebooted,the problem with network started.
On the upper panel the icon of my network card has a red x on it and now every time I restart computer I have to reconfigure adsl connection to get it working!I have to manualy delete files in /etc/ppp/pears/ and then do a "sudo pppoeconf" all over again and then I can connect to internet.I tried to manually configure network card but it is still the same,and I can not configure dsl via network manager because of this problem!
BTW I am also using ppptray for easier connection.

So can anybody help me with this?This is the output of my "lspci" :

kemko@mashina:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600 GSO (rev a2)
02:05.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:06.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
kemko@mashina:~$ 


Thanx in advance

---

### Post by manishsk on 2009-05-03
Hi

Even I am facing the same issue here. I just upgraded from Ubuntu 8.10 to 9.04.
While it was working fine with Ubuntu 8.10.

I need to run pppoeconf after every restart to connect to internet using ADSL.
plog shows below output.

> May  3 21:05:33 user pppd[3614]: Plugin rp-pppoe.so loaded.                              
May  3 21:05:33 user pppd[3614]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
May  3 21:05:33 user pppd[3616]: pppd 2.4.5 started by root, uid 0                       
May  3 21:05:33 user pppd[3616]: error sending pppoe packet: Network is down             
May  3 21:05:33 user pppd[3616]: error receiving pppoe packet: Network is down           
May  3 21:05:38 user pppd[3616]: error sending pppoe packet: Network is down             


---

### Post by manishsk on 2009-05-06
Hi

Following solution worked for me. Try if that works.

Modify /etc/NetworkManager/nm-system-settings.conf file with root permissions.
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false  <----- Set this to true and restart

```

Now I am able to connect to ADSL the same way I used to in 8.10.

---

