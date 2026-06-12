---
title: "Wireless right off the bat?"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by IanA on 2006-01-15
I want to buy a notebook to use with Ubuntu, and it might or might not have integrated wireless. What integrated wireless cards work with minimal effort (if any), or PCMCIA cards work w/ minimal effort? I am not a Linux Guru, nor am I good at it, I'm just tiring of paying for an operating system, and Ubuntu had a nice GUI and works on x86 or PPC, since I have PCs and Macs. 

Thanks in advance,
Ian A.

---

### Post by duke_nukem_time on 2006-01-15
Try this link:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

scroll down till you see the list.

---

### Post by mohapi on 2006-01-16
I've been on both sides of that stick.

The Intel PRO/Wireless 2200BG in my XPS M170 connected with (almost) no effort on my part. Setup was easier than in Windows.

On the other hand, I have a Linksys WPC54G version 2 in my old laptop, and it has proven impossible. 

So there are two suggestions: One that will work, and won't that absolutely won't.

---

### Post by jweila01 on 2006-01-16
Dell 700m worked on Breazy "out-of-the-box." Selected wireless as the primary network interface during Breezy install.

---

### Post by Lambert on 2006-01-16
Do your homework and take your time is the best advice I can give.

Here is a link to the wiki. It's laptops that have been tested and documented.
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

I suggest taking a live cd with you and see if the store will let you boot into ubuntu. Bring up your pci devices with this command

lspci -v

to see what chipset is in the wireless device. They are not documented well up front so this way you know exactly what you're getting. The live cd will also give you a general idea of any other problems you might have or how well ubuntu will work. 

Here is a link to minipci devices and their general linux support.
[http://linux-wless.passys.nl/query_hostif.php?hostif=mini-PCI&zoek=hostif](http://linux-wless.passys.nl/query_hostif.php?hostif=mini-PCI&zoek=hostif)

Anything centrino will have a intel 2200bg chip in it which is supported well with the ipw2200 driver
Anything atheros should be good.

---

### Post by IanA on 2006-01-16
Thanks guys. I'll just look for a cheap used Centrino Laptop.

Ian A.

---

