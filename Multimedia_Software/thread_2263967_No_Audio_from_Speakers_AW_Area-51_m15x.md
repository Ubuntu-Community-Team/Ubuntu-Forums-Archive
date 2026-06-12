---
title: "No Audio from Speakers: AW Area-51 m15x"
date: 2015-02-04
forum: Multimedia Software
---

### Post by vpalko32 on 2015-02-04
Hello all! I had previously got this issue resolved on 12.04LTS few years back and can not find the forum to get the audio working again. Had followed the sequences from the forum I found [here]("http://ubuntuforums.org/showthread.php?t=1732225&page=2") without any luck. Yes, all 3 devices are unmuted and set to max volume. The 2 AUX ports work fine with headphones and external speakers. When I boot into Vista, the audio works fine on the speakers. Just when booting into 14.04.1 LTS is where the issue arises. I still have yet to test out the HDMI output for audio as video output proved to work Monday night. Please bear with me, my fimiliarity with Ubuntu is still low, only 5 months experience on it until my testing platform blew its MB. Thank you again for your time in helping a noob out.  
Specs below.  
[IMG]http://i.imgur.com/whGghUW.png[/IMG]

---

### Post by vpalko32 on 2015-02-09
bump.

Can I at least have a link to the forum in which the issue was resolved?

---

### Post by JeQhdMD on 2015-02-10
If you still have the same user ID (from days of 12.04). . . you should just search under quick links for "show all of my posts" . . . it should still be there if you scroll far enough.

---

### Post by vpalko32 on 2015-02-11
I had to re-register. My original UID was vpalko3 which no longer is active, and no forums appear with that UID when I search for it. =/

---

### Post by Yellow Pasque on 2015-02-11
> **vpalko32 said:**
> I had to re-register. My original UID was vpalko3 which no longer is active, and no forums appear with that UID when I search for it.

Perhaps an administrator could find your old posts: [http://ubuntuforums.org/forumdisplay.php?f=48](http://ubuntuforums.org/forumdisplay.php?f=48)

The suggestion I see when seraching the web is using "options snd-hda-intel model=lenovo-101e" in /etc/modprobe.d/alsa-base.conf file. Does that sound familiar?

---

### Post by vpalko32 on 2015-02-11
It does sound familiar. I've used "=lenovo-101e", "=lenovo101e", "=mbp3", "=generic", "=3stack-6ch-dig", "=3stack-6ch", and "=gateway"

[http://ubuntuforums.org/showthread.php?t=1732225&page=2](http://ubuntuforums.org/showthread.php?t=1732225&page=2) shows a resolved issue with the same rig from a different user; however, it does not work on my end. I doubt the HDD or SSD makes a differece. I had 12.04 on the HDD on the rig that fried on me. (Exact same model rig I am using now, just used as a platform for testing mods, etc.) 

I will contact an admin to see if they can ressurect the old account's post though I recall I fould the solution in the forums. I will ask the admin anyways.

---

### Post by vpalko32 on 2015-02-17
> **Temüjin said:**
> Perhaps an administrator could find your old posts: [http://ubuntuforums.org/forumdisplay.php?f=48](http://ubuntuforums.org/forumdisplay.php?f=48)

The suggestion I see when seraching the web is using "options snd-hda-intel model=lenovo-101e" in /etc/modprobe.d/alsa-base.conf file. Does that sound familiar?

I have contacted the admin from the post you've provided. I have not posted anything using my old account. Any suggestions as to what may be causing the audio to work on the AUX jacks and HDMI out but not on the built in speakers? T

---

### Post by vpalko32 on 2015-02-20
bump.... Did a full format and fresh install of 14.04. Even when integrated/discrete graphics no sound is produced from the built in speakers. =/

---

