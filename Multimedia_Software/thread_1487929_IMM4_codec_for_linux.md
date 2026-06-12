---
title: "IMM4 codec for linux"
date: 2010-05-19
forum: Multimedia Software
---

### Post by maito on 2010-05-19
Hi everyone,

I have been looking for IMM4 codec for linux. I would periodically need to convert some .avi files of security camera and these videos are encoded with this codec. Camera provides Setup.exe for Windows so the watching is possible with Windows Mediaplayer. 
Is there any change to view & edit these files under linux?

Thanks,

---

### Post by wmatthews on 2011-08-08
Did you ever find a solution for this video codec in Linux?

---

### Post by pwabrahams on 2011-09-26
I've also been looking for a Linux version of the IMM4 codec, which is used to interpret .avi files produced by the archiving facilities of security cameras.  I guess it doesn't exist, but it would be nice to learn that I'm wrong about that.

---

### Post by andrew.46 on 2011-09-27
Looks like the 32bit MPlayer can use a windows codec to play these files:

```

andrew@skamandros~$ mplayer -vc help | grep -i imm4
imm4        vfw       working   infinity cctv codec  [VCMIMM4.dll]

```

This one for example:

```

http://samples.mplayerhq.hu/V-codecs/IMM4/200707170736151.avi

```

Plays well enough:

```

andrew@skamandros~/Desktop$ mplayer 200707170736151.avi 
MPlayer SVN-r34132-4.5.2 (C) 2000-2011 MPlayer Team

Playing 200707170736151.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
**[COLOR="Red"]VIDEO:  [IMM4]  704x480  24bpp  29.970 fps  1220.5 kbps (149.0 kbyte/s)[/COLOR]**
Load subtitles in ./
==========================================================================
Opening video decoder: [vfw] Win32/VfW video codecs
Loading codec DLL: 'VCMIMM4.dll'
Loaded DLL driver VCMIMM4.dll at 10000000
[PP] Using codec's postprocessing, max q = 9.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [flip]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x89b1080]BICUBIC scaler, from rgb555le to yuv420p using MMX2
VO: [xv] 704x480 => 704x480 Planar YV12 
**[COLOR="Red"]Selected video codec: [imm4] vfm: vfw (infinity cctv codec)[/COLOR]**
==========================================================================
Audio: no sound
Starting playback...
V:  94.7 2840/2840 22% 18%  0.0% 0 0 


Exiting... (End of file)
andrew@skamandros~/Desktop$ 

```

I attach a screenshot of the gui UMPlayer running the file... One little warning: I had to rename the codec from lower to uppercase for it to work so really the inbuilt codecs.conf should be changed or the name of the codec shipped from MPlayer, but it works with a small manual adjustment :).

---

### Post by pwabrahams on 2011-09-27
Here's what I got with your first call:
```
pwa@pwa-K60IJ:~$ mplayer -vc help | grep -i imm4

pwa@pwa-K60IJ:~$ 

```
I have the mplayer that comes with Kubuntu and the medibuntu1 repository.  So what do I need to do to get the same result you did?

---

### Post by andrew.46 on 2011-09-27
> **pwabrahams said:**
> I have the mplayer that comes with Kubuntu and the medibuntu1 repository.  So what do I need to do to get the same result you did?

I compile my own, perhaps you could search out the guide I have written for this purpose on these Forums one day. But for the moment it looks like IMM4 playback was added a couple of years ago:

```

------------------------------------------------------------------------
r31983 | compn | **[COLOR="Red"]2010-08-20 08:13:25 +1000 (Fri, 20 Aug 2010)[/COLOR]** | 4 lines
[B][COLOR="Red"]
add binary codecs for fourcc: IMM4,[/COLOR][/B] LZOC, DIRC, MHFY, MSA1
map vvvc fourcc to ffh264
works on the single vvvc sample from uncommon codecs list

```

so all you need to do is to make sure you are running the 32bit MPlayer, not the 64bit one, and install the 32bit codecs from Medibuntu:

```

sudo apt-get install w32codecs

```

I am not sure how Medibuntu packages the required codec, you may still have to change the case once it is installed...

---

### Post by pwabrahams on 2012-03-13
> **andrew.46 said:**
> 
so all you need to do is to make sure you are running the 32bit MPlayer, not the 64bit one, and install the 32bit codecs from Medibuntu

So how do I get the 32-bit mplayer rather than the 64-bit one that comes with my 64-bit Kubuntu?  I've installed the 32-bit codecs from Medibuntu, but when I run mplayer, I get this:
```
pwa@pwa-K60IJ:$ mplayer CD_ch15_1203130102_1203130104_00.avi 
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing CD_ch15_1203130102_1203130104_00.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [IMM4]  704x480  24bpp  29.970 fps  267.0 kbps (32.6 kbyte/s)
Load subtitles in ./
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Requested video codec family [imm4] (vfm=vfw) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x344D4D49.
==========================================================================


Exiting... (End of file)

```

---

### Post by andrew.46 on 2012-03-14
> **pwabrahams said:**
> So how do I get the 32-bit mplayer rather than the 64-bit one that comes with my 64-bit Kubuntu? 

You will need to compile the 32bit version on your 64bit setup. It can be done but I am afraid I have not really done this satisfactorily myself :(.

---

