---
title: "Minimal CD, ZD1211 Not working (edit: now LNE100TX)"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by PCunicorn on 2013-07-08
I have a USB Wifi adapter with the [COLOR=#444444][FONT=arial]ZyDAS ZD1211B chip, and the driver is with the minimal CD. But, when I click it in the driver list (not installing via command line, doing it via basic GUI) t just flashes and brings me back. So what's wrong with it?
SEE POST #6[/FONT][/COLOR]

---

### Post by chili555 on 2013-07-08
What's wrong with it is that the driver CD was undoubtedly created for Windows. Windows .exes won't run on Ubuntu Linux. Don't try to put wheels from a Ford on my sleek black BMW!

The driver zd1211rw is built-in but requires firmware which may not be included on a default install.  Let's verify what you have before we make a mistake by guess-work. Please insert the device and then open a terminal Ctrl+Alt+t and run and post the results of these commands:```
lsusb
sudo modprobe zd1211rw
dmesg | grep -i zd12
lsb_release -d
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Thanks.

---

### Post by PCunicorn on 2013-07-08
LOL, no not a driver miniature CD. I meant I am trying to install ubuntu with a minimal CD: 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
And I can't use my wifi adapter.

---

### Post by BreezyBrooke on 2013-07-08
The problem is that the Ubuntu Minimal CD is missing all the required wireless programs and libraries like iwconfig, iw, wireless-tools, ect... which you need to use your Wireless Stick. So you will need a wired connection to install Ubuntu from Minimal CD.

---

### Post by PCunicorn on 2013-07-08
Okay. I will have to move my PC then.

---

### Post by PCunicorn on 2013-07-08
I put in a LNE100TX ethernet card, and though it is supported with the Tulip module, when I click the Tulip module in the minimal CD, it just flashes. Auto detection says no ethernet detected.

---

### Post by PCunicorn on 2013-07-08
Please guys, this is urgent!

---

### Post by fredfillis on 2013-07-11
I have a similar problem although a different driver. I am trying to figure this out but no luck to date. In my case, Ubuntu is not critical so I'm about ready to cut my losses and just dump it. Not much help to you, sorry!

This may be of interest. Did not work for me, maybe too noob. 
[http://askubuntu.com/questions/6499/provide-driver-on-removable-media-during-installation](http://askubuntu.com/questions/6499/provide-driver-on-removable-media-during-installation)

---

