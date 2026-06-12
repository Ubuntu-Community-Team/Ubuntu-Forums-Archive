---
title: "ALSA is broken"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by Desolator on 2007-12-20
Hello everyone, tihs is the first time I post on the Ubuntu Forums, though I've been on IRC for quite a while, some of you might know me as 'ActySofts'.

Well, my problem is that 2 days ago sound worked fine, the only problem was that ALSA didn't support mixing with my sound card, so I went off and picked the .deb of OSSv4 and installed it. It was kinda slow, so I went to 4Front Tech's forums and found a guide to compile OSS on Ubuntu. It went fine, but it linked against older kernel headers all the time and complained that it couldn't relink against the new ones. So I went on, reinstalled and removed it a few times to make sure nothing remains from it, then I reinstalled the packages 'alsa-base' & 'libesd-alsa0'. (I removed 'alsa-oss' later.)

It worked fine until yesterday, when ALSA decided to go mad at me and all the volume controls are partially locked at a specific volume or muted, thus if I want to change the volume it goes up or down like mad, and if it goes over 70% the channel is muted, and I have no sound at all. Any ideas?

I'm using Gutsy, '/' is JFS, '/home' is ext3, I've got a Windows partition mounted at '/media/hdc1', well, what info can I give? You will almost always find me on MSN (and maybe Y!M also) so you can ask to me come to IRC or so. Thanks!

---

### Post by fs3rp4 on 2007-12-20
Try to compile the last version of ALSA and libs from Alsa's site. Aparentily this fix most of problems with HD sound systens.

---

### Post by Desolator on 2007-12-20
Well I've reinstalled Ubuntu, kept my /home partition intact and guess what...ALSA is still mad! So the question now is how to I 'reset' my /home partition?

---

### Post by Desolator on 2007-12-21
It appears that my sound card got fried for some reason. Well, time to get another, as the onboard one is kinda old and broken. Thanks anyway.

---

