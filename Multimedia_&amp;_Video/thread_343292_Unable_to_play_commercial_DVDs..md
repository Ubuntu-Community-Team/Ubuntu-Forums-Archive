---
title: "Unable to play commercial DVDs."
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by Lightspeed on 2007-01-21
I'm ready to give up on this.

I'm trying to play any commercial DVD on my Ubuntu Edgy system. I can play one disc which might be unencrypted, not sure, it's definitely region 0 though. No other disks work. I've tried all of the following.

1. sudo  /usr/share/doc/libdvdread3/install-css.sh
This got me the libdvdcss2 plugin, but no-go with Totem. It still reports the following error:
> "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"
Since I *have* libdvdcss this makes no sense.

2. totem-xine. Didn't change anything.

3. Tried playing the same disk, on the same drive, on Windows. It works no problem.

4. Regionset, which reports that the drive is set to region 2. I'm in the UK, so that's correct, and it matches the region of the DVDs.

5. Tried xine. It reports, "Xine engine error: there is no input plugin available to handle 'dvd:/'. Maybe MRL syntax is wrong or file/stream source doesn't exist." This is immediately followed by "The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g. not disc in drive) (/dev/dvd)". The region 0 disk plays fine, however.

6. Tried VLC. I selected DVD, but it still says "Audio CD - Track 1", and refuses to play any disk as a DVD, except the region 0 disk which again is flawless.

7. Ogle and gxine, same story except they simply crash if they don't like the disk.

8. Someone suggested Automatix, but that hasn't changed anything.

I don't even know if this list is right, I've lost track of all the errors I've seen today. Any help would be greatly appreciated.

---

### Post by Stemp on 2007-01-21
Does the command :

```
ls -l /usr/lib/libdvdcss.so.2 
```

give you something like this ? :

```
lrwxrwxrwx 1 root root 18 2006-10-27 02:57 /usr/lib/libdvdcss.so.2 -> libdvdcss.so.2.0.8
```

---

### Post by Lightspeed on 2007-01-21
Yup, almost exactly that, only the date is different.
> lrwxrwxrwx 1 root root 18 2007-01-21 14:33 /usr/lib/libdvdcss.so.2 -> libdvdcss.so.2.0.8

---

### Post by Stemp on 2007-01-21
```
libdvdnav4
libdvdplay0
libdvdread3
```

are installed ?

---

### Post by Lightspeed on 2007-01-21
Running a "sudo apt-get install" reports that all three are at the latest version. I'm assuming that's right...

---

### Post by Stemp on 2007-01-21
Well i've tried and cannot play my dvd using vlc or gxine :D

Work well with totem-gstreamer and gmplayer

---

### Post by Lightspeed on 2007-01-21
I switched back to totem-gstreamer. It and totem-xine seem to be mutually exclusive.

Now MPlayer is just giving the error "Failed to open dvd://1". Totem itself is now claiming not to have the plugins to play the disk; I'm assuming that's the same error in a different form.

Do all these programs rely on the same base? I've heard VLC is separate but what about the others? Is GStreamer some sort of DirectShow equivalent, or is it Totem's own thing?

---

### Post by Stemp on 2007-01-21
gstreamer and xine are multimedia engines, mplayer and vlc use their own engine.

---

### Post by Cobikegeek on 2007-01-21
I suggest trying VLC.  It just works.  I jumped through all the hoops you are to get gxine to play commerical dvds and found the ubuntu restricted formats page to be very helpful.  Or just install VLC.  Good luck.

---

### Post by Mike_cog on 2007-01-21
I am also having problems playing dvd with totem. It says instal necessari plugins but i dont know how to or what plugin also i am unable to follow what is being said in this furum. I am region 4 and have i come to the right place to ask this question. Ta

---

### Post by livingtarget on 2007-01-22
Probably need some mpeg codecs as most dvds use mpeg format. Maybe you don't have libmpeg or something like that. Try installing libmpeg2 and 3. It'd be good to install w32codecs as well while you are installing codecs anyway.

If you have that, totem-xine and libcss2 then you should be set. 

VLC should work as well as it has most codecs and such built in.

---

### Post by ORiON2012 on 2007-03-26
I was getting the same errors with totem-xine about the lack of a plugin for playing DVD's. Installing libxine1-ffmpeg solved it.

---

