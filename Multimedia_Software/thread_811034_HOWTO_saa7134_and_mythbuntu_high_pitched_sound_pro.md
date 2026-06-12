---
title: "HOWTO: saa7134 and mythbuntu high pitched sound problem fixing"
date: 2008-05-28
forum: Multimedia Software
---

### Post by eldragon on 2008-05-28
ive had this problem for a while.

mythtv works ok, audio works, but the audio has a high pitched echo. cant describe it well, it drove me nuts. and found nothing on how to fix this.
this is why im posting what i did to get this fixed.

for device, i had
/dev/dsp < my sound card's OSS file
/dev/dsp1 < my saa7134 capturecard's OSS module.

i picked from mythtv-setup, under capture card, sound device: /dev/dsp1

and then, at the frontend.
i went to recording profiles, picked livetv. and switched the recording sample rate to 32000. (Apparently the card cant do anything other than that).

you need to do this to all recoding profiles to get it working on them.


:D presto!


good luck

---

### Post by CuraHack on 2008-11-21
Doesn't work for me :mad: and its driving me crazy, 

did you need to install / configure any drivers or so? PLEASE HELP ME :(

I'm using Mythbuntu 8.10 (for the first time), and the SAA7134 card

---

### Post by adamkane on 2009-01-06
You need to turn off Compiz. Then you need to determine your card number and your tuner number to modify /etc/modprobe.d/options

See:

[http://ubuntuforums.org/showthread.php?t=884438](http://ubuntuforums.org/showthread.php?t=884438)

---

### Post by oobe-feisty on 2009-03-02
Thanks you saved me some time


> **eldragon said:**
> .

for device, i had
/dev/dsp < my sound card's OSS file
/dev/dsp1 < my saa7134 capturecard's OSS module.

i picked from mythtv-setup, under capture card, sound device: /dev/dsp1

and then, at the frontend.
i went to recording profiles, picked livetv. and switched the recording sample rate to 32000. (Apparently the card cant do anything other than that).


---

