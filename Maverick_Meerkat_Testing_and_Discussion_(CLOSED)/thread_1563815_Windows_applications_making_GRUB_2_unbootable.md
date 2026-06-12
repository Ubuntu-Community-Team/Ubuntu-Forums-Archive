---
title: "Windows applications making GRUB 2 unbootable"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by plun on 2010-08-29
From Colin Watson blog

> This is a bug in which some proprietary Windows-based software overwrites particular sectors in the gap between the master boot record and the first partition, sometimes called the "embedding area".

**Please read further !**

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)


Ubuntu Maverick bug:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)


---

---

### Post by MacUntu on 2010-08-29
Pirate Adobe products to save Ubuntu! :D

Jokes aside, this is really just sad. :(

---

### Post by plun on 2010-08-29
> **MacUntu said:**
> Pirate Adobe products to save Ubuntu! :D

Jokes aside, this is really just sad. :(

Well... the joke was "bulls eye".....:D

but indeed sad....

---

### Post by Sub101 on 2010-08-29
Isnt this fairly common, particularly for Windows recovery programs, and with a fairly simple fix? (That being to remove the recovery program)

---

### Post by ranch hand on 2010-08-29
Real easy work around.  Delete all signs of MS from your HDD and you will have no trouble.

---

### Post by plun on 2010-08-29
> **ranch hand said:**
> Real easy work around.  Delete all signs of MS from your HDD and you will have no trouble.

Well... I have done that on my PCs but we live in a world with dual-booters...

A challenge....

---

### Post by scorp123 on 2010-08-29
> **ranch hand said:**
> Real easy work around.  Delete all signs of MS from your HDD and you will have no trouble.
 ... or at least banish it into a virtual machine where it can't crash your hardware :D

---

### Post by ranch hand on 2010-08-29
@plun
I multi-boot and have no trouble keeping MS products off my box.

@scorp123
That would work too.  I have never quite understood why you would install Linux on VM in a MS install.  Seems silly to me to put the more secure OS in VM.

If you really are a MS junky then installing it in VB on a more secure OS makes a lot more sense.

Weren't we just being regaled the other day about how much MS loves and supports the FOSS community?  I for one just believed that right off the bat.

Just like I believe this is not intentional.

---

### Post by scorp123 on 2010-08-29
> **ranch hand said:**
>  I have never quite understood why you would install Linux on VM in a MS install.  Seems silly to me to put the more secure OS in VM.  Absolutely!! :D

---

### Post by ktp on 2010-08-29
> **ranch hand said:**
> Real easy work around.  Delete all signs of MS from your HDD and you will have no trouble.

true solution...but might not work for everyone (yes sad).

---

### Post by ranch hand on 2010-08-29
> **ktp said:**
> true solution...but might not work for everyone (yes sad).
Ah yes, but scorp123 had the solution for that.

Basically just don't let the good folks at MS and the app suppliers for them to get anywhere near your HDD with any power to do ANY thing to it.  Then all you have to do is put up with their OS wearing out your HDD with continuous IO cycles of RW.

You can tell is a working OS just by listening to your HDD grumble and grunt.

---

### Post by ktp on 2010-08-29
> **ranch hand said:**
> Ah yes, but scorp123 had the solution for that.

Basically just don't let the good folks at MS and the app suppliers for them to get anywhere near your HDD with any power to do ANY thing to it.  Then all you have to do is put up with their OS wearing out your HDD with continuous IO cycles of RW.

You can tell is a working OS just by listening to your HDD grumble and grunt.

vm is good for most things but still not well for gaming.  

But I guess there is point in time when you just give up games and learn windows is not worth it. =)  But just saying not a perfect solution for everyone.

---

### Post by ranch hand on 2010-08-29
> **ktp said:**
> vm is good for most things but still not well for gaming.  

But I guess there is point in time when you just give up games and learn windows is not worth it. =)  But just saying not a perfect solution for everyone.
I keep hearing about gaming and it really grinds me.  If gamers, I admit that I am not and may feel differently if I were, would just not use games not ported to Linux, AND let the companies know it, I believe this would change in a hurry.  There seems to be a large number of gamers using linux for just about everything else.  An eroding customer base gets attention.

My son is a gamer.  Has not used MS in at least 5 years.  Seems pretty adept at getting them to work under wine and impress folks with how much better his performance is than on their MS rigs.

He has converted a couple to Linux that very way.

While I would rather see them ported to Linux natively, with wine I really think that the gaming excuse is getting thin.  Not gone  by any means but getting thin none the less.

---

### Post by ktp on 2010-08-29
> **ranch hand said:**
> While I would rather see them ported to Linux natively, with wine I really think that the gaming excuse is getting thin.  Not gone  by any means but getting thin none the less.

Yes native linux support would be nice..but the challenges are the video drivers and api. 

But wine is good alternative.  I have seen it work with most popular games and some just refuse to, which I would say goodbye too.

This is off topic now so I will stop here =)

---

### Post by kansasnoob on 2010-08-29
This is not a new problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

You'll see at the bottom of the page it says:

> This page was last modified on 17 February 2010

Personally, if I run into a system that just doesn't want to work with grub2, I switch back to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I do however need to rewrite some of that for those with a separate /boot partition. If only I had some time :(

---

### Post by ktp on 2010-08-29
> **kansasnoob said:**
> This is not a new problem [...]

We know this is not a new problem.  The bug report has be open since "Ubuntu 9.10 beta".  Yes there are workarounds, but it would be nice to have good solution to windows apps killing grub 2.

---

### Post by kansasnoob on 2010-08-30
> **ktp said:**
> We know this is not a new problem.  The bug report has be open since "Ubuntu 9.10 beta".  Yes there are workarounds, but it would be nice to have good solution to windows apps killing grub 2.

I've worked with Colin Watson a few times trying to resolve bugs and I can assure you that if it were easy to fix he'd have fixed it already :)

Some bugs are just hell to fix. But with btrfs coming a change to grub was needed. ATM we're still in transition and there will be times a person will have to "work-around" issues.

---

### Post by wilee-nilee on 2010-08-30
The bug just needs a evil laugh and sinister organ music to make it whole, as it executes.

---

