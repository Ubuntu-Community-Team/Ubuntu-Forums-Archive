---
title: "dvd burning"
date: 2023-03-28
forum: Multimedia Software
---

### Post by coley9225 on 2023-03-28
Hello all. I have been asked to copy some of my movie files to a dvd for my daughter. All the files are mp4 and mkv files. She has a playstation 4, wich will play those file formats. All good so far.

Now the issue. I haven't "burned" a dvd since I moved to a linux system, and I don't know the best way to do this. Easiest method, of course, would be to simply copy the files to the dvd, and be done. Will that work, or is it a bit more involved?

I don't need to convert the files to another format, and if I had spare usb thumbdrives, I would just copy the files and be done. 

So, I geuss what I'm asking, is 'what is the best method, app, etc, for this project?'.

My current system is shown in my signature. I'm running Lubuntu 22.04 with all updates/upgrades.

Thanks in advance for any ideas and tips.

---

### Post by TheFu on 2023-03-28
> **coley9225 said:**
> Hello all. I have been asked to copy some of my movie files to a dvd for my daughter. All the files are mp4 and mkv files. She has a playstation 4, wich will play those file formats. All good so far.

Now the issue. I haven't "burned" a dvd since I moved to a linux system, and I don't know the best way to do this. Easiest method, of course, would be to simply copy the files to the dvd, and be done. Will that work, or is it a bit more involved?

I don't need to convert the files to another format, and if I had spare usb thumbdrives, I would just copy the files and be done. 

So, I geuss what I'm asking, is 'what is the best method, app, etc, for this project?'.

My current system is shown in my signature. I'm running Lubuntu 22.04 with all updates/upgrades.

Thanks in advance for any ideas and tips.

If you don't need to "master" a DVD as an movie-DVD, and just need a data-DVD, then you can use any DVD/CD burning software you like. There are many. I haven't burned an DVDs in years, but remember using **K3b**. [https://www.makeuseof.com/tag/brasero-vs-k3b-top-2-linux-disc-burning-utilities/](https://www.makeuseof.com/tag/brasero-vs-k3b-top-2-linux-disc-burning-utilities/) Just be certain you do not ask it to convert the files into videos/movies and end up with VOB and SUB and IDX files. You don't want those.  Really, it might be easier to just geta 16GB USB flash drive, copy the files over and give those to her. IDK.  Heck, I use microSD flash storage for stuff like this and have a microSD to USB adapter for use in computers.  Kingston makes a cheap, $10, USB3.2 adapter for microSD which works really well.

Since 22.04 Lubuntu is based on Qt, **K3b** (probably also using Qt) would likely have fewer dependencies than other Gnome-based options.

---

### Post by coley9225 on 2023-03-28
Thanks TheFu.
I installed K3b,and a long list of dependencies). I had to use my pal Google to make it run. I have no group 'operator' in my system, but found info on changing ownership of a couple of packages from root:operator to root:cdrom. I also had to change permisions on those packages. At this point, it is at least running, so time will tell if it actually burns the data to the disc. Good advice on the data disc and not convert files and make a video disc.

I'll post back as soon as I know if this is working(probably be a day or so for my daughter to let me know), or if I encounter anymore snafus.

---

### Post by SeijiSensei on 2023-03-28
For the future, I'd have it output a .iso file that you can examine before burning. I know K3b can do that.

---

### Post by TheFu on 2023-03-28
> **coley9225 said:**
> Thanks TheFu.
I installed K3b,and a long list of dependencies). I had to use my pal Google to make it run. I have no group 'operator' in my system, but found info on changing ownership of a couple of packages from root:operator to root:cdrom. I also had to change permisions on those packages. At this point, it is at least running, so time will tell if it actually burns the data to the disc. Good advice on the data disc and not convert files and make a video disc.

I'll post back as soon as I know if this is working(probably be a day or so for my daughter to let me know), or if I encounter anymore snafus.

