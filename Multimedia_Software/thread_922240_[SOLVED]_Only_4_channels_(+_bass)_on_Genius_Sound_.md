---
title: "[SOLVED] Only 4 channels (+ bass) on Genius Sound Maker Value 5.1"
date: 2008-09-17
forum: Multimedia Software
---

### Post by b9k9kiwi on 2008-09-17
Installed a Genius Sound Maker Value 5.1 in my system and, having disabled Azalia in the BIOS, have it blasting out music via a new Logitec X-530 5.1 setup (and irritating the neighbours I suspect).

Only 4 channels (+ the subwoofer) are working, however - the Centre Speaker is mute.  Still pretty good (compared with two Logitech 2.1 systems via a Y connector off the onboard AC97).

I would dearly love to get the whole lot working so any help or hints would be appreciated.

---

### Post by markbuntu on 2008-09-17
You can look in my guide for getting your surround sound working:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by b9k9kiwi on 2008-09-18
> **markbuntu said:**
> You can look in my guide for getting your surround sound working:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Thanks for the pointer - I have fiddled around with .asoundrc, AlsaMixer and the various (not very helpful) PulseAudio applets, to no avail.

I really don't think it is worth the heartache and so I have 'fixed' the problem by running the centre speaker off of the same cable as the rear speakers via a Y connector.  It may not be exactly surround sound, but at least I have noise coming from all the speakers - sounds good (neighbours haven't complained yet, so I obviously need to crank up the volume a bit :) ).

---

### Post by Curlydave on 2008-09-18
Same problem here. I found an option in the sound settings (the name wasn't very descriptive) that let the rear speakers mimic the front ones in 2-channel audio, but the center is still dead.

---

### Post by markbuntu on 2008-09-18
What does aplay -l tell you?

---

### Post by b9k9kiwi on 2008-09-18
> **markbuntu said:**
> What does aplay -l tell you?

As follows;

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by markbuntu on 2008-09-18
I just happen to have a CMI-8738 myself though it is a MC8. 

I found out this for my card, right click in the Volume Control click Open Volume Control. Make sure it says C-Media ..... If it does not, click file/Change Device and change it to the C-Media ...

Go to the Options Section. There is a Line-In Mode box and a Mic-In box. The Line-In can be switched to Rear Output or Bass Output. The Mic-In can be switched to Center/LFE Output. These will supposedly switch the plugs on the sound card. Do you have these?

---

### Post by markbuntu on 2008-09-18
Sorry, double post.

---

### Post by b9k9kiwi on 2008-09-18
> **markbuntu said:**
> 
...
Go to the Options Section. There is a Line-In Mode box and a Mic-In box. The Line-In can be switched to Rear Output or Bass Output. The Mic-In can be switched to Center/LFE Output. These will supposedly switch the plugs on the sound card. Do you have these?

I'd forgotten all about Volume Control dialogue.

First I removed the centre speaker cable plug from the Y socket adapter and inserted it into its own dedicated cable.

Device was set to C-Media CMI8378 (Alsa Mixer).

I switched Mic-in Mode to Center/LFE Output to no effect (Firstly with output plug in C/LFE socket then switched to Mic-in socket).  I returned Mic-in Mode to Mic-in and then switched Line-in Mode to Rear Output to no effect (with output plug in C/LFE socket, but I get sound through centre speaker with output plug in Line In socket.  Which is nice, thank you.  Wierd setup though, not exactly intuitive.

I don't know about the much vaunted PulseAudio which is installed on this machine and displays an applet in the top panel offering lots of options, all of which have no effect.  Anyway, it seems I can now flag this thread as solved.

Incidentally, for your information, my .asoundrc is as follows;

pcm.!default {
type plug
slave.pcm "softvol"
}

pcm.softvol {
type softvol
slave {
pcm "ch51dup"
}
control {
name "All"
card 0
}
}

pcm.ch51dup {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

Thanks again.

---

### Post by markbuntu on 2008-09-19
A lot of hardware needs to be reset before changes take effect. Changes are written into a configuration file or the cards memory but that is ususally only read at startup.

So, making hardware configuration changes take effect often requires a reboot.

---

### Post by ~TheMik on 2008-10-29
I know this is an old topic, don't shoot me.

On my setup I have the cmi9739, though reported as 9761.  I don't have a center either, or so I thought.  Upon putting my ear next to the speaker during a speaker-test I ever so barely heard the nice lady say front center.  If I setup it to be independent instead of shared I can hear through the front center loud and clear, but I have no rear speakers then.

So I went to the asoundrc and it is setup like yours with the 5.1 routing table and softvol to actually control the sound.  I set the center channel to receive 100 times (not at first but gradually) the signal level of the left and right side.  This made it more audible but it was messed up sounding, like digital static if that makes sense.  In fact after boosting to ten was the same as 100.  Although changing the table up to receive more gain under shared helped a little, under independent it was very very loud.  

I am currently scouring the web and anything named alsa on my puter to see if there is a setting somewhere that is limiting the center output by default that I am not seeing.  Hopefully I can come with something and report back.

---

