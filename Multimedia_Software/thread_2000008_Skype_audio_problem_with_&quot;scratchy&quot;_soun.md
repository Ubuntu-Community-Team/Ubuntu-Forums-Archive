---
title: "Skype audio problem with &quot;scratchy&quot; sound"
date: 2012-06-08
forum: Multimedia Software
---

### Post by michael37 on 2012-06-08
I upgraded to 12.04 64-bit and had problem with Skype audio quality. Skype version is 2.2.0.35 from partner repository. Both incoming and outgoing sound was very scratchy. People had hard time hearing me.

Skype installation required installation of comprehensive 32-bit ia32-libs as expected in previous versions.

Unusual: In Precise 12.04, Skype gives me one and only option to use PulseAudio Server (local) in Skype->Options->Sound devices

I then following instructions for [https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting) with no luck initially.

Luckily, there are a few fixes that worked for me:

1. It's gedit ~/.asoundrc. Slash is quite important.
2. Since Skype is 32-bit, you need 32-bit aoss, not the default 64-bit: sudo apt-get install alsa-oss:i386

Once you make these two corrections, sound works fine. I updated the wiki... hope it works for you too.

---

