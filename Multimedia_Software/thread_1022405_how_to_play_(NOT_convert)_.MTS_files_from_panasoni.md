---
title: "how to play (NOT convert) .MTS files from panasonic sd9"
date: 2008-12-26
forum: Multimedia Software
---

### Post by mortuk on 2008-12-26
Got myself a Panasonic SD9 and I want to be able to just copy the MTS files over and play them back on my asus eee 1000.

I dont want to have to convert them unless i know i want to keep them, yet i cannot find anything that will play them. VLC loads the first frame then just plays sound.

Any ideas?

---

### Post by Geekkit on 2009-02-10
I'd like to see the same and even taken a step further. I'd like to see thumbnails of the videos in Nautilus and be able to play MTS files in Totem. I have a Panasonic HDC-SD100 which saves videos as MTS files.

Currently what I had to do was download via SVN the latest copy of ffmpeg, compile, install (instructions at: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=529871&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=529871&page=2) )

Then use ffmpeg, mplayer, and mencoder to create AVI versions (instructions at: [http://www.bitboysblog.com/?tag=m2ts](http://www.bitboysblog.com/?tag=m2ts) )

I don't know if this will be in 9.04 - I can only hope!

---

### Post by cotcot on 2009-02-10
It seems that mplayer can handle MTS better that ffmpeg for the moment.
Suppose you have installed a recent version of mplayer you can playback tha AVCHD files with this command :

```
mplayer -demuxer lavf -lavdopts threads=4:fast:skiploopfilter=all:skipframe=none -fps 25 -vf pp=lb  yourfile.MTS

```

---

### Post by Geekkit on 2009-02-10
> **cotcot said:**
> It seems that mplayer can handle MTS better that ffmpeg for the moment.
Suppose you have installed a recent version of mplayer you can playback tha AVCHD files with this command :

```
mplayer -demuxer lavf -lavdopts threads=4:fast:skiploopfilter=all:skipframe=none -fps 25 -vf pp=lb  yourfile.MTS

```

cotcot, thanks for your reply. Can you define recent version. I'm in Ubuntu 8.04 and using 2:1.0~rc2-0 and I get the following error:

[h264 @ 0x89398d0]PAFF interlacing is not implemented

This is the same problem I had before and had to do what I posted at:

[http://ubuntuforums.org/showthread.php?t=935293](http://ubuntuforums.org/showthread.php?t=935293)

Bottom line for me is that I really hope that MTS support becomes native to an Ubuntu release soon so that it's part of Nautilus's ability to render thumbnails, and is included in Totem so that I can preview/play before adding to an editing project.

---

### Post by cariboo on 2009-02-10
If you want .mts file support, create a bug at [Launchpad]("http://bugs.launchpad.net/"), you'll have to create an account. If the devs don't know there is a demand for something, they can't do anything about it.

Jim

---

### Post by Geekkit on 2009-02-10
> **cariboo907 said:**
> If you want .mts file support, create a bug at [Launchpad]("http://bugs.launchpad.net/"), you'll have to create an account. If the devs don't know there is a demand for something, they can't do anything about it.

Jim

Thanks, I think I'll do that.

---

### Post by andrew.46 on 2009-02-11
Hi,

Any links to .mts files?

Andrew

---

### Post by cotcot on 2009-02-11
> **Geekkit said:**
> cotcot, thanks for your reply. Can you define recent version. I'm in Ubuntu 8.04 and using 2:1.0~rc2-0 and I get the following error:

[h264 @ 0x89398d0]PAFF interlacing is not implemented

This is the same problem I had before and had to do what I posted at:

[http://ubuntuforums.org/showthread.php?t=935293](http://ubuntuforums.org/showthread.php?t=935293)

Bottom line for me is that I really hope that MTS support becomes native to an Ubuntu release soon so that it's part of Nautilus's ability to render thumbnails, and is included in Totem so that I can preview/play before adding to an editing project.

I am using the same version however installed from SVN. [[COLOR="Red"]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1024592") is a howto for intrepid. 
I have seen that error also, but I do not remember how and when and if it was with the mplayer version I have now. Do you get the error also if you remove "-vf pp=lb" from the command line instruction. -vf is the instruction to deinterlace the .MTS you are playing, but maybe your .MTS is not interlaced.

---

### Post by shantiq on 2011-08-14
well with a decent graphics card which can handle HD (720 and 1080) there is a program which can play mts straight off

**smplayer**  in synaptic or ```
sudo apt-get install smplayer
```  then go options/preferences/video and pick vdpau

works fine for me on a very average computer

those mts files are bluray when i read them through mediainfo

---

