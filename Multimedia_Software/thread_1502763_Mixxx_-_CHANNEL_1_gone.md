---
title: "Mixxx - CHANNEL 1 gone"
date: 2010-06-06
forum: Multimedia Software
---

### Post by paulera on 2010-06-06
Hi there.

Since some time i am having a issue with mixxx, and now i´m able to give details.

Executing Mixxx first time: i choose my Music folder and everything is ok. Both CHANNEL 1 and CHANNEL 2 waveform displays ok and mixxx works fine. Closed mixxx.

Executing Mixxx for the second time (and others): the "CHANNEL 1" waveform display is all black. I can move files to it, and click play, but no waveform displayed. And, if i try to load any file in CHANNEL 2, all sound stops and mixxx does not respond to any of the play buttons (CH1 and CH2). The interface does not stop responding.

Now, i go to the terminal and remove ~/.mixxx folder, with all my configuration.

Executing mixxx after the configuration reset (removing folder mentioned above): the musics folder is requested again. I select it, and mixxx runs fine again!

But, if i close it and run again, all the history repeats. The problem is in the configuration files in ~/.mixxx folder, i guess.

I am running a fresh Ubuntu Netbook Remix 10.4 on a Acer Aspire One 110 (ZG5). I have just installed the OS, them the Mixxx application.

Please help!!!

Tks!!!!

---

### Post by 1ain on 2010-08-06
I'm having the same problem in 10.04 on my laptop and I've found this work around useful.

In MIXXX click options> preferences> interface, then left click twice on skin (without changing it) at the top of the window, click OK and the A deck display should return to normal ...... until the next time you want to use it!

If anyone knows a permanent solution it would be much appreciated. :)

---

### Post by rryan on 2010-09-18
Hi all, 

I'm a Mixxx developer and what you're hitting is a known Qt bug.

We have a bug for it in our tracker here: [https://bugs.launchpad.net/mixxx/+bug/521509](https://bugs.launchpad.net/mixxx/+bug/521509)

1ain's workaround is the only way around the visual corruption bug for 1.7.x unfortunately. Version 1.8.0 which will be released in about a week (and is included in Ubuntu 10.10) will have a workaround for this bug built in.

Cheers,
RJ Ryan

---

