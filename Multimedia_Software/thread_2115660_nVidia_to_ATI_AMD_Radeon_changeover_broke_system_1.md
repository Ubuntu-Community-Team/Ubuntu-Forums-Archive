---
title: "nVidia to ATI AMD Radeon changeover broke system 11.10"
date: 2013-02-13
forum: Multimedia Software
---

### Post by Handssolow on 2013-02-13
Today I replaced my son's Geforce 6600GT with an AMD Radeon HD 7750 graphics card, hoping for a modest increase in performance within the limits of the motherboard etc. The CPU is a dual core Athlon 64x2  4200+.

Silly me, I expected things to be automatic but they weren't, so from a command line I eventually removed the xorg.conf file making first a copy of the old file. A reboot and I had a GUI again.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_oldnVidia
Sudo rm /etc/X11/xorg.conf

With wifi now, I looked for a new graphics driver but there was an error message. I overlooked that for the moment as Update Manager had kicked in and I accepted the several updates available. A reboot brought a blank screen.

Currently I seem unable to obtain a usable login, only the read only recovery root login. I can successfully run a live CD so the file information isn't lost.
xorg.conf has limited information but gives the module as glx.

Can I rescue the current system?

If I can't, I favour a fresh install on a new HD of 11.10. If so would just copying home be enough?

---

### Post by QIII on 2013-02-13
If you had the NVIDIA proprietary driver installed, did you uninstall it before switching the cards?

Yes, you can most likely recover.

---

### Post by Handssolow on 2013-02-13
I did deactivate the nVidia driver first, in "Additional Drivers".

---

### Post by papibe on 2013-02-13
Hi Handssolow.

I would start booting into the BIOS to make sure the new graphic card is being both detected, and selected over integrated graphics from the motherboard or CPU.

If you haven't had the chance to to get to the desktop and install the the AMD proprietary driver, you're probably using the open source driver. Since your card appears to be fairly new, there's a possibility that it doesn't support it completely.

When you boot into a black screen, you can go to a text-mode console by pressing Ctrl+Alt+F1. There, you can install the AMD proprietary following the steps described [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installing_via_the_command_line").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Handssolow on 2013-02-13
I'm left with Ctrl+Alt+F1 dumping me back to grub and the choices of booting normally, recovery mode, past versions or memory test.

Recovery mode choices are normal boot or read only root.

As I mentioned earlier, after removing the old /etc/X11/xorg.cong file I did get a  GUI, so something was right, even if I wasn't yet using the recommended driver. After a reboot following Update Manager I was left with with no GUI and lack of access to a text console, that's causing the current problem. All I have is root read only input. System shafted?

---

### Post by Handssolow on 2013-02-13
It's still work in progress but recovery root read only can be changed. I copied /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf then eventually got input with tty1.
mount -o remount,rw /

I've not sorted out a GUI but it's progress of a sort.

Edit 15 Feb 2013

Some time was lost before I discovered that the motherboard's enabled network port didn't work and needed to fit a network card.
Perhaps a fresh install would have got the AMD Radeon HD 7750 working, instead after deleting /etc/X11/xorg.org I put the nVidia Geforce 6600GT graphics card back and got a GUI back.

---

