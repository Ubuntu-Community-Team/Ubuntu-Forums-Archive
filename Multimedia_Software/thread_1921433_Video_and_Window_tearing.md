---
title: "Video and Window tearing"
date: 2012-02-06
forum: Multimedia Software
---

### Post by gobr3800 on 2012-02-06
Hi,

I posted this in the Hardware forum and haven't had much luck. Is there anyone here who can help me with this problem? ...

I have been struggling for days to do a clean install of my system. I keep running into the same problem - window and video tearing. I'm assuming it's a problem with my video card, so I've been focussing on that. I did have it working fine before (on 10.04). Even though I'm trying to do the clean install on 10.04, the tearing just persists.

Here's what I do to try and set things up:

- Install the video driver Ubuntu recommends (the current Nvidia driver), then reboot.
- Check the 'sync to vblank' option in the NVidia X Server Settings.
- Check the 'sync to vblank' option in Compiz Config Settings Manager.
- Uncheck 'detect refresh rate' in CCSM.

This is the process I followed when I originally installed Ubuntu on this machine and it stopped the tearing fine. But now it doesn't seem to.

I've also tried installing 11.04 (and also 8.04 and 9.10) - I get tearing on all distros, so it doesn't seem to make a difference. I'd prefer to use the LTS version (10.04).

Any ideas on how I can fix the tearing?

Here's the output of lspci -v:

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8296
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fe880000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

Thanks!

---

### Post by BicyclerBoy on 2012-02-07
The tearing is caused by badly/incorrectly timed screen redrawing.
The use of composite effects (screen redirection & blitter) makes this more complicated.

VDPAU video:
nVidia VDPAU dynamically uses blitter or overlay for video presentation. Only overlay is guaranteed not to tear. Blitter is only best attempt.
Overlay VDPAU is always internally sync (no setting).
Composite desktop effects/manager forces VDPAU blitter method.

Dual monitors & twinview causes another set of problems.
VDPAU blitter with twinview can only sync one monitor.
Twinview refresh rate/screen size reporting seems to confuse the composite managers.

Easiest working setup:
No composite effects
No twinview

Useful settings:
CSSM unredirect full screen
CSSM enable legacy full screen support
CSSM Set/enter the real refresh rate

I find that *buntu 10.04.3 & nVidia GT240 & composite effects & VDPAU works okay with separate X screens.

Ubuntu 11.04 nVidia 9400GT composite (unity) & VDPAU works okay (one screen only)

---

