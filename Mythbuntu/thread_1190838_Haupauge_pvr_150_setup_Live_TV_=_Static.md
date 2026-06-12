---
title: "Haupauge pvr 150 setup? Live TV = Static"
date: 2009-06-18
forum: Mythbuntu
---

### Post by RonPDX on 2009-06-18
Good morning everyone, 

I recently came across a Haupauge PVR-150 that I decided to stick in along side my Pinnacle HDTV 800. The problem I am having is getting only static on all channels with Live TV. 

In the backend the card is recognized and is setup under Capture Card. I have also scanned for channels (my channels are picked up) and filled the database. 

I am understanding that the drivers for this card are part of kernal so I am thinking that I do not have to install them, is this correct?

Is there any additional settings that I have to do for the pvr 150?


Thanks in advance, 

Ron

---

### Post by ian dobson on 2009-06-18
Hi,

Can you record an program then play it back, do you then have static? 
You've setup the card as a MPEG decoder right and not as a V4L card.

What do you see in your mythtv backend log:-
/var/log/mythbackend.log.

I have a problem with the drivers/firmare for by PVR500 (Dual PVR150) and ended up installing the bleeding edge drivers from the ivtv web site.

Regards
Ian Dobson

---

### Post by xinix on 2009-06-18
It could be something as simple as making sure the cable is plugged into the right jack (the second from the top).  I say this because the pvr-150 has worked out of the box for me for a while now, that and I've made the mistake of not paying attention to where I plug things in and then scratch my head for a while.

---

### Post by RonPDX on 2009-06-19
Ian & Xinix, 

Thank you both for you help. The problem was solved after selecting the IPTV Tweaks from the Control Panel. 

Ron

p.s. someone please kick me in the butt next time I buy a Pinnacle vs. Haupauage. The Haupauge has a better picture quality and performance.

---

