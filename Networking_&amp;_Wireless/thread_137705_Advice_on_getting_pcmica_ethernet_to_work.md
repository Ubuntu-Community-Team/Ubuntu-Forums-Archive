---
title: "Advice on getting pcmica ethernet to work"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by copperwave on 2006-02-28
[COLOR="Navy"]I had been struggling with this for ages but couldn't believe I could not crack it. The scenario is detailed elsewhere suffice to say a pcmcia ethernet card - in my case a 3Com575BT (using the 3C59x Vortex driver by default) would work in DSL Linux, FreeBSD, Ubuntu Live CD's and during the install process. The problem was, once installed with either Hoary or Breezy, networking just wouldn't come up. The two led's on the cable adaptor would flash briefly as the system booted but in terms of finding my DHCP server, (which it did do during install) nada. 

So, hard coding ifconfig eth0 didn't work either nor any amount of acpi= or pci= settings on the kernel would work. Since I know it works in XP and other versions of Linux there had to be something funky going on. 

Turns out setting: 

#mii-tool -F 100baseTx-HD 

did the trick. There might be more elegent ways of doing this - and I'd be interested to know, but popping this statement into #/etc/rc6.d/S35networking (so it happens at boot time) works a treat. Your mileage may vary but it is worth experimenting to find what yours will support.

For what ever reason under Ubuntu (install) this driver won't work in full-duplex but forcing it too half-duplex works fine. I imagine there is going to a small performance hit but too be honest now I have this working and understood I'm rocking and rolling. \\:D/ 

Later
//copperwave[/COLOR]

---

