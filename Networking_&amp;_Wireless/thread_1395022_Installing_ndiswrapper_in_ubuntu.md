---
title: "Installing ndiswrapper in ubuntu"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by kamcauliffe on 2010-01-31
Hello, I'm just wondering if anyone could explain how I should install my wireless card on my Acer Aspire One (AO751h). The card is an Atheros AR5001, and I'm using Ubuntu 9.10. 

I found some instructions [here]("https://help.ubuntu.com/community/AspireOne/AO751h#Wireless%20Configurations%20AO751h") but I'm not quite sure what to do. I've blacklisted ath5k as it instructs, and downloaded the card driver from the acer website and ndiswrapper (1.55) but ndiswrapper doesn't seem to be installing. If I follow the ndiswrapper installation instructions ```
tar zxvf ndiswrapper-version.tar.gz
``` it comes up with the error 
```

tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

```The zipped file is saved on my desktop. Does anyone have any ideas what I'm doing wrong? I'm a complete beginner to this so any help would be great.  Thank you!

EDIT: I gave up trying to do it and installed Jaunty (9.04) instead - worked straight away. Thanks for all your help!

---

### Post by kamcauliffe on 2010-01-31
Ok, I've managed to install ndiswrapper somehow, but now I'm having difficulty with the driver from the Acer website. I'm typing:

> 
"Wireless LAN_Atheros_7.7.0.343_Vitasx64Vistax86_A.zip"  && cd "Wireless LAN_Atheros_7.7.0.343_Vitasx64Vistax86"[FONT=monospace] [/FONT]sudo ndiswrapper -i netathw.inf


but I'm getting the following error

> 
unzip: cannot find or open WIreless LAN_Atheros_7.7.0.343_VistaxVistax86_A.zip, Wireless LAN_Atheros_7.7.0.343_Vista64Vistax86_A.zip or Wireless LAN_Atheros_7.7.0.343_Vista64Vistax86_A.zip.ZIP.


Any ideas? Thanks!

---

### Post by bkratz on 2010-01-31
> **kamcauliffe said:**
> Ok, I've managed to install ndiswrapper somehow, but now I'm having difficulty with the driver from the Acer website. I'm typing:



but I'm getting the following error



Any ideas? Thanks!


sorry, a stupid question
Did you actually download the driver (XP) from the website mentioned?

---

### Post by kamcauliffe on 2010-01-31
Yeah I did, I've got it sitting on my desktop. Do you know why it's not working? I've also just checked the ndiswrapper and it seems to be uninstalled again, I don't know why!

---

### Post by kamcauliffe on 2010-01-31
Ok, so I seem to have managed to get the acer driver running now, as well as ndiswrapper, but when I run ```
user@ubuntu:~$ sudo ndiswrapper -l
```
I get
```
sudo: ndiswrapper: command not found
```
I've also found that the network card is still unclaimed when running lshw.

---

### Post by 73ckn797 on 2010-01-31
Have you tried installing "ndisgtk" from Synaptic? It is a graphical installer. If you have the driver disk that comes with the network card you can, from the program, select the Windows XP driver and it will install it for you.

---

### Post by kamcauliffe on 2010-01-31
Ok, thank you! I have that installed now, but when I go to add the .inf file in ndisgtk it says it is an invalid driver. I've tried both the netathr.inf and netathrx.inf files.

However, when I tried again, it said both drivers were already installed, but gave me no further options. It also says they're installed when I input >   sudo ndiswrapper -i ~/drivers/drivername.inf into the terminal. It also comes up with invalid driver when I input > sudo ndiswrapper -l into the terminal, although this is an improvement as it was coming up with an error before.

---

### Post by chicoharv on 2010-01-31
I have an acer laptop that has a built in broadcom  card and I got it working by installing b43-fwcutter.Also you might try installing hostapd in the package manager.

---

### Post by kamcauliffe on 2010-01-31
> **chicoharv said:**
> I have an acer laptop that has a built in broadcom  card and I got it working by installing b43-fwcutter.Also you might try installing hostapd in the package manager.
OK, thanks. A quick search on b43-fwcutter brings up that it's a driver for broadcom cards, so presumably it wont work on my atheros? I'll give the hostapd a try though. Thanks!

I've just realised my ubuntu is 32-bit kernel, but the driver I downloaded from the Acer website is 64 bit. Is this my problem? If so, where can I find a 32-bit driver, as there only seems to be a 64-bit one on the acer website... 

Can you tell I'm new to this?!

---

### Post by Scooter_Jdh on 2010-01-31
heres a really helpful link.
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Since you have a different wireless card you won't be able to follow it step by step.
The link still has really helpful information that lays out general direction on installing the ndiswrapper and the drivers for the card.

hope it helps

---

### Post by 73ckn797 on 2010-01-31
Maybe a simple (dumb) question. Have you tried rebooting?

---

### Post by kamcauliffe on 2010-02-01
I rebooted and removed athrx.inf and athr.inf installed this time. That seems to have installed. When I run ndiswrapper -l it comes up with >  WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathr : driver installed
            device (168C:001C) is present (alternate driver: ath5k)But when I run iwconfig it comes up with >  lo          no wireless extensions.
eth0        no wireless extensions.
pan0        no wireless extensions.and then when I run ifconfig it comes up with >  
eth0        Link encap:Ethernet HWaddr 00:23:8b:b3:57:42
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
            Interrupt:24 Base address:0x4000

lo          Link encap:Local Loopback
            inet addr:127.0.0.1 Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

Also, when I run  disgtk it comes up with an error message 'Unable to see if hardware is present' when it opens. When I click ok, it shows me the currently installed windows drivers screen with 'nethathr: Hardware present: Yes'. So what does that mean?

---

