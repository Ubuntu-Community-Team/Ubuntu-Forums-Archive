---
title: "Wake on lan (WOL) not working with ASUS M2NPV-VM"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Virtual DarKness on 2009-04-27
Hello,
I've a pc with an ASUS M2NPV-VM motherboard and if I set up wake up by PCI on the bios settings (that includes the NV LAN integrated network card/chipset) and then I save the bios and just shutdown the computer I can turn it on sending a magic packet using the wakeonlan command from another pc.. so my network configuration is ok.

But then if I start ubuntu (9.04) and I shutdown the pc, I can't turn it on again sending the magick packet..

Not that I do use ethtool to activate wol.. in fact if I type:

```
sudo ethtool eth0
```

I get:
```
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
[B]        Supports Wake-on: g
        Wake-on: g[/B]
        Link detected: yes

```

At this point, theorically, shutting down the computer using the halt command should be ok and sending the magick packet the computer should turn on as expected. but it doesn't :confused:

any suggestion?

thanks.

bye,
Giovanni.

p.s.
I've read [here]("http://blog.thedebianuser.org/?p=162") a post of a user that was able of doing it using the same motherboard I have and doing exaclty the things I did.. so wonder why it doesn't works for me..

also the lights near the network plug are on also when the pc is turned on.

---

### Post by Virtual DarKness on 2009-04-27
Ok.. solved the problem:

[http://www.nvnews.net/vbulletin/showthread.php?t=70384](http://www.nvnews.net/vbulletin/showthread.php?t=70384)

> long story short, at linux close forcedeth 0.56 (and unknown number of versions
earlier) wrote the MAC back to the device in the reverse order. So 01:02:03:04:05
became 05:04:03:02:01. The nforce4 board will WOL if the magic packet is sent
to the reversed MAC instead of the correct MAC, assuming that

ethtool -s eth0 wol g

has been issued before poweroff. [I]The forcedeth driver is being modified to fix this
problem[/I]. In the meantime, if you have an older version of forcedeth and WOL isn't
working **try sending the magic packet to the reversed MAC**.

the post is dated 2006.. so the driver seems to still have that bug ](*,)


Thanks a lot to mathog for providing a workaround to this ;)

bye,
Giovanni.

---

### Post by James79 on 2009-04-28
Wow, thanks for posting that! I have the exact same issue with the exact same motherboard.

This has always worked flawlessly from 7.04 to 8.10, only Jaunty has an issue for me. I'm wondering why a bug from 2006 has suddenly resurfaced?

I'll have to wait until I get home to test this, but it sounds like I'll be able to get it working at least which is good news.

---

### Post by James79 on 2009-04-30
I just wanted to follow up and confirm that this does indeed work.

It me took a while to get it to work, until I figured out what exactly they meant by "reverse". It's not litterally reversed, the pairs remain together. Example:

AB:CD:EF:GH:IJ:KL

would become:

KL:IJ:GH:EF:CD:AB

I'm still wondering how this regression/bug got into the forcedeth drivers. Hopefully a fix a forthcoming.

---

