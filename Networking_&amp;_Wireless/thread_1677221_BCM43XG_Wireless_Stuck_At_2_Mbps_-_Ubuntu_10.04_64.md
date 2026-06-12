---
title: "BCM43XG Wireless Stuck At 2 Mbps - Ubuntu 10.04 64 Bit - STA Driver"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by BeastTurbo on 2011-01-28
I just installed a Netgear WN311B cards which is based on the BCM43XG chipset on Ubuntu 10.04 64 Bit.  The Broadcom STA drivers were installed using System > Administration > Hardware Drivers without incident.  The network card connects fine and has 100% (5/5) signal, but will not negotiate a speed faster then 2 Mbps with my Router with is a Netgear WNR3500 with WMM turned off and WPA2 turned on.

In addition to this computer I have a Dell Latitude D830 using BCM43xx drivers installed via the bw43-cutter tool on Ubuntu 10.04 64 bit which is able to reach 130 Mbits. This cards starts at 2Mbps and quickly negotiates its way up to 130 Mbps.

For the WN311B I tried using the NDISwrapper to alternatively install the Neatgear drivers, which did not work because the Windows XP drivers are only 32 bit and the Vista / Windows 7 are not compatible.  I also tried the BCM43xx drivers from Hardware Drivers, but they did not work I returned to STA which works, but I am stuck at 2Mbps. 

Any hints on getting this cards to negotiate more then 2Mbits from my connection? Is it possible to tweak the STA drivers?

---

### Post by bkratz on 2011-01-28
> **BeastTurbo said:**
> I just installed a Netgear WN311B cards which is based on the BCM43XG chipset on Ubuntu 10.04 64 Bit.  The Broadcom STA drivers were installed using System > Administration > Hardware Drivers without incident.  The network card connects fine and has 100% (5/5) signal, but will not negotiate a speed faster then 2 Mbps with my Router with is a Netgear WNR3500 with WMM turned off and WPA2 turned on.

In addition to this computer I have a Dell Latitude D830 using BCM43xx drivers installed via the bw43-cutter tool on Ubuntu 10.04 64 bit which is able to reach 130 Mbits. This cards starts at 2Mbps and quickly negotiates its way up to 130 Mbps.

For the WN311B I tried using the NDISwrapper to alternatively install the Neatgear drivers, which did not work because the Windows XP drivers are only 32 bit and the Vista / Windows 7 are not compatible.  I also tried the BCM43xx drivers from Hardware Drivers, but they did not work I returned to STA which works, but I am stuck at 2Mbps. 

Any hints on getting this cards to negotiate more then 2Mbits from my connection? Is it possible to tweak the STA drivers?

Do you have any luck changing it with

```
sudo iwconfig wlan0 rate 54M

```


or substituting eth1 for wlan0 if that is what your wireless card is called.

---

### Post by BeastTurbo on 2011-01-28
After entering iwconfig line the speeds reads as increased as noted in the output below.

```

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11bgn  ESSID:"ATM"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:24:B2:03:FB:23   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-41 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:24  Rx invalid frag:0
          Tx excessive retries:90  Invalid misc:0   Missed beacon:0

```

I will have to test and see for sure if the speed is actually increased later, but for now that seemed to work.  Thank you so much for the response, what would cause it not to discover the network speed?

---

### Post by BeastTurbo on 2011-01-29
Just A little more to report on the issue the problems seems to be with iwconfig not reporting the correct speed even though I am actually connecting at 54Mp/s.  Setting the rate using iwconfig worked, but it actually slowed the connection speed down.  

If I set "iwconfig eth2 rate auto" I actually get 54Mb/s transfer speed when copying a file even though it only reports 2Mp/s as my connection speed.

For anyone that does not know iwconfig only works with speeds up to 54Mps so it seems I am actually obtaining the correct transfer rate even thought it is being reported as much less.

Thanks again bkratz for your quick response to help me figure out my issue.

---

