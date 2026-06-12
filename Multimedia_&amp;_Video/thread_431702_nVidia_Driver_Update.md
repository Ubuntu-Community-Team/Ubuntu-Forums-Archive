---
title: "nVidia Driver Update?"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-05-03
I have nVidia drivers loaded on my Ubuntu 7.04 install and they work fine however the driver version # is complteley different from what is available on [nVidia's site](http://www.nvidia.com/object/unix.html). I assume because this is a Ubuntu version of their drivers and not their vendor free script they provide from nvidia's site.

How do I know when there is a new version available and what would be the best way to upgrade my version?

---

### Post by 5-HT on 2007-05-03
Due to Ubuntu's release policy, further nvidia driver releases will (most likely) not be available from the official repositories. Currently, the nvidia-glx-new package provides the most recent 1.0-9755driver. In terms of upgrading the driver to a later version, you'll need to grab it from nvidia's site and install it yourself. There are many walkthroughs around the forums giving step by step instructions on how to install the drivers from nvidia's site.

---

### Post by jagolis on 2007-05-03
Remember to remove /lib/linux-restricted-modules/.nvidia_new_installed manually after removing nvidia-glx-new.

---

