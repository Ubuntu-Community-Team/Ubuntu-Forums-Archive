---
title: "Error installing aodv 0.9.5 with deb package"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by autodimay on 2009-02-12
Hi all,

I am newbie of aodv user and I am trying to compile aodv-0.9.5 in Ubuntu 8.04 server Hardy (kernel 2.6.24-17-generic) with deb package which I download from [http://debian.azertyfab.net](http://debian.azertyfab.net). I use "dpkg -i" command and it was fine. But the aodvd.rtlog file says:

- A kernel module could not be loaded, check your installation... 0
- ERROR: Module kaodv does not exist in /proc/modules
- FATAL: Module kaodv not found

And the aodvd.log file says:

- 04:00:27.488 host_init: Attaching to ath0, override with -i <if1,if2,...>.
- 04:00:27.632 cleanup: CLEANING UP!

Then when I use "modprobe kaodv" command, it says:

- FATAL: Module kaodv not found.

So, where can I find the module kaodv. Or do I need something else to do the installation right?

Thanks in advance and best regards.

---

