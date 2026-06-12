---
title: "No Sound in Sony Vaio VPCEA1S1E"
date: 2010-10-05
forum: Multimedia Software
---

### Post by k.mammasis on 2010-10-05
Hi all,

I am having a problem with my new laptop Sony VPCEA1S1E. I installed Ubuntu 10.04 LTS and since then I cannot hear any sound. I have tried a lot of things before posting in here but nothing seems to work. From changing the module value in  the alsa=base.conf file to installing the updated alsa drivers (drivers,utils,base}. I have also checked the alsamixer so that nothing is muted. I am struggling with this problem two days now and it does not look like I am getting somewhere. The various postings I have read so far did not work for my case. 

A few things which might be useful at first:

card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]

cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC269


cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 36: [ 1- 0]: hardware dependent
 51: [ 1- 3]: digital audio playback

Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Oct  5 2010 for kernel 2.6.32-24-generic (SMP).

I would appreciate your help on this. 

Best Regards

Konstantinos

---

### Post by tommcd on 2010-10-06
> **k.mammasis said:**
> 
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Which sound card are you trying to use? When you run alsamixer which sound card does it say is in use? 
You can select the sound card you want to use in alsamixer by using the F6 key. Try toggling the sound cards in alsamixer by using F6 and see if you can get sound.

And welcome to the Ubuntu forums!

---

### Post by vothratzis on 2010-10-09
I have the same laptop (VPCEA1s1E) and also have NO SOUND at all in ubuntu 10.4.

Sound works perfectly in windows.

If you find a solution please post it!!

---

### Post by vothratzis on 2010-10-09
RESOLVED!!!

The solution is to upgrade the alsa driver, as shown here:

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/#comments](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/#comments)

---

### Post by chooyanzou on 2010-10-15
Having the same problem with my Ubuntu 10.10. Running Vaio VPCEB1M1E and I already have the latest version of ALSA. (1.0.23)

According to the Vaio support there are no known Linux drivers for Vaio sound cards. Not even one that he could recommend unofficially.

I do have an external card with Linux drivers but who the f__k wants to carry that s__t around at the university...!?

According to official information on the Vaio website, Sony seem to have some sort of brown nose deal with Micro$oft concerning other software... =/

I promise you, that if anyone here is able to help me find some drivers for my sound card I will be super happy. I would clap my hands and scream even.

Best regards!

/Choo

---

### Post by danwar72 on 2011-06-12
> **vothratzis said:**
> RESOLVED!!!

The solution is to upgrade the alsa driver, as shown here:

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/#comments](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/#comments)


Thanks buddy, It solved my problem.

---

