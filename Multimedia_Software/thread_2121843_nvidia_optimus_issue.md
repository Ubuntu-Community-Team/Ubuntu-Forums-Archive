---
title: "nvidia optimus issue"
date: 2013-03-03
forum: Multimedia Software
---

### Post by pappice on 2013-03-03
Hi all,
I have a laptop Dell xps 702x with an nvidia graphic card using optimus technology. I have followed the following steps in order to install Bumblebee on my system: [https://wiki.ubuntu.com/Bumblebee#Installation](https://wiki.ubuntu.com/Bumblebee#Installation). Unfortunately, when I run the command: ```
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
```
I got the following error:
 ```
The following packages have unmet dependencies:
 bumblebee-nvidia : Depends: nvidia-current but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
May you please help me figuring out what is happening?
Thank you!

---

### Post by pappice on 2013-03-03
I don't know if it may be useful, but i put here also the output of the command
```
lspci | grep VGA
```

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 124d (rev a1)

```

---

### Post by pappice on 2013-03-04
My problem is installing Bumblebee on Ubuntu 12.04 LTS... can someoneat least point me on a direction? Just a metodology to follow in order to solve the problem may suffice... please :)

---

