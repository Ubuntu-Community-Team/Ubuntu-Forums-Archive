---
title: "No sound.  Help?"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by nintennuendo on 2007-07-07
I have no sound.  No system beeps, no music, nuthin.  In alsamixer, everything is unmuted.  I don't know how or where the devide manager is, In windows it listed attached hardware.  In Volume Control > File >Change device, I have HDA nVidia(Alsa Mixer)  and SigmaTel STAC9200 (OSS Mixer).  

ANy help would be wonderfully appreciated.

---

### Post by scholzilla on 2007-07-08
Hi,

This might be the result in a known bug in ubuntu 7.04 (see launchpad bug #121105). Here's what I would suggest if nothing else seems to work: Reinstall ubuntu, but do not use update manager to install all updates. At least if you do, uncheck the kernel updates (which are listed first, as security updates). One of these definitely disables the sound on my laptop. 

No one has bothered to answer posts I've made about what sort of risk not doing the security updates causes, but unfortunately, it's pretty frequent that nobody bothers to respond to posts (see multiple posts I've made). I use <apt-get upgrade> from term to do my upgrades because, by default, this withholds the kernel updates. I don't know if anyone is actually working on this issue, that's another question that no one seems to want to answer. Welcome to ubuntu!

---

