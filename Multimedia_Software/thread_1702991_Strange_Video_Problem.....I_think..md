---
title: "Strange Video Problem.....I think."
date: 2011-03-08
forum: Multimedia Software
---

### Post by defensorfedei on 2011-03-08
Hey Folks.  I have a Dell Dimension 2400 desktop running 10.04.  I have noticed that sometimes after 30 minutes of use to a couple of hours, my monitor goes blank and then flashes with some barcode looking lines across the screen at every flash.  The computer doesn't power off; just the monitor drops off.

I suspect that perhaps my video driver is dropping off @ some point during operation.  

Here is the output of lshw:

vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

I have checked other threads and found this fellow who has the same video hardware as I do, but his system is running a different driver.  He also seems to be suffering from a different problem than I am.

Here is the link: [http://ubuntuforums.org/showthread.php?t=1448684&highlight=i915](http://ubuntuforums.org/showthread.php?t=1448684&highlight=i915)

My motherboard has no apg slot, (since I am using an integrated graphics device),  so I am assuming that the system has loaded the wrong driver which malfunctions at what point, I do not know.  As of yet, I have been unsuccessful at forcing/replicating the error.  

Anyone have any ideas?   Thanks.

---

### Post by defensorfedei on 2011-03-08
So far there have been 44 views of this thread and no response at all? Can anyone perhaps tell me how I can configure Xorg to use the i915 driver?

Update:  I have decided to try[ this]("https://launchpad.net/%7Eglasen/+archive/intel-driver") to see if it would come to any avail.  I basically added the repository for the intel driver set furnished by Glasen.  So far it has been 2 hours and no sign of my problem.  I will post back again in a day or so to provide an update.

---

### Post by defensorfedei on 2011-03-09
I have had the machine running 6hrs with various tasks and activities going on....no repeat of the original problem yet.  The computer does fail to resume from suspend 50% of the time, and when it does successfully resume, it most often freezes up (mouse, keyboard, everything), justifying a hard reboot. Suspend was never a problem before, so I can only assume that the new driver has botched this one for me.  Hibernate works however. 

I have ordered a new graphics card for the system (supposedly well supported for ubuntu), so we shall see if this resolves all the issues for me.  I am quite surprised that intel hardware drivers and hardware don't play well together in ubuntu.  

I am also surprised that nobody else has had a similar problem with this chipset, and/or responded with a post on how to even attempt to troubleshoot the issue.

Cheers

---

### Post by no2498 on 2011-03-10
install htop
type it in a terminal it tells you how to install it
comes up in system tools on a terminal type htop click enter
look for what is using memory or cpu

---

### Post by defensorfedei on 2011-03-10
Thanks for the reply.  I did that, and nothing would turn up....it was like a phantom bug that was driving me nuts.  I just installed 10.10 about 4 hours ago, and boy is this thing running like a top! I don't know what bugs the devs have tackled to straighten this version out, but I sure do appreciate it.  Everything is running awesome now.

I reinstalled after upgrading to the latest x-org drivers, which made the system freeze constantly and caused the xserver to crash just as frequently.  I got ticked off and reinstalled.  Well worth it.

Thanks anyway.  I will mark this one as solved.

---

