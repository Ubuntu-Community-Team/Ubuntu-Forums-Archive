---
title: "Audacity click track mayhem?"
date: 2008-01-10
forum: Multimedia Production
---

### Post by Belliinator on 2008-01-10
Hey,

Im currently using Kubuntu 7.04 on this laptop, which 'boasts ' of two in-built speakers a mic input and headphone input.

I downloaded audacity, which works well, but when insert a click track, and then record another track through the microphone of my guitar, it records the click track again as well, making this annoying distorted noise of the two click tracks out of synch and my guitar continues as normal.

I wear headphones to hear the click track, and my microphone is no where near me. Am I recording the machines ouput and input at the same time? Thanks in advance.

---

### Post by tgalati4 on 2008-01-11
Some sound chips have a "monitor" mode where the input and output are patched.  You can sometimes turn this off, sometimes it's hardwired on.  Double click on the speaker icon and bring up the mixer.  Edit-->preferences and turn on all the channels and switches.  Explore each one to see if you can turn the monitor mode off.

Audacity has a "software monitor" in the preferences where you can play a track as you are recording it.  Of course this can cause stuttering because it's using the same sound hardware to record and play back at the same time.  Some chips handle full-duplex mode fine.  Others choke badly.

For serious recording, you need to run a real-time kernel that minimizes interrupts to the sound hardware.  Burn a copy of Dynebolic (dynebolic.org) and boot it Live.  You can save a "nest" on your hard drive to preserve user settings and recordings.  You may get better recording performance from Dynebolic than kubuntu.

---

