---
title: "Toshiba Satellite wlan trouble"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by mttfrzr on 2010-02-17
I recently purchased a Toshiba Satellite A505-S6995. I'm currently dual-booting Win7 and Karmic, but I've had trouble finding a wlan driver that works. I found and installed one, and it works for about 5 minutes, but after that I can't connect to anything. It will still say that I'm connected to whatever I was originally connected to, but I can't send or receive any data.

Help?

---

### Post by 2hot6ft2 on 2010-02-17
What wifi card does it have?
Post the results of
Applications > Accessories > Terminal
```
lspci
```

---

### Post by mttfrzr on 2010-02-17
Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

---

### Post by rampage355 on 2010-04-20
# Login as normal. Now we're going to get the wireless driver running. Download the driver from the RealTek web-site:
Download the 8192se drivers
[http://www.realtek.com/downloads/dow...Downloads=true]("http://www.realtek.com/downloads/dow...Downloads=true")

# Now build and install your wireless driver:
Code:
You have to be root to build the drivers, sudo cause disconnect and lock up problems with the OS
```

su -
cd /home/someuser/Downloads
tar xvzf rtl8192se_linux_2.6.0015.0127.2010.tar.gz
cd rtl8192se_linux_2.6.0015.0127.2010
make
sudo make install
sudo modprobe r8192se_pci

```

---

