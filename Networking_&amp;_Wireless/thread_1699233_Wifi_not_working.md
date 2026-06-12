---
title: "Wifi not working"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by Brad55 on 2011-03-03
I have a Toshiba MX35 laptop it's a little old but does the job. I'm have a problem getting the wireless to work. I can boot a live CD either Ubuntu 10.10 or Fedora 14 and they will see the wireless card. The card is Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01).

I have Ubuntu 9.10 installed and that is the OS that is having the problem seeing the wireless. The computer will not handle Ubuntu 10.10 (at least it won't handle the desktop effects under Ubuntu 10.10) but handles them just fine under 9.10 and that's why I have 9.10 installed.

I really need the Wifi to work because I'm going to travel in a few days.
Can any one give me some pointers to get it working?

---

### Post by Koffeehaus on 2011-03-03
Yeah I had the same issue with 10.10



Try this:

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

Then go to System > Administration > Additional Drivers

Activate the drivers.

Then restart the wireless:

```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```

---

### Post by Koffeehaus on 2011-03-03
> **Brad55 said:**
>  The computer will not handle Ubuntu 10.10


Was your problem to do with decreased performance when working off battery power by any chance?

---

### Post by Brad55 on 2011-03-03
> **Koffeehaus said:**
> Was your problem to do with decreased performance when working off battery power by any chance?

No it will not handle the desktop effects, it's the video card.

---

### Post by Brad55 on 2011-03-03
> **Koffeehaus said:**
> Yeah I had the same issue with 10.10



Try this:

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

Then go to System > Administration > Additional Drivers

Activate the drivers.

Then restart the wireless:

```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```

I installed bcmwl-kernel-source but I don't have any Additional Drivers. It seems like some thing is not loaded for the wifi to work.

---

### Post by kranu2 on 2011-03-03
ok i have done all to this point, but when i type the sudo modprobe to restart i get
FATAL: Module wl not found....

what i need to do to fix this?

hp g60 laptop ubuntu 10.10 netbook ver

---

