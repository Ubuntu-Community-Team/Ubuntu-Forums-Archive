---
title: "Recording pacat output with parec?"
date: 2011-11-21
forum: Multimedia Software
---

### Post by Dingbats on 2011-11-21
It's quite fun to send non-audio files to pacat and listen to the noise it makes.  Like the contents of my /usr/bin, for example.  But I want to record this.  I figured parec would be a sensible option, but how do I do it?  I can't just run

pacat FILE1 | parec FILE2

That just plays FILE1 and writes silence to FILE2.

Anyone?

---

### Post by Dingbats on 2011-11-22
After some serious consideration, I have decided to bump this thread.

---

### Post by neu2buntu on 2011-11-23
@dingbats, hi since reading this post i have been tinkering around with the commands, and have solved the problem for myself, using this command ```
pacat /dev/urandom --fix-format | paplay --record  ~/Desktop/out.wav
```was not working for me either to start with, but then i remembered that my install of ubuntu can be problematic at times , especially with pulseaudio streams, heres what i did to remedy it

(1) run my command above from the terminal ( your command should also work)

(2) while pacat is "catting" the /dev/urandom file, open up padevchooser, left click the icon and choose volume control

(3) make sure that you switch the playback and record streams to something like monitor of source, you will know the right ones because the volume display bar will be raised.

(4) press ctrl c in the terminal running the pacat command to quit .


now you will have a file named out.wav containing the audio you heard from the pacat command . ( you may have to create a blank document named out.wav on your desktop beforehand and change the ownership permissions to read and write, im unsure of this though )

```
pacat /dev/snd/pcmC0D0p --fix-format | paplay --record  ~/Desktop/out.wav
```

this command records anything that you listen to on your desktop, eg hovering over a .wav file or listening to a song online .

---

### Post by Dingbats on 2011-11-25
> **neu2buntu said:**
> @dingbats, hi since reading this post i have been tinkering around with the commands, and have solved the problem for myself, using this command ```
pacat /dev/urandom --fix-format | paplay --record  ~/Desktop/out.wav
```was not working for me either to start with, but then i remembered that my install of ubuntu can be problematic at times , especially with pulseaudio streams, heres what i did to remedy it

(1) run my command above from the terminal ( your command should also work)

(2) while pacat is "catting" the /dev/urandom file, open up padevchooser, left click the icon and choose volume control

(3) make sure that you switch the playback and record streams to something like monitor of source, you will know the right ones because the volume display bar will be raised.

(4) press ctrl c in the terminal running the pacat command to quit .


now you will have a file named out.wav containing the audio you heard from the pacat command . ( you may have to create a blank document named out.wav on your desktop beforehand and change the ownership permissions to read and write, im unsure of this though )

```
pacat /dev/snd/pcmC0D0p --fix-format | paplay --record  ~/Desktop/out.wav
```

this command records anything that you listen to on your desktop, eg hovering over a .wav file or listening to a song online .
Amazing!  Thank you so much! :D  I'll keep this thread bookmarked for future reference in case I want to do this again!

---

