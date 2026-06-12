---
title: "nVidia driver screwed after system updates, not cool!"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by mayamaniac on 2007-06-01
Ran system updates and rebooted to find out the nvidia driver got screwed. Spent the next hour figuring out how to fix it. Finally got it running again after restoring default xorg.conf and reinstalling the nvidia driver with Envy.

Why is system updates breaking the nvidia driver? Is there a way to prevent this in the future?

---

### Post by EndPerform on 2007-06-01
Most likely the last system update you did installed a new kernel, which would cause this.  When the nvidia driver is installed via Envy or manually, it will build a kernel module specifically for the kernel running on your machine at the time. .

The only way to prevent it is to use the drivers in the repository, I believe, otherwise when a kernel update is released, you'll have to go through the same steps again.  Thankfully kernel updates are few and far between, so it doesn't happen on every update.

---

### Post by mayamaniac on 2007-06-01
Thanks for the explaination.

So what I'll have to remember to do is after a system update, I'll need to uninstall and reinstall the nVidia driver through envy. Also, the for nVidia drivers in the repository, is that the same or as good as the ones installed by Envy? Meaning, does it allow full 2D/3D acceleration or is it just a standard VGA driver?

---

