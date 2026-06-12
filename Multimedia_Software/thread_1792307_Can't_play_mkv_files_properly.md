---
title: "Can't play mkv files properly"
date: 2011-06-28
forum: Multimedia Software
---

### Post by flagstar on 2011-06-28
I owned a eee pc 900HA netbook which I installed with Ubuntu 10.04 and Windows XP on separate partition...

I've been using Ubuntu for almost 2 years now and the thing is, I still got this problem since 9.10.

In Windows, I was able to play an .mkv files fully playable on 480p but not with 720p. In Ubuntu, it have problem even playing 480p mkv files and also with flv 480p. 720p is already out of question. By default, it'll download a codec used to play mkv files when the first time I try to run the video.

I have no problem with playing other format (AVI, OGG) on 480p or lower mkv, flv resolution. Is there a reason why it can't run normally on Ubuntu but perfectly rendered in Windows?

I've try almost all codec (mplayer, totem, vlc) but still have problem running at full speed.

---

### Post by SeijiSensei on 2011-06-28
It's likely that the files you're trying to play include video encoded with the H.264 codec.  This is a highly-compressed format that requires some serious CPU power to decode at full-speed.  The 1.6 GHz Atom processor in your netbook isn't really up to the task.  I'm not sure whether there's anything out there that will fix this problem for you entirely.

I've used mencoder to re-encode H.264 videos in the Matroska container to XviD encodings in the AVI container when I had a machine without the horsepower to play 720p H.264 files.  Posting #4 in [this thread](https://bbs.archlinux.org/viewtopic.php?id=56202) provides the code required if you want to go down this path.

---

### Post by BicyclerBoy on 2011-06-28
The windows intel graphics driver is very likely able to take maximum advantage of the weak graphics.

Does you netbook use 945GME chipset graphics ?
This chipset has GMA900 graphics & has some basic video decode functions.

Use ffmpeg or mediainfo or VLC to determine the video codec etc used in your mkv.

A workable solution for me was:
ubuntu netbook remix 10.10 (3 months ago)
945GME
atom cpu
H264 576i (watchable could be dropping frames, looks like slow LCD TV)
i915 driver (xorg-edgers ppa)

A couple lines in xorg.conf (maybe these made no difference).
The xorg-edgers ppa made difference...without this the framerate was 1-2 fps.

720i50 not watchable
1080i50 3-4 fps, dropped frames.

Broadcomm CrystalHD mini-PCIe card could be a viable solution..there are/were some unresolved issues with drivers because Broadcomm will not co-operate.

The best soln is a new netbook with nvidia graphics or maybe the new zacate/fusion APU.

---

