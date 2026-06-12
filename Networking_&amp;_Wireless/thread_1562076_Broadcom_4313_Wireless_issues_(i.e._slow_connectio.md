---
title: "Broadcom 4313 Wireless issues (i.e. slow connections)"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by promet on 2010-08-27
I've recently been having some very sluggish wireless performance on the Broadcom 4313 [14E4:4727], running on the Broadcom STA Driver (bcmwl-kernel-source from the repos, as activated via "Administration" -> "Hardware Drivers").

This is all running on a Lenovo G555, Ubuntu 10.04 64bit.

The most recent performance issues had vaguely coincided, I thought, with the automated system updates, specifically, the kernel updates. So, I tried to boot into a previous kernel to see if that helped (Previous kernel=2.6.32-22-generic), which it didn't, but while in this kernel I tried the following command, which I'd heard might help from the Broadcom Linux Support Doc, under the "Ubuntu" section, at the bottom of this page:

[http://www.broadcom.com/docs/linux_sta/README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt")

The command I'm referring to is this:

NOTE:  Before executing the below command, I deactivated the current version of the driver in the "Hardware Driver" tool mentioned above and, since this left me without wireless, I completed this command with via a wired ethernet connection...

```
sudo apt-get --reinstall install bcmwl-kernel-source
```

I noticed, while the driver was being built that it was referring to the previous kernel version (as mentioned above) explicitly during the build. So, I rebooted back into my current kernel (2.6.32-23-generic) and reinstalled the bcmwl-kernel-cource for that specific kernel, hoping the "kernel specific" driver compile would improve performance and, for me at least, in this case, it seems like it has, a lot...

NOTE: This command (sudo apt-get --reinstall install bcmwl-kernel-source) will auto-compile the driver, and so, you will need to have the current kernel's linux-headers as well as the "build-essentials" package from the repos to be able to allow a successful compilation.

I'm no guru or anything, but I can say, all of the Broadcom Wireless issues that I have been having appear to have been resolved by this. I will be reinstalling the bcmwl-kernel-source on each new kernel update from here on out.

There seem to be some occasional system instabilities that crop up with each kernel release (I am currently suspicious of some pulseaudio kernel update issues, but I digress).

If this is indeed an actual "solution" (and I'm not sure that it is, only know my "local" results), I would love to see the developers incorporate this kind of kernel update instability issue into their planning. Perhaps something as simple as a bulletin saying "REMINDER: be sure to update your kernel drivers along with this new kernel release". As I say, I'm no guru, and could obviously use a reminder like that, and I bet some other people who don't meditate like gurus on the implications of automated kernel updates could too. 

I'm not complaining mind you, I loves me some Ubuntu. I guess what I should really do is throw that on the "Brainstorm" site. At any rate, I hope this may be of use to someone.

Cheers! :popcorn:

---

### Post by CBMCO on 2010-10-20
I was having the same issue with Ubuntu 10.10 on my Dell Mini 10v. My wireless speeds are now literally 10 times faster than what they were before you showed me how to fix it. I can't thank you enough!!!

---

### Post by luddek on 2010-12-22
This works great on my macbook pro, now I have proper wireless speed again. Thank you.
EDIT: Thought it worked but the problem came back. Reloading the drivers seems to solve the problem temporarily.
EDIT2: The problem is with the powermanagment, fix is here [https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Proprietary](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Proprietary)

---

### Post by richnfamous on 2011-03-16
i'm running Mint on an Acer Extensa 5210 with a Broadcom 4313 card

i've been having wireless issues as described and this has fixed them - thanks

---

### Post by nyex on 2011-05-11
<3 you.

I was having this problem since upgrading to 11.04 (I have a Dell Inspiron n4020). Following these steps fixed it. I guess I'll have to bookmark this page for whenever there is a kernel update. As long as it works, I'll be happy :)

---

