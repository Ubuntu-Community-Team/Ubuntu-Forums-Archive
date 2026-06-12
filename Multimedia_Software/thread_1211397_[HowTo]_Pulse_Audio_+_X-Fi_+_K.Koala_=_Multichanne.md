---
title: "[HowTo] Pulse Audio + X-Fi + K.Koala = Multichannel"
date: 2009-07-12
forum: Multimedia Software
---

### Post by EagleDM on 2009-07-12
I decided to post a mini-guide to this because, simply stated, X-Fi works but not in Multichannel due to problems with PulseAudio and the way the X-Fi driver is made.


X-Fi contrary to the rest of the most common linux drivers is made in a basis of addin "sub-devices" inside the master device, so, basically, PulseAudio has no way to detect that devices (the common Plug51 and Surround51 does NOT work) so, one has to MANUALLY add each sub-device of X-Fi to obtain perfect mapping of all channels.

This guide only works with Karmic Koala and their newest Kernel 2.6.31-2 since that kernel has support for X-Fi and all of it's output channels (including Side channels).



First of all, go to /etc/pulse

now, edit this the file daemon.conf  (sudo kate daemon.conf)


now: change the following lines at the end of the file (or uncomment them)

default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 6
default-fragments = 8
default-fragment-size-msec = 10


Now, edit the file default.pa (if this file is not present, just install pavucontrol and do pulseaudio --k and then pulseaudio -D and it will create the file for you, now, copy this inside the file)

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hw:0,0 channels=2 channel_map=front-left,front-right
#load-module module-alsa-sink device=hw:0,1 (this is for surround or Back channels in 7.1, no need to put this line in 5.1 setup)
load-module module-alsa-sink device=hw:0,2 channels=2 channel_map=center,lfe
load-module module-alsa-sink device=hw:0,3 channels=2 channel_map=side-left,side-right

AS you can see, each sub-device has 2 channels each that are responsable for multichannel, now, to remove automatic detection in PA.


Then REMOVE or comment with # this lines
load-module module-hal-detect tsched=0
load-module module-detect


That should put a STOP to PulseAudio trying to detect devices on his own which is the main cause of the lack of 5.1.

With this setup you are MANUALLY setting up each sub-device with each channel mapping to obtain perfect 5.1 through PulseAudio, the reason I mapped Side channels instead of Surround is because X-Fi uses the typical "surround" channels in a 5.1 configuration as "Side channels", if you need 7.1 instead of 5.1 you can ADD the line "channels=2 channel_map=rear-left,rear-right to the hw=0,1 and change the default channels to 8 in daemon.conf but DO NOT do this for 5.1 since Side channels behave as rear or surround in a 5.1 configuration. (the surround channels MUST be connected to Side Speakers in the X-Fi back).


Hope this helps, it took me hours of trying to found out the way.

PD: no need to manually set the mapping on daemon.conf because we are instructing PA to do it from the original sink.



Eagle

---

