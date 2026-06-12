---
title: "Wireless card sees networks but does not connect"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by bleriot13 on 2011-02-28
Hi

I'm really new to LUbuntu. In fact, I installed it yesterday (10.10)  in my old Toshiba Portégé 4000.

I have to say that everything works as a charm but the wireless connection.

As soon as I boot, I get a message saying that there are available networks. I choose mine, give the connection password and then wait... until the password box is reissued because of (I guess) a connection failure. No matter how many times I try, I get the same results. In fact (besides the connection password) this behaviour is the same if I try to connect to a neighbour's open network (no harm intended! Only experimenting the wireless capabilities!).

I have been able to connect seamlessly to my router using other Linux-based operating systems (as, for instance, Puppy Linux 4.31) and this very same laptop, so I guess that the problem lies not in the wireless adapter but in the software included in Lubuntu.

I also connect to my router using the regular Ubuntu 10.10 in a much modern laptop.

I have NO information about the specific wireless adaptor. I've been searching the internet for the specifications for a Toshiba Portégé 4000 and the only information I have obtained is that it is a "Toshiba wireless minicard".

When I used Puppy 4.31, the driver loaded was something called "orinoco_cs", valid for PCMCIA cards. It also stated something about "Lucent Technologies". Sorry, but I have no more information.

Could you lend me a hand? This is the only remaining thing blocking the way to a revamped, rugged and faithful laptop on the road again.

Thank you very much!

Bleriot.

---

### Post by sanderj on 2011-02-28
You can try these things:

- System -> Administration -> Additional Drivers: are there any drivers installable? (Make sure you're connected to Internet with a wire/cable). If so, install them, reboot, and try again.

- run "lspci" from the command line, and post the output here

- run 10.04 from Live CD and see if you can connect 

- turn off WEP/WPA on the Wifi Access Point temoparily, and check if you can connect. If so, it's a 10.10 bug.

---

### Post by bleriot13 on 2011-02-28
Sanderj,

thank you for your quick reply. I will try your suggestions later; now I'm at work and the laptop is at home.

Just one question. In your list of tests, the third one says that I should try the 10.**04** live cd. Do you really mean 10.**04**? Or you wanted to say "10.**10**"?

Depending on your answer I will download lubuntu 10.04 or not...

Thanks again!

Bleriot

---

### Post by sanderj on 2011-02-28
> **bleriot13 said:**
> Sanderj,

thank you for your quick reply. I will try your suggestions later; now I'm at work and the laptop is at home.

Just one question. In your list of tests, the third one says that I should try the 10.**04** live cd. Do you really mean 10.**04**? Or you wanted to say "10.**10**"?

Depending on your answer I will download lubuntu 10.04 or not...

Thanks again!

Bleriot

I really mean 10.04. I've seen wifi-card that work in 10.04, but not in 10.10. Strangely enough ...

You can download 10.04.2 here: [http://ftp.belnet.be/packages/ubuntu/releases/10.04/ubuntu-10.04.2-desktop-i386.iso](http://ftp.belnet.be/packages/ubuntu/releases/10.04/ubuntu-10.04.2-desktop-i386.iso) (direct link).

---

### Post by sofiamarcella on 2011-02-28
sometime problem with usb hardware or power supply...[IMG]http://freeimagestocks.com/content/5/dot.png[/IMG].....

---

### Post by bleriot13 on 2011-02-28
Thanks again for your speed!

> **sanderj said:**
> I really mean 10.04. I've seen wifi-card that work in 10.04, but not in 10.10. Strangely enough ...

You can download 10.04.2 here: [http://ftp.belnet.be/packages/ubuntu/releases/10.04/ubuntu-10.04.2-desktop-i386.iso](http://ftp.belnet.be/packages/ubuntu/releases/10.04/ubuntu-10.04.2-desktop-i386.iso) (direct link).

The link you posted is for **UBUNTU**, not for **L**ubuntu, the distribution I have installed (it is a really ANCIENT laptop, so I have to use these light distributions). I guess that you didn't notice that I was using this distribution...

Do your former recommendations still apply?

Bleriot.

---

### Post by sanderj on 2011-02-28
> **bleriot13 said:**
> Thanks again for your speed!



The link you posted is for **UBUNTU**, not for **L**ubuntu, the distribution I have installed (it is a really ANCIENT laptop, so I have to use these light distributions). I guess that you didn't notice that I was using this distribution...

Do your former recommendations still apply?

Bleriot.

Yes, they sill apply. Use your own Lubuntu 10.04 link.

BTW: how much RAM has your protege? Is it very low ... something 256 MB or so?

---

### Post by bleriot13 on 2011-02-28
> **sanderj said:**
> BTW: how much RAM has your protege? Is it very low ... something 256 MB or so?

The total amount of RAM is 368 Mb. The processor is a Pentium III @ 750MHz (Coppermine).

It runs Lubuntu 10.0 quite fluently. It even reproduces video @ 720 x 400 pixels without skips. Lubuntu really did a good work on this laptop. Last week it sported a Windows SP3 OS and sluggish was a rather mild way to describe how it behaved. Now it is completely useable. A pity the wireless does not work...

Thanks again.

---

### Post by bleriot13 on 2011-03-01
Sanderj,

I tried everything you suggested. No success.

First, the only additional driver available was a software modem. I installed it, just in case... but no luck.

I tried live-booting with the 10.04 CD. This was still worse. If 10.10 showed, at least, the list of available wifi networks, 10.04 couldn't even find the wireless card.

Again back to 10.10, the connection to my router in open mode failed too.

So I post the output of the command lspci as well as for the command sudo lshw -C network (I found this command in another thread).

lspci

```

00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

```sudo lshw -C network

```

  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 08
       serial: 00:00:39:b4:81:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:f7efe000-f7efefff ioport:eec0(size=64) memory:f7d00000-f7dfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:33:59:82
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.35-25-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

```Thanks again.

Bleriot

---

### Post by sanderj on 2011-03-01
I should have read your first post better: you have probably have a pcmcia card, so "lspcmcia" would be more useful. Can you do that?

And run "ifconfig" too.

As the same hardware (computer + router) does work with another Linux, it can't be a network-type (b versus g) nor WEP/WPA problem.

I only can find this: [http://ubuntuforums.org/showthread.php?t=1617549](http://ubuntuforums.org/showthread.php?t=1617549) . Maybe worth a try?

---

### Post by bleriot13 on 2011-03-01
> **sanderj said:**
> 
I only can find this: [http://ubuntuforums.org/showthread.php?t=1617549](http://ubuntuforums.org/showthread.php?t=1617549) . Maybe worth a try?

Of course I'll try it! This afternoon, however. This means that I won't be back to the forum till tomorrow...

Thanks alot.

Bleriot.

---

### Post by whiskers751 on 2012-03-23
Same problem here!

---

### Post by bleriot13 on 2012-03-23
Whiskers751

> **whiskers751 said:**
> Same problem here!

The solution indicated 2 posts up worked for me. I simply forgot to report that one year ago. I hope it works also for you.

Bleriot13

---

### Post by Elfy on 2012-03-23
Old thread closed.

---

