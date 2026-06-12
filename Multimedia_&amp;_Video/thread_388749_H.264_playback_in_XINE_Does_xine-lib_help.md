---
title: "H.264 playback in XINE: Does xine-lib help?"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by jeeves on 2007-03-19
I installed Xine from the synaptic package manager, so I assume it added all the components it needs. Yet when I run the **xine-check **diagnotic program it complains about xine-lib missing. Is this something I should install with Xine? Oddly enough, I can't find xine-lib in the 

[B]What I am trying to fix  is an unacceptable number of dropped frame when attempting to playback high definition H.264 content with xine.
[/B]
Here are the results  **xine-check .** Any ideas on what would be the most useful to try and fix?]:

```
~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.17-11-generic)
[ good ] intel compatible processor, checking MTRR support
[ hint ] you have MTRR support but it's unused.
         It seems like your X server didn't set any MTRR ranges for the
         graphics card. Maybe upgrading your X server helps...
         You don't have a PCI graphics card, do you? AFAIK, MTRR only
         helps with AGP cards.
         press <enter> to continue...

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

[OUCH!!] no xine-config on this machine.
         This means that xine-lib is either not installed
         or it is installed in a very unusual place.
         So you should probably install xine-lib before running xine-check...
         press <enter> to continue...

[ hint ] unable to determine plugin directory
         I could not determine your plugin directory. That would be much easier
         if you had xine-config installed (see message above)...
         Note that I could not check your xine plugins.
         press <enter> to continue...

[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 YUY2 YV12 UYVY I420
```

---

