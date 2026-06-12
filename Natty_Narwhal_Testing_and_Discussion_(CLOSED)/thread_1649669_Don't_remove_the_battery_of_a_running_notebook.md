---
title: "Don't remove the battery of a running notebook"
date: 2010-12-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-12-20
Causes an oops and crashes the system (which always could cause data loss!).

There's already a patch proposed that seems to fix the problem: [https://lkml.org/lkml/2010/12/19/90](https://lkml.org/lkml/2010/12/19/90)

---

### Post by jfernyhough on 2010-12-20
Do you mean with the AC adapter still connected? Otherwise it'll just turn off; a kernel oops would be the least of your worries. ;)

Some laptops mind having their battery removed as power goes through battery no matter what, others (the better ones?) don't mind as long as they get power from somewhere, e.g. my last two Acers (5580, 5930) and Mini 311c don't (didn't) mind, my old Dell D505 definitely did!

In theory the normal behaviour should be that the battery should act as a UPS, switching from AC to battery only as needed, rather than powering from the battery and topping up from AC.

---

### Post by pressureman on 2010-12-20
I don't have any problems removing the battery mid-flight on my Thinkpad T500. I've done it numerous times, and the only ill-effect is that sometimes Gnome power manager shows two batteries when I reinsert it.

---

### Post by MacUntu on 2010-12-21
> **jfernyhough said:**
> Do you mean with the AC adapter still connected? Otherwise it'll just turn off; a kernel oops would be the least of your worries. ;)

Oh, I thought that was obvious. :P Yes, removing the battery while on AC causes a hard crash for me.

> **pressureman said:**
> I don't have any problems removing the battery mid-flight on my Thinkpad T500. I've done it numerous times, and the only ill-effect is that sometimes Gnome power manager shows two batteries when I reinsert it.

Have you tried this with the latest kernel (the -rc6 based 2.6.37-10)? I see the oops every time with my T510.

---

### Post by jfernyhough on 2010-12-21
(deletd)

---

### Post by pressureman on 2010-12-21
> **MacUntu said:**
> Have you tried this with the latest kernel (the -rc6 based 2.6.37-10)? I see the oops every time with my T510.

Yep, you're right. I tried removing the battery today with 2.6.37-10, and it oopsed. I think this has been working fine up until quite recently though, perhaps up until 2.6.37-9 (which I still have lurking on my /boot - maybe I'll give it a try).

---

### Post by MacUntu on 2010-12-22
Yeah, AFAIK this was introduced with the -rc6 kernel, so Ubuntu kernels up to -9 shouldn't oops.

---

### Post by pressureman on 2010-12-22
I also noticed a (possibly related) oops that appeared in 2.6.37-10 when loading the virtualbox kernel modules, which worked fine in 2.6.37-9

---

### Post by jfernyhough on 2010-12-22
VirtualBox with newer Ubuntu kernels is likely a separate issue, due to new configuration options Ubuntu has added:

[http://ubuntuforums.org/showthread.php?t=1648132](http://ubuntuforums.org/showthread.php?t=1648132)

---

### Post by pressureman on 2010-12-25
For the record, the kernel oops still happens with 2.6.37-11.

---

### Post by MacUntu on 2010-12-26
Well, Natty will likely use the 2.6.38 kernel - if this problem doesn't get fixed during the first RCs, I'll open a bug report on LP (I can confirm that that patch works).

---

### Post by MacUntu on 2010-12-29
This is fixed with kernel 2.6.37-rc8 ([http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=cde44d1740bcb3dcfecbf792a71826431e61686e](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=cde44d1740bcb3dcfecbf792a71826431e61686e)).

---

### Post by plun on 2010-12-29
> **MacUntu said:**
> This is fixed with kernel 2.6.37-rc8 ([http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=cde44d1740bcb3dcfecbf792a71826431e61686e](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=cde44d1740bcb3dcfecbf792a71826431e61686e)).

Or here....

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc8-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc8-natty/)

I still doesn't understand why someone must remove a battery from a running computer....:confused:

But... with my Android I must do it when I find myself within a boot-loop.....):P  but that is a flash-junkie problem....

---

### Post by MacUntu on 2010-12-29
I got two batteries and no external charger - I charge the first one, switch batteries, and charge the second one. ;)

---

### Post by plun on 2010-12-29
> **MacUntu said:**
> I got two batteries and no external charger - I charge the first one, switch batteries, and charge the second one. ;)

Aha.... then I understands it !

---

