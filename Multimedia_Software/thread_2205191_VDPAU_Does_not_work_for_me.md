---
title: "VDPAU Does not work for me"
date: 2014-02-12
forum: Multimedia Software
---

### Post by pim2 on 2014-02-12
Hi New to this Forum.

I am looking for some help on vdpau, either to get it to work or know that it will never work with my HW.
Currently it does not work when I use the command vdpauinfo:  I get

display: :0.0   screen: 0
Error creating VDPAU device: 1

The environment:- hope to be as complete a possible.
Ubuntu 13.10 with the ubuntu nvidia driver after upgrading from 13.04  64bit
Motherboard is a Gigabyte H55M-UD2H - with on board video, disabled by setting BIOS to PEG
Video card GT220 and last week obtained GT610, To close out a video card HW issue, if there was one, both cards give the same.

I can type commands and can interpret them, I have not got the knowledge which commands 
would help in actually determining what the root cause is. I have trawled the web and followed parts of suggestions/advise but never with any success. I feel that this should have a methodical approach. Hence my request for help.

I have "lspci" output which seems to suggest that nvidia is found and the driver is used. (see snippet 1)
I have Xorg log output which does mention VDPAU in the same area where Nvidia is mentioned. ( see snippet 2) 
I presume this is good.

The end goal is to have XBMC using VDPAU - therefore I thought that "good output" from vdpauinfo would be 
the right first step.

Please help. Thanks.

(snippet 1)
           *-display
                description: VGA compatible controller
                product: GT216 [GeForce GT 220]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f9000000-f9ffffff memory:d0000000-dfffffff memory:ee000000-efffffff ioport:bf00(size=128) memory:e0000000-e007ffff

(snippet 2)
[    17.487] (II) Module glx: vendor="NVIDIA Corporation"
[    17.487]     compiled for 4.0.2, module version = 1.0.0
[    17.487]     Module class: X.Org Server Extension
[    17.487] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    17.487] Loading extension GLX
[    17.487] (II) LoadModule: "nvidia"
[    17.487] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.558] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.558]     compiled for 4.0.2, module version = 1.0.0
[    17.558]     Module class: X.Org Video Driver
[    17.565] (II) NVIDIA dlloader X Driver  304.88  Wed Mar 27 14:28:14 PDT 2013
[    17.565] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
some more stuff
[    18.660] (II) Loading sub module "dri2"
[    18.660] (II) LoadModule: "dri2"
[    18.660] (II) Module "dri2" already built-in
[    18.660] (II) NVIDIA(0): [DRI2] Setup complete
[    18.660] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    18.660] (--) RandR disabled

---

### Post by sudodus on 2014-02-12
I have a GeForce GT 430 card in an hp xw8400 workstation running 12.04.4 LTS with nvidia-304 (304.88). I use mplayer2, which I find more responsive than mplayer (svn). I don't think I have done any further tweaking, and vdpau works with mplayer with the following command

```
 mplayer -vo vdpau -vc ffh264vdpau -lavdopts skiploopfilter=nonref -use-filename-title -fs
```

Vdpau make a huge difference in CPU load. I use it as an alias to be able to play full HD (1920x1080, 50p) without lagging.

```
 alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau -lavdopts skiploopfilter=nonref -use-filename-title -fs'
```

It only works with some video codecs for example h264, but not with mp4v.

Depending on hardware and video-clip you may or may not need 'skiploopfilter'.

I notice clear differences between desktop environments: LXLE, XFCE and Unity. Playing my most difficult clips from the camera works without issues in LXDE, not quite as well in XFCE and even worse in Unity. This is with an ageing workstation. A new standard laptop with intel i5 and built-in intel graphics needs no vdpau to play the same video-clip.

---

### Post by pim2 on 2014-02-13
Hi Sudodus,

Thanks for the reply:  

So here is my plan then:
1: Find a video that uses the h264 codec.
2: Install "mediainfo" so I can verify that codec
3: Install mplayer and give it a go with the info you provided. Report the outcome back here.

Unfortunately normal work is in the way of this - hopefully later today or tomorrow..

---

### Post by Yellow Pasque on 2014-02-13
> NVIDIA dlloader X Driver 304.88
I would try an updated driver. 

> therefore I thought that "good output" from vdpauinfo would be the right first step.
I agree. Until you get vdpauinfo to work, messing with mplayer or the like seems pointless (unless vdpauinfo utility is lying or broken).

---

### Post by pim2 on 2014-02-13
Hi Termujin,


Updated Drive - Would that be sudo apt-get install nvidia-current?
Or would you suggest something else......

To install vdpauinfo I used sudo apt-get install vdpauinfo.  After the upgrade to 13.10.   Is there a way that I can check that vdpauinfo is a "working" version?

---

