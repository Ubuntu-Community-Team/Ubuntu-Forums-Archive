---
title: "Anyone having luck with the daily iso's?"
date: 2010-07-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-07-22
For the past few days I've been unable to get daily iso's running.

After dumping to USB stick using "Startup Disk Creator" (in Lucid) I get this on boot up: ```
Unknown keyword in configuration file
```
Not sure what it means but I can't get to a grub menu or boot prompt or anything.

Also tried burning with unetbootin which gives me a kernel panic.

Tried various desktop and netbook isos over the past 4 days or so.
No cd drive to try burning to cd.

---

### Post by jppr on 2010-07-22
> **x-shaney-x said:**
> For the past few days I've been unable to get daily iso's running.

After dumping to USB stick using "Startup Disk Creator" (in Lucid) I get this on boot up: ```
Unknown keyword in configuration file
```Not sure what it means but I can't get to a grub menu or boot prompt or anything.

Also tried burning with unetbootin which gives me a kernel panic.

Tried various desktop and netbook isos over the past 4 days or so.
No cd drive to try burning to cd.

Those are Lucids ucb-creator problems... I did yesterday fresh Ubuntu 10.10 live-cd installation and usb-creator in Maverick works fine. This morning I did fresh Kubuntu 10.10 live-cd installation and... usb-creator works fine again. I have 2 HD, sda1 Ubuntu 10.10 and sdb1 is Kubuntu 10.10

---

### Post by x-shaney-x on 2010-07-22
Yes you are quite right.  Eventually dug out my desktop PC and burned the iso to a cd and it boots and runs just fine.

I had avoided using Maverick's USB creator because I thought I had read there were problems with it but the reports may have been about the Lucid version after all.

On the subject of USB creation, I have found unetbootin to be very flaky as well with less than half of iso's I have burned actually running properly.  Is that just Lucid too?

---

### Post by VMC on 2010-07-22
> **x-shaney-x said:**
> For the past few days I've been unable to get daily iso's running.

After dumping to USB stick using "Startup Disk Creator" (in Lucid) I get this on boot up: ```
Unknown keyword in configuration file
```Not sure what it means but I can't get to a grub menu or boot prompt or anything.

Also tried burning with unetbootin which gives me a kernel panic.

Tried various desktop and netbook isos over the past 4 days or so.
No cd drive to try burning to cd.

Read my [topic]("http://ubuntuforums.org/showthread.php?t=1533282") on this subject. It has to do with Syslinux being updated to 4.01 in Maverick, which uses among other things a new keyword "ui". Either use Maverick or remove the keyword "ui" from syslinx config file at the usb installed location.

---

### Post by x-shaney-x on 2010-07-22
Well I have noticed bugs and irritations mounting up in Lucid so I'm going to be giving Maverick a full run for a few days so hopefully shouldn't be an issue anymore but thanks for that heads up.

---

