---
title: "Sound system has gone missing after trying to install Creative x-fi"
date: 2009-07-28
forum: Multimedia Software
---

### Post by Stolea on 2009-07-28
Hi all,
I followed the instructions on how to install my brand new Creative X-Fi Extreme audio on my Intel DG31PR motherboard. Up until this I was using the on-board sound system which worked just fine.
After the install I had no sound at all and even after unplugging the new card nothing works. The volume control show the mute x and give the following error message "No volume control GStreamer plugins and/or devices found"
In the "Sound Preferences" the tests don't get any response or come back with errors.
I fear I have killed the beast and would like to re-install the default drivers. I would dread to have to do a full reinstall just to get my sound back.
HELP!!!

---

### Post by Stolea on 2009-07-28
anyone???

---

### Post by igorzwx on 2009-07-28
It might be reasonable to have two Ubuntu 9.04 (in dual boot)
with different sound systems.
One of them may work.

Check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by Stolea on 2009-07-28
Thanks

---

### Post by Stolea on 2009-10-28
The way I overcame the issues with X-Fi is to get an older Audigy 2 card. I have tried that card in a couple of other computers with Ubuntu and had the same disappointing result. I am sure that in time there will be a suitable driver that doesn't involve major frustrations.

---

