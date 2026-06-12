---
title: "Dell Wireless 1390 WLAN MiniCard not work"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by iraqb on 2010-07-23
hi there
i have dell insoiron 1525 with Dell Wireless 1390 WLAN MiniCard

and is not work with ubunto 

please help i want leave windows for ever :p

note : is work fine with slax and salcware

---

### Post by iraqb on 2010-07-23
help me

---

### Post by iraqb on 2010-07-24
please help

---

### Post by vikas.sood on 2010-07-24
Ok!!

Yours is a broadcom wireless card. same as mine. The reason it doesnt work is because it uses a proprietary driver which ubuntu can not install by default. Although you can do it urself.

First of all, connect yourself through a wired network and than install the bcmwl-kernel-source.

sudo apt-get install bcmwl-kernel-source

this will install the wireless card driver. Than check the contents of your /etc/modules

sudo cat /etc/modules

check the output of the command and see if there is a line that says "wl". If not, run the following command

echo "wl" | sudo tee -a /etc/modules

This command will append "wl" to the file /etc/modules.

Restart and enjoy!!!

---

### Post by iraqb on 2010-07-24
hi

thanks for reply

i can not contact to internet useing wired network 

is there any way to install the bcmwl-kernel-source without 

wired network

---

### Post by bkratz on 2010-07-24
> **iraqb said:**
> hi

thanks for reply

i can not contact to internet useing wired network 

is there any way to install the bcmwl-kernel-source without 

wired network

section 2.1 shows you how to get the bcmwl-kernel-source from the live CD in this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by iraqb on 2010-07-24
hi
im try the 2.1 section but i have this error


but there is comment say in this topic

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

> NOTE: IF NECESSARY, THE STA AND B43 PACKAGES CAN BE
DOWNLOADED USING THE LINKS BELOW. BE SURE TO INCLUDE THE
APPROPRIATE DEPENDENCIES.

STA Driver Source
[http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source)

B43 Driver Source
[http://packages.ubuntu.com/karmic/b43-fwcutter](http://packages.ubuntu.com/karmic/b43-fwcutter)



so can any one give me bcmwl-kernel-source and b43-fwcutter in .deb pakg

or help me to solv the error in attachments

---

### Post by iraqb on 2010-07-25
help :(

---

### Post by iraqb on 2010-07-25
help me please

---

### Post by vikas.sood on 2010-07-25
There has been a lot of confusion about broadcom STA driver. not just on  this thread and many others. I had been using the same wireless card on  the same laptop on different versions of ubuntu starting from hardy to  lucid. installing the driver manually has worked for me and nothing  else.!!!

I suggest one wiki page for propriety drivers and all necessary links on  that page. Or may be the forum can have a separate space for all such  issues. lest its not already there which i may not know of. 

iraqb: [http://ubuntuforums.org/showthread.php?t=1317801](http://ubuntuforums.org/showthread.php?t=1317801)

---

