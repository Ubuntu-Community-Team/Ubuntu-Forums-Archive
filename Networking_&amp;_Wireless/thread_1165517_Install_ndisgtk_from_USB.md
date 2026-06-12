---
title: "Install ndisgtk from USB"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by mr_raider on 2009-05-20
I'm trying to install ndisgtk package on a box with no internet access. I need it to get wifi working.

I know the package can be installed from the install CD, but when I enable the install CD in synaptic repositories, it borks looking for the package. I installed ubuntu from a USB  stick, but the stick is not recognized as an installation CD. It looks for the default /media/cdrom location.

Any options?

---

### Post by albinootje on 2009-05-20
> **mr_raider said:**
> I'm trying to install ndisgtk package on a box with no internet access. I need it to get wifi working.


```

find /media/cdrom|grep ndis

```
On Ubuntu Hardy you would need these packages : ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

After you've found them, copy them to /var/cache/apt/archives/ and install it with apt-get.

If that fails you can (afair) use the command :
```

sudo apt-cdrom add

```
to add your Ubuntu installation cdrom.

---

### Post by mr_raider on 2009-05-20
I found a more elegant solution:
```

sudo mount /dev/sdb1 /cdrom
```


That fools synaptic into thinking my USB is a CD!

---

### Post by albinootje on 2009-05-20
> **mr_raider said:**
> I found a more elegant solution:
```

sudo mount /dev/sdb1 /cdrom
```


That fools synaptic into thinking my USB is a CD!

Very nice :)

---

