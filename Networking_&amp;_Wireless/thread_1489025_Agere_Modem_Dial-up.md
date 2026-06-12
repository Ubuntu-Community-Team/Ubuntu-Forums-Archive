---
title: "Agere Modem Dial-up"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by rapturestar on 2010-05-20
Trying to get an Agere Pinball modem to work on Ubuntu. Works alright on Vista & XP. Used scanModem and got other packages installed. Still new to the linux scene and any help will be appreciated.
Using Ubuntu 9.10 before I try out 10 later.

---

### Post by M Star on 2010-05-20
[FONT=Comic Sans MS][SIZE=4][COLOR=Sienna]I had similar problem with my prolink soft-modem  so you could try looking at my thread - '[http://ubuntuforums.org/showthread.php?t=1177257](http://ubuntuforums.org/showthread.php?t=1177257)'

Hope this will be helpful! Keep on rocking! :guitar:
[/COLOR][/SIZE][/FONT]

---

### Post by rapturestar on 2010-05-20
The following included is the modem data. Still trying to get it to appear and working.... would like whatever help.

---

### Post by dineshs on 2010-05-21
Pl post the result  ```
dmesg | grep -e "modem" -e "tty" 
```

---

### Post by rapturestar on 2010-05-21
Posted the code but it is only listing one connection. Should be seeing the onboard Lan & internal PCI card.
 
[0.00241] console [tty0] enabled
[0.793076] serial 8256: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[0.793374] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

---

### Post by rapturestar on 2010-05-21
Deleted/removed Ubuntu 9.10 to install Ubuntu 10.04. It is not showing the modem at all except the lan on both live CD & install.

---

### Post by dineshs on 2010-05-22
Is it an internal modem?If yes did you try scanmodem in 10.04?

---

### Post by klemes on 2010-05-22
SoftModems or Winmodems are not real hardware modems and they as opposed to real modems need a driver emulating a modem to function.Trouble is that this driver is usually proprietary and built for windows only.In order for a compatible soft modem to operate under Linux you will need the sl-modem package.This is comprised by two packages under Ubuntu: sl-modem-source and sl-modem-daemon.
After installation of those two packages you get a symbolic /dev/modem device that points in turn to the actual /dev/ttySL0 device which in turn can be used by communication software (mainly pppd)to dial out to your ISP.
Bear in mind that I have no idea if your particular modem is actually compatible with sl-modem but it is the best (if not the only) bet you have to get your modem working under Linux.

---

### Post by rapturestar on 2010-05-22
Yes to both questions. Attached in this response is the Modem.txt
> **dineshs said:**
> Is it an internal modem?If yes did you try scanmodem in 10.04?

---

