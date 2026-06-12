---
title: "xine mp3 playback no longer works"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by sirjis on 2007-08-30
I'm not entirely sure what I did to cause it, but Amarok (and all other mp3 players that use the xine engine) no longer play mp3 files.  They give me an error which is like "xine: couldn't find demux for filename.mp3".  This is on edgy.

I've searched all around for ways to fix this, and it seems to be a fairly common problem.  I have uninstalled and reinstalled Amarok and xine-ui.  I've also uninstalled and reinstalled libxine-extracodecs and installed libxine-dev.  I installed libxine-dev because it was complaining about lack of a xine-config file when I ran xine-check, and some website suggested that doing this would fix it.  

Here is the output of xine-check:
```

xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.17-10-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ hint ] multiple xine executables found
         I have found multiple xine executables on your machine:
         /usr/bin/xine
         /usr/X11R6/bin/xine
         xine is the main player as installed by the xine-ui package.
         You should probably uninstall the instances you don't use...
         press <enter> to continue...

[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[ hint ] several instances of xine-config found in your PATH
         xine-config executables have been found in these places:
         /usr/bin/X11/xine-config
         /usr/bin/xine-config
         This probably means you have several versions of xine-lib installed.
         It's probably best to uninstall all unused xine-libs.
         Further tests will use /usr/bin/X11/xine-config.
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins/1.1.2 exists.
[ good ] found unknown plugin: xineplug_flac.so

[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12
```

Could the duplicate entries be the problem?  I think that neither one is a symlink to the other, since they both show up as green using ls.

Possibly related: I find it strange that when I type "sudo aptitude install xi" and then hit tab, a package with the name of "xine" exists, but when I complete it and hit enter, it says it could not find xine.  And when I try reinstall instead of install, it says it could not reinstall because it wasn't installed.  Is there any reason why something would show up in the tab list and not be recognized?

---

### Post by sirjis on 2007-09-02
Are there any more diagnostics besides xine-check that I should run that would provide more information to help get mp3 playback working again?

Or is there a way to get Amarok to use gstreamer?

Any links or steps to get me started would be greatly appreciated.  Thanks!

---

### Post by planck2007 on 2007-09-05
I had the same problem which I solved by deleting the .xine directory in my home directory. At this point xine was able to play mp3 files

Daniele

---

### Post by sirjis on 2007-09-05
Thank you so much!  That worked perfectly.  

Apparently, I had already done that before once when this happened before (I remember it happening, just not how I fixed it), because there was already a .xine-bkup folder that I had made.

Thanks again.  I'm glad to have Amarok back.

---

