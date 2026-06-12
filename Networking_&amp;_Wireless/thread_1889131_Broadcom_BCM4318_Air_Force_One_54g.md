---
title: "Broadcom BCM4318 Air Force One 54g"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by getsuga97 on 2011-11-30
Okay, I'm sorry that I'm posting this, because it's stickied on the first page, but I have NO idea what it's saying. I just got Ubuntu 11.10 and I'm trying to connect to the internet, but it says I need firmware. So I eventually found out that I needed to download the driver for my wireless card. I have a Broadcom BCM4318 Air Force One 54g card. I've done a bunch of searching and all I've got is confusion and technical jargon. Please help...

---

### Post by getsuga97 on 2011-11-30
Update: I know how to install the package now, but to do so, I need internet axis. How do I fix this?

---

### Post by dFlyer on 2011-11-30
Are you hardwired to the network? If so just run additional drivers under system settings.

---

### Post by mörgæs on 2011-12-01
Changed the title to a more descriptive one.

There have been many questions regarding this card. Have you tried googling this forum thoroughly?

---

### Post by praseodym on 2011-12-01
Hi,

firmware file attached. Save it to "Downloads" and unpack it via terminal (CTRL+ALT+T):

```
sudo tar xvf ~/Downloads/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

