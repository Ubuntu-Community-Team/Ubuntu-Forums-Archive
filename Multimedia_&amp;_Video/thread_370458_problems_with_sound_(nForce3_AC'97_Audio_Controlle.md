---
title: "problems with sound (nForce3 AC'97 Audio Controller)"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by gokekun on 2007-02-25
Hello,

well, I use linux about 1 year, but I'm one of those users that have a friend that installed kubuntu for me and I just know the basic. to complete, i speak english, but its quite horrible. so really sorry about any stupid things that i say

Well, I'm using now Kubuntu 6.10 (EdgyEft) and everything went well on the installation. The only problem is the sound that works, but its quite noisy (i cannot turn up the volume). the problem is not in the hardware, because i use windows too and its working fine there.

i used gentoo for a while and there i had the same problem. i used kurumin's live cd too, and the sound work greatly there. 

I've been searching on the forum but i couldn't find a lot to help me, here are some results:

$ lspci -vt   
-[0000:00]-+-00.0  nVidia Corporation nForce3 250Gb Host Bridge
           +-01.0  nVidia Corporation nForce3 250Gb LPC Bridge
           +-01.1  nVidia Corporation nForce 250Gb PCI System Management
           +-02.0  nVidia Corporation CK8S USB Controller
           +-02.1  nVidia Corporation CK8S USB Controller
           +-02.2  nVidia Corporation nForce3 EHCI USB 2.0 Controller
           +-05.0  nVidia Corporation CK8S Ethernet Controller
           +-06.0  nVidia Corporation nForce3 250Gb AC'97 Audio Controller
           +-08.0  nVidia Corporation CK8S Parallel ATA Controller (v2.5)
           +-09.0  nVidia Corporation CK8S Serial ATA Controller (v2.5)
           +-0a.0  nVidia Corporation CK8S Serial ATA Controller (v2.5)
           +-0b.0-[0000:01]----00.0  nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]
           +-0e.0-[0000:02]--+-09.0  nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]
           |                 \-0c.0  VIA Technologies, Inc. IEEE 1394 Host Controller
           +-18.0  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
           +-18.1  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
           +-18.2  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
           \-18.3  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control



$ lsmod | grep snd
snd_intel8x0           34844  4
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


the only problem is because I don't know where to go after this. i can listen music, but its quite annoying with the noise.

thank you

---

