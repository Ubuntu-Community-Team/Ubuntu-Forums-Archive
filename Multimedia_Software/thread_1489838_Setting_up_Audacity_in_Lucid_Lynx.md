---
title: "Setting up Audacity in Lucid Lynx"
date: 2010-05-21
forum: Multimedia Software
---

### Post by carniola on 2010-05-21
I recently switched to Lucid and have been astounded at how nicely it's been running. The only thing that has eluded me is Audacity. Can someone help me put the final puzzle piece in place? I need Audacity to record whatever's playing on the computer.

Here's my soundcard:

```
$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 82fe
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

Under sound preferences, I have the following under hardware:

Internal Audio
1 Output
Analog stereo output

Quickcam communicate MP/S5500 (the webcam)
1 input
Analog mono input

I have tried fiddling with these (and on Audacity's device settings) but can't seem to get the right combination... I would like to keep the webcam working for Skype and use Audacity to record.

Is this possible?

---

### Post by lidex on 2010-05-21
Have a look here:
[http://ubuntuforums.org/showpost.php?p=9329166&postcount=27]("http://ubuntuforums.org/showpost.php?p=9329166&postcount=27")
This may also be of interest:
[http://ubuntuforums.org/showthread.php?t=1005196]("http://ubuntuforums.org/showthread.php?t=1005196")

---

### Post by carniola on 2010-05-22
Thanks, lidex.

I seem to be stuck on Audacity finding the soundcard. It just seems to find the webcam. (Recording through the webcam works, but that obviously sounds lousy.)

Otherwise everything is running smoothly... My guess was that I had to add the sound card to "input devices".. but that hasn't worked yet.

I'm lost in a Roman wilderness of pain.

---

### Post by carniola on 2010-05-22
I've got it up and running. For anyone who stumbles upon this, what helped me was installing PulseAudio Volume Control (pavucontrol) and then following this post on the Audacity forums:

[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044](http://forum.audacityteam.org/viewtopic.php?p=75044#p75044)

The first part of lidex's second link was also very useful.

---

### Post by Dafydd on 2010-07-23
> **carniola said:**
> I've got it up and running. For anyone who stumbles upon this, what helped me was installing PulseAudio Volume Control (pavucontrol) and then following this post on the Audacity forums:

[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044](http://forum.audacityteam.org/viewtopic.php?p=75044#p75044)

The first part of lidex's second link was also very useful.

Anyone know of simpler software? I used to use Audacity to record off the internet, but now it (or Pulse) is too complicated. I followed the above but most have got something wrong and am sick of fiddling.

Is there any simple FOSS that can record a BBC webstream (not get_iplayer) off the web ie. played via Firefox?

---

### Post by Dafydd on 2010-07-23
> **Dafydd said:**
> Anyone know of simpler software? I used to use Audacity to record off the internet, but now it (or Pulse) is too complicated. I followed the above but most have got something wrong and am sick of fiddling.

Is there any simple FOSS that can record a BBC webstream (not get_iplayer) off the web ie. played via Firefox?

Sorry, I'll have to eat my words. I went back to pavucontrol "PulseAudio Volume Control". I was recording a webstream via Audacity but as usual there was no sign of input. In "PulseAudio Volume Control" I clicked on "recording" and changed the device from the webcam to "Monitor of internal audio analog".

Now it works - it seems.

Thanks for this guide.

---

