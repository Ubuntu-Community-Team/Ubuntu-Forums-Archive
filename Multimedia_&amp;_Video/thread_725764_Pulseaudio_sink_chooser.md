---
title: "Pulseaudio sink chooser"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by moose6589 on 2008-03-16
Hey everyone, 

I installed Pulseaudio a few days ago, and after some rather prodigious tweaking and hacking, I've gotten it working in most things. However, there are a couple of annoyances left. 

The major issue right now is that padevchooser does not seem to work properly. Specifically, under Default Server, Default Sink, and Default Source, there are no entries listed other than Default and Other. From pavucontrol and paman, I know that I should have 2 sinks and several more sources, so this can't be correct. Moreover, I remember seeing entries in there once a long time ago, but they haven't been around recently, meaning I cannot easily switch between sinks (which is the feature that I really need). 

Right now, selecting other and manually pasting the name in from paman works. Incidentally, is it normal to have sink names as long as alsa_output.usb_device_8bb_2902_noserial_if0_alsa_playback_0 and alsa_output.pci_8086_27d8_alsa_playback_0? Selecting Default makes it go to the USB device. 

Has anyone else had this problem with padevchooser not listing the devices properly by default?

---

### Post by tighem on 2008-04-15
Same deal with me. Now I know how to make it work, though. Although this is not very intuitive.

---

### Post by tighem on 2008-04-15
Well I'll be gosh darned. THis is working for me now. Pulse remembered I wanted Banshee running through the speakers and my Skype running through the headset. I logged out and back in and everything stuck and is working...

So while the sink name is crazy long, it works!!!

---

### Post by sindhu_sundar on 2008-07-06
> **moose6589 said:**
> Hey everyone, 

I installed Pulseaudio a few days ago, and after some rather prodigious tweaking and hacking, I've gotten it working in most things. However, there are a couple of annoyances left. 

The major issue right now is that padevchooser does not seem to work properly. Specifically, under Default Server, Default Sink, and Default Source, there are no entries listed other than Default and Other. From pavucontrol and paman, I know that I should have 2 sinks and several more sources, so this can't be correct. Moreover, I remember seeing entries in there once a long time ago, but they haven't been around recently, meaning I cannot easily switch between sinks (which is the feature that I really need). 

Has anyone else had this problem with padevchooser not listing the devices properly by default?

Same problem here, so did it work out for you?

---

