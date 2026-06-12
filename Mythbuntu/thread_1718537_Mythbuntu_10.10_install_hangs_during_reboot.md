---
title: "Mythbuntu 10.10 install hangs during reboot"
date: 2011-03-31
forum: Mythbuntu
---

### Post by Panhead Bill on 2011-03-31
My desktop/myth front end hangs during the reboot after installing 10.10, The screen hangs at the MYTHbuntu splash screen.

  This pc was running 9.04 and 10.04 that I upgraded to 10.10, but I decided to do a clean install to get rid of the assorted cruft that accumulated from various installs and add-ons over time.

I also wanted to see if the fresh install would clear up my on again off again sound through my sound blaster X-Fi SB0730 card.

The MD5 sum's match and I used the slowest speed on my burner for both copies tried.

Any ideas?

---

### Post by uteck on 2011-04-04
I had this problems on my frontend using an Atom cpu.  The kernel is trying to use an invalid display resolution.
Go into your grub menu and add "nomodeset" to the options to tell the kernel to not probe for video modes, then it just uses the default mode.

But even that did not work for 10.04 and 10.10 on this particular system, and it would still freeze up, but it does work with 11.04 and have been running that for a few weeks now.

---

### Post by Panhead Bill on 2011-04-22
uteck:  Your post led me to a fix; I turned off the installation of Nvidia driver during a complete new install and the problem did not occur. I was able to install the driver after the reboot.

---

