---
title: "Pointer Flashing/disappearing"
date: 2010-07-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-07-09
Hi

I just upgraded from 10.04 to 10.10 Alpha2 I'm getting the pointer keeps flashing
or disappearing ......

Any ideas? I'm running dual boot on an iMac 10.6.4 ...IGB of RAM ..

Thanks

Jaco

---

### Post by BwackNinja on 2010-07-09
It's intended behaviour, the package 'unclutter' is now installed by default. If you don't like it, you can just remove it.

---

### Post by 23dornot23d on 2010-07-09
Here check this link out ..... [Mouse Pointer On / Off]("http://ubuntuforums.org/showthread.php?t=1523760")

Since adding unclutter ....

[Solution]("http://ubuntuforums.org/showpost.php?p=9536975&postcount=17")

Set it to false ...... to stop the mouse going off .......

---

### Post by jaco223 on 2010-07-09
> **23dornot23d said:**
> Here check this link out ..... [Mouse Pointer On / Off]("http://ubuntuforums.org/showthread.php?t=1523760")

Hey guys 

Thanks for such a quick reply ....will check the links ...Man that seems to be
the only issue I "Thought" was having ....better read the new features ....I'm
grateful the upgrade went so smoothly ...will be testing and reporting any
oddities I come across ...

Thanks again ...

Jaco

---

### Post by cariboo on 2010-07-09
According to the Ayatana mailing list, unclutter was added by mistake, and should be removed in later versions.

---

### Post by jaco223 on 2010-07-09
> **cariboo907 said:**
> According to the Ayatana mailing list, unclutter was added by mistake, and should be removed in later versions.

Thanks Cariboo ....I did apt-get remove unclutter ...should I go back and do a purge?
And I guess a reboot is needed?

---

### Post by cariboo on 2010-07-09
To completely remove a package, use the purge option. That way it stops working without having to do a reboot.

---

### Post by kyleabaker on 2010-07-09
> **cariboo907 said:**
> According to the Ayatana mailing list, unclutter was added by mistake, and should be removed in later versions.

I never used Unclutter before, but I find it very useful now. I think it would be great to leave in (even if disabled by default) with settings in the mouse preferences dialog. This would make it easier on everyone.

---

### Post by cariboo on 2010-07-09
I use unclutter on my netbook, but I find annoying on my desktop systems.

---

