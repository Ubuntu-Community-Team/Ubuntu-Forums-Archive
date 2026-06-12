---
title: "[SOLVED] fglrx won't install, synaptic wants to remove everything"
date: 2008-10-08
forum: Multimedia Software
---

### Post by mullenrbock on 2008-10-08
When I go into synaptic or jockey, I'm not able to install/activate the xorg-driver-fglrx module. In synaptic when I select fglrx to be installed, it wants to remove "ubuntu-desktop", "xorg", and then pretty much everything that begins with xorg-*. In jockey, when I select the fglrx driver and hit "Activate," the a box pops up with the text: "Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid."

I'm using a Radeon 3100 HD, which I'm not sure is fully supported yet by fglrx even though I thought I read it was, even so I can run glxgears with the radeonhd driver with ease, but at ~120 fps. So, anyone else having problems installing the fglrx driver?

Thanks!

---

### Post by mullenrbock on 2008-10-08
i rebooted and tried again, failure, but then i did "dmesg | grep fglrx" to see what would come up:
```

dmesg | grep fglrx
[   17.710745] [fglrx] Maximum main memory to use for locked dma buffers: 2622 MBytes.
[   17.710815] [fglrx]   vendor: 1002 device: 9613 count: 1
[   17.711453] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   17.712603] [fglrx] PAT is enabled successfully!
[   17.712651] [fglrx] module loaded - fglrx 8.53.4 [Sep  8 2008] with 1 minors


```

uh, what?

i tried "sudo modprobe radeon" just before i grepped dmesg, and it spit out this error:
```

WARNING: Error inserting drm (/lib/modules/2.6.27-6-generic/kernel/drivers/gpu/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.27-6-generic/kernel/drivers/gpu/drm/radeon/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

which is why I did "dmesg | grep fglrx".

I'm starting to think a fresh install sounds nice...

---

### Post by markbuntu on 2008-10-08
Are you using Intrepid?

---

### Post by mullenrbock on 2008-10-12
> **markbuntu said:**
> Are you using Intrepid?

oops, yeah, sorry I didn't specify. I'm using 8.10

---

### Post by markbuntu on 2008-10-13
The ati fglrx driver does not work with xorg7.4 yet which comes with Intrepid so ytou need to either downgrade to xorg7.3 or purge fglrx and the radeon driver and reinstall the radeon driver. The reason you need to do this is that fglrx replaces some files that radeon also uses so both must be removed and just the radeon driver reinstalled. Then you can use xorg7.4. ATI is working towards a solution and may even have it fixed before the release on Oct 30.

---

### Post by mullenrbock on 2008-10-14
Ok, I did what you said, and no more fglrx. "dmesg | grep radeon" and "dmesg | grep fglrx" both yield nothing, so I'm assuming everything's fine. Thanks for the help!

---

### Post by bomanizer on 2008-10-15
I also went away installing the xorg-driver-fglrx package, boy was that fun.. nice that I was still able to boot in low graphics mode and remove that.. :)

---

