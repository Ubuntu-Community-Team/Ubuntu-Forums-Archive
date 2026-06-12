---
title: "No sound through HDMI"
date: 2011-10-16
forum: Multimedia Software
---

### Post by bonne1 on 2011-10-16
I have searched the forum and found that I am not the only one having problems on this one. Allthough none of the solutions I have found has solved my problem - therefor I start my own thread in the hope that someone can guide me to solve my problem.
 
Xubuntu 10.4 upgraded to 10.10 (but problem was there even on 10.4)
ASUS P5N7A-VM (Nvidia onboard chip)
 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Added:
 
load-module module-alsa-sink
load-module module-als-source device=hw:0,7

to default.pa (a suggestion found on the net)
 
SPDIF unmuted in alsamixer
 
As I am planning to use this system as a HTPC - it would be nice to be able to get sound from it  (-;
 
Anyone?
 
Regards, Lars.

---

### Post by BicyclerBoy on 2011-10-16
You made some typos & errors in your /etc/pulse/default.pa

comnent out both the: 
load-module module-alsa-sink
load-module module-als-source device=hw:0,7
(typo & you don't want an input)

add
load-module module-alsa-sink device=hw:0,7

But try:
speaker-test -c 2 -r 48000 -D hw:0,7
(& report the alsa utils version)
cat /etc/modprobe.d/alsa-base.conf | grep snd-hda
dmesg | grep hdmi
ls /proc/asound/card0/eld#*

cat any eld#* files (should be eld#2.0)

---

### Post by mikejonesey on 2011-10-17
i am interested in this too... will be trying out tonight...

---

### Post by bonne1 on 2011-10-23
> **BicyclerBoy said:**
> You made some typos & errors in your /etc/pulse/default.pa
 
Funny... must be a copy and paste error I have done with vi that slipped through
 
Corrected now
 
 
> **BicyclerBoy said:**
> But try:
speaker-test -c 2 -r 48000 -D hw:0,7
 
Pink noice comes out of the TV-speaker through HDMI
 
Version reported as speaker-test 1.0.24.2
 
 
> **BicyclerBoy said:**
> cat /etc/modprobe.d/alsa-base.conf | grep snd-hda
 
options snd-hda-intel model=auto enable=1 index=0
 
(Think I also googled this one on the net)
 
> **BicyclerBoy said:**
> dmesg | grep hdmi
 
Empty output. (?)
 
 
> **BicyclerBoy said:**
> ls /proc/asound/card0/eld#*
 
Got no eld-files:
 
ls /proc/asound/card0
codec#0 codec#3 id pcm0c pcm0p pcm2c pcm3p pcm7p
 
After I have corrected /etc/pulse/default.pa, I can now start pavucontrol - and I can see the soundoutput on the "VU-meter", but no sound goes through the HDMI.
 
Think that I need an understanding of how the sound system works in Ubuntu.
 
Regards, Lars.

---

### Post by BicyclerBoy on 2011-10-23
I made a error by asking you to check the eld# files..
Your chipset is nVidia 730/9300M & I think is does not support eld reporting..
So there will be no HDMI events in dmesg.

Reviews state the HDA audio supports 8 ch 192KHz.

As speaker-test hw:0,7 works then try:
pavucontrol
select the hw:0,7 device as default.
Try some audio output from rhythmbox or similar.

Because the HDMI audio capabilities are not reported you have to control the output formats so it matches the HDMI receiver.

You need to try speaker-test with -c6 -r 48000 -D hw:0,7 etc
to find if 6 ch is supported..etc..

If you plan to run MythTV or XBMC you can just use the hw:0,7 device directly.

The /etc/pulse/default.pa settings is to get system wide pulse audio outputting to hw:0,7

---

### Post by bonne1 on 2011-10-23
> **BicyclerBoy said:**
> 
As speaker-test hw:0,7 works then try:
pavucontrol
select the hw:0,7 device as default.
Try some audio output from rhythmbox or similar.

If you plan to run MythTV or XBMC you can just use the hw:0,7 device directly.

The /etc/pulse/default.pa settings is to get system wide pulse audio outputting to hw:0,7

Amazing - sound is now working though HDMI... Thanks you for exelent help on this!

One thing... in pavucontrol, I am not sure how to set the default device. Under the tab "Playback", I have a setting called "Alsa plug-in". When I set this to "Internal Audio", HDMI works. All new applications shows up there as "Internal Audio Digital Stereo (HDMI)", but I have to set every application to "Internal Audio" for HDMI to work. Isn't there any system wide setting to set all applications to "Internal Audio"?

Regards, Lars.

---

### Post by BicyclerBoy on 2011-10-23
Use the configuration tab to change default input/output devices

You should mess about with speaker-test to find out what your receiver/TV will accept because alsa does not know & assumes full capability..

---

### Post by bizlove11 on 2011-10-23
I also cannot get sound through my HDMI connection. I am a brand new user to Ubuntu with no previous Linux experience. I am running Ubuntu 11.04 on a brand new HTPC build. I have never had sound through the HDMI and I have been researching this for a month with no success.

BicyclerBoy,

I tried your speaker test and heard pink noise through both speakers. I attempted to follow the other suggestions you offered but have not had any success. I feel as though I have tried everything and am close to giving up on Ubuntu. Are you able to offer any advice? What other information do you need from me?

Thanks, Sean

---

### Post by BicyclerBoy on 2011-10-23
Sean
The HDMI audio in this thread is a little different to the norm because it is an early nVidia chipset audio.

There are (3) groups (in my view).
- pre azalia HDA . S/DPIF over HDMI
- early HTPC chipset. no ELD
- current HDMI. ELD reporting & HDMI hot plugging.

So you should post
- The video card model
- video driver in use 
aplay -l

& post the whole speaker-test std output..I want to see the alsa version.

Do you have HDMI connection thru' AVR HT amp ?

No HDMI audio is not a show stopper just use S/PDIF output to amp etc..
Most audio is not HDA or recorded adequately to be worth the trouble.

---

