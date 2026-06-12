---
title: "HDMI only works when there is going sound across"
date: 2011-01-08
forum: Multimedia Software
---

### Post by nullpointer1992 on 2011-01-08
Hi. I have a Zotac Mag Atom computer with Nvidia ION graphics. This computer i use as a HTPC hooked up to my 42" LG flatscreen via HDMI. 

The problem i have is that after i have installed de correct graphics drivers the graphics chip only sends picture over HDMI whilst there allso is going sound. 

Do anyone know how i can fix this? It was not a problem in 10.04

---

### Post by BicyclerBoy on 2011-01-08
A lot of people having trouble with latest nvidia driver re hdmi audio etc.

Some are re-installing version 256.

What nvidia driver version are you using ?

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
This ppa is easier to use compared to nvidia installer but you may not be able to force the version you need.

---

### Post by tjones00 on 2011-01-09
To check what driver is installed.

```
cat /proc/driver/nvidia/version
```

If he installed via jockey it just states "nvidia current" for the nvidia-current package from ubuntu.

---

