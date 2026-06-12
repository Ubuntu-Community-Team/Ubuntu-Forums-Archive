---
title: "Jack problems... no sound... uhg..."
date: 2010-09-03
forum: Multimedia Software
---

### Post by MegaLoler on 2010-09-03
Muse will not make sound.  The jack server is running, but not from the terminal.  I can only get it to run with the Jack control.  But it IS running.  And still, I hear no sound from muse.  Muse is connected to the system in the connection window.  So, whats the problem?  Anybody, please?  Thanks :???:

---

### Post by dchurch24 on 2010-09-06
Hi, can you post a screenshot of the Settings window in JackCtl and also of the Connections window.

Which sound card are you using, and does it show up when you do "aplay -l" ? (post the output here)

Can you post the output of "dmesg |grep [insert sound card manufacturer here]" as well.

---

### Post by MegaLoler on 2010-09-08
Thanks for the reply!  I dont know what sound card I am using, but I run ppc ubuntu on a 2005 mac mini

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SoundByLayout [SoundByLayout], device 0: Master []
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I dont know my card manurfacturer, sorry, is there a command to get it?

sorry for the late reply btw

---

### Post by MegaLoler on 2010-09-09
Fixed it!  Turns out jack was working all along, but every program I tried to test in it, i couldn't get to work for some reason... Thanks xD

---

