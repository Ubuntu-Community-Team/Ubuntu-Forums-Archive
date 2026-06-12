---
title: "ubuntu dapper drake sound nigthmare"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by mjurce on 2006-06-26
I installed a new ubuntu dapper drake,  horrible nigthmare with sound, via 8235 chipset.

Ubuntu randomly decides when sounds will work e and when will not.

I read threads about sound troubles, but no way to make it working.
](*,)

---

### Post by LordRaiden on 2006-06-26
I have the same chipset and I know what you are talking about. I got my sound working by plugging my speakers into my headset adapter at the front. 

First of all, try doing what I did unless you have ready done it.

If that does not work, go into a shell (konsole/gnome terminal/xterm) and type
```
alsamixer
```

Fiddle with some of the settings there, (M is mute/unmute, left and right keys navigate left and right, up and down keys control volume).

If alsamixer gives you an error, you probably have a deeper problem, (I can help you with it but I'll need a little time).

---

### Post by mjurce on 2006-06-29
I switched back to ubuntu breezy

---

### Post by MrDelmo on 2006-06-29
I also have the 8235 chipset, and no sound at all. I opened alsamixer in the terminal but none of the values will change.

---

### Post by gratefulfrog on 2006-06-29
try rebooting, and be sure that no sound using devices are running, then start alsamixer in a terminal and play with the settings.  first try to get sound to play, then input on the mic with the sound recorder - mic should be set to "capture"...

If you have other sound using devices running they may take over the control of the mixer settings.

Don't panic, it's rough going but once you've done it, it'll be forgotten!

Cheers,
GF.
[http://gratefulfrog.net]("http://gratefulfrog.net")

---

### Post by MrDelmo on 2006-06-29
I got the bars to move but the sound still doesn't work. I was searching the forum and someone suggested running "sudo modprobe snd-" in the terminal, which I tried and I got the message. 

> FATAL: Module snd_ not found.  which I know can't be a good sign.

---

### Post by MrDelmo on 2006-06-30
Well after playing with various commands somehow I got my sound to work. I guess maybe it was just muted. Thank you all for your help.

---

### Post by gratefulfrog on 2006-07-02
Great! I remember how I felt when I got mine to work at first, too!
Cheers,
GF.

---

