---
title: "No Sound on External speakers"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by Wainui on 2008-04-10
Hi all,

I'm a first time Ubuntu user. Just installed **Ubuntu Linux 7.10 **on a Compaq Deskpro EN which was previously running Windows 2000 on a seperate HDD. All was OK but when I installed Ubuntu on a different HDD I cannot heard any sound on the External speakers which are plugged into the Mobo, only sound on the little internal speaker.:(

The sound chip is : **Intel 82801BA(M) ICH2 - AC"97 Audio Controller**

I did have a look at the Volume Control panel and the speakers are not muted. Any ideas on how to get the External speakers give out sound.

Thank you.

---

### Post by Metaljaz on 2008-04-11
Try opening the terminal and typing this command:
alsamixer

scroll until you get to external. Make sure it is on or unmuted. Press "M" to mute or unmute.

May be the solution.

---

### Post by deadgobby on 2008-04-11
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller?highlight=%28intel%29](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller?highlight=%28intel%29)
All so double click on the speaker ICON and check if the little ditty is not click on.

---

### Post by Wainui on 2008-04-12
Thank you both for your input.

**Metaljaz**,  your post gave me a lead and it was quite by acident I managed to fix my problem. I expanded the  **Alsamixer terminal ** as you suggested but there was no option for an **External Speaker**, instead the **Master Control **, which was not available initially in the Volume Control  settings but I managed to insert by fiddling in the **Volume Control Preference Menu**, controls the volume on the External speakers. :)

So, I'm all happy chappies again. :guitar:

Cheers.

---

