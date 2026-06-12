---
title: "Lose video on install of Mythbuntu 7.10"
date: 2007-10-07
forum: Mythbuntu
---

### Post by technoboi on 2007-10-07
My hardware: 
Abit iL-90MV (motherboard for 'mobile' CPUs) with on-board graphics.
Core 2 Duo Mobile CPU 1.83GHz.
2GB Corsair memory.


I load the Mythbuntu 7.01 CD into the CD drive, check its integrity and then restart to boot. It boots OK. Then the Mythbuntu screen appears with the 'cylon' eye going back and forth. For a short while there  is quiet, then the CD starts up again. The loading starts up and, once loaded, the video disappears. After about 10 minutes the CD starts up again but still the video does not reappear - and does not appear again.

I tried using the 'safe graphics' option on the Mythbuntu screen. This time there was a bit more action, I didn't lose video, but the install stalled when it reported 'LIRC not configured'. After trying to run the LIRC Deamon it reported: 
'The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0.'  
I don't currently, have an Infrared device. Is it essential for the install?

I had the nasty feeling that my motherboard might not be compatible with Linux so I tried booting from a Fiesty Fawn 7.04 beta disk that I happened to have. It booted up perfectly and I didn't lose video at any time.

Any suggestions as to what I can do to get the Mythbuntu disk to work?

---

### Post by laga on 2007-10-07
Hi,

does this also happen with a regular gutsy disk?

---

### Post by technoboi on 2007-10-07
> **laga said:**
> Hi,

does this also happen with a regular gutsy disk?

I don't know - I've only tried 7.04. I'll download 7.10, try it, and report back.

---

### Post by technoboi on 2007-10-07
I've just checked the computer out with Ubuntu 7.10 Desktop beta.
The results were similar to that with Mythbuntu. So it looks like it is the 7.10 beta that is at fault and not Mythbuntu.
I suppose all that can be done now is hope that it is fixed for the 'release' version of 7.10 and then, presumably, a release of Mythbuntu will follow.

---

### Post by laga on 2007-10-07
> **technoboi said:**
> 
I suppose all that can be done now is hope that it is fixed for the 'release' version of 7.10 and then, presumably, a release of Mythbuntu will follow.

There's even more you can do: file a bug. I presume that the xorg driver is at fault, although I can't be sure. You can file a bug here: [https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel)

---

