---
title: "I need some major help please respond"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by kutche555 on 2009-05-19
Hey, i have recently installed the latest ubuntu (9.0.4). All seems well until i tried connecting to thr internet. First off i gotta install the driver. When i try to install ndiswrapper i cant becuase its unable to mount drive e: . For some odd reason. Also why am i not able to mount it!!! I would love to use ubuntu and this problem is the only thing holding me back. Thank you for your time.

---

### Post by chiefbutz on 2009-05-19
If you are needing to use ndiswrapper then I am assuming that you are trying to connect to the internet view wireless. What wireless card are you using? Do you have the model number?


As for mounting drive "e". What sort of device is it? Is it a flash drive, or another harddrive?

---

### Post by kutche555 on 2009-05-19
> **chiefbutz said:**
> If you are needing to use ndiswrapper then I am assuming that you are trying to connect to the internet view wireless. What wireless card are you using? Do you have the model number?


As for mounting drive "e". What sort of device is it? Is it a flash drive, or another harddrive?

It is a linksys wireless g adapter so yes its a wireless internet connection


And the e drive is a Cd/dvd drive i belive

---

### Post by chiefbutz on 2009-05-19
Theoretically when a CD is inserted into the drive the disk should automatically mount. But have you tried running this command:

```
mount /dev/cdrom /mnt/cdrom 
```

This should mount the cd drive for you and let you get whatever you need off of it.

---

### Post by kutche555 on 2009-05-19
> **chiefbutz said:**
> Theoretically when a CD is inserted into the drive the disk should automatically mount. But have you tried running this command:

```
mount /dev/cdrom /mnt/cdrom 
```

This should mount the cd drive for you and let you get whatever you need off of it.


No i havent tried tht i will try it toMmorow and let u kno thr results

---

