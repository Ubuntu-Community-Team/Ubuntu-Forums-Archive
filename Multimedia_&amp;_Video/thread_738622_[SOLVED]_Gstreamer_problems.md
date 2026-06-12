---
title: "[SOLVED] Gstreamer problems"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by charliwest on 2008-03-28
Hello, I'm a fairly new user to Xubuntu and am having some trouble. I'm trying to use songbird, and loving the look and feel of it. Only one major issue so far... I can't play any music with it. Every track I try it mentions about GStreamer, I have checked my synaptics package it is telling me that the core and some add-ons are installed, so I tried adding a few more just incase, still no luck. So although I love the look of this program it is next to useless at the moment :( I hope someone can help.

I am running on Xubuntu 7.10 and songbird 0.5. I've tried following [http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer) and the terminal bit doesn't play mp3's and I have the debug print if anyone can help.

I am a bit of a noob but have set this instaltion up with emeralde, compiz and a few other bells and whistles so know a bit. Any help would be great.

Thanks

---

### Post by granny6989 on 2008-03-28
Try installing gstreamer plugins from synaptic, sets are called ugly and ugly multiverse. Make sure and enable multiverse repositories under the settings tab in synaptic first. These are ususlly the ones you need to get mp3, etc support.

whoops, didn't realize you are on Kubuntu... Try this:

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

S*

ooops' I mean Xubuntu...
should fix it one of those two ways.

---

### Post by charliwest on 2008-03-29
Yeah I have added both the ugly and bad and multiverse for both as well.

I had seen that page before, but it actually doesn't include Xubuntu for 7.10, but have already added both the packages they suggest anyway. :(

---

### Post by charliwest on 2008-04-02
Just so you know, incase anyone was checking this I seem to have resolved the issue. I uninstalled all the items relating to gstreamer that I could with recking anything else, and also removed the ubuntu restricted extra's package, then put all the gstreamer stuff back, and now its working! 

Thanks for looking.

---

