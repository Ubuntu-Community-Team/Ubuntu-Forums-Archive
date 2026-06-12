---
title: "Dial-Up via Mobile Broadband? [NEED HELP]"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by Kamron3 on 2010-07-06
I have a Verizon Wireless phone and I can use it as a modem. Is there anyway to use Ubuntu to dial the number with a specific username and password?



EX:

Port(Phone) Number: #777
Username: [email]BlaghUbuntu@vwz3g.com[/email]
Password: Linux

(DIALING #777... with username BlaghUbuntu)

(Connected Successfully!)

*browses internet*

Will update title when I have a resolved question.

_k

---

### Post by jepong on 2010-07-06
actually there is... try to install wvdial and hope this links work [http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html) :-)

---

### Post by Kamron3 on 2010-07-09
Unfortunately, it did not work. WVDial can't find the modem; and I can't edit the config file for it... :(

---

### Post by dineshs on 2010-07-09
Did you try to configure it via Network Manager (using the tab mobile broadband)?please post the results of the following commands
```
lsusb
```
```
dmesg | grep -e "modem" -e "tty"
```
Here is a guide by alexfish
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

---

