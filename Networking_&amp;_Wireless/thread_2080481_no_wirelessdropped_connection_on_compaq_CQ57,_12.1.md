---
title: "no wireless/dropped connection on compaq CQ57, 12.10"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by jan-banan on 2012-11-04
So this is the background: I installed Quantal and all was fine until i noticed that my wireless connection would drop from time to time so i googled and tried to find a solution and this thread seemed to be good enough: [http://ubuntuforums.org/showthread.php?t=2078176](http://ubuntuforums.org/showthread.php?t=2078176)
We have the same computer/wireless card so i figured that it would do the trick. I followed the steps on the german website and when i do modprobe rt5390sta the computer freezes. Sometimes when i boot the computer it will freeze instantly. 

Anyhow here are some terminal outputs that might be informative.
lspci -nnk
> 07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
	Kernel driver in use: rt2860
	Kernel modules: rt5390sta, rt2800pci
iwconfig> 
ra0       Ralink STA  ESSID:"dd-wrt"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 34:08:04:12:8E:4E   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-30 dBm  Noise level:-40 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.


What can i do to fix it?

---

