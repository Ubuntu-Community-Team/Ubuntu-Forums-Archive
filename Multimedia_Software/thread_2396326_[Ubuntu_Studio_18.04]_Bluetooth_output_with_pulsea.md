---
title: "[Ubuntu Studio 18.04] Bluetooth output with pulseaudio and jack"
date: 2018-07-13
forum: Multimedia Software
---

### Post by jessemillwood on 2018-07-13
I just started using Ubuntu Studio and as such just started using jack as well. Currently I have used qjackctrl to set my input audio card as my guitar USB device and I can route the audio to the system speakers. I want to route it to my Bluetooth headphones though. I can pair and connect to the headphones. But I have tried everything in the sink section of the patches and nothing comes out of the headphones. My understanding is that the headphones are talking to pulseaudio and that is talking to jack which is talking to alsa. Is there something else I can do or set up or is this just generally not supported? 

This is the jack settings I have: 

[IMG]https://i.imgur.com/5NpFBT5.png[/IMG]

And this is my connections that allow my guitar usb device to talk to guitarix and to the system speakers: 

[IMG]https://i.imgur.com/QTzBdYV.png[/IMG]

This is also with my bluetooth headphones connected via the blueman-applet. I can see the headphones in the volume control window:

[IMG]https://i.imgur.com/sw1w4xT.png[/IMG]

I tried connecting the outs of gx_head_fx to the pulse audio jack source but that didn't seem to help either. If I play a video in Firefox though, I can hear it in the headphones. 

Thanks

---

