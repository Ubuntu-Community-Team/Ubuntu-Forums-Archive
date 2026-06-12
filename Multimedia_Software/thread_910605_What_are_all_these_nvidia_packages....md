---
title: "What are all these nvidia packages...?"
date: 2008-09-04
forum: Multimedia Software
---

### Post by Sneachtuil on 2008-09-04
I ran an aptitude search nvidia and I realized that the following packages are all listed:

nvidia-glx-new
nvidia-glx-new-dev
nvidia-glx-new-envy
nvidia-glx-new-envy-dev

Now, I've installed my drivers with envy, and they work fine, but does this mean that the envy from the repositories (as opposed to the old envy that, before Hardy, you had to download from the author's website) does not build the drivers from source anymore, but installs the nvidia-glx-new-envy package on my system?  That's what it looks like in aptitude (that package has an "i" next to it instead of a "p").

If this is the case, do I have a reason to even have envy on my system?  Don't the packages automatically update with the rest of the system when I run aptitude safe-upgrade?  Also, doesn't this also mean that envy is now just essentially running aptitude install nvidia-glx-new-envy?

---

### Post by Sneachtuil on 2008-09-08
Anyone?

---

### Post by kpkeerthi on 2008-09-09
nvidia-glx-new is the package containing the nvidia binary driver.
nvidia-glx-new-dev is the package containing the kernel headers for the nvidia driver.

The other two packages does not exist in the repository.

As of hardy, envy is part of [official repositories]("http://packages.ubuntu.com/search?keywords=envy&searchon=names&suite=hardy&section=all"). You can install envy from the official repos/synaptic or download it off envy's website. No matter where you got envy from, it always gets you the nvidia drivers off nvidia's website.

---

