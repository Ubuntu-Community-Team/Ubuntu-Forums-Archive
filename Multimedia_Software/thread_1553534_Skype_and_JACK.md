---
title: "Skype and JACK"
date: 2010-08-15
forum: Multimedia Software
---

### Post by Tyrlup on 2010-08-15
Is there anyway i can Make Skype work with JACK?

What I want is to make sounds from Flash(Youtube, etc.) play through the Skype Microphone without Holding my microphone to the speakers.
I've been searching the whole internet the last 12 hours and I have found some clues how to do it but nothing in particularly to the newest ubuntu sound system.
Some of the threads i've come across are from 2005 where about running skype with artsdp with a script
other threads i've read mentioned editing the /etc/asound.conf

In the end I am still clueless how to run Skype with Jack.:confused:

but at least I figured out how to jackify Flash [Link]("http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507")


I'm running Lucid Lynx without KDE.

Please provide me with some information, clues or solutions.
thank you.

---

### Post by simosx on 2010-08-15
Skype does not support Jack; for sound mixing you would need to use PulseAudio which Skype supports.

I would suggest to install 'padevchooser' which is the PulseAudio Device Chooser (find it in Applications/Sound and Video) and allows you to connect sources and sinks as you wish. Google then for 'padevchooser' for help on how to add more audio inputs, etc.

---

### Post by Tyrlup on 2010-08-15
Great! I allready have padevchooser installed but no Sinks or Sources shows up? Any adwise, I've tried to type Skype In the Sink and Rhythmbox in the source but when i test call, it says "Problem with Audio Capture"

---

### Post by simosx on 2010-08-15
> **Tyrlup said:**
> Great! I allready have padevchooser installed but no Sinks or Sources shows up? Any adwise, I've tried to type Skype In the Sink and Rhythmbox in the source but when i test call, it says "Problem with Audio Capture"

Have a look at [http://www.youtube.com/watch?v=AwKyJRPlsxw](http://www.youtube.com/watch?v=AwKyJRPlsxw)
It explains in an easy way how to setup your PulseAudio.

In general, you can google for more on this with "pulseaudio record from soundcard".

---

