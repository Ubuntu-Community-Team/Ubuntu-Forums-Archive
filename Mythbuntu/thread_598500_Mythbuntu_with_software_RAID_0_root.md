---
title: "Mythbuntu with software RAID 0 root?"
date: 2007-10-31
forum: Mythbuntu
---

### Post by nitestick on 2007-10-31
this evening i've been attempting to build a RAID 0 array to use as the root partition but i have no idea how to (or if it is even possible) install mythbuntu 7.10 on it :(

so if anyone could shed some light on this it would be greatly appreciated , standing by with popcorn :popcorn:b

---

### Post by napsilan on 2007-10-31
Are you using an onboard software raid (fake raid) controller?  I'm going to assume so for this.  I managed to install dapper (I think) on my software raid a while ago using dmraid.  Check out the links below since the process  has probably changed since then, but the outline that I used was.

1. install dmraid in livecd
2. mount raid array (after setting up in bios)
3. chroot, debootstrap and  apt-get install ubuntu-desktop (probably mythbuntu-desktop in this case)
4. manually install bootloader and retarget to raid

This could have changed since then, and if you are using a hardware raid controller, or none at all, then this will probably be different (perhaps involving lvm?).  The first thing that I'd try for simplicity's sake is installing dmraid in the live CD, mounting your array, and then using the standard installer and see if the newer versions just work with it.  

Links:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

