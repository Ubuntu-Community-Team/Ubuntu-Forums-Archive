---
title: "slight crackle in sound output, not present in windows"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by hardyn on 2007-03-07
i have a Asus notebook with realtek sound, i have notices a slight, but very noticeable crackly noise in audio output that is not present in windows.

i have pretty conservative gains, and the noise is proportional to volume, but not the speaker volume, but sound card volume.

this is a pretty vague description, but i would appreciate any help...

is sound supposed to be any better in feisty?

thanks.

---

### Post by ssavelan on 2007-03-10
Sound can be great in Edgy.  Ubuntu Studio is coming out with Feisty for real realtime competition with the commercial junk....

Is this happening with every program you use and... crucially... what programs are you using.

Please Post:

Sound card, version of ALSA, programs used... any other helpful info.

---

### Post by hardyn on 2007-03-11
82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller

ALC880

/org/freedesktop/Hal/devices/pci_8086_2668

maybe there is version id in there somewhere? ;)

---

### Post by ssavelan on 2007-03-13
The only time that I've had such a crackle is when I have an internal peak/overdrive.

alsamixer -c0 -Vall


(perhaps "alsamixer -c1 -Vall" if you have 2 soundcards)

I know that you already mentioned that your levels are moderate.

The only other kind of crackle that I can think of is an x-run in JACK where the processor/mem can not completely handle the processes demanded.  What kind of proc./how much memory do you run?

This is probably not the problem either, b/c ubuntu is typically lighter than Windows.

You might try compiling the latest drivers/libs from ALSA.  I have noticed (on a variety of soundcards) that the latest (even the testing version) is much better than the ubuntu defaults.  It's worth a try.  In case you don't have the link:
[URL="www.alsa-project.org/"]
www.alsa-project.org/[/URL]

---

