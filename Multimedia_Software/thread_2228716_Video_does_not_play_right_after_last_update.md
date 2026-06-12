---
title: "Video does not play right after last update"
date: 2014-06-09
forum: Multimedia Software
---

### Post by ycp101 on 2014-06-09
After update on Jun 7, 2014, my Ubuntu 10.04 system became very unstable. Many applications becomes non-responding. Major problem is that I cannot watches movie files in avi and mp4 formats. There is my update history below.

Commit Log for Sat Jun  7 17:57:16 2014

Upgraded the following packages:
kdelibs-bin (4:4.4.5-0ubuntu1.2) to 4:4.4.5-0ubuntu1.3
kdelibs5 (4:4.4.5-0ubuntu1.2) to 4:4.4.5-0ubuntu1.3
kdelibs5-data (4:4.4.5-0ubuntu1.2) to 4:4.4.5-0ubuntu1.3
libgnutls-dev (2.8.5-2ubuntu0.5) to 2.8.5-2ubuntu0.6
libgnutls26 (2.8.5-2ubuntu0.5) to 2.8.5-2ubuntu0.6
libplasma3 (4:4.4.5-0ubuntu1.2) to 4:4.4.5-0ubuntu1.3
libssl0.9.8 (0.9.8k-7ubuntu8.15) to 0.9.8k-7ubuntu8.18
libxalan2-java (2.7.1-5ubuntu1) to 2.7.1-5ubuntu1.1
linux-generic (2.6.32.60.67) to 2.6.32.61.68
linux-headers-generic (2.6.32.60.67) to 2.6.32.61.68
linux-image-generic (2.6.32.60.67) to 2.6.32.61.68
linux-libc-dev (2.6.32-60.122) to 2.6.32-61.124
openssl (0.9.8k-7ubuntu8.15) to 0.9.8k-7ubuntu8.18

Installed the following packages:
linux-headers-2.6.32-61 (2.6.32-61.124)
linux-headers-2.6.32-61-generic (2.6.32-61.124)
linux-image-2.6.32-61-generic (2.6.32-61.124)


For mplayer, I get below message

Warning unknown option dsize at line 6
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing a.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [H264]  1280x720  24bpp  29.979 fps  3051.2 kbps (372.5 kbyte/s)
Clip info:
 Software:  
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
[VO_XV] Could not grab port 75.
[VO_XV] Could not grab port 76.
[VO_XV] Could not grab port 77.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================



Thank you.

---

### Post by Yellow Pasque on 2014-06-09
It's a problem with the -61 kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1327014](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1327014)

Boot into the previous kernel (hold shift when you boot to get grub menu).

---

### Post by ajgreeny on 2014-06-09
But you are at risk of breaches of security if you are still using Lucid 10.04 as a desktop system and really ought to update to a newer version.

If your hardware will not run unity properly, as some older machines will not, I suggest you have a look at Lubuntu or Xubuntu 14.04, both of which should be OK on a computer which ran 10.04 with gnome 2.

---

### Post by tojonukokhadush on 2014-06-09
i could not play videos with vlc as well! i would better update to 12.04 asap! but **[COLOR=#000000][ajgreeny]("http://ubuntuforums.org/member.php?u=27747")[/COLOR]** i would like to know what do you mean by "risk of security breaches". i was hesitating to upgrade to 12.04 as i have low configuration old laptop![B][COLOR=#000000]
[/COLOR][/B]

---

### Post by ajgreeny on 2014-06-09
> **tojonukokhadush said:**
> i could not play videos with vlc as well! i would better update to 12.04 asap! but **[COLOR=#000000][ajgreeny]("http://ubuntuforums.org/member.php?u=27747")[/COLOR]** i would like to know what do you mean by "risk of security breaches". i was hesitating to upgrade to 12.04 as i have low configuration old laptop![B][COLOR=#000000]
[/COLOR][/B]
Security breaches as a result of no further package security updates to any of the GUI parts of ubuntu 10.04 is what I meant.

If your hardware is too old to run Unity properly I suggest you look at Xubuntu 14.04 first, and if that is still too slow maybe Lubuntu 14.04.

---

