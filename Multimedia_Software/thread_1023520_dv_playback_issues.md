---
title: "dv playback issues"
date: 2008-12-28
forum: Multimedia Software
---

### Post by lcbruzer on 2008-12-28
Apologies if I missed it but I searched the forum for this and didn't find an answer.

Here's the story: trying to setup an htpc.
OS:
Ubuntu 8.10
Linux htpc 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:35 UTC 2008 x86_64 GNU/Linux

Hardware: quad-core dell 
video card: Radeon HD 3650 512MB with HDMI

Driver: I had to load the proprietary fglrx:
$ dpkg -l | grep fglrx
ii  fglrx-amdcccle                             2:8.552-0ubuntu0.1                      Catalyst Control Center for the ATI graphics
ii  fglrx-kernel-source                        2:8.552-0ubuntu0.1                      Kernel module source for the ATI graphics ac
ii  fglrx-modaliases                           2:8.552-0ubuntu0.1                      Identifiers supported by the ATI graphics dr
ii  xorg-driver-fglrx                          2:8.552-0ubuntu0.1                      Video driver for the ATI graphics accelerato

What works: So far, I am able to use vlc to view HD video made with new Canon Vixia HF100 and also older AVI movies. I have to use the ALSA interface for sound through the HDMI card output.

What also works: I am trying to record older 8mm videos from a Sony camcorder. With both Kino and dvgrab I can create .dv movies through the native firewire interface on the PC.

What doesn't: playback of the older video. When I use vlc, I get good video but loud crackly audio. When I use totem, I get good audio but terrible flicker in the video. Before I switched the vlc to use X11 video output I also saw the flicker. So I suspect if I could figure out how to get the video in totem to use the same output, or the audio setup in vlc to be the same as totem's I'd be set. But I cannot seem to get either of those configured. Again, I believe I am stuck with ALSA unless someone knows how to use another sound server with this card. When I test using the Preferences->sound utility, only the "HDA ATI HDMI ATI HDMI (ALSA)" setting enables sound.
Since one (vlc) has good video and the other (totem) has good audio I think that the created DV file is valid. I tried a few encoding specs but didn't find a winner.

Maybe if someone can show me how to see the audio details of totem or set the video output module I can go from there. I'm also open to DV encoding suggestions.

### update - I am able to set the video output wth gstreamer and that enables me to use totem with decent video out. I still cannot get the crackly audio fixed for vlc.

Thanks in advance!
LCB.

---