It isn't like you don't have the DVD.  Insert it into your computer and try to play the files from it.  If they work, then it is good.

BTW, extensions for video files are "containers", not specifically tied to any single video or audio codec, so saying you have an mp4 file is like saying you have a blue truck.  We don't know what's inside the bed/trailer (it could be a semi).  Each codec has their own standards for different purposes and not all players can handle all those available standards either.

The most limited, yet modern, container is webm which is what Google uses.  It will either have vp8 or vp9 videos and vorbis audio.  Those are excellent and 100% F/LOSS.  My playback systems cannot handle vp9, so I usually encode to h.264 video and put them into an mkv container. I prefer vorbis audio for everything. It is very high quality lossy multi-channel audio compression.  MKV as a container can handle any video codec and any audio codec as well as chapters, subs, srts, ass, and text files - as many as we like of each.  MKV is the most versitile video container that I know.  Sadly, mka, the audio container version, never took off. I suppose that's because many audio players, cough Apple, don't like too many choices. If Apple snubs a video or audio format, it is unlikely to gain acceptance.  The reason webm got support was purely because Google pushed it and added it to Chrome and Chromium browsers.  They also made it F/LOSS, so every other browser could add it freely ... and both Firefox and whatever MSFT has for a browser did too.

---

### Post by qyot27 on 2023-03-29
[https://www.playstation.com/en-us/support/hardware/play-video-music-discs-usb-drives/](https://www.playstation.com/en-us/support/hardware/play-video-music-discs-usb-drives/)

Note the 'Unsupported disc formats on PS5 consoles and PS4 consoles' section, where it lists
```
BD-RE ver.1.0
BD-R/RE XL
```
as unsupported, while at the same time but in the 'Supported disc formats' dropdown, it has
```
BD-R/RE (BDAV, BDMV)
```

Which would very strongly imply that user-created BD-R discs have to be authored specifically for video playback, rather than just dumping a bunch of as-is video files on the disc with no formal structure.  And when getting into the weeds of authoring, you have to adhere to both the video/audio format specs (which encompass things such as bitrate and buffer constraints as well as the particular features used by the encoder to be compliant with a certain Profile and Level), as well as making sure the disc/menu structure is correctly created (the actual purpose of authoring programs), **and** that the disc is created using the correct version of the UDF filesystem (for Blu-ray Video, that's either 2.50 or 2.60).

My limited attempt at just sticking a normal Bluray data archive disc into my PS5 would seem to corroborate this: it spat back a message about the disc being unsupported.  Even a DVD data archive was unsupported.

So yeah, I would echo that it's far more reasonable to put the files on a USB flash drive and let the console play off of that.

---

### Post by TheFu on 2023-03-29
Don't think anyone mentioned bluray.  That would be an important detail.  Bluray is broken-by-design on all platforms, but especially on Linux.  Much easier to just avoid it completely.

---

### Post by coley9225 on 2023-03-29
Thanks for all the tips. I did put the dvd into my computer, and the movies play in vlc. My only concern at this point is if the playstation will play them. I can't remember if I had to format something different or not, I don't believe I did. Anyway, you guys have come through again. Many thanks to you all. I can go back up to the op and mark this 1 solved.

In case anyone else has this problem, here are the command I had to use to get it working. I logged in as root, to avoid typing sudo for every command(bad practice, I know), so be aware that sudo is required fir these commands.

```

chown root:cdrom /usr/bin/cdrdaochown root:cdrom /usr/bin/cdrecord
chown root:cdrom /usr/bin/growisofs
chmod 4710 /usr/bin/cdrdao
chmod 4710 /usr/bin/cdrecord
chmod 750 /usr/bin/growisofs



```

Afterward, K3b runs fine. Thanks again everyone.

---

### Post by TheFu on 2023-03-29
using the setuid bit is dangerous.  With it, someone can overwrite the OS - or worse.  Beware.

---

