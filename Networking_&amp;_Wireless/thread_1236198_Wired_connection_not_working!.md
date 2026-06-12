---
title: "Wired connection not working!"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by jrsc109 on 2009-08-10
Hi all

Could really do with your help on this one.

I have 2 PCs, both wired.  Both running 9.04.
1 x PC connects without issue

The 2nd PC can see the router, no problem (and it appears as an attached device on the router), but it will not connect to the internet.

I've run lspci, and that shows the controller (but it must be there if it can see the router!).

Can someone please shed some light on this - my children are going nuts without their access!!!

Many thanks

---

### Post by zkriesse on 2009-08-10
it might have had an issue with installing a driver...did you try shutting the router system down? maybe switching cables?

---

### Post by zkriesse on 2009-08-10
OR!!!!!!!do you have a wireless card?

---

### Post by jrsc109 on 2009-08-10
The card is not wireless, and I know there is no issue with the cable, as I can see (and even administer) the router.  I have re-booted the router, just in case, but that made no difference.

Strange that I can get as far as the router and no further.  The other PC, connected to the same router (also on 9.04) is fine.

Any other suggestions gratefully received.

---

### Post by jrsc109 on 2009-08-10
I am really confused.  I've run **lshw -C network** and the output shows a working network card.
Since I can see the router, I am in no doubt that the network card works fine (it was fine before I upgraded to 9.04!)
Therefore, don't believe this to be a driver issue.
Please, someone, offer some comforting words of advice - otherwise, my children are going to have me for breakfast!!

---

### Post by AmerNewbieInDE on 2009-08-10
you say you can admin the router from the pc, but can not get to the internet? and this is a wired connection..  i would have to thihk the block is on the router... is it using dhcp? since it is wired, tri to connect the pc direct to the modem and see if it goes then. if it does, definate the router.

---

### Post by Iowan on 2009-08-10
If one works and one doesn't, you have an excellent opportunity to compare/contrast.  Verify IP addresses, compare /etc/resolv.conf (maybe even backup existing, and copy from working to non-working), check firewall settings...

---

### Post by jrsc109 on 2009-08-11
I am thinking that because the working PC is a dual-boot with XP, this is why it's still working.

There appears to be a problem with 9.04 connecting, since I've now read a number of posts by people with the same problem.

Will continue to work to resolve this, but I think someone needs to take a good look at this issue and possibly release a software fix to put this to bed.

Oh, the frustration - why do we do it!!!

---

### Post by jrsc109 on 2009-08-12
FIXED - Used sudo dhclient and all is well. Finally..:)

---

### Post by Iowan on 2009-08-12
Hope it *stays* fixed after next reboot/restart.

---

