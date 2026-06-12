---
title: "Will wireless ever be fixed?"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2011-04-15
For some time now I've had random wireless dropouts. It happens without fail every single time I unplug the laptop from the charger. First it drops out for about 20 seconds then comes back, then within 5 minutes dies completely and a reboot is the only way to solve it.

It's getting old pretty fast.

---

### Post by Grenage on 2011-04-15
> **macroshaft said:**
> It's getting old pretty fast.

As I'm sure, are problems without specifics. ;)

It's worth posting your full system spec, specifically the wireless adapter and laptop model.

---

### Post by macroshaft on 2011-04-15
> **Grenage said:**
> As I'm sure, are problems without specifics. ;)

It's worth posting your full system spec, specifically the wireless adapter and laptop model.

I was afraid you'd ask that. It's silver, I forget the rest :D

HP TX1000
Broadcom BCM4321

---

### Post by Grenage on 2011-04-15
> **macroshaft said:**
> I was afraid you'd ask that. It's silver, I forget the rest :D

Smartass ;)

Ok; let's work on the assumption that since it works on main power, but not battery power, that power management is turning off your card (or interfering in another way).

When you unplug the laptop, type this into the terminal:

```
sudo iwconfig eth1 power off
```

If it stops happening, great; we can take it from there.

---

### Post by macroshaft on 2011-04-15
Seems to be working at the moment. I'll keep an eye on it.

---

### Post by Kevbert on 2011-04-15
I assume you've seen [this]("http://ubuntuforums.org/showthread.php?t=1604868") as it's probably still relevant. Part of the problem is that these propriety drivers are provided by Broadcomm and so we have little influence on them. 
Do you really mean a BCM4321 or BCM4312?
What's the output of
```
lspci | grep Network
```?

---

### Post by macroshaft on 2011-04-15
> **Kevbert said:**
> I assume you've seen [this]("http://ubuntuforums.org/showthread.php?t=1604868") as it's probably still relevant. Part of the problem is that these propriety drivers are provided by Broadcomm and so we have little influence on them. 
Do you really mean a BCM4321 or BCM4312?
What's the output of
```
lspci | grep Network
```?

I copied the model number directly from the output as lspci

---

### Post by Grenage on 2011-04-15
> **macroshaft said:**
> Seems to be working at the moment. I'll keep an eye on it.

If it stays working, post 4 [here]("https://bbs.archlinux.org/viewtopic.php?pid=825440") should help you make it permanent.

---

### Post by macroshaft on 2011-04-15
> **Grenage said:**
> If it stays working, post 4 [here]("https://bbs.archlinux.org/viewtopic.php?pid=825440") should help you make it permanent.

Thanks, I've give it a try

---

