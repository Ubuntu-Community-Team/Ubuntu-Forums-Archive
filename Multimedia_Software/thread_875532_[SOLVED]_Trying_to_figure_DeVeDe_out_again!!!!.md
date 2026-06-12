---
title: "[SOLVED] Trying to figure DeVeDe out again!!!!"
date: 2008-07-30
forum: Multimedia Software
---

### Post by GNUway Tech on 2008-07-30
I am a newbie to Kubuntu, and so far I'm really liking it. I just have one small problem with one of my primary programs I've always used.:(

On a previous distro, I used DeVeDe to prepare DVDs of my home videos, and it worked great. But, since switching distros, I can't seem to get any DVDs made with DeVeDe to play in a home DVD player. I start it up, pick the file, pick to make an iso, and run it. The iso will burn to a DVD, and it will play in a computer. For some reason, though, it will not work in a home DVD player.:confused:

It doesn't make sense, because I can burn an audio CD that will play in a CD player. Is there something I'm missing, or another way I can burn avi files to DVD? I've tried transcoding the files with Avidemux, and I get the exact same result. All the files I'm using are avis of home videos made with a video camera.

---

### Post by pi.boy.travis on 2008-07-30
Have you tried other DVD players?  The DVDs I make with DeVeDe won't play on my really old player, but they play on all of my computers and newer players.

---

### Post by GNUway Tech on 2008-07-30
The 1st DVD I made with it played in both my DVD players. None that I've made since then have played in them.:mad: I did manage to get one to play in my mother's portable DVD player, but it didn't have any sound.:confused:

---

### Post by pi.boy.travis on 2008-07-30
Now that you mention it, none of mine ever worked in portable players. . .  I've never looked into this problem, because they always did what I needed them for. . .

---

### Post by GNUway Tech on 2008-07-31
Is there anybody else with this experience, or advice about how to fix it????

---

### Post by pi.boy.travis on 2008-08-01
Do you have the proper libs?  libdvdcss2, libdvdnav4, libdvdread2, etc?

---

### Post by GNUway Tech on 2008-08-01
Can you tell me all of the libs that I need????????

---

### Post by pi.boy.travis on 2008-08-01
Those are the only ones I know of. . .

---

### Post by GNUway Tech on 2008-08-01
How do I install those??????? Can I find them in Adept?????

---

### Post by pi.boy.travis on 2008-08-02
Please excuse my lack of KDE experience.  If adept is you package manager, then yes, you should.

---

### Post by GNUway Tech on 2008-08-03
First of all, I can't find those libraries in Adept. Also, the Avi's I'm dealing with are in XviD and DivX codecs. Does that make a difference????????

They'll play in the computer, and so will the DVD's. They just won't play in a DVD player

---

### Post by pi.boy.travis on 2008-08-03
If you can't find those libraries in you package manager, you could try:

```
sudo apt-get install {name of package}
```

This command will manually install any specified package in the repositories.  If this command reports that the package could not be found, make sure you have the Ubuntu official repositories enabled.  Id you don't, I'm nos sure how to enable them using KDE.  Someone with more KDE experience should be able to help you enable the proper repositories.

Sorry I can't provide more info.  I am addicted to GNOME!

Hope this helps!

---

### Post by saygin on 2008-08-05
I have the sam problem too... I've been trying to make a DVD from a wmv file and after creating iso, I've mounted it on virtual drive. However, neither mplayer nor totem was able to open it. Vlc did actually with no problem, but after burning to the disc, my friends windows PC couldn't open the disc. I tried even the iso file, but again, it couldn't open. So I guess it is a bug or a problem of DeVeDe's this version (3.6) or I don't know why. I installed it via add/remove program so libraries and dependencies should be ok. But unfortunatelly this program cost me a lot of time and in the end, I have nothing!

---

### Post by xc3RnbFO8P on 2008-08-05
> my friends windows PC couldn't open the disc.

[http://ubuntuforums.org/showthread.php?t=787299&page=5]("http://ubuntuforums.org/showthread.php?t=787299&page=5")

---

### Post by saygin on 2008-08-05
thanks for the quick answer but, it is not caused burning, because I tried to mount the iso file on virtual machine in MS windows and it still could'nt see any files in it. So the problem is DeVeDe itself. Right?

---

### Post by Pauly Psychotic on 2008-08-05
Did you make sure it was NTSC instead of PAL format? 

Open up DeVeDe select Video DVD (First Option) 

First Select Menu Options Under Menu Format make sure NTSC is selected not PAL (If you are a Us/Canada Resident) which is normal for most of our players. Press OK

Second add your file again make sure you see NTSC not PAL Look for Video and underneath you will see Output Video Format.

That is the only thing that I could think of why it isn't playing in your home dvd player that you have PAL as default selection. That's what happened to me first time using it too hope this works and good luck.

---

### Post by xc3RnbFO8P on 2008-08-05
> **saygin said:**
> thanks for the quick answer but, it is not caused burning, because I tried to mount the iso file on virtual machine in MS windows and it still could'nt see any files in it. So the problem is DeVeDe itself. Right?

No it is a bug in genisoimage.

---

### Post by Clappy on 2008-08-27
Yeah, I noticed that by default, PAL options are set for the video and menu options. You need to change those to NTSC (north american encoding). If you don't have a DVD player that plays all regions, it's not going to work.

Stupid europeans*


*joking of course

---

### Post by pi.boy.travis on 2008-08-27
Same problem here first time I used DeVeDe.  I was baffled that the DVD wouldn't play on my older player, but worked on my newer one.

---

