---
title: "New Ubuntu user soliciting help with G45 Intel graphics chipset."
date: 2008-10-11
forum: Multimedia Software
---

### Post by AreonEpta on 2008-10-11
Hey, I recently picked up a new laptop with some newer hardware. I have been having problems with video, wireless, and the media hotkeys, but I have a lead on everything but the video. I have heard tell that the required drivers will be included in the newest version of x.org, but that's not due til the 30th, and I have no inclination to sit around and wait.

I'm a scrub. I've read up on the FAQ's and stuff, and frankly, so far, I'm confused. I'd love to hear, "Oh, yeah. Common problem. Do A then B then C and you'll be good." Or even, "Yeah, common problem. You're fked." But the complete inability to figure out how to get 3d acceleration (or even 2d drivers for that matter) is depressing.

I've always been a windows guru, but I've had it. I want to learn this stuff, but I need the time to sit and read, and time, I do not have. I'd love it if someone could sit down and be like "You're dumb. Here's the answer and here's why it works." If anyone has any interest in aiding me in my hunt for an easy ( or even hard ffs) way to get me some drivers, please either PM me, or post. Thanks in advance.

Areon

---

### Post by jackocleebrown on 2008-10-18
The drivers for the chipset are available, the code for them is hosted here [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/). So, it is possible if you are very ambitious to compile them yourself. The problem is that because they are cutting edge they rely on the newest versions of lots of other packages (such as Xorg and Mesa). Which means that there is a lot of compiling work to do if you want to get them working "by hand".

The alternative: Ubuntu Intrepid 8.10 is released on the 30th of October and includes the correct intel drivers for your chipset. Because Ubuntu open source you don't have to wait until then. The beta release is out right now and you can download it and try it out. [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)
It is a beta release, this is the final stage of testing before the official release at the end of the month. So... there are probably a few small bugs left but the big problems have been discovered and fixed in the alpha testing stages. Why not download the live CD version and see if it works for you.

Cheers, Jack.
(using Intrepid on a HP6730b laptop with the G45 chipset, 3D works for me!)

---

### Post by redDEADresolve on 2008-10-22
the g45 freezing on login bug a been fixed with todays, October 22 2008, intel driver and kernel update. Happy Ubuntu'ing!

PS You have to be patient with Linux, it's not like your paying for it.

---

