---
title: "Xine: There is no Mrl"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by prokoro on 2008-01-21
Hi, I new to Ubuntu 7.10 coming from Mandrake 10.1. Xine is my favorite software. Can someone help configure Xine to work.
when i run xine-check this is the result
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.22-12-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/local/bin/xine-config in your PATH
[ good ] plugin directory /usr/local/lib/xine/plugins/1.1.6 exists.
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[OUCH!!] no skin directory (/usr/local/share/xine/skins)
         The skin-directory doesn't exist. xine-config claims that there
         is a skin directory at /usr/local/share/xine/skins.
         However, there is no such directory.
         You probably need to reinstall xine-ui.
         press <enter> to continue...
    
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
[ good ] Xv ports:  YUY2 YV12 I420 RV15 RV16

---

### Post by dixonstalbert on 2008-01-21
Hi Prokoro


I have been using gui for xine : gxine  for playing dvds and listening to streams without problems.

I ran xine-check and got multiple error messages:

[ good ] plugin directory /usr/lib/xine/plugins exists.
[ good ] found unknown plugin: *.so
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

So I am not sure if xine-check works on Debian systems. I installed all these codec with medibuntu and maybe they are in different directories...

I notice your error message from xine-check was about no skin directory in /usr/local/share... 

xine-check on my system is dated march 17 2007 and script looks for skins in /usr/share... 
Did you install xine from synaptic or add-remove programs option?

---

### Post by jerrykenny on 2008-01-21
You possibly have all the xine libraries, but not the gui . . . 

try

[SIZE="4"]sudo apt-get install xine-ui[/SIZE]

edit, i get a heap of ouches as well, but xine works ok, is xine being problematic ? if its not playing particular files its prob just the lack of certain codecs, rather than the installation

---

### Post by prokoro on 2008-01-22
I can't seem to get xine to work. I installed kmplayer which is using xine as it backend. Everytime I start xine  the screen closes before the dvd starts to work. Kmplayer will play at least so I stick with it for now. As far as xine skins I can't seem to find them for ubuntu.

Thank-you for your help.

---

