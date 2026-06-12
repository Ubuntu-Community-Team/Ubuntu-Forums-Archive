---
title: "EXPERTS - WEIRD dual head /  monitor question"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by mrmcd on 2006-06-13
Ok, so I just spent a lot of money on 2 x 19" flat panels and don't have much moeny left for a video card with dual DVI.

Can anyone please tell me if its even **POSSIBLE** to do a dual head monitor setup (one X session across both monitors, not two X sessions or cloned) with any of the following:

- use 2 PCI video cards (of same make/model) and run one monitor off of each
- Run 1 monitor from an AGP video card and the other monitor from a PCI video card (video cards would be same make and closest models).

I have gotten dual monitors working with a single ATI or NVIDIA card in the past (somewhat) easily, but this is not my area of expertise.  I just want to know if such things are even possible or if I should start saving money for a $100, dual DVI ouput card.

---

### Post by myk.dinis on 2007-07-26
Absolutely...You need to declare two sections in your xorg.conf, 1 for 1 card/Monitor/Screen<Combo of card and monitor> and another for the other set of hardware...Just look at the single config...and copy it below the first one changing default monitor or default screen to things that make sense...screen0 and screen1 monitor0 and monitor1 and of course if the cards are the same you have to be specific about which card also...

Like where it says Identifier "Default Screen"  <--- Change it for each setup...(monitor, card, screen)

After you've successfully done all that you need to change your server layout to look something like this:

Section "ServerLayout"
	Identifier	"Default Layout"
  Screen 0 "Default Screen" 0 0
  Screen 1 "Screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

And then either use xinerama like so:

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

That'll give you what you need...if you need more help reply back to this thread and I'll see what else I can help you with...

BTW...  Resize and Rotate (xrandr, grandr, etc...) do not work with xinerama...so you have to know exactly which resolution you want...and if you ever have to change it you'll have to edit the xorg.conf...

You posted to the expert group so I assume you know what xorg.conf is but if you don't you'l have to find it in /etc/X11
Case sensitive BTW...

And to edit it you'll need to type something like "sudo gedit /etc/X11/xorg.conf"  from a terminal/console...

While in X of course...

I hope this helps...

cheers!

---

### Post by MrHippocampus on 2007-07-26
> 
Can anyone please tell me if its even POSSIBLE to do a dual head monitor setup (one X session across both monitors, not two X sessions or cloned) with any of the following:


You think thats not possible? Try having two totally separate computers and having one X-session spanning across two screens each connected to different computers :D (Yes, it is possible)

---

