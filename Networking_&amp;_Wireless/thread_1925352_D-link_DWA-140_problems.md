---
title: "D-link DWA-140 problems"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by fredcarru on 2012-02-14
I'm using Ubuntu 11.10 with a D-link DWA-140 usb wireless adapter.
When booting from the CD the adapter doesn't function. After installation it worked fine and I installed several packages,  for video and photo editing/viewing.

Now it won't connect. I've tried adding rt2870sta in /etc/modules but no luck

---

### Post by praseodym on 2012-02-14
If you compiled the driver with an old kernel and a kernel upgrade occured you need to compile/install again.

---

### Post by fredcarru on 2012-02-15
Pressing and holding the D-Link button solved this.

I've no idea why it got that way but I have noticed that Windows sometimes takes a little while to connect, perhaps this is the driver "pressing the button".

Ta for your input praseodym

That only worked once it's back to trying 3 or 4 times then giving up.

---

### Post by praseodym on 2012-02-15
Try to reset the BIOS

---

### Post by fredcarru on 2012-02-18
Resetting the bios is dramatic removing lots of useful features.
fortunately there's a bios button, rather than a jumper, to do this which lets you inspect the result before implementing, I exited without saving.

  I decided to rearrange the partitions on sdb to get the linux partition before the swap, previously I'd defined the swap first.

  After re-installing Ubuntu everything works fine. I don't have a wired internet connection so the only divers for the D-link DWA-140 must have come from the installation CD.

  It would seem very easy to corrupt these and difficult to recover them from the CD without doing a full installation.

Today 18th feb it doesn't work back to 3 or 4 tries then offline

---

