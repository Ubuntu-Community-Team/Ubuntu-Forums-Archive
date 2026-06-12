---
title: "nvidia-glx and nvidia-glx-dev are being held back for upgrade"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by fatsheep on 2007-06-11
As the title says nvidia-glx and nvidia-glx-dev are refusing to upgrade (they are being "kept back").  I used the envy script to install my Nvidia drivers and I haven't touched these packages or configured them since so I really don't know why there is a problem.  Below is the output of my attempt to upgrade with apt-get.  (Ignore the error about ia32-libs, I have reported this bug on launchpad and hopefully the package maintainers will fix it shortly).

> **fatsheep:~$ sudo apt-get -f upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nvidia-glx nvidia-glx-dev
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 0B/17.9MB of archives.
After unpacking 5460kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 171918 files and directories currently installed.)
Preparing to replace ia32-libs 1.5ubuntu5 (using .../ia32-libs_1.5ubuntu9_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/libaudio.so.2.4', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Syke on 2007-06-12
I think it means, because of Envy, you have newer drivers than Feisty, so it's "holding back" the older drivers.

---

### Post by fatsheep on 2007-06-13
> **Syke said:**
> I think it means, because of Envy, you have newer drivers than Feisty, so it's "holding back" the older drivers.

How can I tell for sure?  And does that mean I can remove nvidia-glx and nvidia-glx-dev or is envy still using these packages?

---

### Post by dabl on 2007-06-13
> **fatsheep said:**
> does that mean I can remove nvidia-glx and nvidia-glx-dev or is envy still using these packages?

Envy doesn't use the packages.  Envy installs the proprietary Nvidia driver, and the packages also contain and install the proprietary Nvidia driver.  So it's "either-or".   You can mark the packages and remove them with Adept or apt-get remove --purge.
:)

---

### Post by fatsheep on 2007-06-14
> **dabl said:**
> Envy doesn't use the packages.  Envy installs the proprietary Nvidia driver, and the packages also contain and install the proprietary Nvidia driver.  So it's "either-or".   You can mark the packages and remove them with Adept or apt-get remove --purge.
:)

Great!  Thanks for this info.

---

### Post by fatsheep on 2007-06-14
> **dabl said:**
> Envy doesn't use the packages.  Envy installs the proprietary Nvidia driver, and the packages also contain and install the proprietary Nvidia driver.  So it's "either-or".   You can mark the packages and remove them with Adept or apt-get remove --purge.
:)

Removing nvidia-glx and nvidia-glx-dev caused my Xserver to crash due to an API mismatch between the Xserver and the Nvidia driver.  However, I used envy to "Clean the installation of any Nvidia driver", then I installed the Nvidia Driver, and restarted Xserver with envy and all is well and nvidia-glx and nvidia-glx-dev are no longer being held back by the package manager.

---

### Post by dabl on 2007-06-14
Interesting.  Since the x server crashed, it must have been using the driver from the packages (Envy must not have actually installed it like you thought, the first time).  But, "all is well that ends well"!  :)

---

