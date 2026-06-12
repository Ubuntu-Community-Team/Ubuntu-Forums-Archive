---
title: "Crazy slow graphics"
date: 2008-05-08
forum: Multimedia Software
---

### Post by airbornemist6 on 2008-05-08
For awhile now I've been having problems with the graphics being RIDICULOUSLY slow on my laptop. Compiz only manages about 10FPS with rotate cube if I'm lucky, and I know it should be doing a lot higher framerates than that. Disabling lighting and changing texture quality doesn't help. I mean I've seen compiz running faster on a pentium 3 with an geforce 5 card with the same plugins enabled. I'm running a geforce 7150M and a turion 64 x2 1.9 GHz with 2GB of ram. I mean honestly, vista ultimate runs aero very fast on this laptop, so there's no good reason why compiz shouldn't run fast.

I think this probably has a lot to do with drivers, does anyone have any ideas? I'm currently running the restricted driver, and I've been contemplating trying envy.

Currently I'm running hardy.

---

### Post by unutbu on 2008-05-08
This is just a guess -- please post output to:
```
cat /proc/mtrr
```

---

### Post by airbornemist6 on 2008-05-08
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1

---

### Post by unutbu on 2008-05-08
Your mtrr looks fine. Sorry, that's not the problem.

---

### Post by airbornemist6 on 2008-05-08
Hooray! Wait... damn, that means it's somewhere else that most likely won't be found immediately. Do you think switching to envy drivers would help?

---

### Post by airbornemist6 on 2008-06-28
*bump*

I hadn't thought about this before, but, might it be possible that this is being caused by my processor being clocked down by power management? Is is possible to turn off processor stepping when the power is plugged in?

---

### Post by unutbu on 2008-06-28
To see what cpu scaling governor you are currently using, run:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
To change the scaling governor to "performance":
```
echo performance | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
To watch your cpu clock speed:
```
watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

```
After changing the scaling governor to performance, does compiz run any faster?

The change to the scaling governer can be reverted -- just change performance to whatever it was before. Also, rebooting will reset the scaling governor to whatever it was before.

---

### Post by airbornemist6 on 2008-06-28
oh. my. god. that helped SO much. thanks! so is this permanant? or should i create a script to run every time i plug in?

---

### Post by |{urse on 2008-06-28
beautiful, seems to ave increased my graphics responsiveness in 3d games too.

---

### Post by unutbu on 2008-06-28
To make the change permanent, edit /etc/rc.local:

```
gksudo gedit /etc/rc.local

```
Add this to the end, above "exit 0":
```
echo performance | tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
exit 0
```
Reboot, and then check that it worked.

You might want to experiment with other governors, like "ondemand". "performance" makes your cpu run at full speed even when it should be idle. "ondemand" will ramp up the cpu speed only when needed. I think that would be better if it works for you.

---

