---
title: "[SOLVED] Video Player/Codec problem"
date: 2009-01-10
forum: Multimedia Software
---

### Post by jak113 on 2009-01-10
Not long ago I had only been running Ubuntu, however I recently repartioned my hard drive in order to change back to a dual-boot. I'm not quite sure what happened along the way, but now my system seems to disagree with playing video files.

I'd installed the various gstreamer codes as well as VLC the same as I had before, however when I attempted to watch a .ogm file I've ran numerous times VLC opened it up and promptly closed. The same thing happened with Totem as well as mplayer. When opened in GNOME Mplayer, it doesn't close the window and you can hear the audio, however there is still no video. Tried the same thing with a .avi file, but the same error occured.

Uninstalled the codecs again and attempted to run the file in Totem and received this error message:

"An error occured

The playback of this movie requires the following decoders which are not installed:

MPEG-1 Layer 3 (MP3) decoder
XVID MPEG-4 decoder"

Installing either the "GStreamer ffmpeg video plugin" or the "GStreamer extra plugins" and re-opening the file doesn't bring up the error message but once again causes the player to close. Needless to say, the same thing happens when both are installed.

I'm running an ATI video card on the built-in Ubuntu drivers, the same as I had on the previous single-boot so nothing should have changed there. Excepting that something somewhere along the way got mixed up and I could use some assistance figuring out where to start. I'd appreciate the help.

---

### Post by wmoore on 2009-01-10
Mrs M has been having the same issue on her Fedora 9 laptop. I'm still not 100% sure but I believe the radeon driver has been updated and is causing this issue. I fixed it on her laptop by changing to the radeonhd driver in xorg.conf.

> **jak113 said:**
> Not long ago I had only been running Ubuntu, however I recently repartioned my hard drive in order to change back to a dual-boot. I'm not quite sure what happened along the way, but now my system seems to disagree with playing video files.

I'd installed the various gstreamer codes as well as VLC the same as I had before, however when I attempted to watch a .ogm file I've ran numerous times VLC opened it up and promptly closed. The same thing happened with Totem as well as mplayer. When opened in GNOME Mplayer, it doesn't close the window and you can hear the audio, however there is still no video. Tried the same thing with a .avi file, but the same error occured.

Uninstalled the codecs again and attempted to run the file in Totem and received this error message:

"An error occured

The playback of this movie requires the following decoders which are not installed:

MPEG-1 Layer 3 (MP3) decoder
XVID MPEG-4 decoder"

Installing either the "GStreamer ffmpeg video plugin" or the "GStreamer extra plugins" and re-opening the file doesn't bring up the error message but once again causes the player to close. Needless to say, the same thing happens when both are installed.

I'm running an ATI video card on the built-in Ubuntu drivers, the same as I had on the previous single-boot so nothing should have changed there. Excepting that something somewhere along the way got mixed up and I could use some assistance figuring out where to start. I'd appreciate the help.

---

### Post by 2hot6ft2 on 2009-01-10
Try re-installing the codecs

Put this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)
When it gets to the agreement hit Tab then Enter to accept the Java agreement.

---

### Post by jak113 on 2009-01-11
Thanks for the advice.

Re-installing the codecs again still did not alleviate the problem. However, when I switched over to the ATI FGLRX driver, the video files would run. Catch there, the screen inside the video player flickers constantly, whether the file is paused or not. I've tried opening three different files, 2 .ogm's and an .avi, in three different video players. Totem, VLC, and GNOME Mplayer, all to the same effect. Other than that, the video looked fine.

I've also removed and re-installed the "ubuntu-restricted-extras" files in Terminal while running the FGLRX drivers to no effect.

Any suggestions? Thanks in advance.

Just fyi, I'm running Intrepid.

---

### Post by deanjm1963 on 2009-01-11
Make sure "libxvidcore - just search for xvidcore in synaptic" is installed and install gstreamer0.10-ugly + ugly-multiverse are installed ... I had a similar problem with Hardy.

Hope this helps

Flickering will occur if you use compiz while running videos using ATI/fglrx drivers. Install "fusion-icon" to "enable/disable" compiz as you need.

---

### Post by jak113 on 2009-01-11
Disabled compiz and the flickering's all gone. Thanks for the help. It was appreciated.

---

