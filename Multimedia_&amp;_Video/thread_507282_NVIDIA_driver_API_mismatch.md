---
title: "NVIDIA driver: API mismatch"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by Nuld on 2007-07-22
Hey all. I am trying to get the NVIDIA driver to work on my new system. I have a Gigabyte GeForce 8800GTS. I already followed some guides from this forum, but I wasn't lucky yet. So far, I installed Ubuntu 7.04 and upgraded everything to the latest version. Then I installed libc6-dev, because the NVIDIA installer needs to build a kernel module during the installation process. Then I installed the latest NVIDIA driver (100.14.11). Now I get the following error when I restart the xserver:

Error: API mismatch: this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA driver components have the same version.

I tried adding "nv" to the DISABLED_MODULES list in /etc/default/linux-restricted-modules-common as suggested somewhere here on the forums, but that didn't help either.

Thanks for any help!

---

### Post by mbrady on 2007-07-24
I'm in the exact same boat as you... awaiting a solution, as searching turns up no other fixes (yet)

---

### Post by Cappy on 2007-07-24
Here is the home page so you can read it first : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

You are probably mainly missing the first two lines of the code below:

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb
sudo dpkg -i envy*.deb
sudo envy -t
```

As the nvidia script runs, allow it to configure X (xorg.conf).

Once you are in X you can configure (dual monitors, resolution, etc) with ```
gksudo nvidia-settings
```

---

### Post by Nuld on 2007-07-24
Awesome, that worked! Thanks a lot Cappy.

---

### Post by mbrady on 2007-07-24
I got mine working by adding nv, nvidia, nvidia_legacy, and nvidia_new to the disabled modules.

---

### Post by fyo on 2007-08-08
> **mbrady said:**
> I got mine working by adding nv, nvidia, nvidia_legacy, and nvidia_new to the disabled modules.

Adding "nv" covers all the other modules, you list, so that should be enough.

Like the original poster, I had already tried this, to no effect.

Cappy's solution did work, but not for the stated reason. (all previous drivers were already removed and the listed packages already installed).

What worked was using "Envy" instead of letting NVIDIA's driver do the trick. I would have liked a slimmed-down version of Envy, text-based, which didn't require 900 packages to be installed, including a handful of non-standard Ubuntu packages (and an old version of GCC).  (Why does Envy need the Xinerama-dev package, for example? Or all the qt stuff...)

The process was messy and Envy failed to install the first two times. The first because some 10 dependencies were not fulfilled (mine is a relatively clean install of Feisty). The second time because Envy doesn't retry downloading packages if the connection is reset for whatever reason (which happened during a good handful of the 50+ packages Envy downloads automatically). Simply rerunning Envy until all packages are successfully downloaded solves the problem (Envy fortunately checks for local copies before attempting to download).

Anyway, it's hard to complain with success and Envy worked where NVIDIA's installer failed.

---

### Post by tseliot on 2007-08-09
> **fyo said:**
> I would have liked a slimmed-down version of Envy, text-based, which didn't require 900 packages to be installed, including a handful of non-standard Ubuntu packages (and an old version of GCC).  (Why does Envy need the Xinerama-dev package, for example? Or all the qt stuff...)
It doesn't depend one the fact that it has a GUI (its textual interface does the same). The dependencies are required by the packaging scripts which Envy uses.

> **fyo said:**
> The process was messy and Envy failed to install the first two times. The first because some 10 dependencies were not fulfilled (mine is a relatively clean install of Feisty). The second time because Envy doesn't retry downloading packages if the connection is reset for whatever reason (which happened during a good handful of the 50+ packages Envy downloads automatically). Simply rerunning Envy until all packages are successfully downloaded solves the problem (Envy fortunately checks for local copies before attempting to download).
the latest release of Envy aborts the operation if the dependencies are not (and can't be) satisfied

---

### Post by fyo on 2007-08-09
I'd like to start off by repeating: It's hard to argue with success. Envy worked where NVIDIA's installer failed.

I'm very happy to finally have the driver installed (although that didn't really solve my problem with my 8500GT's DVI output and my Samsung 225BW monitor - but at least one more diagnosis was ruled out).

> **tseliot said:**
> It doesn't depend one the fact that it has a GUI (its textual interface does the same). The dependencies are required by the packaging scripts which Envy uses.


As a user, the difference is moot. 

> the latest release of Envy aborts the operation if the dependencies are not (and can't be) satisfied

What happened in my case was that Envy failed to install, spitting out a handful of unfullfilled dependencies, and was left as a "broken" package when I started up Synaptic to manually fulfill them (and it had to be removed, before the dependent packages could be installed). After doing that, the installer would run and proceeded to download a TON of packages. During a handful of these a "connection reset by peer" error occurred (no idea why). This caused Envy to abort once it had completed (one attempt of) each package. Rerunning Envy solved the problem, as mentioned earlier.

---

### Post by Riddic on 2007-08-12
Same error here, I had to haggle with modules a bit longer before X started up properly again.
Envy/nvidia installer package would drop the freshly compiled (*nvidia.ko*) module in 
*/lib/modules/$(uname -r)/nvidia/*
whereas modprobe by default loads the module from
*/lib/modules/$(uname -r)/kernel/drivers/video/*.
Anyhow, all is good now, 3d support is restored.

---

