---
title: "Crackling Sound. Ubuntu 9.10"
date: 2009-10-30
forum: Multimedia Software
---

### Post by chrispche on 2009-10-30
Has anyone else found that the start up sound when logging on is crackly? Even if I change the sound this happens. Any ideas?

---

### Post by Ubuntero100 on 2009-12-04
> **chrispche said:**
> Has anyone else found that the start up sound when logging on is crackly? Even if I change the sound this happens. Any ideas?


Yes same here. Also have problems with sound on skype. Again crackling sound instead of dial tones.

---

### Post by Cardale on 2009-12-05
Yes I have crackling sounds on occasion.  Kind of annoying since I have a ok sound card and pretty good surround sound speakers.

---

### Post by Rytron on 2009-12-09
I have noticed crackling sound on Open Arena and some other games.

---

### Post by duanedesign on 2010-01-04
not sure about 9.10 but in 9.04 a lot of times this could be fixed by checking if PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
alsamixer -Dhw
```

[This forum post]("http://swiss.ubuntuforums.org/showthread.php?t=1311262") explains a workaround that fixes a problem similar to yours.

Additional resource
[DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by nicklikesfire on 2010-01-08
I've also got this problem.

Just playing audio through rhythmbox, and the output is full of crackling.

If anyone finds a working solution I'd love to hear about it. This is killing me. Thanks.

---

### Post by mizukiov on 2010-01-08
probably pulseaudio being its awesome self again.

```
sudo aptitude purge pulseaudio
```

---

### Post by LuisGMarine on 2010-01-08
It seems to have already been reported here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755")

However the problem is still not fixed ... I've spend a few days reading this bug report and attempting every fix that they mention on here, and to this day nothing has seemed to work.  I guess if you remove ("purge") pulseaudio it might fix the problem, but it's not going to help the well being of Ubuntu.  Pulseaudio isn't going anywhere, so we have to try and find a fix for this annoying bug.  

I'm going to try to compile the latest alsa drivers and see if that might make a difference.

---

### Post by Rytron on 2010-01-09
Use Esound. ;)

---

### Post by chrispche on 2010-01-18
I have noticed the same crackling in Fedora 12 to. I think it must be a universal thing. Mandriva did the same thing to. I hope it gets fixed soon.

---

### Post by LuisGMarine on 2010-01-18
I agree that this has to be a universal thing.  I tried out Archlinux, OpenSUSE, and Mandriva, and still experiencing the same problem.

I don't have windows installed so I can't check if the same thing happens on windows.  This could also mean that our sound cards might be failing or something.  It might turn out that its not really a software, but rather a hardware problem.

---

### Post by chrispche on 2010-01-21
> **mizukiov said:**
> probably pulseaudio being its awesome self again.

```
sudo aptitude purge pulseaudio
```

What would happen is you do this? What sound card driver would replace it?

---

