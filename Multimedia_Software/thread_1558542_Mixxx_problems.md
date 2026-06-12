---
title: "Mixxx problems"
date: 2010-08-22
forum: Multimedia Software
---

### Post by michael.the.bone on 2010-08-22
On the first use of Mixxx, everything was working.

However, now my waveform displays have stopped working, ive changed my  options to simple and then back again, unistalled and reinstalled. 

The top one now shows only a block white box with random little black squares and the second below has begun to work.

Any suggestions to fix this?

Also, is there an option the check the sound levels of songs so they are  the same. On my last mix, my levels were all over the place.

Cheers

---

### Post by rryan on 2010-09-18
Hi michael.the.bone,

I'm a Mixxx developer and what you're hitting is a known Qt bug.

We have a bug for it in our tracker here: [https://bugs.launchpad.net/mixxx/+bug/521509](https://bugs.launchpad.net/mixxx/+bug/521509)

To work around it, you can try going to Preferences -> Interfaces -> Skin and change the skin to a different skin then back to your current skin. For some people that has helped. 

Version 1.8.0 which will be released in about a week will have a workaround for this built in, and future versions of Qt will have this bug fixed for good. 

Cheers,
RJ Ryan

---

