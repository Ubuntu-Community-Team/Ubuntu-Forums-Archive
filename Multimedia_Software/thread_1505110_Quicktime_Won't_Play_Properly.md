---
title: "Quicktime Won't Play Properly"
date: 2010-06-08
forum: Multimedia Software
---

### Post by elfortunawe on 2010-06-08
I recently got a Canon Powershot SD780 IS. It takes HD video at 780p. It's great, except that the videos won't display properly in Ubuntu Netbook Remix (Lucid) on my Dell Mini 10v.

I've tried using Gstreamer (Banshee), Xine (Totem-xine), and MPlayer (GNOME MPlayer). These all should have worked, which makes me think something may be wrong either with the files themselves or my computer. Anyone have any idea what's going on here?

FYI, when I pull up the Properties dialogue for one of the videos and look in the Audio/Video tab, it says:

Video
  Dimensions:  1280 x 720
  Codec:       H.264 / AVC
  Framerate:   30 frames per second
  Bitrate:     N/A

Audio
  Codec:       Raw 16-bit PCM audio
  Channels:    Mono
  Sample rate: 44100 Hz
  Bitrate:     N/A

---

### Post by Jinger on 2010-06-09
Have you tried using Vlc?

---

### Post by elfortunawe on 2010-06-09
I hadn't, thanks.

EDIT:

Just tried it, still not playing right. I should probably mention that the problem is the same in every case: video starts then freezes and sometimes starts again (but not in sync with the audio), while audio continues to play.

But VLC did tell me that the video codec is specifically AVC1, which seems to have been problematic [for]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/454714") <a href="http://ubuntuforums.org/showthread.php?t=1191352&page=2">others</a>.

EDIT:

Uninstalled GNOME MPlayer, reinstalled MPlayer by itself. Playing files with MPlayer from the cm works fine. :confused:

---

### Post by Jinger on 2010-06-09
Let's try! Download Kino through this command:
```
sudo apt-get install kino
```

After installing, import the quicktime video in this programme and the video will turn into a file.dv . Try opening it with Vlc.

---

### Post by no2498 on 2010-06-10
if what Jinger said does not help

try smplayer it loads more codes like 264 for mp4's

open a terminal type, smplayer click enter
it tells you how to install it

hope this helps

---

