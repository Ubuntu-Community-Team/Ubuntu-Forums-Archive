---
title: "surround sound in 2.1 system with pulseaudio"
date: 2012-06-23
forum: Multimedia Software
---

### Post by deepclutch on 2012-06-23
Hi,
I have  a 2.1 speaker system(logitech LS21) and want to configure it correctly for surround sound(atleast configuration!). 

It has a single pin connected to audio line out to subwoofer from which front right and left speakers are connected.

Motherboard onboard HD Audio 7.1 surround supporting.
```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
```using pulseaudio and I understands that /etc/pulse/daemon.conf editing will help. but I am clueless here. 
[http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html](http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html)

using pulseaudio. and sound profiles shows only 4.1,5.1 as choices and currently I have selected "Analog stereo duplex".  I think it is  not proper.
will pulseaudio downmix 7.1 surround to 2.1 If I enter below lines in daemon.conf?  :P  and what about sound profile for 2.1 ?
```

default-sample-channels = 8 
default-channel-map = front-left,front-right,subwoofer

```the default value was default-sample-channels=2 and channel map front-left and front-right. 

OR is there a way to remap "default channels"? I am not sure that 2 channels will not be correct configuration for a 2.1 speaker system.

Kindly Help.

Regards,
DC

Here is the board audio jack details:

[IMG]http://img3.uploadhouse.com/fileuploads/16253/1625397938de49ae6ea8194e46d692fe54891f52.png[/IMG]

---

