---
title: "Xine no plugins in Gutsy?"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by MikePB on 2007-10-28
Hey all. I'm having trouble getting some of my audio to play. Gstreamer doesn't show up in Amarok, so I can't try that.

I was trying some stuff and got this when I ran xine-check:

> 

Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.22-14-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ hint ] No xine-config found. Assuming xine from Debian package
         The xine-config script can be used to determine some file locations
         used by xine-lib, but you don't have such a script on your system.
         However, it looks like you installed xine from the Debian packages.
         So I'll just guess that you are using the standard locations.
         If you want me to be sure about those file locations, you can install
         the 'libxine-dev' package, which contains xine-config. However, this
         package is not really needed to run xine...
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins exists.
[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/scd0

[ good ] /dev/dvd points to /dev/scd0
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...
[ good ] found xvinfo: X-Video Extension version 2.2

[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 YUY2 YV12 UYVY I420



While it says to reinstall xine-lib, I couldn't find it anywhere, and I tried xinelib, libxine, etc. I'm at a loss. I've got over 20k songs and all the media players I've tried only seem to find/read 419 of them. I'm at a loss!

---

### Post by aidanr on 2007-10-28
It's libxine1

---

### Post by MikePB on 2007-10-28
Okay, checked that, here's what I got:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1 is already the newest version.
libxine1 set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


What does 'libxine1 set to manual installed." mean?

---

### Post by pashashome on 2007-10-28
This link seems to state what set to manual installed means. Man I spent a bit of time in man apt-get and didn't come close to seeing what that means.

[https://lists.ubuntu.com/archives/ubuntu-users/2007-April/112756.html]("https://lists.ubuntu.com/archives/ubuntu-users/2007-April/112756.html")

---

### Post by MikePB on 2007-10-29
Yikes! Okay...After playing around, I tried playing the music in Kaffiene. Still didn't work, however, it did give me a permissions error...

Okay, going with that, how can I change the permissions on that drive? It's an ext3 external USB drive.

---

### Post by GPRawb on 2007-11-01
Hello,

I'm somewhat a new user to Ubuntu, ran 7.04 for a bit and had issues setting up partitions yadda yadda :D

anywho, i'm using 7.10 now and I'm having a similar issue, except its with all purchased DVD that don't play.

I've look into installing whatever codecs I can find for xine (libxine1) and still get the error when I run xine-check

Here's a copy of the check

[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.22-14-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ hint ] No xine-config found. Assuming xine from Debian package
         The xine-config script can be used to determine some file locations
         used by xine-lib, but you don't have such a script on your system.
         However, it looks like you installed xine from the Debian packages.
         So I'll just guess that you are using the standard locations.
         If you want me to be sure about those file locations, you can install
         the 'libxine-dev' package, which contains xine-config. However, this
         package is not really needed to run xine...
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins exists.
[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/scd0
[ good ] /dev/dvd points to /dev/scd0
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  RGBA RGBT RGB2 YUY2 UYVY YV12 I420

any pointers for a newbie?

Thanks,

Rob

---

### Post by bidjix on 2007-11-06
I have the exact same problem.
edit: I'm reffering to the output of xine-check. All of my audio seems to play fine.

I reinstalled libxine1, still nothing.

I'm able to play my .AVI-s, but the video quality is horrible when I enable fullscreen. I had no problems of this sort prior to upgrading to Gutsy.

In Kaffeine, under Settings -> xine Engine Parameters -> video -> begginer options -> driver I can only set "auto". Everything else seems to produce an error.

---

