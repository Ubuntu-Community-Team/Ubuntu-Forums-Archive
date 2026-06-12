---
title: "installing wireless Netgear N300 USB adapter"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by dagreen0415 on 2011-08-21
I am trying to install a Netgear N300 Wireless USB Adapter on my UBUNTU desktop.
I have a Windows PC (using for this message) running wireless. I have no eathernet cable connection where I live.
 sudo lshw -C network ...shows the device ...  <Bus001 Device 002 ID 0846:9020 NetGear, Inc.>
 If the answer is real complicated can you recommend a wireless USB adapter that will work right out of the box?
  .....  Don Green

---

### Post by praseodym on 2011-08-21
Hello,

this is a Broadcom-USB-device. It only works with Ndiswrapper. You may install the packages **ndiswrapper-common**, **ndiswrapper-utils-1.9**, and **ndisgtk** from CD/DVD, or download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) for 32 or 64bit. The driver is attached.

More [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Start ndisgtk with:

```
gksu ndisgtk
```
and install the needed driver (.INF) for 32 or 64 bit.

---

### Post by Anfanglir on 2012-01-03
Thanx praseodym, worked fine for me.

/ Anfanglir

---

### Post by Tenorman on 2012-01-08
Just tried this, and installing the driver works.  The dongle picks up my wifi router, but will not connect.  It keeps asking for my encryption key, which I have put in, but it will not connect.  Is this a problem anyone has seen before?

---

### Post by stefano60 on 2012-01-15
> **Tenorman said:**
> Just tried this, and installing the driver works.  The dongle picks up my wifi router, but will not connect.  It keeps asking for my encryption key, which I have put in, but it will not connect.  Is this a problem anyone has seen before?

Also i had the same problem, i was requested encryption key during negotiation, but it was not accepted and i didn't get connection. I solved it changing speed of wireless router from 300 Mb to 54 Mb with  protection WPA2-PSK [AES], the one that should work for 150 and 300 speed, but in my experience not for linux ndiswrapper. I hope to find a workaround in future for a better speed also in linux.
hope this helps
stefano

---

### Post by Maud Dib on 2012-01-15
Hi, 

Thanks for the tip, but I am very new to Linux/Ubuntu. Does anyone know how to install these packages and also install a driver? 

I also am having difficulty finding the mentioned packages (in my CD file/on my USB). Is there anything I need to know in order to find them on my boot-USB (I have the Ubuntu Install package on a USB)? 

 I also tried searching the packages on the directory, I did find one there, but it said I needed a special program to best install all of the included files, but when I went to that installer program it also did not have clear documentation for how to install or use that.   

I am willing to learn-- but am also curious tom know if there is a very minimal download-and-click option for this. 

**If not-- I am happy to learn the Linux procedures.    

I have Linux 11.10

Sincere thanks in advance. :)



> **praseodym said:**
> Hello,

this is a Broadcom-USB-device. It only works with Ndiswrapper. You may install the packages **ndiswrapper-common**, **ndiswrapper-utils-1.9**, and **ndisgtk** from CD/DVD, or download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) for 32 or 64bit. The driver is attached.

More [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Start ndisgtk with:

```
gksu ndisgtk
```and install the needed driver (.INF) for 32 or 64 bit.

---

### Post by gubbels on 2012-01-21
great instructions and it worked great for me. once i logged out of my profile and restarted it wasn't recognizing the usb adapter so i had to re-install the driver and it worked fine. shut down the computer again to see if it would have the same problem and it again didn't recognize the adapter. any help so i don't have to re-install the driver every time?

---

### Post by danielhulsey on 2012-01-29
I too have this same problem, i.e. not using the driver after reboot, on 11.10. I have to uninstall/reinstall the driver for it to work. On other computers I have installed the latest version of Zorin OS and using these instructions and it works flawlessly everytime. At least those my clients computers and not my own. I'm running Ubuntu 11.10 and so far that's the only one I have trouble with.

Any suggestions.
D

---

### Post by Tsubi on 2013-04-21
> **praseodym said:**
> Hello,

this is a Broadcom-USB-device. It only works with Ndiswrapper. You may install the packages **ndiswrapper-common**, **ndiswrapper-utils-1.9**, and **ndisgtk** from CD/DVD, or download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) for 32 or 64bit. The driver is attached.

More [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Start ndisgtk with:

```
gksu ndisgtk
```
and install the needed driver (.INF) for 32 or 64 bit.

I tried this and it still isnt doing anything, I have, "bcmwlhigh5" and "bcmn43xx32" installed with WND I think, but when I unplug my ethernet, it says nothing. And running the Auto-run.exe with Wine just keeps telling me to put it into my computer again and again without recgonising it. Any ideas? I've been working on this for over an hour and its is getting very frustrating.

---

### Post by sandyfreshy on 2013-07-20
i installed the ndis wrapper package, but when i try to run the driver, it says i do not have ndis wrapper installed. Help?

---

### Post by praseodym on 2013-07-31
Install the packages "ndiswrapper-dkms" and "dkms", too

---

### Post by tony_rocks on 2014-04-28
I know this is an old thread, but I managed to get connected by installing all of the following:

dkms_2.2.0.3-1.1ubuntu4_all.deb
ndiswrapper-dkms_1.58-2_all.deb
libgksu2-0_2.0.13~pre1-6ubuntu3_i386.deb
gksu_2.0.2-6ubuntu2_i386.deb
ndisgtk_0.8.5-1ubuntu1_i386.deb
ndiswrapper-utils-1.9_1.58-2_i386.deb
ndiswrapper-common_1.58-2_all.deb

from 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and using the INF file contained in the tar on the previous page:

[Broadcom_bcm43xx_USB_32_64bit_v2.tar]("http://ubuntuforums.org/attachment.php?attachmentid=200521&d=1313937303")


Make sure you reboot after installing all of these and you should be good to go!

---

