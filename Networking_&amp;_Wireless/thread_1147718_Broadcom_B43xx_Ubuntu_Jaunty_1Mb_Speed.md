---
title: "Broadcom B43xx Ubuntu Jaunty 1Mb Speed"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by willempoort on 2009-05-03
When I installed Ubuntu 9.04 on my Acer Ferrari 3000 laptop I noticed that the wireless connection was dropped after some network traffic. It turned out that the information on the wireless connection reported a speed of 1Mb.

This problem is a known problem but following the different guides and tips on the internet did not do the trick for me.
After some fiddeling around I found this was the solution for me:

  export FIRMWARE_INSTALL_DIR="/lib/firmware"
  wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
  tar xjf broadcom-wl-4.80.53.0.tar.bz2
  cd broadcom-wl-4.80.53.0/kmod
  sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

Despite the guidelines telling me I should use version 4.150.10.5, it turnes out that the older version 4.80.53.0 is working for Ubuntu 9.04

---

### Post by chocko on 2009-05-03
I have the same issue with a BCM4328 but my issue only occurs with one of the wireless routers I use at home and it occurs using any OS not just ubuntu. Does your issue affect you on all wireless routers? it just sounds very similar my issue thats all.

---

### Post by definingmoment on 2009-05-03
What is the specific number for your card? To the post right above me... have you tried the broadcom Linux drivers for this card?

---

### Post by chocko on 2009-05-04
I should have noted that the BCM4328 has never worked on my system even with the linux drivers installed but my problem appears to be unique as I have read of other using the adapter just fine with Ubuntu.

The issue the original poster is talking about sounds like the issue I had with my system when running XP and using specifically my access point, it works fine with every other access point!

I can see the BMC4328 on my system I just can't use it! very frustrating but I dont want to take over this thread with the details :)

---

### Post by Kevbert on 2009-05-04
What's the make,model and version of the wireless ?
You can get this info in terminal with
```
lspci
```
What's the signal like when you're connected ? You can get this with
```
iwconfig
```
Are there any other wireless signals being received, you may be able to get this info with
```
iwlist scanning
```
if the modem supports it, otherwise just left-click on the wireless signal applet when connected. It may be that someone else is using the same wireless channel.

---

