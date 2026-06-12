---
title: "Toshiba Satellite, wireless networks seen but can't connect"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by Antster on 2011-05-13
Hi all

I'm pretty new to linux and have installed Lubuntu 10.10 on my Girlfriend's ancient Toshiba Satellite Pro SP6000 in an attempt to breathe some life back into it. 

The problem I'm having is that I can see the wireless network I want to connect to, but when I select it & enter the key it hangs for about a minute, then asks for the key again. This process loops on & on, until eventually it just gives up & tells me I'm not connected.

iwconfig shows this (not sure how to put it in a separate box as in other threads I have seen, apologies!):

                                 ***sophie@sophie-000000:~$ iwconfig***
***lo        no wireless extensions.***

***eth0      no wireless extensions.***

***irda0     no wireless extensions.***

***eth1      IEEE 802.11b  ESSID:"Smellus Wireless Network"   ***
***          Mode:Managed  Frequency:2.457 GHz  Access Point: None    ***
***          Bit Rate:11 Mb/s   Sensitivity:1/0   ***
***          Retry limit:8   RTS thr=2347 B   Fragment thr:off***
***          Power Management:off***
***          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm***
***          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:15***
***          Tx excessive retries:0  Invalid misc:0   Missed beacon:0***

The next part is a bit of the lspci -v output that shows the ethernet controller (I assume that the same controller is recognising the wireless networks and should be able to connect to them?):

      ***00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)***
[I][B]    Subsystem: Toshiba America Info Systems 8255x-based Ethernet Adapter 
    (10/100)[/B][/I]
***    Flags: bus master, medium devsel, latency 64, IRQ 11***
***    Memory at f7efe000 (32-bit, non-prefetchable) [size=4K]***
***    I/O ports at eec0 [size=64]***
***    Memory at f7ec0000 (32-bit, non-prefetchable) [size=128K]***
***    Capabilities: <access denied>***
***    Kernel driver in use: e100***
***    Kernel modules: e100***

I have no internet connection on the laptop in question (cant even get my 3 dongle to work!) but I can download stuff & move it over on a memory stick. 

OK, that's about the size of it. If anyone could help me I'd really appreciate it. 

Many thanks

 P.S. I also messed up the XP bootloader when I installed Lubuntu (working on that too, no help required yet!). The GF's  back in two days and I'd look way cooler presenting her with a new-&-improved browsing machine  rather than a completely broken mess!

---

### Post by Antster on 2011-05-14
Right, ended up giving up on the internal wireless card. 
It turns out that the driver is the orinoco_c or orinoco_s (can't remember which...). Found this by installing device manager and checking the wireless card details. 

I have now installed a different card & used Ndiswrapper to run a Windows driver for it. 
Not an ideal solution, but it seems that the internal card is one of a dying breed!

Marking this as closed - if anyone else finds that they are in the same position I'd suggest getting a new card (or laptop!). That is unless you can find anything that makes the orinoco driver work...

---

