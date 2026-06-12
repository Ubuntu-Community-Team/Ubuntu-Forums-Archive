---
title: "Wireless Connection Problem"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by ZeroCool096 on 2011-07-15
I have a toshiba satelite L505D-GS6000 and i just put ubuntu 11.04 on it last night. Then the wireless was working perfectly fine but then this morning i try to connect to my wireless it wont work.

Any ideas?

---

### Post by atomicben on 2011-07-15
I'm not trying to be a smart-a55 here man but have you rebooted?

If you have and still cannot connect you're going to need to provide more into than that.

Do you see ANY (or your) wireless networks in your network manager?
If above is true, then what happens when you click your network?  Any messages?

---

### Post by wildmanne39 on 2011-07-15
> **ZeroCool096 said:**
> I have a toshiba satelite L505D-GS6000 and i just put ubuntu 11.04 on it last night. Then the wireless was working perfectly fine but then this morning i try to connect to my wireless it wont work.

Any ideas?Hi run these commands in a terminal 
```
lspci -nn
```
```
sudo lshw -C network
```
```
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

