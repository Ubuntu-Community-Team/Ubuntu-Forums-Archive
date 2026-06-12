---
title: "Oneiric hangs several minutes after booting"
date: 2011-10-16
forum: Multimedia Software
---

### Post by EngineerScotty on 2011-10-16
Just upgraded a desktop PC (HP HPE510t, i52300 CPU, Radeon HD6450 graphics) from Natty to Oreinic, and now the computer generally hangs a few minutes after logging in.  Appears to be graphics-related, as kern.log is full of "Failed to schedule IB" driver messages.  System worked fine under Natty.

Currently, it's using the free ati drivers and not the proprietary drivers.  I tried switching to the proprietary driver, but that doesn't seem to help.  Installing the "post release updates" from jockey doesn't work.  Tried installing Catalyst 11.9 drivers directly from ATI, based on the advice somewhere that Ubuntu-supplied drivers were out of date, but that produced a nonfunctional system; have had to re-install twice after managing to make gfx nonfunctional from trying to solve this.

Oh, one more surprise.  When I do a reinstall ("upgrading from 11.10 to 11.10" according to the livecd) it corrupts grub2, and I have to manually reinstall grub2 by booting of the livecd to get the system to boot.  (This wasn't hard to do, but annoying and certainly not something a newbie could manage).

On the plus side, oreinic finally loads the right network driver (realtek 8168, not 8169); Natty could never figure that out, and every time update manager pulled across a kernel upgrade, I'd have to manually update the ramfs to have a functional network on next boot.

Currently, the box is booted to Windows.  :(

---

### Post by jlindbergh on 2011-10-19
Dito here :(
At first I went with the included drivers, but they also froze the system after a short while. I then installed the fglrx proprietary ("update" version) drivers, but when I run fglrxinfo on tty1 I get Error: couldn't open display (null). I then try it when logged into Unity and get instant freeze.

Also I too experienced the corrupt grub2-bug after reinstalling.

Reverting to the LTS release now..

---

