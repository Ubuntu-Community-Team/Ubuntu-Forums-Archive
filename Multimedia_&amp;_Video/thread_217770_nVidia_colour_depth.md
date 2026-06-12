---
title: "nVidia colour depth?"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by martinielsen on 2006-07-17
I wonder why the max colour depth in the nvidia driver in Linux is 24 bit ("DefaultDepth 24") and not 32 bit. I'm used to run 32 bit in Windows XP. How come? Is it because the 32 bit in Windows is not "real" 32 bit?

Best regards
Martin

---

### Post by mgor on 2006-07-17
yes, that's true. the "last" 8 channels in windows are alpha channels, if i'm not misstaking.

---

### Post by tseliot on 2006-07-17
> 32-bit color

"32-bit color" is a misnomer when regarding display color depth. A common misconception is that 32-bit color produces 4,294,967,296 distinct colors.

In reality, 32-bit color actually refers to 24-bit color (Truecolor) with an additional 8 bits either as empty padding space or to represent an alpha channel. Considering red, green, and blue use the same amount of bits for their respective color (with the exception of 16-bit color), the total bits used will be a multiple of 3: like 15-bit color (5 bits each) and 24-bit color (8 bits each). The reason for using empty space is that all but the newest modern computers process data internally in units of 32 bits; as such, using this amount for each pixel can allow optimizations.

Quoted from Wikipedia:
[http://en.wikipedia.org/wiki/Color_depth](http://en.wikipedia.org/wiki/Color_depth)

---

### Post by martinielsen on 2006-07-17
Thanks - that was a quick answer! I don't know anything about "alpha channels" though :-D

---

### Post by martinielsen on 2006-07-17
Ups! Thanks for the new reply and the explanation.

---

### Post by whatever on 2006-07-17
the alphachannel describes "how transparent" something is.
on your desktop it does not matter at all, as your monitor can only display colors, but no transparency :). so the output of your graphics card never contains more than 24bit color information - neither under linux nor under windows.

however, as 32 is a power of two, your graphics card usually calculates the 24bit image with 32bit data, where the additional 8 bits don't matter for the resulting image when doing 2d graphics. it needs more memory than 24bit calculation, but calculations can be done faster.
when calculating 3d scenes, the additional 8bits are used for alpha information which is needed for blending transparent textures etc.. the resulting output is again "only" 24bit.

summary: in windows you choose how the graphics is calculated, in linux you choose the result you want :)

---

### Post by martinielsen on 2006-07-17
Ah OK - so let's say that i want to play 3D games in Ubuntu (not that i plan to do that before i can get Oblivion for Linux :) ) will it then be slower calculated in Linux or is the "extra" 8 bits still supported and used?

Do you know any good 3D games for Linux for testing purposes? (sorry if this question is not relevant here)

Martin

---

### Post by jejones3141 on 2006-09-19
OK...if the maximum Depth value is 24, does that mean that X.Org can't do translucency?

---

### Post by kabalas on 2006-11-08
> **whatever said:**
> the alphachannel describes "how transparent" something is.
on your desktop it does not matter at all, as your monitor can only display colors, but no transparency :). so the output of your graphics card never contains more than 24bit color information - neither under linux nor under windows.

however, as 32 is a power of two, your graphics card usually calculates the 24bit image with 32bit data, where the additional 8 bits don't matter for the resulting image when doing 2d graphics. it needs more memory than 24bit calculation, but calculations can be done faster.
when calculating 3d scenes, the additional 8bits are used for alpha information which is needed for blending transparent textures etc.. the resulting output is again "only" 24bit.

summary: in windows you choose how the graphics is calculated, in linux you choose the result you want :)
You can look at Loki Games, they've created some Linux executables for some games, i'm still testing this, however.

---

