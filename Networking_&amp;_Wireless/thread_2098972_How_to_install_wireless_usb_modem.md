---
title: "How to install wireless usb modem?"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by maruf7 on 2012-12-28
Hello, 
I've read a lot of threads and tips but nothing worked. I've been trying to connect to internet with wireless usb modem, but failed to connect. Modem is detected, but no successfull connection. Please help! Thanks.

---

### Post by audiomick on 2012-12-28
First thing: in a terminal do
```
lsusb
```

and post the output of that here so that people can see exactly what sort of device you are dealing with.

---

### Post by rrich1974 on 2012-12-28
that is because you need the dial number, username and password for your ISP. call them to tell you this and try to setup connection manually from network manager. what isp do you have and what kind of modem are we talking about? 
now, i have had an older modem witch only worked with wvdial. 
now....put the output of lsusb

---

### Post by maruf7 on 2012-12-28
Thanks for your response. Output of lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1a2c:0027
Bus 002 Device 004: ID 19d2:fff1 ZTE WCDMA Technologies MSM
```

I've already tried stting up the connection manually with username, password and number, but connection fails.

---

### Post by audiomick on 2012-12-28
Hi. Can you say for sure that this
```
Bus 002 Device 004: ID 19d2:fff1 ZTE WCDMA Technologies MSM
```

is your device? Or that it isn't?

---

### Post by maruf7 on 2012-12-28
> **audiomick said:**
> hi. Can you say for sure that this
```
bus 002 device 004: Id 19d2:fff1 zte wcdma technologies msm
```

is your device? Or that it isn't?

yeah thats my modem, zte is the manufacturer.

---

### Post by 3rdalbum on 2012-12-28
Try it without a username and password. None of my 3g devices have ever needed it.

---

### Post by audiomick on 2012-12-28
Have a look here, particularly at the step immediatly after selecting "add" where the author describes selecting the type of modem. 

I don't recall having to make that selection when setting up my Hauwei stick, but maybe that could help you.

[http://www.watkissonline.co.uk/wordpress/?p=4082]("http://www.watkissonline.co.uk/wordpress/?p=4082")

Also, tell us which version of Ubuntu you are using. That might be relevant...

---

### Post by rrich1974 on 2012-12-28
would you like to try wvdial? 
it is not that hard...
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
go to alternative way 1. 
and also, install wvdial.
if wvdial doesn't see your modem, try to use setserial.

---

### Post by verzx on 2012-12-28
Go to the site which the modem is from and see if there are drivers or to see if there's information on how to set it up.

---

### Post by rrich1974 on 2012-12-28
there is no driver for linux, foget it!

---

### Post by Bucky Ball on 2012-12-28
[I]Thread moved to[B] Networking & Wireless

[/B][/I]Modem and router drivers for Linux? Shouldn't be required.

---

### Post by maruf7 on 2012-12-29
> **3rdalbum said:**
> Try it without a username and password. None of my 3g devices have ever needed it.

I've tried without username & password, but no luck. Thanks anyway.

---

### Post by rrich1974 on 2012-12-29
have you tried wvdial? 
as i told you before!
when you plug the modem, it appears like a usb stick device? unmount it! 
put some screenshots to see what is going on. give us more details so we can help you.

---

### Post by maruf7 on 2012-12-29
> **audiomick said:**
> Have a look here, particularly at the step immediatly after selecting "add" where the author describes selecting the type of modem. 

I don't recall having to make that selection when setting up my Hauwei stick, but maybe that could help you.

[http://www.watkissonline.co.uk/wordpress/?p=4082]("http://www.watkissonline.co.uk/wordpress/?p=4082")

Also, tell us which version of Ubuntu you are using. That might be relevant...

Tried the tutorial, and I was able to connect successfully the very first time after configuring according to the tutorial.... After I made a restart, it fails to connect....
By the way, I'm using Ubuntu 12.04(Precise) 32-bit.

---

### Post by maruf7 on 2012-12-29
> **rrich1974 said:**
> have you tried wvdial? 
as i told you before!
when you plug the modem, it appears like a usb stick device? unmount it! 
put some screenshots to see what is going on. give us more details so we can help you.

Thanks for your suggestion. I've configured wvdial with my provider's info, but after running wvdial I get the following error:

```
wvdial citycell
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB0: Permission denied
--> Cannot open /dev/ttyUSB0: Permission denied
--> Cannot open /dev/ttyUSB0: Permission denied
```

---

### Post by rrich1974 on 2012-12-29
com on man.....i am sure that you can do more than that! 
try 
sudo wvdial
instead of wvdial. 

that permission denied means that you must run the command as sudo, at least in this case. 

sorry of being late with the answer.

LE. dont close terminal while use the connection.

---

### Post by audiomick on 2012-12-29
> **maruf7 said:**
> Tried the tutorial, and I was able to connect successfully the very first time after configuring according to the tutorial.... After I made a restart, it fails to connect....
By the way, I'm using Ubuntu 12.04(Precise) 32-bit.

Well that's a start, anyway. :-k

---

### Post by maruf7 on 2012-12-29
> **rrich1974 said:**
> com on man.....i am sure that you can do more than that! 
try 
sudo wvdial
instead of wvdial. 

that permission denied means that you must run the command as sudo, at least in this case. 

sorry of being late with the answer.

LE. dont close terminal while use the connection.

Thanks. Well now I'm connected with wvdial. Would there be any diffrence of speed between wvdial based connection and network manager based connection?

---

### Post by audiomick on 2012-12-29
> **maruf7 said:**
>  Would there be any diffrence of speed between wvdial based connection and network manager based connection?

Shouldn't be, theoretically. I have read a few things from people who claimed that the on worked better on some machines, the other on other machines. I think you can happily just stick to what is working.

---

### Post by rrich1974 on 2012-12-29
i have use wvdial for some time and i did not noticed a slow speed or instability. 
i am glad that you made it and you also learned something. 
but still i am surprised that "network manager" does not work due to the fact that you have a pretty new modem.

---

### Post by Bucky Ball on 2012-12-31
If it ain't broke, don't fix it ... ;)

---

### Post by maruf7 on 2012-12-31
Thank you all for your support.

---

