---
title: "TV DVB-T USB Conax"
date: 2010-06-02
forum: Multimedia Software
---

### Post by Wobbo on 2010-06-02
Hello,
 

 I was pleased to find a product which offers Linux drivers. For over 5 years I use only Linux, specifically Ubuntu.
 

 I bought the Infinity USB Unlimited, because it offers more possibilities and more options for the future.
 

 “[http://www.infinityusb.com/default.asp?show=download&DownloadID=39](http://www.infinityusb.com/default.asp?show=download&DownloadID=39)” > “iuu_phoenix-0.9.tgz” > “iuu_phoenix-0.9” > “V2.6”
 

 I did expect an installation on Linux to be somewhat more difficult. So i carefully read the Readme file. In this file there is a reference to the file “iuu_phoenix-2.6.22.ko”, wich you can install if you dont know how to build a kernel yourself. The file “iuu_phoenix-2.6.22.ko” is not in the driver downloaded from your site? So how to install then???
 

 I need this to work, so I can watch TV from my DVB-T subscription (with encryption). It uses a CAM from Conax > “[http://www.conax.com/](http://www.conax.com/)” for the Dutch company KPN  “[http://www.conax.com/storage/Illustrations/conax_customer_mapDTT.jpg](http://www.conax.com/storage/Illustrations/conax_customer_mapDTT.jpg)”.
 

 What to do now? I need help with this installation preferably an installation file in “.deb”.
 

 Thanks,
 Ernst Lanser

---

### Post by Wobbo on 2010-06-07
Any help

---

### Post by xc3RnbFO8P on 2010-06-07
In Terminal, show the output of:
> lsusb
and 
> dmesg

---

### Post by Wobbo on 2010-06-14
I used the "lsusb" end now it is a "Asus". 

** TV DVB-T ****USB****: **
```
Bus 001 Device 010: ID 0b05:173f ASUSTek Computer, Inc. 
```Now wat? lol

---

### Post by Wobbo on 2010-06-14
And: 

**Conax ****USB****: **
```
Bus 001 Device 011: ID 104f:0004 WB Electronics Infinity Unlimited
```[http://www.infinityusb.com/default.asp?show=productsdetail&productID=11](http://www.infinityusb.com/default.asp?show=productsdetail&productID=11)

---

### Post by xc3RnbFO8P on 2010-06-15
Can you show the output of **dmesg** ?

---

### Post by gt.hu on 2011-10-02
I guess you already installed this. I just wanted to say thank you, because after many hours of search this is the first decent reader I found. Too bad that I would be able to help you, but your issue was 4 months ago.

---

