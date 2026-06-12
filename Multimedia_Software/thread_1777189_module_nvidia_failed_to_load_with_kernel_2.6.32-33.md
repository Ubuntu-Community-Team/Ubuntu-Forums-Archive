---
title: "module nvidia failed to load with kernel 2.6.32-33"
date: 2011-06-07
forum: Multimedia Software
---

### Post by levymichel on 2011-06-07
I am using Ubuntu 10.04 LTS.
With the last update, I have installed the kernel 2.6.32-33.
And I have the message "module nvidia failed to load" in Xorg.log.0
My "current" nvidia module is 195.
I have tried without success to reinstall nvidia.
What I must do ? Wait for a new update of nvidia ? 
Do you know a solution to this problem ?

---

### Post by levymichel on 2011-06-07
> **levymichel said:**
> I am using Ubuntu 10.04 LTS.
With the last update, I have installed the kernel 2.6.32-33.
And I have the message "module nvidia failed to load" in Xorg.log.0
My "current" nvidia module is 195.
I have tried without success to reinstall nvidia.
What I must do ? Wait for a new update of nvidia ? 
Do you know a solution to this problem ?
[SOLVED]
With the last update, I have installed the nvidia driver 270 as my current nvidia driver.
At first, the nvidia module was not loaded, but after a change in 
system>preferences>apparence and visual effects from none to normal, the nvidia module
was successfully reinstalled and at the next boot, was loaded.
Strange, isn't it ?

---

### Post by GoodJava on 2011-06-07
Can you share with me the details on getting & loading (Synaptic??) that nvidia driver? I have a GeForce 9500GT card using nvidia-current. Currently no display candy at all.

---

### Post by levymichel on 2011-06-08
I have reinstall nvidia-current and nvidia-settings via synaptic.

---

