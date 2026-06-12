---
title: "Need help with wireless on Lenovo b570"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by ashluvsu on 2012-05-29
I've posted before about this but no one seemed to want to help.
I have a Lenovo b570 and I just installed Ubuntu 12.04.
I can not get the wireless to work.
And there's a hardblock on whatever wireless thing it says.
Helpppp?!

---

### Post by carl4926 on 2012-05-29
Post result of
```
lspci -nnk | grep -iA2 net
```

If you have rfkill installed it might be worth posting

```
rfkill list all
```

---

### Post by ashluvsu on 2012-05-29
Thank youu for replying. Please help. I'm getting so desperate

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r816
```

```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by carl4926 on 2012-05-30
```
rfkill unblock all
```

I don't think I see you device here
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Could go on IRC #bcm-users
Ask there

---

### Post by ashluvsu on 2012-05-30
rfkill unblock all doesn't seem to be working.
And where am I looking?

---

### Post by ashluvsu on 2012-05-31
I've been searching for ages and I've been having so many problems with my computer.
I found a forum post about Jupiter and a hardware reset.
I installed Jupiter through terminal and then I shut down my computer  and took out the battery and held the power button for 30 seconds.
I'm not sure which one of those two things did it, but I'm posting this from my wireless connection(:

---

### Post by carl4926 on 2012-05-31
> **ashluvsu said:**
> I've been searching for ages and I've been having so many problems with my computer.
I found a forum post about Jupiter and a hardware reset.
I installed Jupiter through terminal and then I shut down my computer  and took out the battery and held the power button for 30 seconds.
I'm not sure which one of those two things did it, but I'm posting this from my wireless connection(:
What you did can help remove a hardware block

---

