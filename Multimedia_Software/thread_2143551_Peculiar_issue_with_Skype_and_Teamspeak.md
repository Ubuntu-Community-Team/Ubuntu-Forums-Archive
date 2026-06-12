---
title: "Peculiar issue with Skype and Teamspeak"
date: 2013-05-09
forum: Multimedia Software
---

### Post by goatboy73 on 2013-05-09
I have a peculiar issue with Skype and TeamSpeak in my Ubuntu 12.04.2 installation.  On first boot, both software systems will pretty much exhibit the same behavior: capture of audio appears to be fine, but playback of audio from the other side of the connection causes the program to "sort-of" freeze.  My sound card is a SoundBlaster X-Fi Titanium (EMU20K), and it works beautifully except for this.

However, if I run TeamSpeak's loopback test BEFORE I try to use either program, that seems to "clear something up", and then everything works flawlessly.  From the symptoms, it feels as if it may have something to do with full-duplex playback+record not being activated on boot, and so when the software packages attempt to use it, they run into those problems.  Somehow TeamSpeak's loopback test re-sets that, and then everything works fine.

Skype's Test Call "loopback test" (which is nowhere near the same as TeamSpeak's) also fails to work until the aforementioned workaround is applied.

This is workable, and I can live with this for now, but I'd like input and suggestions as to what setting (via alsa/pulse/whatever) I should be examining or re-setting manually.  Importantly, if you need me to provide feedback of command outputs (i.e. to determine the state of the system upon boot vs. the state after "fixing"), I'll be more than happy to provide it.  Hopefully through such dumps we can figure out what the problem is and come up with a script I can run on login to fix things automagically.

Cheers!

---

