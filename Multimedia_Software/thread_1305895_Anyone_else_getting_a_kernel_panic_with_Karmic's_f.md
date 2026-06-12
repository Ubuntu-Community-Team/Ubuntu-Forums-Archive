---
title: "Anyone else getting a kernel panic with Karmic's fglrx?"
date: 2009-10-30
forum: Multimedia Software
---

### Post by humphreybc on 2009-10-30
Specifically, [this bug]("https://bugs.launchpad.net/bugs/464525")?

Does anyone know what version of Catalyst drivers are in the Ubuntu repos?

Also, can anyone explain why dpkg-reconfigure -phigh xserver-xorg isn't working?

Thanks!

---

### Post by zajc on 2009-10-30
I'm ](*,) with the same problem. Toshiba Satellite A300.

The only solution which I found is to delete newly created xorg.conf file and uninstall restricted driver (this is not necessary) :(

---

### Post by humphreybc on 2009-10-30
> **zajc said:**
> I'm ](*,) with the same problem. Toshiba Satellite A300.

The only solution which I found is to delete newly created xorg.conf file and uninstall restricted driver (this is not necessary) :(

What graphics card have you got?

---

### Post by zajc on 2009-10-30
> **humphreybc said:**
> What graphics card have you got?

ATI Mobility Radeon HD 3400 Series

---

### Post by humphreybc on 2009-10-30
Well, that's good, at least it's not just confined to my card. Hopefully they can act on the bug report.

Have you tried downloading it directly from ATI/AMD and installing that way? I would myself, but our internet is too slow and unreliable to get the 80mb file.

---

### Post by humphreybc on 2009-11-02
I can confirm this still happens with the .run file downloaded from ATI AMD themselves. Far out.

---

### Post by Rafaelcrocha on 2009-11-03
Hi, I am using karmic since alpha and I am battling against this bug... I think the correct bug is this:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/285701](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/285701)

I marked the other as a duplicate.
We actually don't get a kernel panic, instead a blank screen...

I also work in a toshiba a300 with hd 3400 series card..

I don't see much progress on this issue.

What I did as a workaorund was to activate experimental opensource drive radeon acceleration . With this I can enable some desktop effects and use some software, but I am not getting the same performance as with fglrx.

Rafael

---

### Post by Rafaelcrocha on 2009-11-03
Rereading I am not sure if it is the same issue. i don't get a kernel panic, instead I get a blank screen whren X tries to load... Sorry

---

### Post by humphreybc on 2009-11-03
> **Rafaelcrocha said:**
> Rereading I am not sure if it is the same issue. i don't get a kernel panic, instead I get a blank screen whren X tries to load... Sorry

Well obviously I get a blank screen as well when X tries to load, only difference is that my caps lock light is flashing. Are you sure yours isn't?

Where can I find this experimental driver?

---

### Post by adam111316 on 2009-11-06
Hey guys also getting the kernel panic here with Toshiba A300 using [COLOR=#000000]ATI Mobility Radeon HD 3650. Haven't tried the drivers off the ati site yet. Also on the karmic alphas/betas i was just getting a black screen. Please let me know if you guys get any updates on this.
[/COLOR]

---

### Post by humphreybc on 2009-11-06
> **adam111316 said:**
> Hey guys also getting the kernel panic here with Toshiba A300 using [COLOR=#000000]ATI Mobility Radeon HD 3650. Haven't tried the drivers off the ati site yet. Also on the karmic alphas/betas i was just getting a black screen. Please let me know if you guys get any updates on this.
[/COLOR]

Hi, if you could visit [this bug]("https://bugs.launchpad.net/bugs/464525") and add a comment with some details of your computer, what you're experiencing and also how to reproduce the bug, that'd be excellent.

Don't bother trying the drivers off the ATI/AMD site, it won't make any difference if you're getting a kernel panic with the Hardware Drivers.

Thanks

---

### Post by zajc on 2010-01-23
The solution :D

sudo apt-get instal xorg-driver-fglrx
sudo aticonfig --initial -f
sudo aticonfig --acpi-services=off

---

### Post by Bat on 2010-02-21
Yes, thanks for your "solution", zajc.  I eventually got my laptop to boot again after I tried it.  Please, in future, don't post untested and undocumented "solutions".  People here are having real difficulties.  They don't need useless "solutions".

---

### Post by scoalegil on 2010-03-08
I am also having this problem with an ATI Mobility Radeon HD3650 on a Toshiba A300 laptop.  With fglrx enabled it seldom boots.  Yes, that means is occasionally does boot.  I.e. several cold reboots will eventually work ... sometimes it is 2 or 3, others it is 5 or 6.

---

### Post by zajc on 2010-05-02
> **Bat said:**
> Yes, thanks for your "solution", zajc.  I eventually got my laptop to boot again after I tried it.  Please, in future, don't post untested and undocumented "solutions".  People here are having real difficulties.  They don't need useless "solutions".

Bat, it is not useless solution :confused: It fixes issue on my laptop Satellite A300-1EG. I would never post untested solution(s).

Let me explain my "solution". I found the solution on [http://tiagoboldt.net/blog/install-fglrx-in-karmic/](http://tiagoboldt.net/blog/install-fglrx-in-karmic/) the only difference is that I use driver from Ubuntu repository instead downloading it from ATI's site.

---

