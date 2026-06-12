---
title: "Live CD no unity"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sashin on 2011-02-03
Has anyone else noticed that when booting alpha 2 and trying it out there is no unity? (Ima trying on one with an nvidia graphics card that should be powerful enough but its still reverting back to classic...).

---

### Post by keypox on 2011-02-03
open source drivers for your card are not working, or any nvidia for that matter.  You would have to install and then install restricted drivers.

---

### Post by cariboo on 2011-02-03
You don't have any 3D drives installed, that's why Unity won't work. The only time I've seen Unity work on the live Cd is with Intel 945 or better graphics chipsets.

---

### Post by Harry33 on 2011-02-03
> **keypox said:**
> open source drivers for your card are not working, or any nvidia for that matter.  You would have to install and then install restricted drivers.

Well alfa2 runs with xserver 1.10 rc1+git20110131
and nvidia restricted drivers (nvidia-current) do not support that.
You would have to downgrade to xserver 1.9 first.

---

### Post by nilarimogard on 2011-02-03
The only way to get the Ubuntu 11.04 Live CD to work without any tweaking is to boot from a computer using an Intel graphics card - works just fine on my netbook.

---

### Post by Sashin on 2011-02-03
Is this only for the time being, or will unity work on all graphics cards by launch? With the NVIDIA drivers, KMS fails which makes things look less smooth.

---

### Post by coffeecat on 2011-02-03
> **cariboo907 said:**
> The only time I've seen Unity work on the live Cd is with Intel 945 or better graphics chipsets.

> **nilarimogard said:**
> The only way to get the Ubuntu 11.04 Live CD to work without any tweaking is to boot from a computer using an Intel graphics card - works just fine on my netbook.

Or certain ATI cards - such as my HD4350 and Mobility HD4200 :cool:

:wink:

---

### Post by plun on 2011-02-03
> **nilarimogard said:**
> The only way to get the Ubuntu 11.04 Live CD to work without any tweaking is to boot from a computer using an Intel graphics card - works just fine on my netbook.

Well.... "Intel rule the world"...):P

---

### Post by Sashin on 2011-02-03
How do I downgrade x-server?

---

### Post by Harry33 on 2011-02-04
> **Sashin said:**
> How do I downgrade x-server?

You need to download (from Launchpad) the previous versions of xserver-xorg and all input and video drivers you have installed.
Then you need to go to the terminal and with the command
```

sudo dpkg -i package1.deb package2.deb ...

```
install all of them at the same time.
This is necessary to avoid unmet dependencies and broken packages.

You need the packages:
- xserver-xorg
- xserver-xorg-core
- xserver-xorg-input-*
- xserver-xorg-video-*
Note that you do not need to downgrade the packages x11-common, xorg, xserver-common.

After that if you need nvidia-current, install it. Only then reboot.

---

### Post by ssam on 2011-02-04
> **coffeecat said:**
> Or certain ATI cards - such as my HD4350 and Mobility HD4200 :cool:

:wink:

or radeon 3650.

opensource radeon driver has been fine for compiz for years (though maybe not if you have the very latest card).

---

### Post by coffeecat on 2011-02-04
> **ssam said:**
> or radeon 3650.

opensource radeon driver has been fine for compiz for years (though maybe not if you have the very latest card).

Good to hear from another great mind. :wink: But we are lone voices crying in the wilderness against the overwhelming tide of anti-ATI negativity, and people who install the fglrx driver merely because Jockey tells them it is available. And then wish they hadn't!

---

