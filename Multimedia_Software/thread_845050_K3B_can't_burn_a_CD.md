---
title: "K3B can't burn a CD"
date: 2008-06-30
forum: Multimedia Software
---

### Post by editrix on 2008-06-30
Tried asking this in General Help, but after five days and two bumps, no answer.

I *think* I have the bug described here:
[https://bugs.launchpad.net/ubuntu/+s...3b/+bug/121980](https://bugs.launchpad.net/ubuntu/+s...3b/+bug/121980)

Except I'm using Hardy.

K3B will read the original CD, but when I put in the one to be burned, it freezes. Then I can't eject the CD either with K3B, or the desktop icon, or Konqueror, or by pressing the eject button. And there's no pinhole to use a paper clip on! (an HP Pavilion 753n)

Eventually, the CD icon disappears from my desktop. I have to reboot to get the CD out.

Steps taken so far:

1. Turned off autonotification when the blank CD is inserted.

2. Added myself to all groups.

3. Gave myself full permissions on the CD writer: 
```
sudo chmod o+r+rw /dev/scd0
``` 

But, as I understand it, you need to reboot for this to register, and once you reboot, the permissions revert to the original, i.e.:
 0  dev='/dev/scd0'     rwrw-- : 'CyberDrv' 'CW078D CD-R/RW'

I'm using kernel = 2.6.24-18-generic, if that makes any difference.

UPDATE: I can rip a CD with KAudioCreator, but if I try to burn it in Brasero, I get an "unknown error." Has anyone got any ideas? Please?

---

