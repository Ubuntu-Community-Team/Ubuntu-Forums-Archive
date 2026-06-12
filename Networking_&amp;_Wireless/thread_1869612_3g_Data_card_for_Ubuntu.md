---
title: "3g Data card for Ubuntu"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by anantapdash on 2011-10-26
Hey friends!
I want to buy a 3g data card for my laptop.
I am using Ubuntu 10.04.
is there any 3g data card that support both windows & linux ?(other than Bsnl 3g datacard).

If yes then please give me the name & the address/site where i can buy that.  

Thank you

Ananta
Brahmapur,India

---

### Post by dineshs on 2011-10-28
I use Huawei e173 with BSNL 3G SIM.You may install [mobile partner]("http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html") for linux

---

### Post by xlearner on 2011-11-29
@dineshs

I use Micromax 310G card.I am running ubuntu 10.10. It does not connect to Internet with this card although it works fine on windows. Any suggestions as to how to get this work? 

Thanks

---

### Post by dineshs on 2011-11-30
Try sakis3g if network manager doesnt help
[http://micromax-mmx-310g.blogspot.com/](http://micromax-mmx-310g.blogspot.com/)
What do you get for the following commands?```
lsusb
``````
dmesg | grep tty
```

---

### Post by xlearner on 2011-12-10
Hello Dineshs,

Thanks for your reply. I am replying back late. For some reason, I did not get any notification when you replied.

I am pasting the output of these commands:

$ lsusb
lsusb: cannot open "/var/lib/misc/usb.ids", No such file or directory
Bus 002 Device 009: ID 1c9e:f000  
Bus 002 Device 006: ID 0c45:6450  
Bus 002 Device 004: ID 093a:2510  
Bus 002 Device 003: ID 045e:00dd  
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002  
Bus 001 Device 006: ID 413c:8160  
Bus 001 Device 005: ID 413c:8162  
Bus 001 Device 004: ID 413c:8161  
Bus 001 Device 003: ID 0a5c:4500  
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002

$ dmesg|grep tty
[    0.000000] console [tty0] enabled

Hopefully you can suggest me something to make this work. 

Xlearner

---

