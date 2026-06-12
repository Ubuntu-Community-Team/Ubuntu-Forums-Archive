---
title: "How to mix Nvidia with ATI (Legacy).. ?"
date: 2010-11-25
forum: Multimedia Software
---

### Post by 67comet on 2010-11-25
I've got three monitors sitting on my desk; two work (connected to the AGP Nvidia 7600GS). The third monitor connected to the PCI Radeon 7500 is as black as a moonless night.

My ideal is to have the nVidia card fire up the two monitors under TwinView; and the little ATI card do a separate X session for its self.

When I run lspci | grep VGA this is the result:
```

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
02:0c.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

```

When I boot up after making the BIOS use the PCI device first it works fine until I install the nvidia drivers (via hardware updater). After that the PCI (ATI) monitor goes black and so do the nvidia monitors (I get a CLI login but that's it).

If I boot with the BIOS using the AGP card first my dual monitors work well; but there is no way that I've seen to get the PCI (ATI) card working. It does show up with lspci; just not with anything else I've seen.

Any help is greatly appreciated; thank you.

P.S. For work reasons I have small partition dedicated to "that other OS"; tried it there and it worked well after installing the drivers (one long desktop). So I know both cards work as expected.

---

### Post by markwb on 2011-04-21
Hey There,

Sorry to bring up an old thread but... I am having the exact same problem.  Two monitors working on a new NVIDIA card and a third monitor on a legacy ATI.

Did you ever get this to work?

Thanks!

-M

---

