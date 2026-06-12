---
title: "Dual Monitors Not Working at Boot in Ubuntu"
date: 2013-09-17
forum: Multimedia Software
---

### Post by B34N on 2013-09-17
I have a Dell XPS 8500 with an NVIDIA GeForce GT 640. My two monitors are an Acer S271HL (through HDMI) and an old Dell 2001FP (throught DVI and/or DVI to VGA).

When I boot with just the 2001FP connected everything is fine. I can get into Ubuntu, plug in the S271HL, select Displays and be off in running with dual monitors. If I reset I won't get anything but "no signal" on both of the monitors. I beleive they both show the Dell logo upon initial boot. I get the same no signals whenever I boot and both are connected. I can start off fine with just HDMI to the 27". 

Any thoughts?

Win 8 boots just dine with both connected. The Acer is 1920x1080 and the Dell is 1600x1200.

Thank you in advance!

---

### Post by arranskye on 2013-09-17
Hi I had this problem but not too sure if memory serves me correctly but you could try > sudo apt-get install nvidia current.  if this code is not exactly correct im sure someone will be along soon to advise.

---

### Post by B34N on 2013-09-18
> **arranskye said:**
>  if this code is not exactly correct im sure someone will be along soon to advise.

Arranskye,

Thank you. That's all it required. 

The code was missing a dash but was close enough to help me implement the solution. For those finding this thread when trying to solve teh same problem I did:
```
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
```

I don't know if this step was necessary but I kept only one monitor attached during reboot and then hooked up the second. This time the system automatically applied the end monitor. It now works find with both connected at boot time.

---

### Post by B34N on 2013-09-19
I'm not sure if this is related to the NVIDIA drivers but I'm having trouble with using HOBLink to login to my wirk system using Java ever since the NVIDIA driver upgrade. I now just get a black screen where I used to see my remote desktop.

---

