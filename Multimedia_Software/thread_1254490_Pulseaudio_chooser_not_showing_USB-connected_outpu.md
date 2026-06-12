---
title: "Pulseaudio chooser not showing USB-connected output device"
date: 2009-08-31
forum: Multimedia Software
---

### Post by LinuxBob on 2009-08-31
I installed PulseAudio chooser on two Ubuntyu PCs.  Both PCs have an RCA Wireless Lyra transmitter plugged into the USB port.  I successfully moved the flash audio stream on one pc to the Lyra transmitter and am now able to hear Interent audio streams on three stereo receivers around my home to which I have Lyra receivers plugged into the aux input.

My problem is that Pulseaudio chooser does not display the USB Lyra transmitter as an available output device when I try to move the audio stream on the second Ubuntu PC.  I did try a bunch of stuff before stumbling across the Pulseaudio solution (initial problem was no sound except for Rythmbox and local files).  For example, from the command line I set ICH5 as the default sound card when following a suggested solution that did not work.  Now I am thinking it may be the reason why I only see ICH5 in Pulseaudio chooser.

Anyone know the command to list attached audio cards/devices and set/unset the default?

Anyone have any other ideas as to why the USB connected transmitter is not displayed on the one PC in Pulseaudio chooser but is on the other PC?

---

