---
title: "TV-out on a Zepto znote 6024W"
date: 2008-07-30
forum: Multimedia Software
---

### Post by jonwestin on 2008-07-30
Hi. Im trying to get the tv out to work on my laptop with Hardy but no luck so far. 

lspic:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

and xorg.conf:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

My graphic card is an Intel x3100 on a 965GM chipset.  

I have no idea what to add and where.. Any help is appreciated. Thanks
/Jon

---

### Post by Tavathlon on 2008-08-15
I'm not sure about how to do it with an integrated graphics card, but a hint for other Zepto users who have bought their models with nvidia cards is this guide: [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

The thread is old, but it apparently still works - I just set up my computer according to it, and it works perfectly. However, I had to change one thing about the hardware: My TV-out is s-video, so of course that is what I used, and plugged it into a scart adapter. I only got greyscale this way, no colors however I tweaked around in xorg.conf. Finally, a friend told me that it would work if I put an adapter from s-video to composite between the cable and the scart, and it actually did work out when I tried that. This is apparently the case also in windows, since my friend is a win-user.

So sorry Jon, I can't really help you. But I figured that other Zepto users might find your thread...

---

### Post by jonwestin on 2008-08-23
Ah thanks anyways mate, added you on msn for some Zepto/Ubuntu talk :)

Anyone else? Pliiiz?

---

### Post by jonwestin on 2008-08-27
A little bump, really wanna get this working. I have a picture on the TV when the login page is loading but it disappears when Gnome loads.

---

