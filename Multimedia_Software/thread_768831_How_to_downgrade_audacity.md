---
title: "How to downgrade audacity"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Anders J on 2008-04-26
I upgraded from ubuntu 7.10 to 8.04 and got the audacity 1.3.4beta, which is missing the "change tempo" and "change pitch" functions, which are both the very essence of Audacity.

Tried to download the Debian package, but was told the was an error since a later version was already installed.

Being only one year into Linux ubuntu, what is the best way to downgrade to a suitable version?

---

### Post by horace on 2008-05-04
Uninstall 1.3.4 in the Synaptic Package Manager, then download the 1.3.3 .deb from [http://packages.ubuntu.com/gutsy/i386/audacity/download]("http://packages.ubuntu.com/gutsy/i386/audacity/download") and install that instead (assuming i386 - I got the amd64 version). 

I've just been doing this for the same reason, but hadn't seen your post till now. With any luck the bug will be fixed soon and you will be able to update to the current version.

hth

---

### Post by alibro on 2008-07-01
Thanks for the tip. :guitar:

I put a clean installation of Ubuntu Studio 64 8.04 on my AMD PC and if I started Jack, Audacity wouldn't see it or any sound card at all, even though Ardour could see Jack no problem. Without Jack running Audacity worked fine and could see the sound card (an M Audio Delta66). I downgraded as suggested and now it works with and without Jack running.

Cheers
Alibro

---

