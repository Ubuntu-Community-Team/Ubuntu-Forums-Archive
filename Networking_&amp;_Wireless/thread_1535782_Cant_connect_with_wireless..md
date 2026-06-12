---
title: "Cant connect with wireless."
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by jesterzl-1 on 2010-07-21
Hi, I am new to Ubuntu, and heres what I have. I have a IBM thinkpad that I replaced the hard drive in. I installed ubuntu, thats all thats on there, (no windows).
My machine does not have an internal wireless card, so I have a USB external antenna type wireless conection.
I tried to load the driver,on cd,it didnt seem to load.
When I turn on the laptop, the external antenna does blink, but I still cannot get online wirelessly.

I did plug in ethernet cable, and was able to connect. How do I get my wireless to work??

Thanks alot.

---

### Post by JackNocturne on 2010-07-21
This is probably a **wireless driver** problem , 

type in terminal
```
lsusb
```

this lists interfaces connected to the usb ports at that time. Look for the name of your **wireless card** and search for its **drivers**

---

### Post by jesterzl-1 on 2010-07-21
I hate to sound dumb,but where do I type this in?
Or how do I do what you described, maybe step by step?

---

### Post by Alvina on 2010-07-21
> **jesterzl-1 said:**
> I hate to sound dumb,but where do I type this in?
Or how do I do what you described, maybe step by step?

I'm using Ubuntu 10.04 and my terminal can be found by going to:

**Applications **-> **Accessories **-> **Terminal**

---

### Post by jesterzl-1 on 2010-07-21
OK, got that far,

found this

Bus 002 Device 002:148f:3070 Ralink Technology Corp.


question is where can I find the driver, then how to install it,

Thanks

---

### Post by JackNocturne on 2010-07-21
> **jesterzl-1 said:**
> OK, got that far,

found this

Bus 002 Device 002:148f:3070 Ralink Technology Corp.


question is where can I find the driver, then how to install it,

Thanks

Ok thats good,  do you know what number(ID or something) is it?
check here below if your product is listed

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by jesterzl-1 on 2010-07-21
OK , I got the driver, and it says connection is established to my 2wire modem, now the problem is when I try to use firefox, and enter an www. address , it says server not found...what do i do now?

---

### Post by jesterzl-1 on 2010-07-21
also noticed where it shows connected, there is a yellow lock symbol over the signal bars. I must be getting close to being able to get online, any more help is much appreciated.
Thanks

---

### Post by JackNocturne on 2010-07-21
Ok thats **good** you got the driver. Im not sure why firefox doesn't work

Try typing the following in [B]terminal

[/B]```
ifconfig
```And print the output here

---

