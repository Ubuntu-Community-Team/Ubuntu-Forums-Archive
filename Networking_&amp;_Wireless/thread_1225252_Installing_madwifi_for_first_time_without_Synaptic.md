---
title: "Installing madwifi for first time without Synaptic package manager"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by brback on 2009-07-28
Hi, i got a DWA-547 wireless card that i want to use trough Madwifi, or somehow else. The problem is that most install guides for madwifi requires that you have an internet connection, which I don't have because my wireless card isn't working in ubuntu. I have dual boot with windows on my pc, and is using windows to write this. Just to make it clear, i don't have access to a wired connection and i am just starting to learning how to use ubuntu. Is there any way to download the files needed in windows, then install it afterwards in Ubuntu ?

---

### Post by t0mppa on 2009-07-28
Sure there is. Grab a snapshot from [here]("http://snapshots.madwifi-project.org/"). A lot of people use the hal-10.5.6-current, but since the free branch (without the proprietary HAL modules, so it's purely open source) was merged to trunk on spring, I guess that'd be a good choice too.

Ubuntu can read Fat32 and NTFS partitions, so you can just save it on your Windows partition and then mount it when you swap to Ubuntu and copy it over from there. You're going to have to rebuild the modules after every update on your kernel, so either keep the files in saved up or then bookmark the download URL, so you can always grab a fresh build - new ones show up about once a week.

After you've the file copied on your linux file system just extract the contents somewhere and follow the build instructions in README and/or INSTALL files. And if you run into trouble, just post back for more help.

---

