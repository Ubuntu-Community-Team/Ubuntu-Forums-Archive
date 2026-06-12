---
title: "Cannot change screen birghtness - HP 8440p Laptop"
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rebootme on 2011-02-05
Any ideas?  The Fn+F9 Fn+F10 key combos that are supposed to lower and raise the brightness don't work.  There's also no brightness slider in the power management preferences.

---

### Post by fil0~ on 2011-02-05
It's a problem related to the early development stage of the 2.6.38 kernel; affects me too. 
No way now, I think.

---

### Post by MacUntu on 2011-02-05
Nvidia binary driver? Then you probably need to add the option "EnableBrightnessControl=1" to the device section of your xorg.conf file.

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
        **Option          "RegistryDwords"    "EnableBrightnessControl=1"**
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


```

---

### Post by rebootme on 2011-02-05
I was feeling lucky and decided to try the experimental nvidia "Nouveau" driver.  That's probably what's screwing me up.

Since you're running the binary driver may I ask does 3D Unity work with it yet?

---

### Post by cariboo on 2011-02-05
If you've just installed alpha2 the restricted nvidia drivers won't work with the latest Xorg server, we'll have to wait for the nvidia devs to come up with a working driver.  The only reason I'm using the nvidia restricted driver is that I haven't upgraded any package  that starts with **x** yet, and won't until a new driver is available.

---

### Post by rebootme on 2011-02-05
Thanks for that.  I saw the issue in the release notes and was wondering about the current status.

I hope those nvidia developers are igniting the midnight petroleum!

---

### Post by Harry33 on 2011-02-06
> **rebootme said:**
> Thanks for that.  I saw the issue in the release notes and was wondering about the current status.

I hope those nvidia developers are igniting the midnight petroleum!

Sure Nvidia devs are aware of this all.
The issue is that we have xserver 1.10 rc1+git20110131 in Natty right now.
And that is not anymore rc1, but it isn't yet rc2 either.
Once all ABI changes are set in rc2, there will soon be binary drivers from Nvidia Corp. available.

Like Cariboo, I haven't moved to xserver 1.10 series yet.
I tried it when it was true rc1. Back then nvidia-current_270.18 worked well with it.
However, I didn't see much difference between xserver 1.10 and xserver 1.9.2.
It is much more important for me to use Nvidia proprietary driver.
There is a huge difference between that and nouveuau.

---

