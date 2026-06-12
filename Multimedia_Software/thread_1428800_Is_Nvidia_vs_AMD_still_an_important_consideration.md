---
title: "Is Nvidia vs AMD still an important consideration?"
date: 2010-03-13
forum: Multimedia Software
---

### Post by Aikon- on 2010-03-13
I am in the process of building a new computer as my current tower is ~6.5 years old; in the past few months, it has started to show it's inability to keep up with the times.

One outstanding decision I have is the selection of video card. I use my Ubuntu desktop heavily for multimedia, so the first and foremost requirements for a video card are:
[LIST=1]
[*]Seamless Compiz support
[*]Seamless hardware video acceleration of MPEG-1/2/4, VC-1/WMV9, and H.264
[/LIST]

I have a laptop with an Nvidia Quadro NVS140M, and while it only supports feature set A, I got it working with some (not all) H.264 videos, greatly reducing my CPU usage. This has led me to the conclusion that an Nvidia card will suit my Linux needs just fine.

Having said that, I will also be doing some gaming on this computer (under Windows), and so I will also require a high-performing 3D card. My current understanding is that AMD is ruling the roost in this regard with respect to bang/buck.

My question boils down to this: is AMD's XvBA hardware video acceleration at a useable state, and if so, does it perform as well as Nvidia's offerings?

Advice welcomed!

-Aikon

---

### Post by markbuntu on 2010-03-13
Unfortunately XvBA is not as completely implemented as Nvidia's VDPAU at the moment and ATI is lagging in recent kernel and X-server support with their linux proprietary driver fglrx but there are hints that will be changing over the next few months. Where XvbBA is working it works at least as well as VDPAU and mplayer can now be compiled with XvBA support.

One thing to consider if you are planning on keeping the machine for any length of time is that the ATI open source drivers are improving very quickly and they are also implementing hardware video decoding thrrough the open source gallium project which is also supported by Intel. Soon you will have choices for drivers. The open source effort is well supported by ATI with full document releases and devs on the payroll.

Nvidia has had a lot of hardware problems and they should be fixed with the latest cards but only time will tell us that. Also the latest proprietary Nvidia driver release caused some nividia cards to melt due to faulty fan controls. The open source noveau driver is making slow progress but is getting no support from nvidia at all so this is to be expected.

---

### Post by Yellow Pasque on 2010-03-13
This is the best thing I can link you to. I've given up on decoding nvidia's naming scheme. [http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs](http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs)

> One thing to consider if you are planning on keeping the machine for any length of time is that the ATI open source drivers are improving very quickly and they are also implementing hardware video decoding thrrough the open source gallium project which is also supported by Intel. Soon you will have choices for drivers.
I think it's going to be a while before we see shader-based video accel through Gallium3D. G3D itself is still maturing, and the R600/R700 G3D driver just got started.

---

### Post by cascade9 on 2010-03-15
From what I know, XvBA is useable now, but its not as developed as VDPAU. Its probably worth spendin g the extra on a nVidia rather than going for the slightly cheaper ATI cards now just for the long term support of nVidia. BTW, while the ATI cards are the best in bang for buck now, its not a huge difference between them. 

> **Temüjin said:**
> This is the best thing I can link you to. I've given up on decoding nvidia's naming scheme. [http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs](http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs)


Un part that is because there is no easy logic in the naming scheme. Its more about marketing than anythign else....nVidia finds it easier to rename cards to make them seemer newer than to sell 'upgraded' old cards. Eg- 8800GT, + minor upgrades = 9800 GT.  9800 GT + minor upgrades = GTS250.

---

### Post by Aikon- on 2010-03-16
Thank you everyone for your input, I think I have a fairly decent grasp on the state of affairs now.

It appears to me that the AMD drivers are in a rapid state of improvement due to having open documentation; does this extend to their XvBA and 3D acceleration features as well? Furthermore, we are still waiting on nVidia's DX11 parts, which should drive down the cost of some of their cards and bring the $/performance more in line with AMDs offerings.

As such, I am considering purchasing the cheapest AMD card I can find that supports UVD2.2 (i.e. Radeon HD 4350 for $30 CAD), which will allow me to assembly my new computer and to tinker with AMDs XvBA while simultaneously waiting on the drivers and nVidia. Then, a few months down the road when I need it, I'll have a better idea of whether an AMD card will work for me.

Another question that has come up since I originally posted: what about GPGPU support? I use BOINC for SETI@home, and if I am going to have a fairly heavy graphics card (that won't be used all that heavily in Linux), I figure I may as well put it to use. So, in addition to what I asked above,
[LIST=1]
[*]is CUDA support fairly seamless on Ubuntu?
[*]what is AMD's version, and how does it compare on Linux?
[/LIST]

-Aikon

---

