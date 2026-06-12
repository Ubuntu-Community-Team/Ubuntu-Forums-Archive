---
title: "What's different about Kubuntu and Ubuntu's sound systems?"
date: 2009-09-14
forum: Multimedia Software
---

### Post by rogueleader12345 on 2009-09-14
I had been having sound issues in Ubuntu, so I decided to switch to Kubuntu and the sound worked right after I installed it, and I didn't have to change anything. I tried and tried with Ubuntu, and FINALLY got it working, but not for online sound. A friend of mine said he'd had a similar problem, that Ubuntu has problems with HDA Intel cards, or RealTek. Ubuntu and Kubuntu are the same operating systems, just with different apps and desktop environments, so, what's the difference?

---

### Post by markbuntu on 2009-09-14
Kubuntu uses the Phonon sound server which is part of KDE4 and Ubuntu uses the Pulseaudio sound server. That is the big difference there.

They both use the same alsa hardware drivers which are part of the kernel but the way the sound servers interact with the drivers differs somewhat.

---

