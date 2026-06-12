---
title: "Aspect Ratio Wrong Playing Videos in Totem Under XGL/FGLRX"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by BaronAaron on 2007-04-29
Hello first post, hoping someone can help me.

I'm running:

-Ubuntu 7.04 Feisty Fawn
-ATI binary driver 8.34.8-1
-XGL with Beryl

I need to use XGL and the binary driver because I have a Radeon x1600 which isn't supported by the open source driver yet.

XGL and Beryl are working fine.

The problem:

All videos (I've tried mpeg, xvid, and mpeg2) play with the wrong aspect ratio under totem-gstreamer and totem-xine (latest versions from the official repos).  The video are stretched height wise (y axis I suppose) about twice what they should be. Using the aspect ratio feature of totem does little to help.

Under a standard Gnome session without XGL totem-xine videos play fine. totem-gstreamer videos play with the wrong colors but the aspect ratio is fine. The color issue has been brought up by other people and may be a seaperate bug.

VLC and Mplayer both play videos fine under XGL, but I'd rather not use them because they don't support the gnomevfs. I play a lot of videos across my network from samba shares, and I rather not mount them. I prefer to use Natillus to browse and play videos from across the network which Totem seems to handle well.

Anyone got any suggestions? If I can't fix Totem, anyone know of an alternative media player that support gnomevfs when it comes to the smb:// URI?

Thanks,

Aaron

---

### Post by ihatethedekoys on 2007-04-29
I have the same problem, only for me, the videos are stretched to wide.

---

### Post by ihatethedekoys on 2007-04-30
I solved my problem by adding the line
```
DisplaySize	540	405
```

to my xorg.conf file

it appears that xine automatically adjust the video size to try and fit your monitors aspect ratio, so if you have the ratio set wrong in xorg.conf, it displays wrong.

---

### Post by darkdays on 2007-04-30
> I solved my problem by adding the line
Code:
```

DisplaySize	540	405
```

to my xorg.conf file


What would those numbers be? 
What resolution are you on? 
The same numbers go for all resolutions?

---

