---
title: "Install fresh Mythbuntu or install MythTV on latest stable Ubuntu release?"
date: 2011-07-24
forum: Mythbuntu
---

### Post by aquarius18 on 2011-07-24
After reading through the threads I am in 2 minds if I should install a fresh Mythbuntu (all-in-one) or add MythTV 0.24 to an existing 11.04 Ubuntu install.

Either way, the whole lot would go on a newly built box.

Can anyone give me some hints please? 

Thanks all

---

### Post by klc5555 on 2011-07-24
Depends on what the machine is primarily intended for. If it's primary purpose is TV and media, then go with the Mythbuntu installation. Mythbuntu is mostly Xubuntu + Mythtv packages, but with most extra stuff normally intended for a general-purpose desktop machine having been jettisoned.

If, however, the machine's intended to be mostly a general desktop, but with some TV and media functionality added, then you're likely better off adding the Mythtv packages to an existing Ubuntu installation.

---

### Post by KevinJaeger on 2011-07-24
> **klc5555 said:**
> Depends on what the machine is primarily intended for. If it's primary purpose is TV and media, then go with the Mythbuntu installation. Mythbuntu is mostly Xubuntu + Mythtv packages, but with most extra stuff normally intended for a general-purpose desktop machine having been jettisoned.

If, however, the machine's intended to be mostly a general desktop, but with some TV and media functionality added, then you're likely better off adding the Mythtv packages to an existing Ubuntu installation.This has largely nailed it.  Keep in mind that you can quite easily add any additional packages to a Mythbuntu installation if you want to add those desktop applications later.  But it is primarily aimed at running a dedicated Myth box, which is what I'm using it for.

---

### Post by aquarius18 on 2011-07-24
Thanks to both of you.

The machine is intended to act as a dedicated media machine only, so a Mythbuntu install appears to be most appropriate.

Then, adding MythTV to my desktop would just turn it into a frontend.

All good - thanks again.

---

### Post by itlarson on 2011-07-24
Actually, I haven't tried unity yet, and I'm wondering how it would be on a television screen.  The xfce panel is so small when used this way that I just turn it off and use desktop launchers.

---

### Post by klc5555 on 2011-07-25
> **aquarius18 said:**
> Thanks to both of you.

The machine is intended to act as a dedicated media machine only, so a Mythbuntu install appears to be most appropriate.

Then, adding MythTV to my desktop would just turn it into a frontend.

All good - thanks again.

For a remote frontend-only on your desktop, you won't need to add all of "mythtv", just the two critical packages: mythtv-common and mythtv-frontend. Later if you want them you can add some of the optional stuff like the mythtv-plugins and/or the extra mythtv-themes. The dedicated mythtv distros tend to treat mythtv as some sort of monolithic entity that must all be installed or not. But it's really closer to a swarm of related apps, utilities, and scripts that gives you considerable flexibility as to what you actually need on any individual PC.

Have fun!

---

### Post by aquarius18 on 2011-07-26
> **klc5555 said:**
> For a remote frontend-only on your desktop, you won't need to add all of "mythtv", just the two critical packages: mythtv-common and mythtv-frontend. Later if you want them you can add some of the optional stuff like the mythtv-plugins and/or the extra mythtv-themes. The dedicated mythtv distros tend to treat mythtv as some sort of monolithic entity that must all be installed or not. But it's really closer to a swarm of related apps, utilities, and scripts that gives you considerable flexibility as to what you actually need on any individual PC.

Have fun!

Thanks a Zillion! More food for thought. And yes, fun I will have \\:D/

---

