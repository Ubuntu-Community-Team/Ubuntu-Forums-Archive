---
title: "No audio after upgrade to Natty"
date: 2011-06-11
forum: Multimedia Software
---

### Post by putt1ck on 2011-06-11
Hi all

Ok, following chained updates of my music server from 10.04 to 11.04 I no longer have any sound, which is sort of bad for a music server...

Primary soundcard in the setup is USB

So I tried the command posted in various "no sound" threads

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

Which reinstalled stuff as expected, except had this error in the output:

Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.38-8-generic"

Could the error be because of backports?

aplay -l helpfully reports

aplay: device_list:240: no soundcards found...

and the output from 

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

can be viewed here:

 [http://www.alsa-project.org/db/?f=cb7dea14b93392304c212d358754c3f65b70dec7](http://www.alsa-project.org/db/?f=cb7dea14b93392304c212d358754c3f65b70dec7)       

All input gratefully received...

---

### Post by putt1ck on 2011-06-11
Ok, figured out the fix. If you use backports you have to install the backports modules rather than the ubuntu-linux ones.

Separately my user isn't in a group it should be (for whatever reason) but once I guessed at that issue and used sudo aplay I got outputs listed, so used those to reconfigure mpd and all is well. 

Hope this helps someone else...

---

