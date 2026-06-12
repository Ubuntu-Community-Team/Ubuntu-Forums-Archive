---
title: "Error trying to enable Nvidia drivers"
date: 2009-02-02
forum: Multimedia Software
---

### Post by ddarsow on 2009-02-02
I have been experiencing a memory leak in Compiz.real on my 8.04 system. After some investigation, I decided to try a "fix" that others with a similar problem used. In short, I installed and ran Envy. Bad Idea.

After rebooting my system, I no longer have the correct Nvidia driver installed and although I was able to reset the xorgconfig file to get the proper screen resolution, I am still unable to install a working Nvidia (7300 series) driver so as to be able to enable Compiz effects. 

When I try to enable Nvidia drivers, I get the following error:
```
E: /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.16-23.56_i386.deb: subprocess pre-installation script returned error exit status 2
```

I get a similar error when trying other nvidia drivers. 

Aside from the relatively minor memory leak, 8.04 has been running flawlessly on my laptop for almost a year now.

In retrospect, I should have done a backup before screwing with it.

Any ideas about how to remedy this situation?

---

### Post by ddarsow on 2009-02-05
bump...

---

### Post by ddarsow on 2009-02-07
anyone?...

---

### Post by ddarsow on 2009-02-09
bump...

---

### Post by Ataris on 2009-02-09
You got errors even when using the driver from Nvidia's site itself and installing it by shutting down the xserver?

---

### Post by ddarsow on 2009-02-09
> **Ataris said:**
> You got errors even when using the driver from Nvidia's site itself and installing it by shutting down the xserver?

That is correct

---

### Post by ddarsow on 2009-02-11
bump

---

### Post by ddarsow on 2009-02-16
still not resolved...

---

### Post by ddarsow on 2009-02-20
Since I always got answers in the past when needed...
I will keep trying.
bump...

---

### Post by ddarsow on 2009-03-09
bump

---

### Post by norwoods on 2009-03-10
back in the old days when i ran 8.04, i once had to use envygt to install a 177 driver, remove the 177 driver and then use the nvidia installer for a 180 driver.  i moved to 8.10 because the driver situation is much better and am now happily running 180.39.

---

