---
title: "eth0 dropping packets in Natty"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by slimjim8094 on 2011-06-02
Hey all - This ought to be a pretty good one. To get it out of the way, I've been using Linux for a number of years and I'm now stumped.

So I have a mobo-integrated Realtek GBE card. Works just dandy on Windows, rock-solid ping, just-what-I-pay-for 30Mbps/5Mbps performance.

But with no differences in the card, machine, or cable, I drop approximately 25% of my packets, as shown in ping. This is, naturally, killing my throughput - I'm lucky to see 150kbps of those 30Mbps. 

Since I'm trying to use the Linux side of this box for my real work, this isn't really acceptable. This is consistent since I installed yesterday, and the rest of the system is working fine. It's a home-built system, but that shouldn't matter. Neither should the fact that it's the Kubuntu variant, or x64. The kernel log is unremarkable.

Any guesses? More details on request.

---

### Post by Zorael on 2011-06-02
Have you searched [Launchpad](http://launchpad.net/ubuntu) (and google) for existing bug reports? Try the network chipset model as search criteria - running '**lshw**' in the terminal should list it. You can get a more verbose description if you install the **[lshw](apt://lshw)** tool and run '**lshw -c network**'.

Failing that, I'd try upgrading to the 2.6.39 kernel and see if the driver has been improved since the version included in natty. There are compiled packages in the **kernel-ppa** ppa.

```
$ sudo add-apt-repository ppa:kernel-ppa/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```

If that doesn't help either I'd suggest you [file a new bug report](https://bugs.launchpad.net/ubuntu/+source/linux). Remember, unreported bugs can only be fixed by accident.

---

### Post by slimjim8094 on 2011-06-02
So you're thinking a bug? Ugh...

I'll try more specific Googles, and a new kernel. I was hoping it'd be something simple.

---

### Post by slimjim8094 on 2011-06-02
Got it fixed. Turns out I had the infamous r8169 driver, which sucks. I was getting hundreds of:

> Jun  2 22:44:29 rmead-kubuntu kernel: [  197.338599] r8169 0000:06:00.0: eth0: link up
Jun  2 22:44:30 rmead-kubuntu kernel: [  198.175445] r8169 0000:06:00.0: eth0: link up
Jun  2 22:44:31 rmead-kubuntu kernel: [  199.241444] r8169 0000:06:00.0: eth0: link up
Jun  2 22:44:32 rmead-kubuntu kernel: [  200.287494] r8169 0000:06:00.0: eth0: link up
Jun  2 22:44:36 rmead-kubuntu kernel: [  203.844177] r8169 0000:06:00.0: eth0: link up

Note how they're a few seconds apart. I'm actually astonished I was able to get *any* connectivity. 

So I dug around and found this. [http://djlab.com/2010/10/fixing-rtl8111-8168b-driver-debian-ubuntu/](http://djlab.com/2010/10/fixing-rtl8111-8168b-driver-debian-ubuntu/) . Use those instructions (I recommend the dkms version) with the updated driver at [ftp://WebUser:fH7s5YL@202.134.71.22/cn/nic/r8168-8.024.00.tar.bz2](ftp://WebUser:fH7s5YL@202.134.71.22/cn/nic/r8168-8.024.00.tar.bz2) . I have the MSI P67A-C43 mobo and the version he has on his site doesn't work because it doesn't recognize the chip. Update the version appropriately (-v 8.024.00) and you'll be good to go. I now have the 3MB/s I'm supposed to have, and no dropped packets.

---

