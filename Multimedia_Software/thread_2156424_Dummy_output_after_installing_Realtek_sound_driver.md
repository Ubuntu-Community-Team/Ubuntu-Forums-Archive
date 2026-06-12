---
title: "Dummy output after installing Realtek sound drivers"
date: 2013-06-21
forum: Multimedia Software
---

### Post by Thee on 2013-06-21
Hi

I had some crackling sound when using the mic, so I tried some suggestions that I've found on the web, and none fixed my problem, and then I found a suggestion on Ubuntu documentation that I should try installing the Realtek drivers.

Boy, how wrong was I to do that. After I installed the drivers/restarted, a new problem accrued, I could now only see "Dummy Output" and no sound was present.
So I thought I'd uninstall the driver, which I did, but that did not fix the problem. I tried various solutions to get the sound back, but now I ran out of solutions.

I should note also, that I can't start alsamixer anymore. It says:

```
cannot open mixer: No such file or directory

```
Even through it worked before, and I did not uninstall it.

Also doing:

```
sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: Barts HDMI Audio [Radeon HD 6800 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:fdefc000-fdefffff
  *-multimedia UNCLAIMED
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fe024000-fe027fff

```

Shows that the device is unclaimed, what ever that means.
I'm running Ubuntu 13.04

Some help would be greatly appreciated, because I really don't know where to start to solve this problem which I got myself into.

Thanks

---

### Post by Yellow Pasque on 2013-06-21
You have to reinstall the kernel module, and since you have to do that, you might as well get the latest version: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by Thee on 2013-06-21
That did the trick :) Thanks a lot!

It's still crackling when recording, but at least I got the sound back.
Now I know a thing or two more if I run into this problem again.

Thanks again

---

### Post by Thee on 2013-06-21
One more question. I've now added an extra PCI soundcard that I had laying around in an effort to resolve the crackling issue by using that soundcard instead.
Only problem is that, that sound card doesn't show up and is also unclaimed.
How can I enable kernel module for this sound card too now?

more info about the soundcard:

 ```
 *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: CMI8738/CMI8768 PCI Audio
       vendor: C-Media Electronics Inc
       physical id: 8
       bus info: pci@0000:04:08.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=24 mingnt=2
       resources: ioport:be00(size=256)

```

Thanks

---

### Post by Thee on 2013-06-21
Ok, I solved the problem by installing a new kernel.

---

