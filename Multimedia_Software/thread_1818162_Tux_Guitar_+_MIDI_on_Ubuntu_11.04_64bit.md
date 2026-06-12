---
title: "Tux Guitar + MIDI on Ubuntu 11.04 64bit"
date: 2011-08-04
forum: Multimedia Software
---

### Post by mon_r on 2011-08-04
I installed Tuxguitar and Timidity via Synaptic. It worked once then after a while reverts to default.
I opened up Synaptic and searched for tuxguitar and timidity, marked it for re-installation and it worked again for a while. Then stopped working again.

I went to search for answers and found this:
[https://help.ubuntu.com/community/Midi/HardwareSynthesisSe](https://help.ubuntu.com/community/Midi/HardwareSynthesisSe)

added the alsa-tools via terminal apt-get install and installed awesfx and alsa-tools

Then this time, searched for tuxguitar on Synaptic again and installed all the non-installed MIDI options.
Still only one was available

Using the command in terminal gets the results:
$ aplaymidi -l 
Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0

I have sound but not good.

---

### Post by mon_r on 2011-08-05
Found this in the forums:
[http://ubuntuforums.org/showthread.php?t=980975](http://ubuntuforums.org/showthread.php?t=980975)
Specifically this post:
[http://ubuntuforums.org/showpost.php?p=6168289&postcount=2](http://ubuntuforums.org/showpost.php?p=6168289&postcount=2)

Says to do this in terminal:
timidity -iA -Os
But the poster said that you have to do this every time.

I tried it and I can now see the other options in Tuxguitar and it's playing as it should. But closing the terminal also ends the timidity session and you're back to the previous setting of having no sound playback.

---

### Post by mon_r on 2011-08-05
Added the command on Startup Applications

---

