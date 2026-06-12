---
title: "Help with Broadcom BCM4313 802.11?"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by btk6 on 2013-01-01
I been trying for 10 hours now. I have tried ever thread, but nothing works. I all so tried in stalling ndisgtk_0.8.5-1_amd64, and dpkg did not work for me.

My laptop is a Acer Aspire 5517, 64 bit, running windows 7 with Ubuntu 12.04. I can re-install Ubuntu 12.10 if i need to.

Also no internet.

---

### Post by chili555 on 2013-01-01
Please run and post:```
lspci -nn | grep 0280
rfkill list all
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by btk6 on 2013-01-01
Ok here you go.
 
```
btk6@ubuntu:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
btk6@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2013-01-01
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]A rather unique device. It needs a special firmware package that I've attached here. Download the package and transfer it on a USB key or similar to the desktop. Right-click it and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
```The folder may already exist; that's fine, just proceed.```
sudo cp Desktop/firmware_lpphy/*  /lib/firmware/b43
```Now we'll reload the driver so it sees the shiny new firmware:```
sudo modprobe -r b43
sudo modprobe b43
```Any improvement?

---

### Post by btk6 on 2013-01-01
> **chili555 said:**
> Any improvement?

Thank you. I can happily say that i am running wi-fi on Ubuntu. Thank you for your help.

&#9733;&#9733;&#9733;&#9733;&#9733;

---

### Post by Bucky Ball on 2013-01-01
Good news. Please mark thread as solved from 'Thread tools' at top right of this page to help others. Cheers, and enjoy the OS and the forums. ;)

---

