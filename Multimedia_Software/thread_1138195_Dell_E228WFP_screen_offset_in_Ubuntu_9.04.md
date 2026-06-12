---
title: "Dell E228WFP screen offset in Ubuntu 9.04"
date: 2009-04-26
forum: Multimedia Software
---

### Post by teohhanhui on 2009-04-26
In Ubuntu 9.04, the display is offset a little to the right on my Dell E228WFP monitor using VGA input. My graphics card is ATI Radeon X550 (no proprietary driver available). It can be corrected using the monitor's "Auto Adjust" function but having to do that every time I switch between Ubuntu and Windows is a nuisance. Is this a bug and if so how do I report it correctly?

---

### Post by goodjonx on 2009-04-26
I have that too with an ATI ax600. I had it with 8.10 too, but there I could just use the proprietary drivers, now that those dropped support for older (?!) cards, I have not been able to resolve this problem.

- 'legacy' drivers by ATI .. couldn't get them installed..

- adjusting the modeline in my xorg.conf .. ignored

This bug has been around for ages and affects many video cards, I don't get why it hasn't been fixed by now. It's just annoying and makes any linux distro look like a beta of a real OS..

Anyway, maybe it will work for you, do a search for 'xorg.conf xvidtune modeline' ..

---

### Post by teohhanhui on 2009-04-26
I've tried that earlier with no luck. I agree that they should treat RELEASES more seriously. It is not a massive public beta. Obvious bugs like this should have been fixed even if they're at the upstream.

---

### Post by goodjonx on 2009-04-27
So, does anyone know how to adjust resolution and offset settings for the open drivers (modeline etc..)? xorg.conf is deprecated, I gathered, how is it done nowadays?

---

### Post by gsilver352 on 2009-07-29
I would like to know the same...currently looking for a tool or something to adjust the Offset on my screen, and force a slightly lower resolution. I see in the Nvidia Server program through advanced you can pick resolutions and if you look in metamode it looks like it shows resolution and offset selections, but they always show 0+0.  "Im still looking"

---

### Post by ModusOperandi on 2009-08-01
Thirding this problem. The proprietary ATI drivers had the same values for whatever setting it is on Linux as on Windows, meaning no shifting, but with the discontinuation of support of many cards--including mine--by newer driver versions, I can only use the open-source ones which have a different setting. It is annoying to have to press the auto-adjust setting on my monitor every time I boot between Ubuntu and Windows.

---

### Post by uber_n00ber on 2009-09-16
Four-thing (?) this problem. I'm also looking for a solution.

---

### Post by uber_n00ber on 2009-09-16
FWIW, I think this bug report is related:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/262857](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/262857)

---

### Post by uber_n00ber on 2009-09-17
Actually, sorry to everyone here, but I think I jacked this thread. My video card is a Geforce4 Ti 4200 (not ATI) and I was using the default nv drivers which showed up as a display offset annoyance like described above.

Not that this helps the people in this thread, but if other people in my situation stumble across this thread, my fix was turning on the restricted drives via System > Administration > Hardware Drivers. I'm not sure if that will help you ATI users but HTH.

---

