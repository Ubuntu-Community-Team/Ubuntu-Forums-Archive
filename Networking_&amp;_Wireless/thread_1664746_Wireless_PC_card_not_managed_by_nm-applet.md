---
title: "Wireless PC card not managed by nm-applet?"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by HankB on 2011-01-11
I'm trying to get a wireless PC (PCMCIA?) card working under 10.04 desktop. It does not seem to be recognized by nm-applet and I cannot see any particular reason why. I have disabled the built in wireless (Intel 2200) in both BIOS and by blacklisting the appropriate module so there should be no interference from that. The card is a Linksys WPC300N V1. It has Power and Link/Act LEDs both of which remain dark.

Here's the information I have collected regarding the card:

lshw:

```
hbarta@willow:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:49:50:e8
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:c0210000-c021ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:c4000000-c4003fff
```

iwconfig:
```
hbarta@willow:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

hbarta@willow:~$
```

lspci:
hbarta@willow:~$ sudo lspci -v

...

```
03:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
	Subsystem: Linksys Device 0058
	Flags: bus master, fast devsel, latency 64, IRQ 11
	Memory at c4000000 (32-bit, non-prefetchable) [size=16K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```

relavent info from 'dmesg'

```
[   23.630905] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[   23.630921] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   23.630935] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
...
[   24.213425] b43-phy0: Broadcom 4321 WLAN found (core revision 11)
[   24.256034] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
[   24.256065] b43: probe of ssb0:0 failed with error -95
[   24.256109] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
```

I searched the forum for "ERROR: FOUND UNSUPPORTED PHY" and found no solution to the problem (or indication that it prevented the card from working.)

I saw some commenta about b43legacy module so I loaded it. (b43 was already loaded.) 'dmesg' after 'sudo modprobe b43legacy'

```
[ 1967.221541] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
```


After this, the following modules were loaded:
```
hbarta@willow:~$ lsmod|grep b43
b43legacy             115152  0 
b43                   163524  0 
mac80211              205402  2 b43legacy,b43
cfg80211              126528  3 b43legacy,b43,mac80211
ssb                    38902  2 b43legacy,b43
led_class               2864  3 b43legacy,b43,thinkpad_acpi
hbarta@willow:~$ 
```

I saw a comment about 'You need to have "managed=true" for NetworkManager to bring the interfaces up. in '[FONT="Courier New"]/etc/NetworkManager/nm-system-settings.conf
[/FONT] and did so but I see no change.

I understand that modules must be compiled to support network-manager but I would expect that to be the case with modules that ship with 10.04. I don't see any obvious indications for why this is not coming up with network-manager. Is there something I;m overlooking or something else I need to do?

thanks,
hank

---

### Post by chili555 on 2011-01-11
First, I wonder why the usually robust ipw2200 is not working for you. I would expect it to out-perform a Broadcom PCMCIA. 

Either b43 ***or*** b43legacy is correct; not both. Let's see which is appropriate. Please post:```
lspcmcia ident
```Next, let's be sure the correct firmware is loading. Please post:```
ls /lib/firmware/b43
```Thanks.

---

### Post by HankB on 2011-01-11
Thanks for the quick reply.

> **chili555 said:**
> First, I wonder why the usually robust ipw2200 is not working for you. I would expect it to out-perform a Broadcom PCMCIA.
I configured my AP for N only. The ipw2200 works fine with G. I guess if I get N working with the PC card, I'll have to see if it actually provides an improvement.

> Either b43 ***or*** b43legacy is correct; not both. Let's see which is appropriate. Please post:```
lspcmcia ident
```Next, let's be sure the correct firmware is loading. Please post:```
ls /lib/firmware/b43
```Thanks.

The b43 module loads by default. I see no hint in dmesg output that it tries to load firmware and there is none installed in /etc/firmware.

Here's what I find for the card:

```
hbarta@willow:~$ lspcmcia ident
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.0)
  CardBus card -- see "lspci" for more information
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.1)
hbarta@willow:~$ lspci -nnvv

...

03:00.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
	Subsystem: Linksys Device [1737:0058]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c4000000 (32-bit, non-prefetchable) [size=16K]
	Kernel driver in use: b43-pci-bridge
```

thanks,
hank

---

### Post by chili555 on 2011-01-11
Can you temporarily get a wired ethernet connection and do:```
sudo apt-get install bcmwl-kernel-source dkms
```Reboot and you should be all set.

---

### Post by HankB on 2011-01-11
> **chili555 said:**
> ... Reboot and you should be all set.

You say that with a great deal of confidence.


... which is justified :guitar:

Thanks! It works. Does this mean that the drivers I required are not part of the standard desktop install?

BTW:
```
hbarta@willow:~$ netperf -H oak
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to oak.example.net (192.168.100.100) port 0 AF_INET : demo
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.07      75.84   
hbarta@willow:~$
``` 

Thanks!

-hank

---

### Post by chili555 on 2011-01-11
> Does this mean that the drivers I required are not part of the standard desktop install?That's correct. Part or all of the Broadcom drivers are proprietary and are not distributed with a standard Ubuntu install, which is entirely open source; i.e. ***not*** proprietary. If we want proprietary drivers, codecs, etc., we must install them ourselves after the fact. 

This is changing, however:  [http://www.zdnet.com/blog/open-source/broadcom-yes-broadcom-joins-the-linux-foundation/8040](http://www.zdnet.com/blog/open-source/broadcom-yes-broadcom-joins-the-linux-foundation/8040)> You say that with a great deal of confidence.It's amazing what ten years of experience, often fifteen hours a day and seven days a week can do!

---

