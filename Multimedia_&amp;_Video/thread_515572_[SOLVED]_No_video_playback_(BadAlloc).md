---
title: "[SOLVED] No video playback (BadAlloc)"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by IamAcoconut on 2007-08-02
Before I go into details, could you tell me how to remove all video players along with their settings and all video codecs in order to start from scratch - And what to do next?

When I try to run xine itself form the terminal I get:
```
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2257
  Current serial number in output stream:  2258
```

When trying to open a file in totem-gstreamer (totem xine had also been failing), terminal tells me:
```
(totem:8395): GStreamer-WARNING **: adding flushing pad 'video_e0' to running element 'flupsdemux0'

(totem:8395): GStreamer-WARNING **: adding flushing pad 'audio_c0' to running element 'flupsdemux0'
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 52 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```


I do know it's not so very uncommon problem, I did try to follow advice given in some threads yet to no avail, so I had no choice than starting a new thread (reinstalling from scratch is NOT an option in a long time).
BTW, here's a piece of my xorg.conf:
```
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option  	"VideoRam"      "65536"
        Option  	"CacheLines"    "1980"
EndSection
```

Thanks in advance, this is terribly important for me :(

---

### Post by RomeReactor on 2007-08-02
Hi. This may be due to the RAM available to the Intel video card (64MB); are you running Desktop Effects (Compiz), Compiz Fusion or Beryl? Try disabling them if you do, and see if it plays now.

---

### Post by IamAcoconut on 2007-08-02
I disabled C_Fusion. Now I can open xine and totem-gstreamer. 

Xine plays only sound, and didn't want to even play sound in a high-res movie.
Same with Totem and same with VLC.

And BTW, my graphic card (intel's integrated) has no memory of it's own - it rents it from RAM (512) instead. I had previously added those entries ("VideoRam" and "CacheLines") to xorg.conf to make it possible for hi-res vids to be played, which otherwise had been crashing due to (reportedly) insufficient resources.

---

### Post by RomeReactor on 2007-08-02
Maybe this entry in [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback") can be of help.

---

### Post by IamAcoconut on 2007-08-02
Wow. It works!

I mean, I fixed gstreamer, VLC and MPlayer, but then whenever I try to run xine (no arguments, no particular file) to fix it, the whole system hangs (worst crash that ever happened to me in Linux). What can I do?

Here's the output of my xine-check BTW:```
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.20-16-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ hint ] multiple xine executables found
         I have found multiple xine executables on your machine:
         /usr/bin/xine
         /usr/X11R6/bin/xine
         xine is the main player as installed by the xine-ui package.
         You should probably uninstall the instances you don't use...
         press <enter> to continue...

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
[ good ] Xv ports:  YUY2 YV12 I420 UYVY
```

---

### Post by RomeReactor on 2007-08-02
> [OUCH!!] There are no input plugins.
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

Seeing these errors, you could probably do as the output recommends and reinstall **libxine** (I couldn't find xine-lib, but suppose this is what it's called now), Look for it in Synaptic and mark it for reinstallation. While you're at it, look for **libxine1-ffmpeg, libxine1-gnome**, and **libxine-extracodecs**  and see if they're marked as broken packages--if so, then mark them all for reinstallation.

Note that this *could* further break your system. In any case, at least try to reinstall **Gxine**.

Also, does Totem work?

---

### Post by IamAcoconut on 2007-08-03
**RomeReactor**, all these packages you mention are installed - were actually reinstalled recently - and none is broken. I only don't have Gxine - been using xine-ui till now. Should I install gxine?

---

### Post by RomeReactor on 2007-08-03
Try Gxine and see if it makes a difference. Doesn't Totem-Xine work for you?

---

### Post by IamAcoconut on 2007-08-03
I'm using totem-gstreamer and it does work. Gxine hangs entire system after a few seconds, just like xine, so I assume Totem-xine would do the same. How can I reconfigure xine without using any GUI?

---

### Post by RomeReactor on 2007-08-03
Try this from the terminal:
```
mv ~/.xine/config ~
```
that will move the xine configuration file to your home folder. **Don't delete this file yet**; start Xine-UI or Gxine again so the config file gets re-generated. If you want to restore the previous configuration:
```
mv ~/config ~/.xine
```
Otherwise, if you want to keep the new configuration, feel free to delete the **config** file that's in your home folder.

That's all I can suggest to generate a new configuration file for Xine. I myself haven't used it.

---

### Post by IamAcoconut on 2007-08-03
I generated a new config file, than edited ~/.xine/config so that driver=xshm but xine still makes the system crash.

---

### Post by RomeReactor on 2007-08-03
This problem seems to be related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/39050") . A workaround could be to edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
and adding the following line in **Section  "Device"**:
```
Option "LinearAlloc" "8160"
```

---

### Post by IamAcoconut on 2007-08-05
> **RomeReactor said:**
> This problem seems to be related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/39050") . A workaround could be to edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
and adding the following line in **Section  "Device"**:
```
Option "LinearAlloc" "8160"
```
That's it. Now all the players work [mostly] ok!

---

