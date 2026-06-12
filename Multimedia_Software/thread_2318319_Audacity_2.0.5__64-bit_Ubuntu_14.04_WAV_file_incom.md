---
title: "Audacity 2.0.5 / 64-bit Ubuntu 14.04: WAV file incomplete read"
date: 2016-03-25
forum: Multimedia Software
---

### Post by brilyant on 2016-03-25
This has cropped up in the last two weeks.

When I load a 30+ minute stereo WAV file, the first 25 minutes look and sound OK: thereafter the waveform has a complicated but repeating pattern.  Playing this part of the file results in no output.

If I delete a few seconds from the beginning of the file, I lose more audio from one track than the other.

I have tried three different files, all are treated the same.

It works ok on my 32-bit dektop.


Any clues?  Has there been a recent update that might affect Audacity/

Andrew

---

### Post by ajgreeny on 2016-03-25
I am using audacity 2.1.2-1 from a ppa at [https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity) and do not see this problem on my Xubuntu Trusty 64bit system.  It might be worth you trying that ppa version.

---

### Post by Bucky Ball on 2016-03-25
You should be on 2.0.6 so maybe there's an update that can fix the issue rather than one that caused it. I suggest 
> 
sudo apt-get update
sudo apt-get dist-upgrade

... reboot and try again. I don't have any audio files that long to test it so let us know how you go.

---

### Post by brilyant on 2016-03-27
Thanks for your thoughts.

I've done the dist-upgrade, and Audacity remains stubbornly version 2.0.5.

Is there a downside to using a package from a later distribution?  I don't have any editing booked for a few weeks now, so I'm inclined to upgrade to Ubuntu 16.04 next month, and see what happens.  That will presumably pull in a later version of Audacity.

Will report back.  Thanks again.

---

### Post by ajgreeny on 2016-03-27
You may have problems trying to install a later version without enabling the ppa as I suggested above; I suspect you will find some dependency problems, though I have never tried to do it, so could be wrong..

---

### Post by Bucky Ball on 2016-03-27
You did 'sudo apt-get update' prior to running the dist-upgrade command? Essential. If so, very peculiar. :-k

---

### Post by brilyant on 2016-04-11
Upgraded to 2.1.2 using ppa, but no difference.

Realised the onset of the problem was at the same point in time for all files, so began to suspect memory/storage problems.

Discovered Audacity was putting temp audio data files into /var/tmp, which occupies a relatively small partition on my laptop.

Shifted data file directory to a larger partition and all now ok.

Will now talk to Audacity about a warning flag for this.

Thanks again for your interest and your help,

Andrew.

---

