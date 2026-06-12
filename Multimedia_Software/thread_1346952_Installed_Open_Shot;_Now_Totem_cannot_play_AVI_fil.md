---
title: "Installed Open Shot; Now Totem cannot play AVI files"
date: 2009-12-05
forum: Multimedia Software
---

### Post by Szdfan on 2009-12-05
I installed and then uninstalled Open Shot.  I am no longer able to play AVI files.  The developer appears to be aware of the problem -- it appears the ppa installation of Open Shot removes certain required packages -- 
[https://answers.launchpad.net/openshot/+faq/723](https://answers.launchpad.net/openshot/+faq/723)

How do I reinstall these packages?  When I try to run an AVI file in the movie player, I get the message "Internal Data Stream Error."  In terminal, I get the following error message --

[FONT="Courier New"][SIZE="3"]** Message: Error: Internal data stream error.
gstavidemux.c(4443): gst_avi_demux_loop (): /GstPlayBin2: play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstAviDemux:avidemux0:
streaming stopped, reason not-negotiated[/SIZE][/FONT]

---

### Post by mc4man on 2009-12-05
see here, various ways to do the same thing 
[http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

if you wish openshot after fixing things then 2 choices...
use this version instead
[https://launchpad.net/~jonoomph/+archive/openshot-edge](https://launchpad.net/~jonoomph/+archive/openshot-edge)

or first  build a static x264 and ffmpeg to /usr/local, then build the dev. openshot from the source in the ppa you had. (a bit of work but will remove the dep on the shared ffmpeg libs that bork vlc, totem ect.

---

### Post by Szdfan on 2009-12-05
That made it work.  Thanks!

Not sure if I want to try Open Shot again, but will consider it.

---

### Post by carolinason on 2010-01-20
openshot total yorked my system and lost most all my audio and video software functionality i tried the fixes in the forums, but they didn't work.

AUGH!

---

### Post by n3had on 2010-01-20
> **carolinason said:**
> openshot total yorked my system and lost most all my audio and video software functionality i tried the fixes in the forums, but they didn't work.

AUGH!

I was just thinking of installing the latest version and thanks but no thanks will give it a shot when its clean btw mplayer was borked due to openshot-ffmpeg had to purge all the openshot related packages and now things are fine.

---

