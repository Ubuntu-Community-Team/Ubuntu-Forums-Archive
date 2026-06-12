---
title: "Another Karmic sound issue"
date: 2009-10-30
forum: Multimedia Software
---

### Post by d_in_Conduct on 2009-10-30
Card: Intel 82801JI (ICH10 family)
Karmic Koala.  Fresh install from the Beta CD.  Up to date as of this moment.  I installed some pulseaudio stuff as suggested in some of the comprehensive sound troubleshooting threads.  No threads describing this issue have been found and no pulseaudio installs have changed it.

I wrote a python program that watches the system clock and according to a schedule tunes my shortwave radio and records what's there using ecasound.  The capture device is line-in and capture gain is about 70%.  Often, when I open one of the resulting .wav files with Audacity, the capture gain drops to zero.  I haven't been able to pin down what other conditions might be causing this.  It doesn't seem to do that when ecasound begins recording.

The program runs 24/7, so if I forget to reset the capture gain before leaving the computer, I get silent recordings until I get back.

---

