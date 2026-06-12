---
title: "Sound woes"
date: 2009-04-30
forum: Multimedia Software
---

### Post by rickbeton on 2009-04-30
First up, I'm a dumb noob when it comes to Linux Sound. I shouldn't be - I've been round this loop too many times now. It doesn't seem to get any easier. Everything else Ubuntu seems to "just work" for me - but not sound.

I've been through the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449").  Some things work, most things don't.  I'd appreciate a little help at this point.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
When I open the System > Preferences > Sound Preferences control panel, I get a test tone to work ONLY when I select some of the OSS outputs. The drop down menu lists these choices (exactly verbatim):

[LIST=1]
[*]Autodetect
[*]M Audio Audiophile 24/96 ICE1712 multi (ALSA)
[*]HDA Intel AD198x Digital (ALSA)
[*]HDA Intel AD198x Analog (ALSA)
[*]M Audio Audiophile 24/96 ICE1712 multi (OSS)
[*]M Audio Audiophile 24/96 ICE1712 multi (OSS)
[*]Logitech Inc, QuickCam Pro 9000 OSS PCM Device (OSS)
[*]Logitech Inc, QuickCam Pro 9000 OSS PCM Device (OSS)
[*]HDA Intel AD198x Analog (OSS)
[*]HDA Intel AD198x Analog (OSS)
[*]HDA Intel AD198x Analog (OSS)
[*]ALSA - Advanced Linux Sound Architecture
[*]OSS - Open Sound System
[*]PulseAudio Sound Server
[/LIST]

Ignoring the Audiophile card, which I haven't tested recently, only items 10 and 11 produce a sound when the Test button is pressed (this is via the motherboard's own green output socket fed to my speakers). Notably, none of the Alsa options work.

I want Alsa to work because I want more than one source to be mixed together - am I right thinking OSS can't do this?

Because the OSS works, I can at least listen to one thing at a time. But I have to terminate that application completely in order to be able to switch between sources. Not good. Bad, in fact.

Particularly, this is the sort of thing Ubuntu _needs_ to make much easier if Ubuntu isn't going to be roundly rejected by Windows users who might otherwise be tempted to switch.

Suggestions most welcome.

Rick  :-)

---

### Post by markbuntu on 2009-04-30
Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by rickbeton on 2009-04-30
I have Jaunty and the instructions here
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
are brilliant!!

Thanks, **markbuntu**.

My solution came from installing the PulseAudio applet (via padevchooser). This allows you to see the routing of your signals- in my case I have two sound cards and everything was by default routed to the wrong one.

Now I know how to switch between output devices, which is what I needed to know.

This leaves the remaining question - how other newbies can avoid landing in this difficulty in future. I won't attempt an answer here.

Thanks once again,
Rick  :-D

---

### Post by markbuntu on 2009-05-01
Your sig says Intrepid so I sent you to the intrepid sound solutions. Lucky for you I put a link there just recently to Jaunty sound solutions,

---

