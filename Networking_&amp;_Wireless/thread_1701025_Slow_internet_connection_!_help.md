---
title: "Slow internet connection ! help"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by sesipdo on 2011-03-05
i have 12 meg service

when i had windows 7 on my laptop my internet would download at 1-3mbp\s and now all im getting is 200kbps Ubuntu 10.10 :( 

and i have a B\g\n wifi connection so that is not the problem :/

---

### Post by jeremyjjbrown on 2011-03-05
try this.

[http://ubuntuforums.org/showthread.php?t=1610609](http://ubuntuforums.org/showthread.php?t=1610609)

---

### Post by sesipdo on 2011-03-05
Should i do this? 

remove..... /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf 

scene that is what every one on that page says to do ?

but i dont have a Intel card or anything Intel in my computer .. :/

---

### Post by jeremyjjbrown on 2011-03-05
Open a terminal type this and post the results.

lspci

---

### Post by sesipdo on 2011-03-06
heres a little run down  .. 
eth0 is : nvida network lan 10\100\1000 
wlan0 is : Atheros AR5007 Wireless Network Adapter
ubuntu finds Atheros ar5001 but windows ar5007 !! windows drivers confirm this 

results --


shawn@shawn-pc-pc:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
shawn@shawn-pc-pc:~$

---

### Post by jeremyjjbrown on 2011-03-06
Have you Googled for slow wifi with Atheros AR5007 Wireless Network Adapter in your version of Ubuntu?

---

### Post by sesipdo on 2011-03-06
thats just the thing u can google that and this card is so talked about for drivers for ubuntu 10.10 it so hard for me to find any other info on it ,,

on windows 7 it moves so fast and on here its insane slowwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwW like i get 24kbs - 250kb on downloads .. 
 
BArf

---

### Post by jeremyjjbrown on 2011-03-06
Really. If I google for "slow wifi with Atheros AR5007 10.04" I get lot's of version specific stuff. 

[http://ubuntuforums.org/archive/index.php/t-1486948.html](http://ubuntuforums.org/archive/index.php/t-1486948.html)

What's your version?

---

### Post by fogNL on 2011-03-06
I'm suddenly having an issue with wireless in my HTPC running 10.10.

The chipset is  Realtek Semiconductor Corp. RTL8191S WLAN Adapter .  It seemed that a bunch of updates that came down not too long ago (include kernel update), has rendered my wireless very very slow.  It looks like its using r8712u module.

For example, transferring a file to my HTPC tops out at 30-40kb/s now from what it used to be of around 2-3MB/s.  If I try to upload a file to it by filezilla, and then open up a putty session to it, the putty session is extremely slow and lagged.

I haven't done anything else on this system different other than running updates.

No solution found yet.l

---

