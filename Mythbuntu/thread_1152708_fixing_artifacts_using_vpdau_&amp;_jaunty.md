---
title: "fixing artifacts using vpdau &amp; jaunty"
date: 2009-05-08
forum: Mythbuntu
---

### Post by dano1 on 2009-05-08
clean install of mythbuntu9.04. used jya's repos to add drivers and vpdau support. am getting artifacts using happauge hvr1600, digital and analogue. Set playback to cpu++ no filters in use. Any suggestions appreciated.

jaunty x86 64
nvidia 9400gt 180.51 drivers
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ 
4gig ram

thanks danny

---

### Post by SiHa on 2009-05-08
Just a thought - I've not tried vdpau yet, but when I've used other hardware acceleration (xvmc), you need to use one of the CPU- or CPU-- profiles. CPU++ will just use software decoding, and not make use of the nVidia hardware.

---

### Post by nickrout on 2009-05-08
> **dano1 said:**
> clean install of mythbuntu9.04. used jya's repos to add drivers and vpdau support. am getting artifacts using happauge hvr1600, digital and analogue. Set playback to cpu++ no filters in use. Any suggestions appreciated.

jaunty x86 64
nvidia 9400gt 180.51 drivers
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ 
4gig ram

thanks danny

cpu++ does not do vdpau. You need to set up a vdpau profile

---

### Post by dano1 on 2009-05-08
confused. cpu++ allows me to change decoder values to vdpau. any links to a guide would be greatly appreciated. I'm not a little lost here ; )

TIA, danny

---

### Post by utar on 2009-05-08
I assume you used cpu++ as a base configuration and then changed the decoder to vdpau.

What sort of artefacts do you get, do these appear when not using vdpau, do they appear on recording as well as live tv?

Can you also post the last few lines of your mythtvfrontend log when these artefacts appear.


Utar

---

### Post by gator on 2009-05-09
i have a 9400GT with avernards repo's.I have colored 'blocks' which looks like bad reception - however it doesnt happen if you use other decoders like ffmpeg - i'm sure i read somewhere that its a known problem and will be fixed in the next nvidia release
edit - It does not happen with h264 decoding as bluray looks sweet and plays smoothly maybe just mpeg2

i'm having random frontend crashes all the time now - liveTV or recorded, all decoders 
logs say....

*** glibc detected *** /usr/bin/mythfrontend.real: double free or corruption (fa
sttop): 0x00007f45dc8ad3a0 ***

anyone else?

---

