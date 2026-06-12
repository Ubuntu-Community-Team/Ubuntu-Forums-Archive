---
title: "[SOLVED] Ubuntu 8.10 64 AMD Playing Movie DVDs"
date: 2008-12-13
forum: Multimedia Software
---

### Post by Robster2 on 2008-12-13
I cannot get the Movie DVDs to play on this Computer under Ubuntu 8.10. 64 bit

I have done all the usual things add Medibuntu repositories.  Downloaded 64 AMD codecs.

I am close I can get play back for about 10 seconds and then it stops or I get an error message.

I have tried Totem and VLC.

I am using a Toshiba Satelite 2 GHZ  2 GB Memory 64x2 AMD.

Any ideas?  

Did Hardy Heron or Gutsy Gibbon 64 bit have the same problem?

---

### Post by Robster2 on 2008-12-13
How embarrassing !  You post a message and the answer is above you on the same page!

Thanks to Ubuntu Freak.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Put this in the terminal

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar

VLC works best for a whole screen experience.   :p

---

