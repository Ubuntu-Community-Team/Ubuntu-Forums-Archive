---
title: "Reliance Netconnect / Tata Photon + on 10.04"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by 7raTEYdCql on 2010-05-18
I am about to buy a wireless connection in India, can anyone tell me their experiences with the above two wireless service providers (Reliance and Tata Photon) when trying to connect their devices to Ubuntu 10.04.

The forum has answers to questions of earlier versions of ubuntu esp. 9.04 only.

Thanking you,
Mehrzad

---

### Post by Tatateleserviceslimited on 2010-05-24
> **i.mehrzad said:**
> I am about to buy a wireless connection in India, can anyone tell me their experiences with the above two wireless service providers (Reliance and Tata Photon) when trying to connect their devices to Ubuntu 10.04.

The forum has answers to questions of earlier versions of ubuntu esp. 9.04 only.

Thanking you,
Mehrzad


		 	  	 	 		 			[FONT=Calibri][SIZE=4][COLOR=#000000]Hi,

currently Photon devices doesnot support Ubuntu.


[/COLOR][/SIZE][/FONT] 		 	   	 	 [SIZE=4]Thanking you[/SIZE]
[SIZE=4]
[/SIZE]
 [SIZE=4]Customer Care 
[/SIZE]
[SIZE=4]
[/SIZE]
 [SIZE=4] Tata Teleservices Limited[/SIZE]

---

### Post by Linuxforall on 2010-05-24
It works fine, please take a look here, I used network manager to connect.

[http://www.techlineinfo.com/how-to-configure-tata-indicom-photon-and-reliance-netconnect-in-ubuntu/](http://www.techlineinfo.com/how-to-configure-tata-indicom-photon-and-reliance-netconnect-in-ubuntu/)

---

### Post by nitinb on 2010-07-14
I'm also able to successfully configure TATA Photon+  (Huawei EC-1261) on My Ubuntu 10.04 Laptop, and in fact I'm posting this using the Tata Photon+ Modem itself.
Please follow the instructions here: [http://digitizor.com/2010/06/28/how-to-use-tata-photon-plus-in-ubuntu-10-04-lucid-lynx/](http://digitizor.com/2010/06/28/how-to-use-tata-photon-plus-in-ubuntu-10-04-lucid-lynx/)

The summary is as follows:
1. Install usb-modeswitch and usb-modeswitch-data packages, using System->Administration->Synaptic Package Manager
2. Edit the usb-modeswitch configuration file ( [I]/etc/usb_modeswitch.d/12d1:1446 ) - add entry for HUAWEI E-1261.
[/I]3. Use Network Manager to add a new Mobile Broadband connection.

Best of Luck.

---

### Post by santa4geeks on 2010-08-18
[SIZE=2]Although the official support doesn't exist for tata photon+ users. But you can follow my instructions at my blog to set up tata photon+ connection with Ubuntu 10.04(Lucid Lynx). This should also work for Reliance Netconnect, BSNL 3G USB Modemsand MTS; Only the  Username and Passwords will vary.
Follow this link to know more...
**[http://www.gizibot.wordpress.com](http://www.gizibot.wordpress.com)**[/SIZE][B]
:KS[/B]

---

### Post by raunhar on 2010-10-23
I have Reliance Broadband+ with the device ZTE-2736. 
I can create a connection through Network mangaer, as the device gets displayed there. But it does not connect to the internet. The username and password are the same as I have entered under Windows.
Do I configure the usb-modeswitch conf file as it is empty.

pl suggest

---

### Post by sks3286 on 2010-12-16
> **raunhar said:**
> I have Reliance Broadband+ with the device ZTE-2736. 
I can create a connection through Network mangaer, as the device gets displayed there. But it does not connect to the internet. The username and password are the same as I have entered under Windows.
Do I configure the usb-modeswitch conf file as it is empty.

pl suggest

bump!

---

### Post by harishsudharsan on 2011-07-14
Guys. Its not a big deal at all. Finally I got it to work easily on Ubuntu 10.04

1. Download the usb-modeswitch-1.1.8.tar.bz2 and usb-modeswitch-data from [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) and follow the installation instruction on the website. (sudo make install stuff)

2.Restart your computer and thats all.

3.Every time you disconnect you don't have to restart your computer. Just unplug and replug your photon!

---

