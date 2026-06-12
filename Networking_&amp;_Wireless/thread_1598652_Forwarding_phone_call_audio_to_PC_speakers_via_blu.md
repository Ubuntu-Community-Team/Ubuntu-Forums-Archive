---
title: "Forwarding phone call audio to PC speakers via bluetooth"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by rocklobster217 on 2010-10-16
I have so far successfully setup media streaming from a Blackberry Curve 8900 to PC speakers using Bluez, Blueman and PulseAudio. This has worked somewhat, the frame rates are out of sync thus the sound is distorted at times but its working.

I would now like to utilize the call forward feature to stream the audio from a phone call to the PC speakers just like hands free in a car.

Guide for media stream:

[http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/](http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/)

I manually entered the bluetooth device mac in /etc/pulse/default.pa to stop pulse audio from crashing when media was streamed, like so:

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
load-module module-bluetooth-device address=00:23:7A:7C:53:2C profile=a2dp
.endif

Will continue to post my finding but would love some support from the community

Thanks!

---

### Post by krshna_r on 2011-07-07
Hi,
 
I am trying to stream audio from my mobile to pc via bluetooth.
I have followed the steps given in the link provided by you.
after establishing the connection when i try to play audio, pulse audio gets crashed.
 
can you please help me out to resolve this issue.

---

