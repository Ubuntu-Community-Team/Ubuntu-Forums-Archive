---
title: "&quot;Enable Wireless&quot; greyed out: Intel PRO/Wireless 2200BG"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by leroybrownbpj on 2009-02-01
Hi, I've just installed Ibex (this is my first encounter with linux of any form), am attempting to get a wireless connection working and am having problems. This install is on an old machine who's history I do not know well and it is not entirely impossible that the problem is hardware related.

Right now I'm able to get an internet connection by plugging an ethernet line directly into this laptop but no wireless. Right clicking the network manager applet right now shows "Enable Wireless" as greyed out and uncheckable.

My chipset is the intel pro/wireless 2200BG. the 2200 is listed as compatible out of the box in the wireless compatibility thread. I'm not sure if this is the same piece or not.

Below is some information described in the HOWTO wireless issue thread. I'm not sure what is useful. Any and all help is greatly appreciated.

---------------------------------------------------------------------

~Laptop make: Velocity Micro

~Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

~result of ifconfig eth1:

sara@sara-lidstrom-laptop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0e:35:40:81:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x2000 Memory:d0000000-d0000fff 

~result from iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

pan0      Interface doesn't support scanning.

NOTE: I have a laptop with XP running right next to me with four visible wireless connections in range.

~result of uname -mr:

2.6.27-7-generic i686

~version

Ibex, downloaded today.

---

### Post by leroybrownbpj on 2009-02-01
There is a switch on the side of my laptop that turns wireless on and off. The switch is set to the "ON" position but the light with the wireless beacon icon on the bottom of the key pad is not lit up. I wonder if the light signals that the wireless hardware is turned on and its absence demonstrates a hardware problem or if it just signals an active wireless connection?

I've also heard about a package that is a wrapper for windows drivers that may help. Does anyone know the name of this package and if it is worth looking into?

---

### Post by thenewcrowd on 2009-02-01
ndiswrapper is the program, here is a how-to on it...

[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

---

### Post by leroybrownbpj on 2009-02-01
Is enable wireless being greyed out usually a symptom of just not having the driver installed properly?

---

