---
title: "Why do I keep getting ths error with Devede"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by Doug11 on 2006-12-29
I,m trying to convert an avi to dvd with devede, worked well before but all of a sudden it starts gving me ths error as soon as it starts to convert--->    ABORTED. THERE CAN BE TEMPORARY FILES AT THE DESTINATION DIRECTORY.   Can anyone tell me a way to fix this?

---

### Post by taurus on 2006-12-30
What version of DeVeDe do you have and maybe want to check your disk space?

```
df -h
```

---

### Post by Doug11 on 2006-12-30
Devede 2.1,,,,,I don't think disc space is a prob.



Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              73G   33G   36G  48% /
varrun                347M  112K  347M   1% /var/run
varlock               347M     0  347M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                347M     0  347M   0% /dev/shm
lrm                   347M   18M  330M   5% /lib/modules/2.6.17-10-generic/volatile

---

### Post by pseudonym on 2006-12-30
Don't mean to intrude on this but does DeVeDe support menus? I checked out what documentation there is at the author's website and, while it didn't say that it could do menus, it didn't say that it couldn't either... Thanks :)

---

### Post by Doug11 on 2006-12-30
I've never tried to do menus with it,,,nor will I,,,I fixed my problem,,,I'm using tovid and it seems to work well.

---

### Post by Doug11 on 2007-01-07
Well,,,I completely removed Devede, then did a full re-install of it and it worked for one DVD. When I tried to do the second, it started with the same error. I don't mind using Tovid,,bit do convert a 700MB avi,,it took just over 3 hours and you lose the widescreen, which makes everyone a little skinnier and taller. Has anyone else ever come across this error?

---

### Post by zba78 on 2007-02-27
To speed up tovid you can reduce the quality setting. Default is now 6 (used to be 8 ), 1 is lowest, 10 highest.

**tovid -quality [NUM] -in infile -out outfile**
Where you replace [NUM] with the quality setting.

Also you can make tovid use ffmpeg to speed things up (my preferred way).

**tovid -ffmpeg -in infile -out outfile**

---

### Post by theJagger on 2007-03-04
yeah I got that same thing, I could not fix it

ALSO

... there is an issue with mplayer/mencoder that a person might run into when using devede.
Basically, the app will just hang when you attempt to open a file . . . because

[MPlayer-users] [BUG] DV video misdetected as MPEG-TS 
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-March/059106.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-March/059106.html)

fixed by changing:
command_var.append("-o")
to:
command_var.append("-demuxer rawdv -o")

and

handler=subprocess.Popen('mplayer -identify -ao null -vo null -frames 0 "'+filename+'" 2>/dev/null |grep ID',shell=True,bufsize=32768,stdout=subprocess.PIPE)
to:
handler=subprocess.Popen('mplayer -demuxer rawdv -identify -ao null -vo null -frames 0 "'+filename+'" 2>/dev/null |grep ID',shell=True,bufsize=32768,stdout=subprocess.PIPE)

---

### Post by Steve H on 2007-04-21
I´m getting the same error: ABORTED: THERE MAY BE TEMPORARY FILES IN THE DESTINATION DIRECTORY.

Is there a log file anywhere? I´ve checked the system logs but there is nothing in there.......I used avidemux to create the mpg, from the original .avi file. I have tried loads of different apps now to try and get this sorted.

---

### Post by Steve H on 2007-04-21
I´ve managed to get DeVeDe to work, but I had to install the source tarball from the [_website_]("http://www.rastersoft.com/descargas/devede-2.13.tar.bz2"). This is version 2.13 and doesn seem to have the problem that I have been experiencing with the other ¨Synaptic¨ version. At least it finished encoding.

I have now tried burning it with K3b, but the audio is all screwy (static), I don´t know if this is Avidemux or DeVeDe that has done this to the file. I´m encoding the avi just using DeVeDe and not using Avidemux at all, to see if that works......I will report back when it is done.

](*,)

---

### Post by robc02 on 2007-04-22
I got DeVeDe to convert a .rec file to DVD when using the default settings for bit rate and sound, but the video quality wasn't that good - when people move across the screen there is a "trace". I tried to do the conversion again but with a higher bit rate to try to improve the quality, but I then got the  same error message that the rest of you are getting - with the addition of "Have you got enough disc space?" or words to that effect. - Well I am sure that I do have enough disc space.
I seem to remeber getting the same error message when I first tried DeVeDe and chose a file name with "/" in it. I chose a simpler file name and it was then OK.
The bottom line for me is - how can I get good quality conversions of my .rec files?

---

