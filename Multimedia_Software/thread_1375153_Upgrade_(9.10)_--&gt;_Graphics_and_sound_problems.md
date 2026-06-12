---
title: "Upgrade (9.10) --&gt; Graphics and sound problems"
date: 2010-01-07
forum: Multimedia Software
---

### Post by blade_ on 2010-01-07
Lo!

Wanted to try out 9.10 on my laptop. Followed the upgrading instructions and updated everything on 9.04 before moving on. 

Upon first inspection everything seemed fine, until I tried watching a movie on VLC. No sound. Altered alsa-base: added "options snd-hda-intel LG model=lg" (since I have an lg laptop) to the end, restarted alsa. Worked a beauty!

Today, one reboot later: my sound card is not working at all. Upon running 
```
sudo lshw -html
``` my html-file answered: 

```
id:	
display
description: 	VGA compatible controller
product: 	RV516 [Mobility Radeon X1350]
vendor: 	ATI Technologies Inc
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	pm pciexpress msi bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	f0000000-f7ffffff(prefetchable)
ioport	:	2000(size=256)
memory	:	fc000000-fc00ffff
memory	:	fc020000-fc03ffff(prefetchable)


id:	
multimedia
description: 	Audio device
product: 	82801G (ICH7 Family) High Definition Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	02
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	fc500000-fc503fff
```

for my graphics card and sound card. 

Removed my alsa-addition and tried to find drivers but have not suceeded. 


By far no expert on this, so please if you know how to fix, let me know!

Thanks

//Blade_


Add-on from prior post: 

I did check mixer and so on so that my sound was not muted in any channel, too. 
I have now patiently waited for the problem to be solved by the magic people making updates. And last weekend it DID! All of a sudden I could hook my lapotop up to a projector and actually see my mirrored screen. All of a sudden I had SOUND! I have since then only hibernated my beloved laptop. But, yesterday I rebooted it by accident of slow thinking and ran the updates...and everything went back to crap again. HELP!

---

