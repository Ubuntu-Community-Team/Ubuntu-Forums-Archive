---
title: "how to convert .vob files to .mpg or .avi??"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by billdotson on 2007-02-20
For 2 weeks until I get my replacement WinTV-PVR-150 I am using the DVD player/recorder that is hooked up to the TV to record my shows.

  I downloaded and installed acidrip and ripped it as an .avi  The video was in .avi but the sound was off from the video either a second behind or ahead I coudn't really tell.  How do I fix this issue?

Also now that I am trying to use acidrip again it isn't recognizing my DVD.

I also tried vob copy but that didn't even get the vob file at all and I also tried to get the vob files into K3B and burn them as an iso and then burn that to a disc and acidrip it but I couldn't find how to burn as an image

---

### Post by majoridiot on 2007-02-22
you can synch the audio using avidemux... 

on the left, below the audio section, check the "shift" box and adjust in milliseconds (+/-)

gnomebaker does a good job with dvd isos... under Tools-->Burn DVD image

---

### Post by rykel on 2008-04-28
Hi,

Is there any commandline program that can automatically convert a .vob file to .avi or .mpg?

Something like pdftk or cat (ie. 1-line to convert) would be great.

---

### Post by Monicker on 2008-04-28
> **rykel said:**
> Hi,

Is there any commandline program that can automatically convert a .vob file to .avi or .mpg?

Something like pdftk or cat (ie. 1-line to convert) would be great.


ffmpeg can convert from vob to mpg.

---

### Post by rykel on 2008-04-28
> **Monicker said:**
> ffmpeg can convert from vob to mpg.

thanks man.

i typed "ffmpeg" in a terminal and was overwhelmed by the options.

how do i convert a .vob to .mpg using ffmpeg?

thanks for helping.

---

### Post by Monicker on 2008-04-28
For a plain vanilla convert: ffmpeg -i some.vob -o new.mpg

I'm not sure what the defaults are.  Its been a while since I used it, though I know I did pass some arguments for bitrate and such.

---

### Post by rykel on 2008-04-28
Hi thanks,

That works, somewhat. But it is exactly what I am looking for, a one-liner that does the conversion.

Unfortunately, my resulting .mpg file played like a slow motion movie with no sound. So I guess I still need to find out how to convert it properly with sound.

Thank you!!

---

### Post by dchurch24 on 2008-07-16
Did you get anywhere with this?

I was experimenting with mplayer but no joy.

---

### Post by rykel on 2008-07-19
Still no joy yet... I just hope someone can show us a .vob to .avi/.mp4/.mpg one-liner like **pdftk** or **convert**. 

I have learnt to love the one-liner commandline! Saves time...

---

### Post by dchurch24 on 2008-07-20
Oh yes, I just found a script to convert the other way - used with 'tovid' I'm wondering if tovid can be used the other way.

Will report back.

EDIT: no go, just the opposite way around. Still a good tool though.

---

