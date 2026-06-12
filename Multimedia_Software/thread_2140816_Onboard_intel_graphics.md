---
title: "Onboard intel graphics"
date: 2013-04-30
forum: Multimedia Software
---

### Post by BcRich on 2013-04-30
Hi 
Am I being punished for using onboard intel graphics?
It kinda feels that way.
Basically, I have a major problem with screen tearing on a Celeron 847, with 2GB RAM and onboard Intel Graphics that uses i915 drivers on Ubuntu 13.04 (Vanilla)  
Heres wut lspci -v turns up 
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Device 1b0a:015b
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


```
Tearing is most insane when the screen changes/updates images fast. I've attached a screenshot (just incase it sounds like I'm exaggerating).
I'm getting the same results with LXDE, Mint13, Ubuntu 12.10 and Openbox on the same machine. The weird thing is that occasionally Ubuntu 13.04 sometimes manages to display without tearing! But after a couple of reboots the problem seems to be back,  then disappears, then it's back again ...I kid you not.
I've also tried upping the allocated RAM to the GPU but this had no effect, plus tried some compiz workarounds, but nothing seems to work.
PPPPPlease Ubuntu Pimp my onboard Intel GPU :_(

---

### Post by papibe on 2013-04-30
Hi  BcRich.

Have you tried setting VSync on CCSM? if not, take a look at [this]("http://askubuntu.com/questions/73909/screen-tearing-in-11-10-with-intel-graphics").

Let us know how it goes.
Regards.

---

### Post by BcRich on 2013-05-04
Hi papibe
Thanks for the help :)
Yes, I've tried those options and workarounds which seem to offer some improvement in Unity and Gnome. So your info is certainly useful, however what I'd really like is to get the tearing to disappear (or atleast improve) in LXDE. I've tried this workaround [http://askubuntu.com/questions/240923/enable-sync-to-vblank-on-lxde-with-intel-video-card](http://askubuntu.com/questions/240923/enable-sync-to-vblank-on-lxde-with-intel-video-card) but the compromise is that the tearing is improved drastically but at the expense of the system becoming very unresponsive and slOOoow. Do you perhaps know of any suggestions on how to achieve a sort of balance between these two extremes? maybe tweak the parameters in the posted askubuntu question, as i really have no idea what those settings are doing (but they seem to be doing something right).

---

### Post by Bucky Ball on 2013-05-04
*Thread moved to **Multimedia & Video***

---

### Post by tgalati4 on 2013-05-04
Open a terminal, post the output of:

```
glxgears -info
```

It should look something like:

298 frames in 5.0 seconds = 59.571 FPS
298 frames in 5.0 seconds = 59.554 FPS
298 frames in 5.0 seconds = 59.551 FPS
299 frames in 5.0 seconds = 59.749 FPS
299 frames in 5.0 seconds = 59.750 FPS

Control-C to quit.

It's possible that your video shares RAM with the main RAM.  Check your settings in BIOS and bump up the Video RAM if possible.  If your rendering is below 24 frames per second, then you will see flicker--just like the movies!

These results are from an Acer laptop with Intel graphics also running i915 module:

tgalati4@Mint14-Extensa ~ $ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

tgalati4@Mint14-Extensa ~ $ lsmod | grep video
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
video                  19391  2 i915,acer_wmi

---

