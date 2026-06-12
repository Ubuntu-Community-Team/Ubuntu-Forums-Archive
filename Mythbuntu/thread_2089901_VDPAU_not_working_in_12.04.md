---
title: "VDPAU not working in 12.04?"
date: 2012-11-30
forum: Mythbuntu
---

### Post by Lido on 2012-11-30
I just upgraded from 11.10 because VDPAU wasn't working there hoping that things were fixed in the next release. The system seems to work ok in general, but I get a lot of jumpy, stuttering video with quite a bit of tearing. When I select any VDPAU option in MythTV video playback setup screen, I get the "Failed to Initialize Video Playback" error message if I attempt to watch a recording.

I tried installing from the edgers ppa as described in this [thread]("http://ubuntuforums.org/showthread.php?t=2029659"), but I'm still getting the same error. Here's some output that seems to say that there's no nvidia driver found (same output before and after installing the edgers ppa code):
```
$ vainfo
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/nouveau_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

---

### Post by nickrout on 2012-11-30
vainfo has nothing to do with vdpau. What video card do you have?

---

### Post by Lido on 2012-12-01
> **nickrout said:**
> vainfo has nothing to do with vdpau. What video card do you have?

Thanks. It's nvidia built into the motherboard. This is what lspci gives:
VGA compatible controller: NVIDIA Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)

I must have misunderstood the thread that mentioned using vainfo to determine if the nvidia driver was in use and VDPAU was working. Regardless, VDPAU doesn't seem to work. This is from the front end log:
```
Nov 30 02:17:41 mythfrontend[3495]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
Nov 30 02:17:41 mythfrontend[3495]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
Nov 30 02:17:41 mythfrontend[3495]: E CoreContext mythrender_vdpau.cpp:389 (Create) VDPAU: No VDPAU device
Nov 30 02:17:41 mythfrontend[3495]: E CoreContext mythrender_vdpau.cpp:405 (Create) VDPAU: Failed to create VDPAU render device.
Nov 30 02:17:41 mythfrontend[3495]: E CoreContext videoout_vdpau.cpp:147 (InitRender) VidOutVDPAU: Failed to initialise VDPAU
l
```

---

### Post by topcat5 on 2012-12-01
I have 3 machines running Myth FE on 12.04 and VDPAU works fine.   Make sure that you have the Nvidia hardware drivers enabled.

---

### Post by SeijiSensei on 2012-12-01
Your adapter [doesn't support vdpau]("http://us.download.nvidia.com/XFree86/Linux-x86/190.32/README/appendix-a.html").  Support began in the 8xxx series.

---

### Post by Lido on 2012-12-01
I can't believe the card isn't supported! I've been using it for years and on at least a couple of installs I think VDPAU setting worked, though apparently it wasn't getting any benefit of the VDPAU acceleration. Oh well...Thanks.

---

### Post by nickrout on 2012-12-01
> **Lido said:**
> I can't believe the card isn't supported! I've been using it for years and on at least a couple of installs I think VDPAU setting worked, though apparently it wasn't getting any benefit of the VDPAU acceleration. Oh well...Thanks.

Believe it or not, it's true.

---

### Post by BicyclerBoy on 2012-12-01
[http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/supportedchips.html)

The nForce 730 & "GeForce 9300 / nForce 730i" look to have been the earliest VDPAU on-board mobo GPUs

---

### Post by SeijiSensei on 2012-12-01
> **BicyclerBoy said:**
> The nForce 730 & "GeForce 9300 / nForce 730i" look to have been the earliest VDPAU on-board mobo GPUs

If so, why does NVIDIA list it as unsupported in the document I linked to above?

---

### Post by nickrout on 2012-12-01
> **SeijiSensei said:**
> If so, why does NVIDIA list it as unsupported in the document I linked to above?
No it doesn't. Read again.

---

### Post by SeijiSensei on 2012-12-01
> ```

NVIDIA GPU product  	 Device PCI ID 	VDPAU features
GeForce 7050 PV / nForce 630a 	0x053A 	-
GeForce 7050 PV / nForce 630a 	0x053B 	-

```

Following the [link]("http://us.download.nvidia.com/XFree86/Linux-x86/190.32/README/appendix-h.html#vdpau-implementation-limits-decoder") on that page to the codes for "VDPAU features" lists the explanations for the A, B and C feature sets.  I don't see any entry corresponding to the hyphen.  Moreover there are lots of cards above this one in the list that I know for sure do not support VDPAU like the 6xxx series that also have a hyphen in the same position.

What do you see that I don't?

---

### Post by nickrout on 2012-12-01
> **SeijiSensei said:**
> Following the [link]("http://us.download.nvidia.com/XFree86/Linux-x86/190.32/README/appendix-h.html#vdpau-implementation-limits-decoder") on that page to the codes for "VDPAU features" lists the explanations for the A, B and C feature sets.  I don't see any entry corresponding to the hyphen.  Moreover there are lots of cards above this one in the list that I know for sure do not support VDPAU like the 6xxx series that also have a hyphen in the same position.

What do you see that I don't?You commented (post #9) that the 9300 is not listed as supported, and I responded that it is. You are now justifying your post by referring to the 7050 entry.

---

### Post by BicyclerBoy on 2012-12-01
The OP has a nForce**630**

My comment was:
The "GeForce 9300 / nForce 730i" was the first good mobo GPU (w.r.t VDPAU)..actually some had HDMI & HDMI audio, not sure if it was real HDA..

The other notable mobo GPU was the 8200m & 8300m MCP78 512MB ram & vdpau B.

---

### Post by SeijiSensei on 2012-12-02
OK, I thought BicyclerBoy was responding to the OP, not to me.

The important thing is that we all seem to agree that the OP's adapter doesn't support VDPAU, which is what really matters here.

---

### Post by Henk Poley on 2012-12-03
Check this wiki page for supported VDPAU adapter cards: [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU). You will want one from the C row.

Personally I bought a "passive" GT 220 (meaning: no spinning fan). But that was a while ago, there must be better low-end cards available now.

---

