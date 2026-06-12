---
title: "Problems to play MKV in Ubuntu 11.10"
date: 2011-10-17
forum: Multimedia Software
---

### Post by fernandoc1 on 2011-10-17
I'm unable to play MKV files in Ubuntu 11.10.

The message that shows to me when I try to open in TOTEM is:
"Could not find GStreamer caps mapping for FFmpeg codec 'h264', and you are using an external libavcodec. This is most likely due to a packaging problem and/or libavcodec having been upgraded to a version that is not compatible with this version of gstreamer-ffmpeg. Make sure your gstreamer-ffmpeg and libavcodec packages come from the same source/repository."

The system used here was: Ubuntu 11.04 64bit with Nvidia Geforce 8800 (Driver 260.19.06). The same file that I tried here, worked in Ubuntu 10.10 32 bit, properly.

The fact that the system is not able to handle the quality and size of the file is not an excuse for not playing, because the same computer can play it on older versions of Ubuntu and in Windows.

I have installed ubuntu-restricted-extras before trying to play the file.

Can someone help me?

---

### Post by SeijiSensei on 2011-10-17
Install **smplayer** and, if you're comfortable installing from repositories, follow [these instruction]("http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html")s to replace mplayer with **mplayer2**.  Make sure you're using the NVIDIA proprietary video driver and select "vdpau" from the drop-down list in smplayer at Options > Preferences > General > Video.

---

### Post by raideen on 2011-10-23
I've read the same workarounds elsewhere, but this used to work with Totem in 11.04. A fresh installation (with the proper packages, of course) results in the same issue. It has been filed as [bug 879066]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/879066"). Those who have the issue should register and mark themselves as being affected.

---

### Post by amr-maro on 2011-11-03
I can't either play any .mkv videos in Totem. The difference here that I don't get any messages, they just don't play. I see only the first frame of the video freezing on Totem where it says "Playing" at the left-bottom and the time stays 0:00 / 0:00.

---

### Post by hydroxph on 2011-11-03
Have you tried using VLC player?

---

### Post by davdo2004 on 2011-11-03
> **fernandoc1 said:**
> I'm unable to play MKV files in Ubuntu 11.10.

I have installed ubuntu-restricted-extras before trying to play the file.

Can someone help me?

Sure, use VLC or mplayer. Totem is a poor choice for a default video player in Ubuntu.

---

### Post by rushikesh988 on 2011-11-03
> **fernandoc1 said:**
> I'm unable to play MKV files in Ubuntu 11.10.

The message that shows to me when I try to open in TOTEM is:
"Could not find GStreamer caps mapping for FFmpeg codec 'h264', and you are using an external libavcodec. This is most likely due to a packaging problem and/or libavcodec having been upgraded to a version that is not compatible with this version of gstreamer-ffmpeg. Make sure your gstreamer-ffmpeg and libavcodec packages come from the same source/repository."

The system used here was: Ubuntu 11.04 64bit with Nvidia Geforce 8800 (Driver 260.19.06). The same file that I tried here, worked in Ubuntu 10.10 32 bit, properly.

The fact that the system is not able to handle the quality and size of the file is not an excuse for not playing, because the same computer can play it on older versions of Ubuntu and in Windows.

I have installed ubuntu-restricted-extras before trying to play the file.

Can someone help me?
USE VLC or SMPLAYER I ALSO GOOD....
> % sudo apt-get update
% sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

---

### Post by amr-maro on 2011-11-03
All types of videos were playing beautifully in Totem before Ubuntu 11.10 and I never had to use Mplayer or VLC until now I have to use Mplayer with .mkv videos.

---

### Post by amr-maro on 2011-11-03
I filed another bug that is more consistent to my problem [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/885793](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/885793).

---

### Post by Kyoushuu on 2011-11-05
Try running Totem in a terminal. It should show some error message from GStreamer. I also have the same problem when I reinstalled Oneiric, then the error message shows that I need gstreamer0.10-ffmpeg to be installed (not sure, maybe its "gstreamer0.10-plugins-good", but it should be installed automatically, I already forgot).

---

