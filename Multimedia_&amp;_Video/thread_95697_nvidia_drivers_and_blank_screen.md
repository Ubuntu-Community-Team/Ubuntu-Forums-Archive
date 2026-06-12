---
title: "nvidia drivers and blank screen"
date: 2005-11-27
forum: Multimedia &amp; Video
---

### Post by tassoman on 2005-11-27
Hi all,
 nvidia drivers wouldn't work at any resolution.
Once i restart gdm screen blanks as any signal is sent.
Now I'm using X with VESA drivers but my screen refresh is about 60hz :(

Here you can find [Xorg.conf]("http://www.tassoman.com/xorg.conf") and [Xorg.0.log]("http://www.tassoman.com/Xorg.0.log").

I really dunno where is the problem. My screen is a crt Philips 202P4 who does 1600x1200x85 and more but its recognized as "Generic Monitor"

```
(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0
```

---

### Post by tseliot on 2005-11-27
Try this guide: [HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by tassoman on 2005-11-27
I've followed this tutorial, I've added Modeline row but it still the same.
I've also switched off the monitor and then on again but it said "no signal"

> Immagine/Display
Max :  2048 x 1536 a 80 Hz
Better :  1600 x 1200 a 85 Hz
Dot Rate video :  360 MHz
Freq H :  30 - 130 KHz
Freq V :  50 - 160 Hz
Better freq :  85 Hz


---

### Post by tassoman on 2005-11-28
[SIZE="7"]WOOA![/SIZE]

Solved...! I just detaching 2nd CRT cable -_-'

Now, i would re attach my lcd projector ... there's any 2ual head howto?

---

### Post by Teroedni on 2005-11-28
I found this to be very helpfull for dual head:)
[http://www.linux-magazine.com/issue/17/DualHead.pdf](http://www.linux-magazine.com/issue/17/DualHead.pdf)

---

