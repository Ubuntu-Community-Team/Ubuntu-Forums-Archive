---
title: "Sierra Wireless AirCard 313U"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by reggler on 2012-04-04
Hi There,

I have a Sierra wireless usb adapter that so it says is Linux compatible. I have been trying around but can't get it to work. What I've tried so far:
```
reg@NB30:~$ usb_modeswitch --default-vendor=0x1199 -default-product=0x68aa --target-vendor=0x1199 --target-product=0x6856

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.9 (C) Josua Dietze 2011
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

reg@NB30:~$ sudo pppd call gsm
Script /usr/sbin/chat -v -t6 -f /etc/ppp/peers/gsm_chat finished (pid 7716), status = 0x1
Connect script failed
``` 
and my **/etc/ppp/peers/gsm** looks like this:
```
reg@NB30:~$ sudo cat /etc/ppp/peers/gsm
-detach
lcp-echo-failure 0
/dev/ttyUSB0
115200
debug
defaultroute
usepeerdns

#ipcp-no-address
#ipcp-no-addresses
ipcp-max-failure 4
ipcp-accept-local
ipcp-accept-remote

# AUTHENTICATION
# If noauth works, use that, otherwise you have to pass
# the user name and password. This is an example of a
# standard Cingular user/pw combo

noauth
#user ISPDA@CINGULARGPRS.COM
#password CINGULAR1

crtscts
lock
connect '/usr/sbin/chat -v -t6 -f /etc/ppp/peers/gsm_chat'
```

I'm not exactly sure how I get to establish that connection. Any help that can be provided is greatly appreciated!

Thank you!
Ron

---

### Post by robertmbowes on 2012-04-04
I'm also trying to get one of these AT&T 313u cards to connect. I followed the directions on this page:

[http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?sSessionID=DD2327DFB3774463BE6652F5BC3F58B4RWGOQZIW&aid=44](http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?sSessionID=DD2327DFB3774463BE6652F5BC3F58B4RWGOQZIW&aid=44)

When I get to the make command, it gives the following error for some of the lines.

'struct usb_serial_port' has no member named 'tty'

I'm using Ubuntu 10.04.2 on a Toshiba M9.

Any suggestions would be appreciated.

---

### Post by reggler on 2012-04-04
> **robertmbowes said:**
> I'm also trying to get one of these AT&T 313u cards to connect. I followed the directions on this page:

[http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?sSessionID=DD2327DFB3774463BE6652F5BC3F58B4RWGOQZIW&aid=44](http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?sSessionID=DD2327DFB3774463BE6652F5BC3F58B4RWGOQZIW&aid=44)

When I get to the make command, it gives the following error for some of the lines.

'struct usb_serial_port' has no member named 'tty'

I'm using Ubuntu 10.04.2 on a Toshiba M9.

Any suggestions would be appreciated.

10.04? What kernel are you running? I don't think you need to compile any of the drivers: "Starting from kernel ver. 2.6.25, most of Linux distributions include the Sierra Linux drivers and are equipped with the Network Manager application."

---

### Post by Estyle on 2013-01-04
i also had the same problem from [sierra 313u Wireless Aircard]("http://www.4gltemall.com/sierra-wireless-aircard-313u-lte-mobile-broadband-modem.html"), but i get online help and soloved.:D

---

### Post by silverbullet007 on 2013-01-17
> **Estyle said:**
> i also had the same problem from [sierra 313u Wireless Aircard]("http://www.4gltemall.com/sierra-wireless-aircard-313u-lte-mobile-broadband-modem.html"), but i get online help and soloved.:D

Your response is less than helpful to the OP.  Mind cluing us in on how your issue was fixed?

---

### Post by phenym on 2013-06-06
Has the OP had any luck getting their Aircard to work?

---

### Post by reggler on 2013-06-06
No I did not get it to work but I also quit trying as I had an alternative way available to connect to the web.
Thanks for all your help tho!

---

