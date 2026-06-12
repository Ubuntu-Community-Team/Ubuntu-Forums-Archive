---
title: "Upgrading from 7.10"
date: 2008-10-29
forum: Mythbuntu
---

### Post by sudleyplace on 2008-10-29
In order to upgrade from Mythbuntu 7.10 to the latest version, the instructions say I need to bring 7.10 up-to-date.  That requires a Mythbuntu 7.10 CD which I don't have.  The Mythbuntu.org site no longer has that CD available, nor have I been able to find it readily available on the 'Net.  Actually, I have tried downloading it through BitTorrent, but the current ETA is over one week.

How do you suggest I proceed -- ignore the requirement to update and just upgrade?  Will a Ubuntu 7.10 CD do just as well?

---

### Post by klc5555 on 2008-10-29
> **sudleyplace said:**
> In order to upgrade from Mythbuntu 7.10 to the latest version, the instructions say I need to bring 7.10 up-to-date.  That requires a Mythbuntu 7.10 CD which I don't have.  The Mythbuntu.org site no longer has that CD available, nor have I been able to find it readily available on the 'Net.  Actually, I have tried downloading it through BitTorrent, but the current ETA is over one week.

How do you suggest I proceed -- ignore the requirement to update and just upgrade?  Will a Ubuntu 7.10 CD do just as well?

The *.iso image for Mythbuntu 7.10 is evidently still available here: [http://linux-iso.bytepedia.org/](http://linux-iso.bytepedia.org/)

Cheers! :)

---

### Post by mrand on 2008-10-29
> **klc5555 said:**
> The *.iso image for Mythbuntu 7.10 is evidently still available here: [http://linux-iso.bytepedia.org/](http://linux-iso.bytepedia.org/)

Cheers! :)Howdy guys,

The .iso won't bring the install up-to-date... that CD was frozen a year ago.

The best (and only?) way to bring a system up-to-date is to use update-manager, or apt-get, or aptitude.

   Marc

---

### Post by klc5555 on 2008-10-29
> **mrand said:**
> Howdy guys,

The .iso won't bring the install up-to-date... that CD was frozen a year ago.

The best (and only?) way to bring a system up-to-date is to use update-manager, or apt-get, or aptitude.

   Marc


Or a clean install, which is likely how I'll try to make the jump from 7.10 to 8.10, skipping 8.04 altogether, which I could never get working satisfactorily on my particular hardware anyway.

Which is why the original poster should download a copy of 7.10 and keep it on hand: if the intended upgrades leave him with a inadvertant 8.04/8.10 doorstop instead of a fully functioning 7.10 box, he might want to have a 7.10 reinstall from scratch available to him as a viable plan B. He'd best also have his recordings tucked away on a separate partition/disk, and have a couple of good copies of his last up-to-date 7.10 mythconverg database tucked away too. Saved me a lot of aggravation on a few up-and-down transitions between 7.10 and 8.04 before I decided to stick to 7.10 and wait a while.

Cheers! :)

---

### Post by Caps18 on 2008-10-29
I'm still running 7.10 and I don't see why it would be worth the risk of breaking what works now to upgrade to 8.04/8.10.

If I did upgrade, I would buy a whole new hard drive, do a fresh install and then add the old hard drive as the second drive to the system.

---

### Post by sudleyplace on 2008-10-29
> **mrand said:**
> Howdy guys,

The .iso won't bring the install up-to-date... that CD was frozen a year ago.

The best (and only?) way to bring a system up-to-date is to use update-manager, or apt-get, or aptitude.

   Marc

Yes, but when I run the UpdateManager, it asks for the CD labeled Mythbuntu 7.10 - i386, so that's why I needed it.

Thanks to the suggestion from klc5555 to get it from bytepedia -- that worked.

---

### Post by klc5555 on 2008-10-29
> **Caps18 said:**
> I'm still running 7.10 and I don't see why it would be worth the risk of breaking what works now to upgrade to 8.04/8.10.

If I did upgrade, I would buy a whole new hard drive, do a fresh install and then add the old hard drive as the second drive to the system.

Unless a version upgrade adds a feature or support you really can't do without, or fixes something that is broken and will not be patched in your release, I don't think there's really any reason to do one. You're right, why bother with the inevitable upgrade breakage fallout if there's no reason to? Especially with super-rapid upgrade cycles.

Just my feeling, anayway.

All the best.

---

### Post by mrand on 2008-10-29
> **sudleyplace said:**
> Yes, but when I run the UpdateManager, it asks for the CD labeled Mythbuntu 7.10 - i386, so that's why I needed it.Ah, yes.  Update-manager has an affinity for whatever source it was originally installed from.  Once my install was complete, I commented out the following line from /etc/apt/sources.list:
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
```

Then it stops asking for the cd.

[INDENT]Marc[/INDENT]

---

