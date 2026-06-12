---
title: "Dell 1397 Wireless card not working with Live USB"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by thomas144 on 2010-03-09
I have a Dell Inspiron 1545 running Windows 7 64-bit. It has a Dell 1397 Wireless card with Broadcom BCM 4312 hardware. This is proven by running lspci in Terminal. I downloaded Ubuntu 9.10 64-bit and burned a disc of it. I used System>Administration>USB Startup Disc Creator to make a Live USB from a 4GB flash drive. I plugged it in and my computer booted into Ubuntu with no trouble. The only problem is that I can't connect to my wireless network. The problem is that no matter how I install the Broadcom STA driver, it just says that the driver is activated but not actively in use. I've used Synaptic Package Manager, Jockey, and even Terminal. I've tried running
```
sudo modprobe wl
```
in Terminal, but nothing seems to happen. In Ubuntu, my computer acts as though it has no wireless card, but the wired connection is fine (except for the inconvenience of connecting with a cable). In Windows 7, the wireless connection is fine. Can anybody help me?

---

### Post by KingJulien on 2010-03-09
Hi Thomas,
After you've installed the Broadcom driver you need to restart before it can be used, but obviously this will just start another Live session when you're running from your USB stick which is no use. You'll need to do a hard disk install, install the restricted driver, then restart and it'll work just fine! :)

---

### Post by thomas144 on 2010-03-10
When I created the live USB, I made it persistent. I can prove that because I have changed some visual settings, and the changes were still applied in later boots. When I activate the driver and reboot, it still says that it is activated but not currently in use. If I try to reboot, the computer just boots into Windows, so I have to shut down and boot again. Maybe that is my problem. I might have to install Ubuntu, or would I?

---

### Post by thomas144 on 2010-03-12
Hello?

---

### Post by KingJulien on 2010-03-14
Sorry perhaps I didn't explain too well, even with persistence, the driver will not be activated after a reboot from a Live USB:

> **KingJulien said:**
> You'll need to do a hard disk install

You need to install Ubuntu to hard drive, then install the driver, reboot etc and I promise it'll work then. :D

---

### Post by thomas144 on 2010-03-15
I have decided that I want to install Ubuntu. But, I don't want help right now because I am going to install when Ubuntu 10.04 comes out. I'll probably get some help then. Thanks for the advice.

---

### Post by rybnik on 2010-08-20
Good thread.  This concerns me too.

[quote=King Julien]You need to install Ubuntu to hard drive, then install the driver, reboot etc and I promise it'll work then.  [/quote]

What if instead of using a liveUSB, I install linux to a usb flash drive as if it were a regular hard drive?  Would I then be able to install drivers?

---

