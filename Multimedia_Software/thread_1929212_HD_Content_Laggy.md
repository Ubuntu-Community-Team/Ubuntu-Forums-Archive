---
title: "HD Content Laggy"
date: 2012-02-21
forum: Multimedia Software
---

### Post by yusuo85 on 2012-02-21
I dual boot Windows and Ubuntu 10.04 together on my laptop and watch alot of 1080p content which works perfectly on my Windows partition with Media Player Classic and it runs fine as long as the format is MKV.

However on my Ubuntu partition i have no luck and its very jiterry and laggy. Ive tried to install all codecs that I was previously advised todo ([http://ubuntuforums.org/showthread.php?t=1879299]("http://ubuntuforums.org/showthread.php?t=1879299")) However it still doesnt work ive tried to install Mplayer 2 and it really doesnt work.

Is there anyway I can sort this as although I do like Ubuntu I can't use it unless i can watch my movie collection.

---

### Post by SeijiSensei on 2012-02-22
What kind of video card do you have?  If it's a recent NVIDIA model, make sure you're using "vdpau" for your video output driver.  (From the command line, use "mplayer -vo vdpau [other options] file.mkv".  In smplayer, you can set the video driver in Options > Preferences > General > Video.

mplayer2, as installed from Ripps' PPA, works just fine here.  You really don't need any other codecs with mplayer; it has its own codec libraries.  Sometimes it's best to uninstall any extra codecs you might have added and just use mplayer/mplayer2.  (You will need restricted-extras if you watch DVDs though, regardless of the player you use.)

---

