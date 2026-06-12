---
title: "tv-out resolution issue"
date: 2005-10-30
forum: Multimedia &amp; Video
---

### Post by chusome on 2005-10-30
I've just installed breezy and its working great (excellent linux distro) but I'm having trouble with tv-out. My TV does have some mirrored display but its all blurred likely due to a refresh rate/resolution issue. I've changed my xorg.conf (which is attached) but haven't seen any results.  I have an ATI Radeon 7000. I'm hoping someone can tell me what's wrong with my xorg.conf:confused: 


P.S. Someone else on this forum has posted a similar issue but mine is slightly different. Apologies to those who disagree with me.

---

### Post by Joh_ on 2005-10-31
You seem to have set the same BusID on both devices. Sure it's not supposed to be **BusID "PCI:1:0:0"** on the first and **BusID "PCI:1:0:1"** on the second?

---

### Post by chusome on 2005-10-31
Tried that and got the same results.:( 

When I started this I used the claimed working config from the following forum as a reference.
[http://ubuntuforums.org/showthread.php?t=84039&highlight=tv](http://ubuntuforums.org/showthread.php?t=84039&highlight=tv)

---

### Post by Kadafi on 2005-10-31
[QUOTE=chusome]Tried that and got the same results.:( 

When I started this I used the claimed working config from the following forum as a reference.
[http://ubuntuforums.org/showthread.php?t=84039&highlight=tv](http://ubuntuforums.org/showthread.php?t=84039&highlight=tv)[/QUOTE]

Isn't that one for NVIDIA? Same? I dunno...

Anyway I had the same problem last week - installed fglrx drivers and dependants, ran fglrxconfig (all as instructed in How-To's here), then added the line:

Option "ForceMonitors"  "tv"

to xorg.conf and it worked...no messing around with refresh rates & modelines. Might not be what you're looking for, but it worked for me.

---

### Post by chusome on 2005-10-31
Unfortunately I can't use this solution either. This driver is only compatible with the 8500 series and up according to ATI

---

### Post by Kadafi on 2005-11-01
Ah...sorry man, not sure - I had a bitch of a time trying to get any kind of TV out working with the "ati" drivers on my card. Hope you have more luck than I did ;)

---

### Post by chusome on 2005-11-06
Well after much searching around the only resoltuion I could find was as follows:

[FONT="Arial"]Here is what I do to get output on my TV with a Radeon 7000. Note: the tv is the only screen attached to the card.
I turn the pc on with the PC already connected to the card, I use a plain text console (no vesa, no fb), and then I have configured Xorg to use the vesa driver at 800x600.
Everything works fine. mplayer and xine also allow you to get accelerated video playing without xv by using something called vidix and the radeon backend scaler.

The box is a plain Ubuntu Hoary with Freevo installed by hand and I use it for DVD, DivX, OGG/MP3, Internet Radio and Photo viewing.[/FONT]

This is ok, but not quite what I'm looking for. Guess us radeon 7000 users are running low on support for new software....

---

