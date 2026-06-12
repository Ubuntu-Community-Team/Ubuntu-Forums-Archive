---
title: "Center channel missing in 10.04 Beta 2"
date: 2010-04-21
forum: Multimedia Software
---

### Post by teerex on 2010-04-21
Hello All:
        I have Ubuntu 10.04 Beta 2 running on an Asus board with on-board HD audio. The codec is a Realtek ALC889. I have a 5.1 surround sound system and when I play a DVD through VLC player, I get sound from the 4 surround speakers and the sub-woofer but no dialog from the center channel. I know the center channel speaker works as I use the same setup with a stand-alone DVD player. pulseaudio shows Analog 5.1 output + Analog Stereo input. In /proc/asound/.../codec#<xx>, it shows the correct Codec (Realtek 889). I have added "options snd-hda-intel model=6stack-dig" to /etc/modprobe.d/alsa-base.conf. I have also looked at the Preferences->Sounds and VLC Player Audio settings but everything seems to be set correctly. I am at a complete loss as to how to debug this further.

Any insight/advice would be appreciated.
Thanks,


EDIT: Well, I feel like kicking myself over and over for spending so many hours trying to fix a problem in Ubuntu that actually was related to the settings of my HT system. I have the Logitech Z5500 and I have connected the 5.1 analog outputs from the PC to the Z5500's inputs. However, I had the effects set to Dolby PL. Once I changed it to 6-channel Direct, I was able to hear the center channel loud and clear. I then went and un-did all the changes to alsa-base.conf and /etc/pulse/daemon.conf. Whew!! I'm glad that saga is over as I was seriously contemplating abandoning this effort and reverting to Win7. 

It was Win7 that helped me track the issue as I used the MoBo's utilities disk to bring up the Realtek HD audio app to debug and realized that only the front 2 speakers were producing sound. Hope this helps someone else in my shoes.

Cheers

---

