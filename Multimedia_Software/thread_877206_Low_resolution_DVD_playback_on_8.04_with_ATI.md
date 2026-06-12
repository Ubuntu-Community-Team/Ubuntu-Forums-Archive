---
title: "Low resolution DVD playback on 8.04 with ATI"
date: 2008-08-01
forum: Multimedia Software
---

### Post by symposer on 2008-08-01
Hello all,

I have a problem with low resolution DVD playback on ubuntu 8.04. I'm using the ATI driver with an integrated Radeon X1200 (desktop) with an Athlon 64 X2 4800+. Mobo is Gigabyte GA-MA69VM-S2.

The video resolution is about half what it should be so when DVDs are played full screen the picture is very pixelated and blocky. I've tried the following:

1) AMD64 and i686 distributions - no difference, currently running i686
2) Standard video driver and proprietry ATI driver - no difference
3) Totem movie player and VLC with various output drivers - no difference
4) BIOS settings for VGA memory size - no difference
5) Commercial DVDs and DVDs created on a DVD recorder - no difference

I've attached a couple of screenshots from Totem so you can see how bad it is.

To get DVD playback working in the first place I just installed libdvdcss - do I need to do anything else to get it working properly? My old PII 450 running VLC on Win98 with 8 meg onboard VGA had no problems with DVD playback!

[I]tim@default:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
tim@default:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7412 Release

tim@default:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon X1200 Series[/I]


Thanks for your suggestions!

Tim

---

