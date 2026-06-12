---
title: "Installing NVIDIA 190.53 uninstalls MythTV"
date: 2010-01-31
forum: Mythbuntu
---

### Post by jquintana on 2010-01-31
I have a fresh install of Mythbuntu 9.10 and I installed the 190.53 drivers for my GeForce 9400GT. After rebooting I no longer have MythTV installed. 

Also, I tried to uninstall the 190.53 drivers using nvidia-uninstall and then I got low-resolutions mode only.

I got frustrated and walked away and will deal with it at a later time.

Has anyone had this happen before? If so, how do I get my MythTV and 190.53 drivers to work?

Thanks!

---

### Post by superm1 on 2010-01-31
> **jquintana said:**
> I have a fresh install of Mythbuntu 9.10 and I installed the 190.53 drivers for my GeForce 9400GT. After rebooting I no longer have MythTV installed. 

Also, I tried to uninstall the 190.53 drivers using nvidia-uninstall and then I got low-resolutions mode only.

I got frustrated and walked away and will deal with it at a later time.

Has anyone had this happen before? If so, how do I get my MythTV and 190.53 drivers to work?

Thanks!
Enable auto-builds from mythbuntu.org/auto-builds and install the NVIDIA driver available from that repo once you are updated.  nvidia-glx-190 will be available.

---

### Post by jquintana on 2010-02-01
> **superm1 said:**
> Enable auto-builds from mythbuntu.org/auto-builds and install the NVIDIA driver available from that repo once you are updated.  nvidia-glx-190 will be available.I am trying to follow your suggestion, but when I try to install 190 or 195 I get an error that says installArchives() failed.

:confused:

---

### Post by superm1 on 2010-02-01
> **jquintana said:**
> I am trying to follow your suggestion, but when I try to install 190 or 195 I get an error that says installArchives() failed.

:confused:

How are you installing it?  You should just need to do:
```
apt-get install nvidia-glx-190
```
once you have the auto-builds repo on and updated.

---

### Post by jquintana on 2010-02-01
> **superm1 said:**
> How are you installing it?  You should just need to do:
```
apt-get install nvidia-glx-190
```once you have the auto-builds repo on and updated.I was using the Hardware Drivers to install the drivers. However, that didnt work and I managed to install the 190 and then the 195 drivers by downloading the .run package from the nvidia website.

Thanks!

---

### Post by yomnym on 2010-03-10
i downloaded the latest driver from Nvidia but i cant seem to install the package i got from them, when i double click the file i just get an error.

---

### Post by tobiz on 2010-03-15
> **yomnym said:**
> i downloaded the latest driver from Nvidia but i cant seem to install the package i got from them, when i double click the file i just get an error.
It's some time since I installed the Nvidia driver package but as I recall you have to: a) drop into single user mode and run as root; b) set the package as 'executable'; c) run the package.  Of course it may have changed since over a year ago.

---

