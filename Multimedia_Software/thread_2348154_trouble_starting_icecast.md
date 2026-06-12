---
title: "trouble starting icecast"
date: 2017-01-01
forum: Multimedia Software
---

### Post by bill-lancaster on 2017-01-01
:~$ darkice -c ~/.darkice.cfg 
DarkIce 1.0 live audio streamer, [http://code.google.com/p/darkice/](http://code.google.com/p/darkice/)
Copyright (c) 2000-2007, Tyrell Hungary, [http://tyrell.hu/](http://tyrell.hu/)
Copyright (c) 2008-2010, Akos Maroy and Rafael Diniz
This is free software, and you are welcome to redistribute it 
under the terms of The GNU General Public License version 3 or
any later version.

Using config file: /home/bill/.darkice.cfg
Using ALSA DSP input device: pulse
DarkIce: ConfigSection.cpp:117: password missing in section icecast2-0 [0]

So it seems that a password is missing, but where?

Any help would be appreciated

Kubuntu 14.04

---

### Post by bill-lancaster on 2017-01-01
OK, I thought I'd copy a default cfg file.  Added 'password = xxx" then it needed mountPoint which I added.
Then :~$ sudo darkice -c ~/.darkice.cfg seemed to work.
Should I be able to 'see' my pc audio on the Sonos App?

---

### Post by SeijiSensei on 2017-01-01
If you're trying to distribute media with DLNA, I recommend using minidlna.  It's trivial to set up and works with all my devices.

---

### Post by bill-lancaster on 2017-01-29
Thanks SeijiSensei
Have just got round to installing minidlna.  It works fine with android devices.
I should have said in the first place that I wanted my Sonos system to play music on my Ubuntu box and it seems that Sonos doesn't support dlna.
So am now looking at other solutions.
Thanks again

---

