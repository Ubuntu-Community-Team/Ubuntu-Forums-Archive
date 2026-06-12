---
title: "help installing ndiswrapper 1.56 on ubuntu remix 10.10(netbook)"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by 2blade30 on 2010-11-06
hi all, i got a problem while im instaling ndiswrapper 1.56 on ubuntu remix(for netbook) 10.10 on my lap top and i tried the sudo make install and i still get the
[all] Error 2,
anyone could help me, i dont know what to do and im new on linux
thanks for fast reply

---

### Post by chili555 on 2010-11-06
Ndiswrapper version 1.56-3 is in the Ubuntu repositories. Are you able to take the netbook over to the router, hook up to the ethernet and do:```
sudo apt-get install ndiswrapper-utils*
```If not, it may also be available on the install CD. Is that a possibility?

---

### Post by 2blade30 on 2010-11-06
hi, thanks for the quick reply,
i cant get the wired internet and i installed from a booting usb(if you dont know what im talking about go on ubuntu web site and watch for the netbook version). Is the usb the same of cd? if so, what should i do

---

### Post by 2blade30 on 2010-11-06
oh well, i just find that i can get the ethernet on my lap top but even with the ethernet i tried the
sudo apt-get install ndiswrapper utils*
and it didnt worked
if this can help you i got a Broadcom corp BCM43225 rev01

---

### Post by bkratz on 2010-11-06
> **2blade30 said:**
> oh well, i just find that i can get the ethernet on my lap top but even with the ethernet i tried the
sudo apt-get install ndiswrapper utils*
and it didnt worked
if this can help you i got a Broadcom corp BCM43225 rev01

did you have the "-" before utils* like Dr Chili said in the posting?

---

### Post by 2blade30 on 2010-11-06
yes, i put it, tried twice, im trying via the software center i found it, install but i dont know how to run it, any idea?

---

### Post by chili555 on 2010-11-06
> is the usb the same of cd?If you can enable the USB key as a software repository, I am not aware.

However, you can go here:
[http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9](http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9)

and here: [http://packages.ubuntu.com/maverick/ndiswrapper-common](http://packages.ubuntu.com/maverick/ndiswrapper-common)

Download the packages on a USB key and drag and drop them to your desktop. Then, in a terminal, do:```
cd Desktop
sudo dpkg -i ndis*
```Post back if you get stuck.

---

### Post by 2blade30 on 2010-11-06
like i just told i suceffuly get ethernet conection and instaled the nsiswrapper from software center and i just found out how to open it, im in the install new drivers right now but i dont know "where" i need to instal the driver

---

### Post by chili555 on 2010-11-06
ndiswrapper will take care of the where and how for you. Here is a guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You can start at section 3.4.2. Assuming the Windows .inf file is in a folder called 'drivers' on your desktop, do:```
cd Desktop
```Proceed with the instructions as in the link.

As always, post back if you get stuck.

---

### Post by 2blade30 on 2010-11-06
here is what i got[IMG]http://img713.imageshack.us/img713/950/screenshotsj.png[/IMG]
in witch file im supose to install the driver, or it is what im supose to have?

---

### Post by 2blade30 on 2010-11-06
where i am suppose to find the inf file?

---

### Post by 2blade30 on 2010-11-06
could you help me get the inf file is i tell you that my pci id is 14e4:4357 and my card is broadcom corp BCM43225 rev01

---

### Post by chili555 on 2010-11-06
I could find the Windows .inf file, but I hate to do things the hard way when there is an easy way. Take that netbook back over to the ethernet cable and do:```
sudo apt-get install bcmwl-kernel-source
```Reboot and your wireless should be working.

---

### Post by 2blade30 on 2010-11-06
i just found in the hardware ready to install my wireless card, i installed it and seem to be working for now, i just need to reboot now, if it still not working ill try your way

---

### Post by 2blade30 on 2010-11-06
just rebooy and fully working, thanks for all the help and for all the fast reply, if i have any other question about something ill be in this forum

---

### Post by chili555 on 2010-11-06
Glad it's working. Have fun!

---

### Post by 2blade30 on 2010-11-06
just before i quit, my adobe flash plugin 10 wont install from the software center, is there another way to get it?

---

### Post by chili555 on 2010-11-06
That's really a question for General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

