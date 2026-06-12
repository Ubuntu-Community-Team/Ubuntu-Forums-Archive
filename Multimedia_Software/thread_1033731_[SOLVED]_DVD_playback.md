---
title: "[SOLVED] DVD playback"
date: 2009-01-07
forum: Multimedia Software
---

### Post by SS7 on 2009-01-07
I've fooled around for a bit trying to get my DVD playback working with no luck.

I've recently installed 8.10.

I've installed the following in hopes to achieve encrypted DVD playback:
libdvd4nav
libdvdread3
gstreamer0.10-plugins-ugly
gxine

I was previously getting a NAV error with totem before running the following command (after installing the previously mentions packages):
sudo /usr/share/doc/libdvdread3/install-css.sh

gxine gives me an "Encrypted or faulty DVD"

I've tried 2 dvds.

Any obvious error?  Any recommendations?

Thanks,
SS

---

### Post by steeleyuk on 2009-01-07
You need to install libdvdcss2.

[Playing encrypted DVDs]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs").

---

### Post by SS7 on 2009-01-07
Thanks, that was another installed but not listed.  A couple of the recommendations were added as package requirements.

I've also since added VLC and removed gxine.  Still no luck.

Also tried the following command (errored "E: Couldn't find package non-free-codecs"):
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

SS



SS

---

### Post by SS7 on 2009-01-07
I've since removed and reinstalled the packages.

Video is now working with VLC, however, it is quite choppy.

I'm running the FGLRX driver with my radeon9800.  

Is there any recommendation for smoother quality video?

SS

---

