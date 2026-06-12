---
title: "amsn sound error"
date: 2008-12-27
forum: Multimedia Software
---

### Post by groovomata on 2008-12-27
Hello All,
I'm trying to configure the audio settings for amsn (amsn_0.97.2~debian-0ubuntu3_i386.deb). I don't have issues with other programs like skype so I know that it can work. Unfortunately, with amsn, when I try to select the output device and play a test sound I get this error:
> An error occurred when trying to play the sound: could not gain access to /dev/dsp for writing.

The error occurs with every option I choose:
/dev/dsp
/dev/dsp1
/dev/audio
/dev/audio1

I'm using ubuntu 8.10 and have no other obvious sound issues. Has anyone had this problem?
Thank you!
Erik.

---

### Post by groovomata on 2008-12-27
I discovered that when I reboot my machine and check the audio settings on amsn before using any other program - it works! Amsn both plays and records sounds. Okay, now to see if I can isolate what keeps access to /dev/dsp.
All the best,
Erik.

---

### Post by groovomata on 2008-12-27
Upon starting up youtube with firefox, I reproduced the sound error amsn was getting. Closing the tab with youtube didn't stop the error, however shutting down firefox did.

---

### Post by Bleezy on 2009-02-17
Oh wow!! Dude...this worked for me! LOL! I had a firefox open to youtube...i closed it down just like this guy said and now my sound works like a charm!!

[SOLVED] :popcorn:

---

