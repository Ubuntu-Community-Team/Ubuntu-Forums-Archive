---
title: "dvgrab 'qt' format problem. can't work with quicktime under Mac OS X"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by wshvic on 2007-04-12
Hi  :D 

I use dvgrab to capture video from my Panasoinc NX500 dv camcorder.
I have two versions of dvgrab, dvgrab1.8 and dvgrab2.1. They have the same problem with qt file format.The command I used looks like this:
dvgrab --format qt QTTest

And then I got a file named "QTTest-001.mov".

I can play it with mplayer, but when I copy this file to Mac OS X and play it with Apple QuickTime, QuickTime player can only display white screen instead of normal video picture while it can play audio well.

File format recognized by QuickTime player is as following:

DV, 720*576(640*480), 16-bit integer(big endian) stereo 32.000khz

640*480 looks weird, because the description of raw dv file which can be played by Quicktime player well is 720*576(768*576).

Did anybody experience the same problem?

ANY advice will be appreciated.

---

