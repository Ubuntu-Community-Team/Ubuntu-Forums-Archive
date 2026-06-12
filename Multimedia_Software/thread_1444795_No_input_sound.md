---
title: "No input sound"
date: 2010-04-01
forum: Multimedia Software
---

### Post by uMany on 2010-04-01
Hi,
I I'm using a Sony Vaio VPCF11FD (F series) intel i7 with ubuntu 9.10, no too much trouble with ubuntu but with some applications. My problem is that I have no input sound, I can't get any sound recorded. I have output sound without problems but I want to do some recordings and I have failed even in knowing what is wrong.

In the common audio problems thread this issue is in the to do list.
Any clue?

Thanks in advance

---

### Post by gordintoronto on 2010-04-01
Sometimes this is because the microphone is muted in Volume Control.

Or perhaps the answer lies in Preferences/Sound.

---

### Post by uMany on 2010-04-01
Gordintoronto,

Thanks for your replay and idea but I already checked the mic in the Volume Control and in the alsacontrol and it still doesn't work

uMany

---

### Post by lyall on 2010-04-01
check your jacks and see which ones you have plugged into

on the motherboard there are three jacks
one for mic, sound in and sound out

sometime on the front of the PC there are two - one headphones and mic

most laptops have the three jacks

also check in alsa control to see if the line in is muted

good luck and have fun learning

---

### Post by uMany on 2010-04-02
Hi Lyall,

Apparently the jacks are fine, and the line in in the alsa control is not muted.
At the Sound preferences is not muted and the input is recognized but there is no level, the level bars are ghosted.
I couldn't been able to solve this yet.
And yes, I had have a lot of fun learning. :-)
Thanks for your 5 cents

---

### Post by lidex on 2010-04-03
Try this. Open a terminal and enter this command:
```
alsamixer
```

Press F6 and select the correct soundcard.
Press F4 to view capture devices. Check levels there. Look for text only entries (no graphic bars). Scroll to select using left-right arrow keys and toggle mode (line/mic) using up-down arrows.

---

### Post by uMany on 2010-04-05
Hi Lidex,

Thanks for you help.
I did what you told me to but nothing happen. Still no input sound.
Any other idea?

Thanks in advance

---

### Post by cchhrriiss121212 on 2010-04-05
The levels look fine to me.
What hardware and program are you using to record with?
Are you using pulse audio to record?

---

### Post by uMany on 2010-04-05
Hi, cchhrriiss121212

I'm -trying- using the external mic of the laptop (Vaio VPCF111FD) and the input line mic with a small mic and for the software I've been trying with the standard sound recorder app and with audacity.
The audio server is pulse audio

Thanks for your time

---

### Post by cchhrriiss121212 on 2010-04-05
Try switching from pulse to alsa in audacity preferences.

---

### Post by mubtasim123 on 2011-02-08
can anyone help mewith this [http://ubuntuforums.org/showthread.php?p=10441012#post10441012](http://ubuntuforums.org/showthread.php?p=10441012#post10441012) sounds similar

---

