---
title: "problems with skype and amsn after upgrade to 8.10"
date: 2008-11-23
forum: Multimedia Software
---

### Post by frank_777 on 2008-11-23
Hi everybody. I recently upgraded from 8.04 to 8.10. Everything went quite allright but the fact that now I'm not able anymore to call or having videochat trough skype or amsn. For the rest, I can normally watch video files and listen music.

My laptop is a Packard Bell easynote and the webcam is internal.


Any idea?

thanks!

francesco

---

### Post by ipburbank on 2008-11-23
There are lots of people with this problem, un-fortunately including me, and there are lots of solutions, and un-fortunately none of them work for me. Actually, if I turn my mixers gain all of the way up, and scream into the mic I can hear a groggy kind of moan that resembles my inflection pattern, but won't quite cut it for tutorial making. If anyone can help out here that would be great, I have tried killing pluseaudio, and also tried doing that with the -w, I have gone into system -> preferences -> sound and changed all of the setting there, but to no avail.

~help anyone? please? - Istvan, Creator of All Free VFX

---

### Post by frank_777 on 2008-11-23
> **ipburbank said:**
> There are lots of people with this problem, un-fortunately including me, and there are lots of solutions, and un-fortunately none of them work for me.

by the way could you indicate me if there are other possible solutions, apart the ones you mentioned here?

best!

---

### Post by psyke83 on 2008-11-23
Please see the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

You need to configure PulseAudio correctly, and configure Skype to use PulseAudio.

Everything's explained in the guide.

---

### Post by ipburbank on 2008-11-23
Here are some other links:

[http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

[http://forum.skype.com/index.php?showtopic=231961](http://forum.skype.com/index.php?showtopic=231961)

but google will turn up links and solutions by the hundreds.

~hope that helps, checking out that other link now - Istvan, creator of all Free VFX

---

### Post by frank_777 on 2008-11-24
> **psyke83 said:**
> Please see the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

You need to configure PulseAudio correctly, and configure Skype to use PulseAudio.

Everything's explained in the guide.

Many thanks. After fixing PulseAudio and specifying on Skype that I want it to use 'pulse' and not a default peripheral, it worked quite well.

Yet I didn't solve the problem with my webcam, even if i followed the different strategies I found on google, like modifying the \etc\profile file or to editing the launcher for skype.

Seems this problem for my laptop is more serious, maybe I have to wait for the next kernel...

---

