---
title: "MP4  sound output not recognised in Ubuntu 22.04 (MSI A520M-A PRO board)"
date: 2024-12-04
forum: Multimedia Software
---

### Post by Robbyx on 2024-12-04
A telephone app in a web portal has suddenly stopped broadcasting sound. This only happened in the last few days post a kernel update. I need access sound access to the portal restored quickly as it is my telephone line. 

I have tried pulseaudio -k  and it made no difference. 

I checked the device sound setup in settings and the test sound outputs were not responding. Gradually i have discovered that my system still plays the sound from videos encoded via  webm but not mp4. 

I am assuming that the website telephone app's loss of sound in and out  is somehow connected to the failure in the  mp4 playback.

The output devices in volume control via pavucontrol shows I have two sound devices one in an hdmi tv set and the other a Family 17m hd audio controller analogue stereo, which is connected to desktop speakers. 

I am using firefox for web browsing and the app called Videos for playing locally stored videos.  

How do I restore the playback and output sound?

---

### Post by TheFu on 2024-12-16
First, webm and mp4 aren't codecs, they are containers.  webm is a highly restricted mkv container.  mp4 is a container type for about 4 different video codecs and a few audio codecs.

Regardless, you'll need to determine the video and audio codec in the files that work and don't work before anyone could possibly help.  **mediainfo** is a tool that will show the codecs and a few important settings for the encoding of each track. There are other tools, if you prefer.

Additionally, the playback software will matter, so try using **mpv**, **mplayer**, **vlc** with each different type of file. Browsers support specific codecs only and google has pushed for the restricted video and audio codecs supported by webm containers to be supported in all modern web browsers. Google uses patent-free codecs, unlike the mp4 container, which can use mostly patent-tied-down codecs.

Getting audio or video working inside a web browser is far beyond my skills. Sorry.  I would begin by determining the specific codecs used and ensure those are supported by the browser as a first step.  Since Ubuntu moved to a snap-based install of firefox, if you are using it, if you need to install any binary add-on extension to support proprietary codecs, you'll want to seek out how to guides for that.  I don't use snaps for desktop stuff.

I don't know what the "Videos" application real-name is.  Wish Canonical/Debian/Gnome would stop renaming things in the menus from the actual program names to generic terms.  Makes helping others challenging.   "Files" is usually "Nautilus", for example.  I just hope that "Videos" isn't "gstreamer".

BTW, inside **pavucontrol**, it is best to have only 1 output device enabled at a time, especially when troubleshooting.  So, either use the onboard audio or the HDMI/TV audio, not both.

---

