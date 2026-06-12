---
title: "Mythbuntu 14.04/0.28 Upgrade"
date: 2017-12-14
forum: Multimedia Software
---

### Post by jamoody on 2017-12-14
I'm currently running Mythbuntu 14.04 with Mythtv 0.28.  I'd like to update my hardware to z270 chipset with Kaby Lake processor.  My investigation suggests that this hardware will require kernel 4.10 and I figure I might as well go to the latest stable which I believe is 4.14.  If I update Ubuntu first to 16.04 LTS which appears to use kernel 4.4 can I then safely upgrade the kernel to 4.14?  ie, can I have a more updated kernel version than the Ubuntu version is built with?  Alternately, if I upgrade to Ubuntu 17.10 which has kernel 4.13 are there any issues to update to 18.04 LTS when it becomes available?  Are there any MythTV concerns in any of these upgrades?  Thanks.

---

### Post by deadflowr on 2017-12-15
Ubuntu 16.04 will use the 18.04 kernel next summer for the last point release aka 16.04.5, 
Currently 16.04 is at the 3rd point release so it now uses the 4.10 kernel.
That will change next month when the 4th point release comes out.

It can be confusing, but to break it down:
There are two supported kernel stacks users can run on LTS versions of Ubuntu
The original kernel stack
And the hardware enablement kernel stack.

The original kernel stack is installable automatically if you install with Ubuntu installation media 16.04( the original iso release in April 2016) and Ubuntu 16.04.1 (the iso released for the first point release)
All other versions of Ubuntu installation media come with the hardware enablement stack installed and installable.

With regards to the hardware enablement stack, older versions only installed a specific version and forced users to manually switch the stack themselves, but with 16.04 that changed and now the stack automatically 
upgrades without any user interaction, so you can actually install any point release version after 16.04.1 and the kernel stack will update to whatever the latest would be.

Quick reference points:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack")

All that said, I think just install/upgrade to 16.04 and utilize the hwe packages.
The thing about installing kernels which are not officially stable kernels, by Ubuntu's concern; of which 4.14 is not stable (or at least something that is not not available in the stable support channels for Ubuntu packages), is the onus would be on the user the maintain a certain level of vigilance and do the proper updating when known bugs (manly security) come out.
And 4.14 might not even be the endgame kernel that will be the kernel used for 18.04 anyway. So if you did install it, you might never see the benefits of Ubuntu security support for it, which only supported stable kernels get.


tl;dr
Just install/upgrade to 16.04 and use the hwe stack packages referenced in the wiki page:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

It feels like a lot of blah, but hope it helps.

---

### Post by jamoody on 2017-12-15
This helps a great deal, thanks.

---

