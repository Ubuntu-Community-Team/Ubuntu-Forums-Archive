---
title: "Play WAV files in Listen Media Player"
date: 2008-11-03
forum: Multimedia Software
---

### Post by buster2209 on 2008-11-03
I can not play WAV files in Listen Media Player

Is there a plugin or fix for this?

And please, I know there are different types of media players out there I could use, but I like Listen and would like to play my WAV files with it

Thanks in advance

---

### Post by buster2209 on 2008-11-03
I also can't play WMA type files

---

### Post by bgs100 on 2009-01-05
Halp! Anyone? (I has teh same problem)

---

### Post by Spectre5 on 2009-03-15
I also have this problems....mp3 and other audio work great but I can't seem to get wav files to play in Listen.

---

### Post by Spectre5 on 2009-03-15
> **Spectre5 said:**
> I also have this problems....mp3 and other audio work great but I can't seem to get wav files to play in Listen.

Install the following from the repos and it works:

libaudio-wav-perl

---

### Post by Spectre5 on 2009-03-15
> **Spectre5 said:**
> I found the solution!

Install the following from the repos and it works perfectly:

libaudio-wav-perl

Oops...nevermind :(

Anyone have a solution yet?

---

### Post by mc4man on 2009-03-16
Not a solution - run this and see what's supported ( probably not .wav or .wma 
 listen --ext-support

---

### Post by Spectre5 on 2009-03-16
> **mc4man said:**
> Not a solution - run this and see what's supported ( probably not .wav or .wma 
 listen --ext-support

Hm, thanks...I did that and get the following:

---
File supported: 
['.mp+', '.m4a', '.mpc', '.oggflac', '.spx', '.flac', '.mp3', '.mp2', '.ogg', '.mp4']
Missing Gstreamer plugins for : 
['.tta']
---

So ya, it doesn't list wav as a supported filetype...I guess I need to find out what it needs to support wav's (Rhythmbox also uses Gstreamer and it plays the wav files fine...so it is weird that Listen, which uses Gstreamer, cannot play them...)

---

### Post by bgs100 on 2009-03-20
for wma files, the deb package has an old song.py file, with no wma support. You can go to the listen website and get the newer song.py, and replace the old. sorry no urls or attchaed files, will get those posted soon

---

