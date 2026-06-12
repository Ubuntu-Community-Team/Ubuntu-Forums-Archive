---
title: "Sudden sound blocking, XINE errors."
date: 2009-05-29
forum: Multimedia Software
---

### Post by tosszyx on 2009-05-29
I've experimenting a sound problem for the last couple of months, and so far my only solution was to restart the computer (it wasn't that often, and once every some week I like to restart my computer because I sense it more "snappy" after a reboot). Lately the problem was appearing more often and I decided to give it a try and solve it.

The problem was that after sometime my sound stopped working, when I wanted to play a video in Firefox, I got no sound and choppy image; when I wanted to play a mp3 file in Amarok I got: 
> 
Audio output unavailable; the device is busy.
xine parameters: 

And finally, if I wanted to play a video using Kaffeine it will give the following error: 
> 
Kaffeine  Loading of player part 'XinePart' failed    Details  All Audio Drivers failed to initialize!

Looking around I found that this is a common problem and I was no able to find that many solutions for it, I tried restarting/closing Firefox, Amarok and even the alsa-utils without any luck.
After a while a came across this command, that will let you see which programs are using you sound card:
```
sudo fuser -v /dev/snd/*
```
And the given answer was:
```

$ sudo fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  ule        6366 F.... kmix
                     ule       23959 F.... amarokapp
/dev/snd/pcmC0D0p:   ule        7265 F.... kpdf
                     ule       24885 F.... kpdf
                     ule       25231 F.... kpdf
                     ule       26855 F.... kpdf
/dev/snd/timer:      ule        7265 f.... kpdf
                     ule       24885 f.... kpdf
                     ule       25231 f.... kpdf
                     ule       26855 f.... kpdf

```
...uh? Kpdf is using my sound card ?? well, if I have tried everything else already, why not just close those pending pdf's... And it worked !!
After closing the pdf files, I could play music again and watch videos without restarting the computer. 

I hope this help somebody else to fix this annoying problem!

---

### Post by tosszyx on 2009-07-28
```
ule@Coatl:~$ sudo fuser -v /dev/snd/*
[sudo] password for ule:
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  ule        6403 F.... kmix
/dev/snd/pcmC0D0p:   ule        9022 F.... soffice
                     ule        9093 F.... soffice.bin
/dev/snd/timer:      ule        9022 f.... soffice
                     ule        9093 f.... soffice.bin

```

Well, a little update in this topic, it seems that the only culprit is not kpdf, the sound has been also block by Open Office and Java, so I'm not so sure where the problem lies (kde?, kmix?, xine?).

---

### Post by jjatria on 2009-09-03
```
user@linux:~/music$ sudo fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  user       6510 F.... knotify4
                     user       6553 F.... kmix
                     user      13356 F.... amarokapp
                     user      18067 F.... ktorrent
/dev/snd/pcmC0D0p:   user      18067 F.... ktorrent
/dev/snd/timer:      user      18067 f.... ktorrent
```

ktorrent also wants to join the list of culprits!
and as stated, once closed, sound was back to normal.

---

