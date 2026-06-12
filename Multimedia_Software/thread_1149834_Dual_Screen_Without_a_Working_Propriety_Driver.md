---
title: "Dual Screen Without a Working Propriety Driver"
date: 2009-05-05
forum: Multimedia Software
---

### Post by addtoqueue on 2009-05-05
Hello,

I have a dual screen problem with my laptop.  It's an Acer Aspire 5100 with ATI Radeon Xpress 1100.

I would like to have my laptop screen to be my primary desktop screen and my monitor to be an extension. As it is right now, my monitor is the primary, (grub, boot splash, panel and desktop icons loads up in my monitor instead). Due the the way my desk is built, I only have room to put my monitor on the left hand side, so my display setup is:
Monitor : Laptop Screen.

I have Googled this problem but most of the solutions stated to use the ATI Catalyst to sort this. However, when I tried installing the proprietary ATI driver from the Synaptic Package Manager, xorg-driver-fglrx, it destroys my display.

With that package, after the boot splash, the screen flickers and then it goes to a black screen. The only way I was able to restore the screen was to boot into recovery mode and start up in terminal mode and place the code:

sudo apt-get remove --purge xorg-driver-fglrx

After restoring the display, I installed EnvyNG to look for a driver for my ATI card. EnvyNG only lists one ATI driver, 8.600-0ubuntu2, and it states that that driver is not compatible and not rcommended.

So, now I'm stuck.

---

### Post by addtoqueue on 2009-05-06
Okay I was able to get my laptop screen to show GRUB and the boot splash by changing BIOS settings, but I still haven't been able to make my laptop the primary screen after log in.

This is for Ubuntu 9.04.

---

### Post by Longinus00 on 2009-05-07
> **addtoqueue said:**
> Okay I was able to get my laptop screen to show GRUB and the boot splash by changing BIOS settings, but I still haven't been able to make my laptop the primary screen after log in.

This is for Ubuntu 9.04.

If you want to move the panels to the other screen, hold down the ALT key and drag them to the other screen.

---

### Post by flyboy284 on 2009-05-15
Comment Removed

---

