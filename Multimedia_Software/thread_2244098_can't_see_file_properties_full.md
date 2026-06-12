---
title: "can't see file properties full"
date: 2014-09-13
forum: Multimedia Software
---

### Post by urvi on 2014-09-13
dear all,
i just installed ubuntu 12.04 LTS
i use ubuntu 11.10 since 10 years without any problem
now 
in ubuntu 12.04 ,
i can't see in file properties -
audio & video tab

request to send details to show this - audio & video properties while click properties of a video file.

thanks and regards,
urvi

---

### Post by 3v3rgr33n on 2014-09-13
Is the problem that the "properties" window pops up but is empty or does it not appear at all?

---

### Post by urvi on 2014-09-13
sir,
properties windows pops up -
3 tabs shown - 
basic 
permissions 
opens with 

but 
audio & video tab not seen

thanks

---

### Post by 3v3rgr33n on 2014-09-13
Sir? No need to be formal ;)

I'm assuming you're using nautilus. Look at this thread [http://ubuntuforums.org/showthread.php?t=2127171](http://ubuntuforums.org/showthread.php?t=2127171) to begin with.
It seems like you're not the first one to come across this, look at this bug report [http://code.google.com/p/gnome-mplayer/issues/detail?id=291](http://code.google.com/p/gnome-mplayer/issues/detail?id=291)

A quick Googling reveals that @cokedude at unix.com has proposed a solution. Here's a link to the proposed solution: [http://www.unix.com/red-hat/167289-nautilus-audio-video-properties-missing-tutorial.html](http://www.unix.com/red-hat/167289-nautilus-audio-video-properties-missing-tutorial.html)

If you really need to access the information quickly and cannot fix nautilus, consider using a command line tool. I suggest that you install ffmpeg and attempt to use it.

> 
sudo apt-get install ffmpeg
ffmpeg -i myfile.extention


---

### Post by 3v3rgr33n on 2014-09-13
Here is a comprehensive list with your possible command line choices [http://askubuntu.com/a/303461](http://askubuntu.com/a/303461)

---

### Post by urvi on 2014-09-13
installed mplayer &  ffmpeg
still can't see file propertiies full

---

### Post by mc4man on 2014-09-13
what's this report
```
apt-cache policy totem
```
If totem isn't installed then install, after that stop & restart nautilus or log out/in.

---

### Post by urvi on 2014-09-13
problem is solved 
thanks a lot

---

### Post by Yellow_Bastard on 2015-05-15
> **urvi said:**
> problem is solved 
thanks a lot

How did you get the sound/video tab added? 
You said that the problem is solved but you did not say how you got it sorted out. 

Thx.

---

### Post by mc4man on 2015-05-15
> **Yellow_Bastard said:**
> How did you get the sound/video tab added? 
You said that the problem is solved but you did not say how you got it sorted out. 

Thx.
see post 7

---

