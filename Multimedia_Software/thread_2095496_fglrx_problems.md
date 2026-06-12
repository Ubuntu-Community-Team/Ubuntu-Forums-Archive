---
title: "fglrx problems"
date: 2012-12-17
forum: Multimedia Software
---

### Post by Kyluke on 2012-12-17
I am running ubuntu 12.10 64bit and am having problems installing fglrx.

I'll explain what I did and what I observed.
I installed fglrx in a clean install of ubuntu 12.10 after having run

sudo apt-get update && sudo apt-get dist-upgrade
I used the option in software sources to change drivers.

I then rebooted. Unity wouldn't even start.
So I pressed Ctrl + Alt + F1 and removed fglrx

I repeated the process but before rebooting ran amdconfig --initial
This did not solve my problem.

I then installed cinnamon and downloaded the driver from the amd site and built it manually for Ubuntu quatzal.
Once installed, cinnamon went into fallback mode.

The same process was also applied to fglrx.

I also have my linux kernel headers installed.

Does anybody know how to fix this or have fglrx installed on 12.10?

---

### Post by Yellow Pasque on 2012-12-17
What kind of card is it?
```
lspci | grep -i vga
```
Keep in mind that ATI recently dropped support for a bunch of "older" cards in fglrx: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/1058040](https://bugs.launchpad.net/ubuntu-release-notes/+bug/1058040)

---

### Post by Kyluke on 2012-12-17
> **Temüjin said:**
> What kind of card is it?
```
lspci | grep -i vga
```
Keep in mind that ATI recently dropped support for a bunch of "older" cards in fglrx: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/1058040](https://bugs.launchpad.net/ubuntu-release-notes/+bug/1058040)

```
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

```

---

### Post by Kyluke on 2012-12-18
bump

---

