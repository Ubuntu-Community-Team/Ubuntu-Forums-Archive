---
title: "Amarok, Rhythmbox does not work but mplayer does"
date: 2008-09-29
forum: Multimedia Software
---

### Post by acidity on 2008-09-29
Hello

So I bough bunch of CD other day and tried to play it on my Linux box for the first time. Youtube etc all works perfect so I have no issue with sound.

Once I put my CD, Rhythmbox and Amarok both recognise the CD and even list the track information but if I play them, nothing happens and both the tools just browse through the list and nothing happens.

I then ripped them to ogg format which went off smoothly but I see that they cant even play ogg files.

I looked into forums and somebody suggested to install Ubuntu Restricted Extras. I tried to install it and it says that its already installed.

Trying to find the issue, I installed the command line mplayer and it can read and play the ogg files but not the CDs. I tried the CD on my friends Vista and it works out of box.

Any ideas?

---

### Post by markbuntu on 2008-09-29
Read this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mc4man on 2008-09-29
> Once I put my CD, Rhythmbox and Amarok both recognise the CD and even list the track information but if I play them, nothing happens and both the tools just browse through the list and nothing happens.

Both players will play audio cds 'out of the box', *no additional libs, codecs needed*. Maybe you should look into your your sound settings or else where. (for amarok - settings -> configure amarok -> engine.

you should certainly follow that sticky and at the very least add medibuntu as a software source. If you don't have it enabled now after adding it you'll be able to upgrade amarok to the medibuntu version.

Again at the very least with medibuntu enabled run this (for 32 bit Os

```
sudo apt-get install w32codecs libxine1-ffmpeg
```

---

### Post by acidity on 2008-09-30
Very strange. I just restarted my machine today morning and everything is working. Rhythmbox, Amarok, Mplayer :)

Dont know what was the problem....

---

