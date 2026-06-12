---
title: "Wireless not working; driver activated but not in use."
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by smith21 on 2012-07-05
Hi, I'm a real  noob here, so please forgive my delinquency if this issue has been solved here many times before, which I suspect it has (I've searched but the help is either too confusing for me or not specific).

Anyway my wireless won't work. When I type: ```
lspci -nn | grep 0280
```

I get:

03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

Additional drivers section is telling me I have a Broadcom STA proprietary wireless driver, which it says is activated but not currently in use. I'm very confused now. Do I perhaps have the wrong driver installed? Any help would be greatly appreciated.

Edit: Using Ubuntu 12.04, on an Acer Aspire 5750Z

---

### Post by chili555 on 2012-07-05
Let's do some more diagnostics. Please run and post:```
lsmod | grep -e wl -e b43
rfkill list all
```Thanks.

---

### Post by smith21 on 2012-07-05
Hi there, I get:

```
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2012-07-05
Nothing for *lsmod*? I suspect the driver isn't loaded and that's the reason the wireless isn't working. Let's load it:```
sudo modprobe wl
```Now is your wireless working? If so, we'll need one more step.

---

### Post by smith21 on 2012-07-05
It's working! Thanks so much for your help :). 

Yet again, copying and pasting stuff into the terminal with knowing what the hell it means has saved the day lol.

---

### Post by chili555 on 2012-07-05
Let's copy and paste a few more things. This will tell the system to load the driver no matter what, so help me Linus:```
sudo su
echo wl >> /etc/modules
exit
```You should be all set. Please use thread tools at the top to mark Solved.

---

### Post by smith21 on 2012-07-05
Ok done that. Thanks again :)

---

