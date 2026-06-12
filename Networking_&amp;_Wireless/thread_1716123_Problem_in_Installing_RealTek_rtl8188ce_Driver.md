---
title: "Problem in Installing RealTek rtl8188ce Driver"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by cyb3rs4m on 2011-03-28
hello guys , I have Toshibha Satellite Series Laptop but i cannot access wifi in it :confused:, i have downloaded it's driver but i don't know how to install it , can you ppl write full proper guide on how to install it ? Thanx

---

### Post by cyb3rs4m on 2011-03-28
anyone here :sad:

---

### Post by Hippytaff on 2011-03-28
It depends what you've downloaded. There should be some kind of readme file, but ```
modprobe {drivername}
``` is the standard way to install drivers. see ```
man modprobe
```

---

### Post by cyb3rs4m on 2011-03-28
[http://download.wireless-driver.com/driver/Realtek/RTL8192CE-VA4/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz](http://download.wireless-driver.com/driver/Realtek/RTL8192CE-VA4/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz)

this is driver , can u read the file and guide me properly ?:P

---

### Post by Hippytaff on 2011-03-28
-Decompress the file (right click and choose the decompress to option)
-open a terminal (CTRL+ALT+T)
-cd to the decompressed folder ```
cd /foldername
```
then
```
sudo apt-get install build-essential
```
```
make
```
```
make install
```
reboot

---

### Post by rayian on 2011-03-31
I've got the same card (RTL8188CE) If you download and unpack the file listed above just open the Readme file.It tells you exactly what to do. The only problem I'm having is when using battery power it constantly disconnects, like every couple of minutes. I've emailed Realtek about this but have yet to hear from them. Does anyone know anything about this?

---

### Post by drewesq on 2011-04-01
You'll want to be downloading the driver from here:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

---

### Post by NoVista on 2011-04-01
Just thought I'd give some input. >>
Have a brand new Dell XPS mini 1018.
As drewesq said, get the driver from:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Follow the instructions in the Readme file.
It all works fine here.
I have no issues with it disconnecting.
EDIT >>
I can not confirm this absolutely, only add what just happened.
I went and created another user account and set up wireless.
Now, on either account, I am experiencing the connection dropping out and reconnecting.
To others having this problem,
is there more than one account on your Ubuntu?

---

### Post by rayian on 2011-04-01
> **NoVista said:**
> 
EDIT >>
I can not confirm this absolutely, only add what just happened.
I went and created another user account and set up wireless.
Now, on either account, I am experiencing the connection dropping out and reconnecting.
To others having this problem,
is there more than one account on your Ubuntu?


I have only one user account on my machine but for me the problem has been solved. One of the teckies at Realtek sent me a brand new driver. No more disconnecting.:D

---

### Post by NoVista on 2011-04-02
> **rayian said:**
> One of the teckies at Realtek sent me a brand new driver. No more disconnecting.:D

Can you post that working driver somewhere, and give us some details, like the version number.

---

### Post by jujuba on 2011-05-21
hello guys

I'm having this same problem and tried to follow the steps you have but it did not work when I give "make" the following error appears:

 make [1]: Entering directory `/ usr/src/linux-headers-2.6.35-28-generic '
 make [1]: *** No rule to make target `de '. Stop.
 make [1]: Leaving directory `/ usr/src/linux-headers-2.6.35-28-generic '
 make: ** [all] Error 2

 I already installed build-essential dpkg-Devmo and give this problem, can someone help me?

---

