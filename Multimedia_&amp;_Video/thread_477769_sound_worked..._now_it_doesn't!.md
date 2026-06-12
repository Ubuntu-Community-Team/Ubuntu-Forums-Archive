---
title: "sound worked... now it doesn't!"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by deshnoodle on 2007-06-18
before i start, can i just say that these forums have been brilliant for the few weeks that i've been using ubuntu.  i'm a complete linux newbie, and you've managed to solve all of my problems without me having to post.  so, y'know, thanks to all!

now then... i'm having sound troubles and i just don't get it.  in the past it has worked fine, then stopped working, and then started again.  right now it doesn't work.  i'm sure it only stops working (and starts again) with reboots... but i'm not sure if it's only after software updates that things change.

i have an audiophile 2046 soundcard.  i'm using 'ice1712 multi' for my playback (in the sound preferences thing) and i get the beep when i press the test button.

from what i can gather from other posts, this is the right setting for my soundcard.  none of the other options in 'sound preferences' give me anything.
> 
alplay ~l gives me this:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

i am getting no sound in amorak or in any of my movie apps (i've tried kaffiene and vlc).  these have all been working fine previously.  all is fine when i boot into windows.

any help (even if it's pointing me to a thread i should have already found) would be appreciated.

---

### Post by EndianX on 2007-06-18
I believe I am experiencing the same problem.

When I first installed Ubuntu, sound worked.  Eventually it stopped.  I thought I had screwed something up.  I couldn't figure out what it was so I just reinstalled.  

Things worked fine for a week or two, but now sound has stopped working again.  This time I was VERY careful not to mess with anything that would effect sound.  I haven't installed any software or updated anything for a couple days.  Reboot won't fix this problem.

Does anybody have any ideas?

---

### Post by EndianX on 2007-06-21
Does anybody know a place to go to find a solution to this problem?

---

### Post by deshnoodle on 2007-06-27
my problem still stands... sort of...

in my grub menu i seem to have ubuntu in there twice, as follows:

Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-16-generic

the default is '16'.. and that has no sound.  if i boot up the other one then i've got sound.

---

### Post by EndianX on 2007-06-27
Interesting.  That means it is a kernel specific problem.  I'll have to try booting to another kernel.  Thanks for the update.

---

