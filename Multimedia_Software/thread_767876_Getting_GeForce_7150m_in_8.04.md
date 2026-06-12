---
title: "Getting GeForce 7150m in 8.04"
date: 2008-04-26
forum: Multimedia Software
---

### Post by n2oboost1 on 2008-04-26
I just installed 8.04 today using Wubi and I can't get my NVIDIA GeForce 7150m to work.  I entered the terminal and did:

```
sudo apt-get update
sudo apt-get nvidia-glx
sudo apt-get nvidia-xconfig
sudo reboot
```

and after reboot, it just loads to a black screen, and I had to enter recovery mode to remove nvidia-glx.  Any ideas on how to get this driver working?

---

### Post by overdrank on 2008-04-26
> **n2oboost1 said:**
> I just installed 8.04 today using Wubi and I can't get my NVIDIA GeForce 7150m to work.  I entered the terminal and did:

```
sudo apt-get update
sudo apt-get nvidia-glx
sudo apt-get nvidia-xconfig
sudo reboot
```

and after reboot, it just loads to a black screen, and I had to enter recovery mode to remove nvidia-glx.  Any ideas on how to get this driver working?

Hi and I believe that graphics card would use the nvidia-glx-new. Have you tried the restricted drivers located under system, administration, Drivers manager?

---

