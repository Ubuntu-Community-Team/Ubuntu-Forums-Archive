---
title: "Responsiveness on remote controls, lirc"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by apanloco on 2006-11-30
I have set up a working MythTV system with a Hauppage PVR-150 card. I am dissapointed in the responsiveness of the remote control, and wonder where the problem actually lies, and especially how to resolve it. If I press for example one button four times, ("rather" quickly), only 3 or in worst case 2 presses goes through. I am constantly monitoring with irw. This is an example output of pressing the button four times in one second:

0000000000001795 00 DOWN apanloco_hauppauge_pvr150
0000000000001795 01 DOWN apanloco_hauppauge_pvr150
0000000000001795 02 DOWN apanloco_hauppauge_pvr150
0000000000001795 00 DOWN apanloco_hauppauge_pvr150
0000000000001795 01 DOWN apanloco_hauppauge_pvr150

Only two commads (00) got through, which was not repeats of same button. And i am holding the remote a couple of centimeters/inches from the receiver.

I have also tried creating a new lircd.conf for this (irrecord), but I get the same result (more or less).

I am dreaming of responsiveness of a game console (xbox, 360 etc) -- instant response and no loss whatsoever. 

Is the problem Hauppauge remotes? Hauppage IR receivers? MY hauppauge remote? Is it perhaps IR in general, or is it just my configuration (tried several on the net, and self-made)?.

PLEASE give me input here.

I am thinking about building my own serial IR receiver. Will this give better response?

---

