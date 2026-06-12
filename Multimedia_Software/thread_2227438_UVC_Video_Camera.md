---
title: "UVC Video Camera"
date: 2014-06-02
forum: Multimedia Software
---

### Post by federico9 on 2014-06-02
Good Morning guys,
I've got a UVC Video Camera, ID: 1871:0101 which I want to use on my linux pc. It works on Ubuntu 12.04 LTS, but not fine as I would.
On Windows it reaches 4000x4000 pixel, but on linux its highest definition is 640x480. I tried many programs (xawtv, cheese, motion exc.) but no one was able to fully use its potential.
I think the problem it's due to the drivers. Searching on the internet I found out Ndiswrapper, which seems to be perfect for me.
I installed the camera driver on a windows PC and then copy them to my Ubuntu machine.
I made these steps:

i) I created a directory called "driver"
ii) I executed the command "ndiswrapper -i /driver/driver_name.inf"
iii) I checked the installation with the command "ndiswrapper -l" which gave me the output:
```
aveodcnt_xp : driver installed
    device (1871:0101) present

```
iv) I executed the commands: "sudo depmod -a" "sudo modprobe ndiswrapper"
v) I executd the command "ndiswrapper -m" and added the "ndiswrapper" string to the file "/etc/module"

None of this command gave me error or remained incomplete, but my camera still has 640x480 as highest definition.
I really don't manage to have it work.
Could you help me?

Thank you!

---

### Post by tgalati4 on 2014-06-02
I am not aware of any video drivers that work with ndiswrapper.

What is the output of:

```
ndiswrapper -l
```

Lower case L--this will list the driver that you have loaded.

Video camera drivers in linux are generally lacking.  So if you have done an extensive web search for your specific camera and have not found any simple work-arounds, then you may be stuck at the lower resolution.  See what switches are available:

```
modinfo uvcvideo
```

parm:           clock:Video buffers timestamp clock
parm:           nodrop:Don't drop incomplete frames (uint)
**parm:           quirks:Forced device quirks (uint)**
parm:           trace:Trace level bitmask (uint)
parm:           timeout:Streaming control requests timeout

Sometimes you need a quirk switch to activate a specific feature on your video camera.

---

### Post by federico9 on 2014-06-02
Thank you for having replied. When I executed the command "modinfo uvcvideo" I get this output:

```
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/media/usb/uvc/uvcvideo.ko
version:        1.1.1
license:        GPL
description:    USB Video Class driver
author:         Laurent Pinchart <laurent.pinchart@ideasonboard.com>
srcversion:     522EC7538EA0B6E2E671A4F
alias:          usb:v*p*d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v1C4Fp3000d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v1B3Bp2951d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v19ABp1000d00*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v19ABp1000d01[0-1]*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v19ABp1000d012[0-6]dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v199Ep8102d*dc*dsc*dp*icFFisc01ip00in*
alias:          usb:v18ECp3290d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v18ECp3288d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v18ECp3188d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v18CDpCAFEd*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v1871p0306d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v17EFp480Bd*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v17DCp0202d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v174Fp8A34d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v174Fp8A33d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v174Fp8A31d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v174Fp8A12d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v174Fp5931d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v174Fp5212d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v152Dp0310d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v13D3p5103d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v0E8Dp0004d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v0BD3p0555d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v0AC8p3420d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v0AC8p3410d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v0AC8p332Dd*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v06F8p300Cd*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05E3p0505d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05C8p0403d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05ACp8501d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05A9p2643d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05A9p264Ad*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05A9p2643d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05A9p2641d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v05A9p2640d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v058Fp3820d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v04F2pB071d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v046Dp08C7d*dc*dsc*dp*icFFisc01ip00in*
alias:          usb:v046Dp08C6d*dc*dsc*dp*icFFisc01ip00in*
alias:          usb:v046Dp08C5d*dc*dsc*dp*icFFisc01ip00in*
alias:          usb:v046Dp08C3d*dc*dsc*dp*icFFisc01ip00in*
alias:          usb:v046Dp08C2d*dc*dsc*dp*icFFisc01ip00in*
alias:          usb:v046Dp08C1d*dc*dsc*dp*icFFisc01ip00in*
alias:          usb:v045Ep0723d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v045Ep0721d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v045Ep00F8d*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v0458p706Ed*dc*dsc*dp*ic0Eisc01ip00in*
alias:          usb:v0416pA91Ad*dc*dsc*dp*ic0Eisc01ip00in*
depends:        videodev,videobuf2-core,videobuf2-vmalloc
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           clock:Video buffers timestamp clock
parm:           nodrop:Don't drop incomplete frames (uint)
parm:           quirks:Forced device quirks (uint)
parm:           trace:Trace level bitmask (uint)
parm:           timeout:Streaming control requests timeout (uint)

```

I noted that I got the string 
**parm:           quirks:Forced device quirks (uint)**
as well.
What do you mean with: "Sometimes you need a quirk switch to activate a specific feature on your video camera?"

---

### Post by tgalati4 on 2014-06-02
Follow the troubleshooting guide and see how far you get:  [http://www.ideasonboard.org/uvc/faq/](http://www.ideasonboard.org/uvc/faq/)

---

### Post by federico9 on 2014-06-03
Thank you for your help. Unfortunately I didn't get so far, just as the beginning. Do you think it could be a problem related to the fact that uvcvideo doesn't support still image capture?

---

### Post by tgalati4 on 2014-06-03
Is your camera a UVC device?  Did it pass the test in the link I provided?

Most video cameras use proprietary drivers and to get the most capability out of them, you need to use the Windows drivers (in Windows) or the Mac drivers in OS X.  If you really want 4k resolution, you will have to learn about writing drivers and dig in yourself to write one.  I don't think still image functionality is an issue.  That is normally handled by the software application that gets the video stream.  In Windows can you get 4k video resolution while shooting video?  Or is it 4k resolution for still images only?

It's possible that the camera is working, but the application can only handle 640x480 for still images.  That you will have to research for the application that has that limitation.

---

