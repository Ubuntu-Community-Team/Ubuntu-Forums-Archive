---
title: "Home WiFi ... how do I do it?"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by smandoli on 2009-12-03
I want to deploy a simplest secure WiFi that will let my family members use the Internet on separate computers (including Win, Mac).    

I have a PC running Karmic.  I receive Internet service through a cable DSL service.  I use firehol, tinyproxy and dansguardian for content filtering.  I also run LAMP.  

I bought a Wireless AP (TrendNet TEW-637AP "Wireless N").  I installed a NIC card so I have a second ethernet cable jack.  I got a cross-over ethernet cable to connect the WAP to the 2nd NIC card.  

I've tried poking around with WPA-GUI (supplicant) and network-tools, but I can't get a usable signal.  

Must I have buy a dedicated router?  If so, can you recommend a cheap one?  Is it possible to avoid making another hardware purchase?  (It seems one common approach is to use a dedicated PC as a router, but I don't have a second PC available.)  

I started my Linux life with Hardy, and usually it's been easier to find a "how-to" guide I can understand.  This home WiFi challenge is different.

---

### Post by Iowan on 2009-12-03
Maybe you already answered this question:
Have you been able to communicate (ping) between the AP and PC?

---

### Post by smandoli on 2009-12-04
Iowan:  I'm used to pinging Localhost but I didn't know it helps me here.  Thanks for the valuable info.  I will try it this evening.  I expect no ping, because I think I don't have an IP address to the AP.

---

### Post by northd_tech on 2009-12-04
Hi smandoli.

Pinging localhost is just going to circle the "loopback" l0 interface.  As far as your ubuntu machine is concerned, the cable modem is just an external IP address (often 192.168.0.0, but don't quote me on that).  I believe that you should also be able to set up a very secure firewall server on the Linux machine (if you don't mind running everyone's internet traffic through that one machine).  

It has been years ago that I did this, but I seem to recall even being able to automatically virus scan files (and delete and/or tarball/quarantine them) sent via sFTP as they travel the network.

We probably need to figure out what kind of network hardware your ubuntu is running first of all.  See this recent thread for some of those needed commands:

[http://ubuntuforums.org/showthread.php?t=1241874](http://ubuntuforums.org/showthread.php?t=1241874)

And this is just a mental note to myself for later (but it might be helpful here too)- gotta run:

[https://help.ubuntu.com/community/NetworkAdmin?action=show&redirect=network-admin](https://help.ubuntu.com/community/NetworkAdmin?action=show&redirect=network-admin)

Edit:  Does your cable modem have wireless antennas externally or built-in, or maybe a 4-port, 8-port, or 10-port switch?  If not you might need to purchase a wireless router/switch (and those often have built in firewall firmware or come with Windows firewall software included, and Vista and 7 have fair firewall abilities built in).

---

### Post by smandoli on 2009-12-04
( SORRY Admins -- I posted this to the wrong thread an hour ago.  8-[ )


You asked about my cable modem.  It is about as simple as can be ([descriptions]("http://www.simplehelp.net/2006/07/11/cable-modem-troubleshooting-ambit-u10c018/") [here]("http://http://crazytechsite.com/u10c018.htm")).  

Below are the results of several commands.  I guess running dhclient tends to mess up my connection ... have rebooted to get back.  
**ifconfig**
```

eth2      Link encap:Ethernet  HWaddr 00:12:17:53:11:55  
          inet addr:24.155.231.190  Bcast:24.155.231.255  Mask:255.255.254.0
          inet6 addr: fe80::212:17ff:fe53:1155/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:424256 (424.2 KB)  TX bytes:105752 (105.7 KB)
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:786427 (786.4 KB)  TX bytes:786427 (786.4 KB)


```

**lshw -C network **
```

  *-network:0             
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth2
       version: 11
       serial: 00:12:17:53:11:55
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=24.155.231.190 latency=64 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:17 ioport:e400(size=256) memory:fad00000-fad003ff memory:fac00000-fac1ffff(prefetchable)
  *-network:1 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:15:f2:27:a2:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:23 ioport:a000(size=256) memory:fa800000-fa8000ff


```
**dhclient eth0**
```

There is already a pid file /var/run/dhclient.pid with pid 2522
killed old client process, removed PID file ...
Listening on LPF/eth0/00:15:f2:27:a2:2c
Sending on   LPF/eth0/00:15:f2:27:a2:2c
Sending on   Socket/fallback
DHCPREQUEST of 67.198.30.163 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 67.198.30.163 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 67.198.30.163 on eth0 to 255.255.255.255 port 67


```
**dhclient eth2**
```

Listening on LPF/eth2/00:12:17:53:11:55
Sending on   LPF/eth2/00:12:17:53:11:55
Sending on   Socket/fallback
DHCPREQUEST of 24.155.231.190 on eth2 to 255.255.255.255 port 67
DHCPACK of 24.155.231.190 from 10.0.3.254
bound to 24.155.231.190 -- renewal in 84848 seconds.


```
**dhclient lo**
```

Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 10

```
**lspci**

```

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0c.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0d.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)

```

---

### Post by Iowan on 2009-12-04
"lo" should have a fixed address (127.0.0.1) Trying to get it a DHCP address (via dhclient) may have helped "mess up" your connection.

The provided information raises a few more questions:
What is the IP Address of the AP? It must be in the same subnet as the card to which it is connected (eth2?). 
Is eth2 getting it's IP address from the AP? (Kinda seems the wrong way around...)
What happened to eth0? Is that supposed to be the internet connection (to DSL modem?)

I don't really expect you to have all the answers - but some things wo work on.

---

### Post by smandoli on 2009-12-04
As a Linux newbie, I been treating the settings as my little sandbox.  Been figuring that unlike the time I misused the [FONT="Verdana"]chown[/FONT] command, anything I do is prolly recoverable.  It seems like the little devices are talking to each other, and so far I can reboot and get my basic connection back.  

I did deduce lo=localhost.  Other than that, blind guessing ... I conclude that I _yes_ I am trying to make my PC the router, and _heck no_ I don't mind that all that traffic's going to go through my PC.  'Cause I'm too ignorant to know why I should.  

I don't know the IP address of the AP, etc., or how to get the info ... but I am going to plug along some more and will post any developments.  If you think of a helpful diagnostic, please let me know.  

I'm very grateful your counsel.

---

### Post by Iowan on 2009-12-05
"lo" is actually the loopback device (although it IS on localhost...) The forums are a great place to learn - as long as some well-intentioned person doesn't steer you the wrong way (meaning me - I hope that doesn't happen...). 

What kind of AP? I'm not well versed in very many (OK, almost none), but the internet is full of information. We can probably find default values (your owner's manual should also have the info) and get the direct connection working.

---

### Post by northd_tech on 2009-12-06
Hi again smandoli.

The easiest way will just be to buy a wireless router with the cable modem built-in.  It is a very beneficial option to have at least a 4-port ethernet switch built in too, so that you can cable in if your wireless gets messed up.

Take a look at some of these:

[http://www.nextag.com/wireless-cable-modem-router/shop-html](http://www.nextag.com/wireless-cable-modem-router/shop-html)

I prefer the Linksys ones (they've been nearly "bulletproof" when I used them in the past).  The [obsolete] 802.11b will give about 11 Mbit/sec, with 802.11g about 54 Mbit/sec, and the newer 802.11n about 100 Mbit/sec (as I recall anyway).

The newer ones are pretty easy to administer- usually you enter the [ethernet] IP address of the cable modem (which is often a different IP address than its "wireless" IP address), enter a username/password, and then you can set the station broadcast ID, frequencies/channels, broadcast power, WPA keys (access "passwords"), etc.

Some of the older wireless routers often came with a firewall software CD (and those were usually Windows software, but newer ones might have Linux software included).

Hey, I just found this page- you should probably read this to save me a lot of typing:

[http://www.firewallguide.com/wireless.htm](http://www.firewallguide.com/wireless.htm)

Years ago, we used an old Red Hat Linux to set up an internet firewall access point at my university (we got hacked mercilessly over the Thanksgiving holiday, and we decided NEVER AGAIN).  That ended up being a customized read-only Linux OS that booted off CD-ROM, and it didn't even have a hard disk to hack, but it had crates of RAM (about 32GB, IIRC) in a rackmount system, and it was damned quick without a hard disk to spin.

You should be able to set up a Linux firewall server in a recent ubuntu now if you're overly concerned about security (although I haven't done it personally).  Here is the firewall HOWTO:

[http://tldp.org/HOWTO/Firewall-HOWTO.html](http://tldp.org/HOWTO/Firewall-HOWTO.html)

A firewall isn't really necessary if you're not all that worried about security though.  WPA keys are often all you will need there for a home network.

Good luck.

Edit:  I also didn't see a wireless adapter in your code output above (but maybe I missed it).  Was that on a desktop PC, or a laptop?  Some of the older laptops won't have a built in WiFi "radio," but you can add a little USB "antenna" or PC-card one to the older ones, and sometimes you can get a router "package" that will have one of these included for not much more money than just the wireless router.

Maybe you should post the make and model of whatever laptops (or phones, etc.) you eventually plan on networking here, and we can try to figure out the wireless hardware thing (it can really be a PITA under Linux, but you can sometimes "ndiswrap" your Windows drivers to get wireless ubuntu).  You can also set up bluetooth "networks" pretty easily, but the software can be quite limited from what I've seen there so far.

You can also add a WiFi PCI adapter card to a desktop computer to save the hassle of stringing cables all through your house or apartment (but these will have varying degrees of compatibility with Linux).  I'd check the forums here and see which cards people have had the least B.S. with under ubuntu.  Here's a big list of those things, too:

[http://products.wi-fiplanet.com/wifi/pci_adapter/index.html](http://products.wi-fiplanet.com/wifi/pci_adapter/index.html)

Edit2:  Also, range can sometimes be an issue with WiFi, so the "range boosted" wireless routers can be nice (but will usually cost more too).  In some areas with a lot of frequency "cross talk", wireless connections can be problematic, so the ethernet cable connections are usually the most reliable and secure.

---

### Post by northd_tech on 2009-12-06
> **smandoli said:**
> 
```

00:0c.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 

```
According to this page, it looks like your ethernet adapter has been working with unbuntu since at least version 7.04.  You will probably want to get a wireless router with ethernet ports/switch and a CAT5 (or CAT6, depending upon price) cable for that computer you ran those commands on, and you can just cable that computer to a wireless router and won't need anything else (as in PCI WiFi cards, etc.).

[http://hardware4linux.info/component/17100/](http://hardware4linux.info/component/17100/)

---

### Post by teward on 2009-12-06
I'm a little confused here, so correct me if I'm wrong.

You're trying to link one of your computers to the Internet, and broadcast wireless from said computer for your home to use it.  Am I following you?

If this is what you're trying to do, I'm going to say don't bother.  I, being a registered tech, recommend that you just go out and get a router, hook that up to the modem.  You can get a basic one (Wireless G) for around $75 (US).

---

### Post by northd_tech on 2009-12-06
> **smandoli said:**
> ```

  *-network:1 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:15:f2:27:a2:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:23 ioport:a000(size=256) memory:fa800000-fa8000ff


```
I'm guessing that this VIA Rhine-II network interface must be an on-motherboard thing.  The other one is probably a PCI card, and I've usually had better luck with the PCI flavor (faster, more reliable, better compatibility, etc.).  It doesn't look like you need to enable that VIA ethernet adapter (but you might see slightly better speed if you had 2 cables running to an ethernet switch).  Probably not worth messing with though- your ADMtech or whatever looks to be working fine.

If you needed to enable the VIA ethernet for some reason, it looks to be fairly well supported under ubuntu according to these pages:

[http://hardware4linux.info/component/4839/](http://hardware4linux.info/component/4839/)

[http://hardware4linux.info/module/via-rhine/](http://hardware4linux.info/module/via-rhine/)

Edit:  Looks like that VIA Rhine-II thing might be buggy- I wouldn't mess around with that one under ubuntu if I were you:

[https://bugs.launchpad.net/ubuntu/+bug/281491](https://bugs.launchpad.net/ubuntu/+bug/281491)

---

### Post by smandoli on 2009-12-06
Thank you for the input, guys.  So much for my 'sandbox' insouciance -- I ended up having to reinstall.  I have no money for hardware.  And right now I won't be able to follow the links you have kindly provided.  

I did learn some good information on this effort, but for now I am going to give up on pursuing this goal.

---

