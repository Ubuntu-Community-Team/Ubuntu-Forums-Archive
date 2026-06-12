---
title: "LinuxSampler + RoseGarden + Virtual Keyboard"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by aaazhyd on 2006-07-21
Alrighty,

](*,) 

I am pretty much a newb when it comes to audio apps under Linux, although not a Linux newb by any means. I am want to do something that seems it would be fairly simple .. I want to use Rosegarden to compose, then use LinuxSampler as the sound engine. 

I got JACK and Rosegarden and Qsampler/Linux sampler installed from synaptic, and they all start up just fine. I am able to get Rosegarden to output to timidity just fine .. 

Here's the errors i'm getting in Qsampler:

23:52:01.594 New Audio device lscp_get_audio_driver_info: AudioOutputDeviceAlsa (errno=0)
ALSA lib control.c:785:(snd_ctl_open_conf) symbol _snd_ctl_hw_open is not defined inside (null)
AudioOutputDeviceAlsa: Cannot open sound control for card 0 - No such device or address
ALSA lib control.c:785:(snd_ctl_open_conf) symbol _snd_ctl_hw_open is not defined inside (null)
AudioOutputDeviceAlsa: Cannot open sound control for card 1 - No such device or address
ALSA lib control.c:785:(snd_ctl_open_conf) symbol _snd_ctl_hw_open is not defined inside (null)
AudioOutputDeviceAlsa: Cannot open sound control for card 2 - No such device or address
AudioOutputDeviceAlsa: Can't find any card

Looks like it can't find the card .. 

any help would be awesome, thanks!

---

### Post by zettberlin on 2006-07-21
It looks like the binary that can be installed with synaptic is not built for jack-support. Maybe you should ask the maintainer to fix this or build linussampler from source with --enable-jack.

---

### Post by aaazhyd on 2006-07-23
i got it recompiled from the deb src, and now JACK audio output seems to be working fine, but I still can not get it to reconize any sort of midi input. snd-seq module is loaded fine, and like i stated before, timidty is working fine too ..

for a test i disasbled timidity as i thought that may be holding the device, not allowing anything else to access. but that doesn't seem to be the case ..

also, should i have a JACK input option? I don't see it listed in the input devices in Qsampler ..

---

### Post by crimsun on 2006-08-06
It is likely that we will remove linuxsampler from Edgy. Its README states "This software is distributed under the GNU General Public License (see COPYING file), and may not be used in commercial applications without asking the authors for permission." Please see Debian bug #328121 for the reason it was removed from Debian.

---

### Post by philipacamaniac on 2006-08-06
Well...hmm...that sucks.

I just compiled libgig, liblscp, linuxsampler and qsampler from CVS, and I still can't get it to connect to jack. Oh, it has jack support, as the options are now there, but anytime I try to connect, it says:

```
Seems Jack server not running.
```

Is there another giga compatible sampler for linux?

---

### Post by pixelblip on 2007-05-27
Hi
I've just read this post as I too am trying to get linux sampler going in Ubuntu Studio. I haven't a bloody clue how to install it!


I find it difficult to understand why the linux sampler isn't allowed in the distro. Linux begs for a good sampler than can stream big files from disk. Arrhgh that's so frustrating.

I am begging whoever is in charge of Linux Sampler - please let the Ubuntu people use this in their distribution. So many of us want to move away from windows onto something that's stable. This is the last big thing needed ( we can live without vst instruments, but need a decent sampler!)

---

