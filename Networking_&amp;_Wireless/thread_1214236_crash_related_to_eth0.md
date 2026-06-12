---
title: "crash related to eth0"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by duffrecords on 2009-07-15
After upgrading to Jaunty Jackalope, I've noticed a serious stability issue.  When eth0 handles a large amount of data (downloading a torrent, streaming video, etc.) the system crashes and takes down my entire home network with it.  I imagine it must be flooding the router, because it won't respond until the computer is rebooted or powered off.  This also happens sometimes, even when there is little to no network activity.  I usually find it crashed in the morning.

I've attached a section of /var/log/messages which shows the errors that happen each time.  There are some similar threads that recommend turning off ACPI in the BIOS (I can't because it's grayed out) or adding acpi=off or pci=noacpi to the kernel boot parameters (my computer won't boot all the way if those are present).  This is the 64-bit version of 2.6.28-rt.  I have a 64-bit Jaunty at work and another 32-bit Jaunty at home, but neither of those machines have this problem, so I'm wondering if RT preemption has something to do with it.  Any suggestions?

---

### Post by duffrecords on 2009-07-19
Now I'm starting to see segmentation faults in the message log:```
kernel: [ 4332.511132] mythfilldatabas[8175]: segfault at 184ad30 ip 000000000184ad30 sp 00007f53ed905d78 error 15
kernel: [21730.183317] mythbackend[29896]: segfault at 0 ip 00007fc88930bf44 sp 00007fc8667ebfd8 error 4 in libqt-mt.so.3.3.8[7fc888d18000+80d000]
```I don't know if this is a comorbid condition or something separate, because segfaults are related to memory access but these crashes are related to high network activity.  I've thought about limiting the bandwidth of eth0 with wondershaper, but I'm not at home to reboot it if it crashes.

---

### Post by duffrecords on 2009-07-24
It's the real-time kernel.  I switched over to the generic kernel and tested it heavily for several hours, streaming HD video to another computer while downloading several Linux ISOs--not even a hint of an error, let alone a crash, the whole time.

Why can't we get the RT kernel working without serious regressions?

---

