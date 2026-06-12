---
title: "sound  problem in watching youtube"
date: 2010-08-22
forum: Multimedia Software
---

### Post by tapas_mishra on 2010-08-22
I am having sound problem in Watching Youtube videos.
Following link gives a solution which does work.
[http://www.ivankristianto.com/os/ubuntu/tips-solving-ubuntu-sound-problem-without-restart/440/](http://www.ivankristianto.com/os/ubuntu/tips-solving-ubuntu-sound-problem-without-restart/440/)
Not sure if it is same bug I am facing,
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654/)

In my case sound does not stop working but it does echos the same sound and the effect is like the audio repeats the sound between a certain section of sound in a loop repeatedly.
This interval is of the order of milli seconds so even if the play head keeps moving and I see the video also correctly I would be hearing a sound and repeatedly same sound to be exact 
which is very annoying and frustrating.

I did alsa-utils restart but did not worked.
Unless I kill firefox and restart again.
> cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on May 24 2010 for kernel 2.6.28-11-generic (SMP).> uname -a
Linux tapas-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 
2009 i686 GNU/Linux
> cat /etc/issue
Ubuntu 9.04 \n \l
Is there some other way?
Killing firefox does work but each time I have to wait for a minute or 2 as so many tabs are open and I have to wait for each of them to load.
More over if it is a one hour video then I have to wait for that to come again for an hour and some of the ISP's have some limit to the data being accessed.For which they charge.
[http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html](http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html)
purging pulseaudio seems to have some effect but not the desired effect.

---

