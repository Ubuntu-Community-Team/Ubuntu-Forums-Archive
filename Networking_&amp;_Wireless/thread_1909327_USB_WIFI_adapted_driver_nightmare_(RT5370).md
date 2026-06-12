---
title: "USB WIFI adapted driver nightmare (RT5370)"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by Pulsar303 on 2012-01-15
I'm having issues with getting my WIFI card to work on ubuntu.  Let me clarify, this is "Crystalbuntu", running on AppleTV.  I don't have a UI, just SSH access.  This is day 4 of googling and trying to find a solution.  Nothing but dead ends everywhere.  I don't know much about Linux.

The Wifi card I bought off ebay is supposed to be Ralink 5370 chipset.  I downloaded the drivers: 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2-1.5.0.3_DPO from ralink site.  Then I did:

sudo make clean
sudo make
sudo make install
sudo modprobe rt5370sta
sudo ifconfig ra0 up

it acts as if it's working but doesn't.

ifconfig:
ra0       Link encap:Ethernet  HWaddr 00:0f:53:71:10:93  
          inet addr:10.0.1.90  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20f:53ff:fe71:1093/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1345700 (1.2 MB)

iwconfig ra0:
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist ra0 scan:
ra0       No scan results


What now?

---

### Post by Pulsar303 on 2012-01-15
No takers?

---

### Post by Pulsar303 on 2012-01-15
Just wanted to post an update.

I give up.  After 5 straight days of research, I came to a conclusion that the drivers simply don't work with the Crystalbuntu Kernel (2.6.24).  I then tried to see if I can upgrade the kernel, but apparently I cannot do that without recompiling the Mach kernel and facing many additional issues with running XBMC on the ATV.  It is truly sad that Linux has not changed in 15 years and is still the OS of choice for those who have loads of free time to compile kernels and building their own drivers from scratch.  So much of my time wasted on this...  Shame.

---

### Post by mindlessgr on 2012-02-14
Try the solution i gave on my blog if you want about rt5370
[http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/](http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/)

---

