---
title: "Disabling Nvidia driver"
date: 2009-04-12
forum: Multimedia Software
---

### Post by djbushido on 2009-04-12
Ok, so I installed the Nvidia driver because I was on another computer. I went back, and X wouldn't start. Booted to recovery, removed the driver. That fixed GDM and X, but not SDL and other games. It appears to still be requesting that driver, which could be reasonable, because it was not removed from the hardware configuration.
As such, I cannot start games like Openarena. I am assuming that it is because I was using the nvidia driver, as that is the only thing that has changed. How do I completely remove the driver from my system? I.e. configuration files? Would it be "sudo rmmod <some_nvidia_mod>"?
Thanks for your help!

---

### Post by norwoods on 2009-04-13
how did you install the driver; apt, synaptic, envy, envyng, jockey, nvidia install file, etc.?

---

### Post by djbushido on 2009-04-13
I did it with hardware manager. After another reboot it worked. Don't know why, but I'm not worried about it.

---

