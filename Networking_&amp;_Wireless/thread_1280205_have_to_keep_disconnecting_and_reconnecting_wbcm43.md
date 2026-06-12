---
title: "have to keep disconnecting and reconnecting w/bcm43xx driver"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by PatchesTheCaveman on 2009-10-01
I have to keep disconnecting and reconnecting from my school's AP randomly (sometimes frequently,  sometimes very infrequently) on my HP Pavillion zv6000 running Kubuntu 9.09 Jaunty and using the bcm43xx driver.  (I couldn't get it to work at all with ndiswrapper.)

I did not have this problem with a Linksys WRT54GL AP at home nor did I have it with Windows XP on the school AP.  

lspci output:
```
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)                                                             
        Subsystem: Hewlett-Packard Company Device 12f8                          
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-                                                   
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at b0200000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb
```

iwconfig output:
```
wlan0     IEEE 802.11bg  ESSID:"AnyU"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:9D:CD:74:E0
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=71/100  Signal level:-51 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig output:
```
wlan0     Link encap:Ethernet  HWaddr 00:90:4b:ec:a9:c8
          inet addr:172.29.82.220  Bcast:172.29.83.255  Mask:255.255.252.0
          inet6 addr: fe80::290:4bff:feec:a9c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:121760603 (121.7 MB)  TX bytes:7354656 (7.3 MB)
```

This is the first time running Linux on my own box in 4 years so I'm a little rusty!

---

### Post by kevdog on 2009-10-01
Id tell you to use the b43 or the openfwwf open source variant.  There is a broadcom wireless reference in my signature to a site that Ayuthia wrote (another ubuntu user).  This should help you a lot!!!

---

### Post by PatchesTheCaveman on 2009-10-01
The b43 instructions linked to in that blog are the ones I followed to get it working.  (I should have said b43 and not bcm43xx in the first post.) The ndiswrapper instructions are also the ones I tried to use and failed. 

However, I will give OpenFWWF a shot tomorrow (I didn't bring an Ethernet cord with me and want one before I start mucking around with it.)  Do I need to remove the firmware files b43-fwcutter put there before using it?  Is that as easy as removing (after backing up) all of the bcm43xx_foo.fw files?  Or do I need to delete the b43 and/or b43legacy folders too?

 I might try ndiswrapper again tomorrow if that fails too...

---

### Post by PatchesTheCaveman on 2009-10-01
Clarifying a couple points:

[LIST]
[*]I did not have problems with my current setup on the home AP, which I am now 300 miles away from.  (Perhaps the problem has something to do with the fact that my school obviously has multiple APs??)
[*]I used b43-fwcutter from the .deb for the beta version of Ubuntu because the version included in Jaunty didn't work with my card according to [http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)
[/LIST]
Might updating the kernel (and therefore the driver?) to the newest version from jaunty-updates help?  [Though I dare not try it until I connect with Ethernet.]

---

### Post by kevdog on 2009-10-01
Hmm

Strange the situation you are describing.  You might need to investigate it further with the command line and looking at the syslogs.

If you want to try the openfwwf approach, please note that the instructions in the linked thread actually "back up" the old b43 drivers within the /lib/firmware directory.  I think it changes the name of the b43 folder to b43-old or something like that.  With this change you can revert to the old driver if something is causing problems.

---

