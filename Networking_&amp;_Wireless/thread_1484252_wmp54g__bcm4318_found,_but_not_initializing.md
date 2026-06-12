---
title: "wmp54g / bcm4318 found, but not initializing"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Bad.Andy on 2010-05-15
Hello all,

I hate to post what I'm sure is an exhausted topic but I've searched forums, google and gone through numerous guides without luck. I've been trying since Ubuntu 7 and am ashamed to admit that I've failed each time. I just installed 10.04 and am still feeling am no better off. (As if it matters, I've been using Ubuntu as a server and media center for years on another wired machine and feel very comfortable navigating and supporting it...)

I really really want to get this wifi card to work with Ubuntu.  I've seen it work with knoppix so I'm sure its possible.

My card is a PCI Linksys WMP54GS with the BCM4318 chipset. Here is precisely what I get from lspci:

```
badandy@baduntu:~$ lspci -vvnn | grep less
0c:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

This says it should work with ndiswrapper and even provides the exact drivers. I can load it up and it sees the hardware but still no network adapters...

Guides I recently failed with:
```
BCM43xx: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
```

Guides I've tried with previous versions of Ubuntu:
[INDENT]All. (Well probably not *all* but all I could find. At least a dozen or so.)[/INDENT]

Currently, I've got ndiswrapper* on it. The driver loaded and it detects the hardware. I've blacklisted the b43 kernel drivers.

ifconfig shows only the loopback adapter. iwconfig shows me nothing.

I find this error in my:

syslog
```
May 15 08:22:53 baduntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwl5a
May 15 08:22:53 baduntu kernel: [   19.360907] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwl5a; check system log for messages from 'loadndisdriver'
```

messages
```
[INDENT]May 15 08:22:53 baduntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwl5a
May 15 08:22:53 baduntu kernel: [   19.386275] usbcore: registered new interface driver ndiswrapper[/INDENT]
```

I don't have a cat5 cable long enough to cross my house to plug in to the network even temporarily however I do have this drive plugged in to VirtualBox (on Win7) bridged to my nic so I can access the Internet to update and download (tho of course it sees the different hardware config and definitely not the wifi card).

My apologies for whatever info I'm missing that will assist. Let me know what else I can post to possibly figure this out. I'm willing to pay for assistance in the form of beer, baked goods or positive vibes.

---

### Post by anotherrandomfellow on 2010-05-17
I have the same problem with the same wireless card! so frustrating!

---

### Post by Bad.Andy on 2010-05-20
Help! Help! 

We're stranded on Windows!

---

### Post by Bad.Andy on 2010-05-20
Nevermind. I got it.

The other random fellow might still be stranded tho. Here's my attempt at helping...

So revisiting previously used guides.... I found my answer here in the very first nw support sticky... yes I'm ashamed:
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

I noticed this which I hadn't seen elsewhere:
> 2. check machine architecture

An important caveat to ndiswrapper, and one that many tutorials fail to mention, is that the architecture of the Windows drivers that you use with ndiswrapper needs to match that of your Linux kernel--no exceptions. In other words, if you're running 64-bit Ubuntu, the Windows drivers that you use need to be built for 64-bit Windows

Of course, I'm running 64 bit and had been using a 32 bit driver.

I followed this link to ndiswrapper driver listings:
[http://www.burnthesorbonne.com/ndiswrapper/b.html](http://www.burnthesorbonne.com/ndiswrapper/b.html)

And used #: 85
> #
Card: Broadcom BCM4318 AirForce One 54g in HP Compaq nx6125 AMD Turion 64 notebook

    *
      Chipset: Broadcom BCM4318 802.11g Wireless LAN Controller (rev 02)
    *
      PCIID: 14e4:4318 (rev 02)
    *
      Driver: 64-bit driver extracted with cabextract from [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
    *
      System: 64-bit Arch Linux (running 2.6.22-ARCH #1 SMP PREEMPT kernel) with ndiswrapper 1.47

Extracted bcmwl5.inf and bcmwl564.sys it w/ 7zip. Removed the old driver, installed the new driver, rebooted in to Ubuntu and the wifi lit right up.

I've attached the files here for convenience. I hope this helps somebody some day.

---

### Post by nylanfs on 2010-05-21
I also had to blacklist b43-pci-bridge to get mine working.

---

