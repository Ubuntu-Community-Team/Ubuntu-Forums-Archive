---
title: "ati driver for ubuntu 64 bit"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Yair87 on 2009-11-19
hey guys, my laptop is a dell 1535 studio.
it has an ati video card, i think its 3450
i downloaded the driver from ati's web site, but i have no idea how to open it...
help?

---

### Post by ovimunt on 2009-11-19
To begin with, I belive the name of the file you downloaded is ***ati-driver-installer-9-11-x86.x86_64.run*** and I'll base my explanation on this.

First start a Terminal session and go to the folder where you put your ATI drivers.

```
cd /<folder name>/.../<folder name>
```Next, you need to change permissions of the file so you can execute it:

```
sudo chmod 755 ati-driver-installer-9-11-x86.x86_64.run
```Then you simply run the file:

```
sudo ./ati-driver-installer-9-11-x86.x86_64.run
```

---

### Post by Yair87 on 2009-11-19
thanks!

---

