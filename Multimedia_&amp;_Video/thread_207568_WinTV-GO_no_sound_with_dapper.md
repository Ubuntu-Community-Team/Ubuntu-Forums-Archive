---
title: "WinTV-GO no sound with dapper?"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by ubtpenguin on 2006-07-02
I found couple of threads about no sound issue with TV capture card.

well

I used this command using mplayer

mplayer tv:// -tv driver=v4l:width=640:height=320:\
outfmt=i420:norm=ntsc:alsa

well it will give you warning like this

 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.

and

Audio: no sound

but this gives me a sound

my card is using bt878 chipset.

I think something is wrong with v4l2 and alsa.

Any Ideas?

---

### Post by mackinax on 2006-07-02
1) did you try driver=**v4l2** ?

2) *''Audio: no sound / but this gives me a sound''*

what do you mean?

. . . . . . . . . .

b-t-w,
I have this card also. TVtime works well, and is easy to install + configure.

---

### Post by ubtpenguin on 2006-07-02
NO

If I used v4l2 driver it will not give me a sound

And further more

for both v4l and v4l2 driver will show me 

Audio: no sound <== this is one of mplayer messages after I run it in terminal.

But v4l driver gives me sound and v4l2 doesn't

---

### Post by El_Matthews on 2006-08-28
Anybody news on this ?

I have the same problem with driver v4l I got sound with v4l2 I don't get any sound.

---

