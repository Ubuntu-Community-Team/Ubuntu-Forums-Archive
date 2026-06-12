---
title: "[SOLVED] Edirol UA-25 plays a second of audio and then crashes"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by karl_forshaw on 2007-12-30
> Hi everyone

I recently upgraded my main computer from Fiesty to Gutsy. Since upgrading, my external soundcard - the Edirol / Roland UA25 (sometimes referred to as the UA-25) will only play about a second's worth of audio before crashing whichever program is using it.

My biggest problem is that I haven't got a clue where I should be looking for error messages, my only hope of diagnosing the problem lies in Google which returns mostly dead ends for me. 
I did manage to discover however that there may have been a bug in the version of alsa-lib that is shipped with Gutsy. In order to test whether this was the source of my problem I downloaded the Alsa modules tarball and the Alsa lib tarball and followed the instructions in their respective INSTALL files. Unfortunately this changed absolutely nothing for me, and I'm not sure of the command to run in order to check which version of alsa-lib is being used.

Could anyone help point me in the direction I should be looking for more information on what error may be occurring. I know this is not a hardware problem as the sound card is still working fine on my windows partition.

Thanks for reading


Karl :)


**Edit**

I have just solved this problem by rolling back the alsa-lib to version 1.0.13. If you are experiencing the same problem you can download the tarball from here

[ftp://ftp.alsa-project.org/pub/lib/]("ftp://ftp.alsa-project.org/pub/lib/")

Be sure you have the build-essential package installed before attempting to build this:

> sudo apt-get install build-essential

Then extract the tarball, open a terminal and 'cd' into the extracted directory, and run..

> 
./configure

make

sudo make install

sudo reboot


That fixed it for me, good luck!

---

### Post by radivx on 2008-02-26
Downgrading worked for me too.
However. I have problems with Audacity and 96KHz recording mode.

---

### Post by karl_forshaw on 2008-02-26
Yes, I have similar problems with Rosegarden. I have no sound whatsoever as far as midi playback is concerned and I haven't got a clue where to start. I'm considering giving Ubuntu Studio another shot.

---

