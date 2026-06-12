---
title: "getting b43-fwcutter to recognize firmware"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by cquigley on 2009-08-02
Hi Everyone--
 
Need some help with my broadcom bcm4318 wireless card. i am running a acer aspire 5100.
 
Running Jaunty 9.04
 
I have followed several tutorials online about this. they said to d/l b43-fwcutter, which I did and installed. Then it had me go get the firmware which I did by typing "sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o, it says;
 
Cannot Open input file wl_apsta-3.130.20.0.o
 
Then I saw that the computer should be connected by hardwire. then only problem is that I have airbus from Verizon, which I am trying to get to work.
 
Anyone know how I can get my wireless to work.
 
thx,
cquigley

---

### Post by kerry_s on 2009-08-02
yeah, you need to get connected using the wired, maybe a friend can help, let you plugin to there internet real quick?

once plugged in it's simple, you just do 2 commands & it will do it's thing and just work(hopefully).
the commands:

[B]sudo apt-get update
sudo apt-get install b43-fwcutter
[/B]

---

### Post by cquigley on 2009-08-02
cool, thx.

Finally got my  usb modem working and on the internet with linux finally. 

However, I got b43fwcutter going just can't figure out how to get the firmware installed. I typed " sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o"

I get an error saying "cannot open input file wl_apsta-3.130.20.0.o"

Anyone know what I need to do? Help would be greatly appreciated.

thanks,
  cquigley

---

### Post by kerry_s on 2009-08-02
> **cquigley said:**
> cool, thx.

Finally got my  usb modem working and on the internet with linux finally. 

However, I got b43fwcutter going just can't figure out how to get the firmware installed. I typed " sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o"

I get an error saying "cannot open input file wl_apsta-3.130.20.0.o"

Anyone know what I need to do? Help would be greatly appreciated.

thanks,
  cquigley


so you have internet? then just forget about trying to manually install, just do the apt-get:

```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

and it will do everything for you.

---

