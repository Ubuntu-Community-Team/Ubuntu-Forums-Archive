---
title: "nvidia and kernel woes"
date: 2009-01-09
forum: Multimedia Software
---

### Post by waveman on 2009-01-09
I am running Ubuntu 8.10 on my desktop. This is an upgrade from 8.04 that I did about a month ago.

My system includes an nVidia 9800GT video card, Intel Dual-Core CPU, and 4 GB of RAM. I also have two monitors connected to my video card.

I made the mistake of accepting an upgrade yesterday of my video card driver when I was prompted for software updates. The last time I did this, it was a disaster, same this time. You'd think I'd have learned.

Now, if I can get to a desktop at all, it is without the benefit of hardware acceleration and with only one monitor.

After a considerable amount of investigation, I think I have the problem narrowed down. Because of the upgrade (I think), I am running kernel 2.6.24-22. However, the kernel headers on my machine are for 2.6.27. nVidia requires the kernel headers to install the hardware accelerated drivers.

This is easy you are thinking: all I need to do is upgrade my kernel or download the 2.6.24-22-generic headers, right? Well, synaptic doesn't see the 2.6.24-22 headers, and I can't figure out how to upgrade my kernel to 2.6.27, so my kernel matches the kernel headers.

My questions: 
1) How can I get my kernel to match my kernel headers? My preference would be to use 2.6.24, but at this point either would be fine.

2) If I did a fresh install as opposed to an upgrade, would it blow away all of my user files? I would just as soon go back to Windows if that is the case...

Any help here would be most appreciated.

Thanks in advance...

---

### Post by tuxxy on 2009-01-09
1) If your system was fully updated you would be running the 2.6.27-9 kernel, have you fully updated your system? or are you keeping it on 2.6.24 for a reason?

2) If you fresh install you wont lose any of your files/settings aslong as you create a seperate /home partition first and then at the fresh installation install the file system only using / mountpoint.

---

### Post by waveman on 2009-01-09
Thank you for the reply.

I am using 2.6.24-22 because that is the default boot option. The other kernel option is 2.6.24-19.
When I upgraded to 8.10, everything appeared to go fine. I am not sure why the upgrade chose to keep the older kernel.

If there is a way to upgrade this to 2.6.27, I would gladly do it, I haven't been able to figure out how.

Unfortunately, /home file system is not a separate partition. Sounds like I would lose everything if I tried a fresh install, is this correct?

---

