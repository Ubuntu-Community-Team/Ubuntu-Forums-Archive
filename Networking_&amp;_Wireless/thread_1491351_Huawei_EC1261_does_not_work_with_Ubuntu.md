---
title: "Huawei EC1261 does not work with Ubuntu"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by jre6 on 2010-05-23
I recently bought a Huawei EC1261 mobile broadband dongle from Tata Teleservices. Unfortunately,neither does the dongle does not work in Ubuntu 9.04(Jaunty Jackalope) nor in Windows XP. The dongle is rather mounted as a drive and not recognised by NetworkManager as a mobile broadband device. The drive can be accessed with Nautilus as well as terminal like any other USB pen drive and located at "/media/disk". Please help.

Also, does the device work in Ubuntu 10.04(Lucid Lynx)? Please report if anyone has tried using the device on Lucid, as I will upgrade to Lucid if the device is supported.

---

### Post by linuxonbute on 2010-05-23
> **jre6 said:**
> I recently bought a Huawei EC1261 mobile broadband dongle from Tata Teleservices. Unfortunately,neither does the dongle does not work in Ubuntu 9.04(Jaunty Jackalope) nor in Windows XP. The dongle is rather mounted as a drive and not recognised by NetworkManager as a mobile broadband device. The drive can be accessed with Nautilus as well as terminal like any other USB pen drive and located at "/media/disk". Please help.

Also, does the device work in Ubuntu 10.04(Lucid Lynx)? Please report if anyone has tried using the device on Lucid, as I will upgrade to Lucid if the device is supported.

Cannot really help with either O/S problems just give some pointers

The devices can usually be be used for mass storage or modem and the default is mass storage. With the drivers installed under windows you should have some means of switching between the two.
For Linux some work has been done to sort this out and I can only suggest you look at this thread:
[http://ubuntuforums.org/showthread.php?t=1193355&highlight=huawei](http://ubuntuforums.org/showthread.php?t=1193355&highlight=huawei)

---

### Post by bumanie on 2010-05-23
I had the same issue with huawei E620 (fortunately it works with the latest lucid kernel). There are two things you can try.
1. I found the development mainline kernel [found here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/") allowed the huawei to work. You will only need the image, not the headers as well.
2. Install these two packages - the data one first, I think. As tehy are .deb, you only need to double click them to install them.
usb-modeswitch-data_20100127-1_all.deb
usb-modeswitch_1.1.0-2_i386.deb

Either solution might work. p to you which one you try first.

---

### Post by monojbaruah on 2010-05-24
Edit /etc/usb_modeswitch.d/12d1:1446,
add 140b to the targetList=

---

### Post by pdc on 2010-05-25
I see this described as CDMA EVDO device

[http://img246.imageshack.us/img246/2015/dsc02657t.jpg](http://img246.imageshack.us/img246/2015/dsc02657t.jpg)

can you type in 

> lsusb in a terminal and copy and paste the results please?

One way to try with ubuntu 10.04 is to download the iso and try that as a liveCD: either as a CD or usb stick; (I suspect this device will work well with 10.04)

I notice if you google on 

> ubuntu Huawei EC1261

seems like the device ID is 

> 12d1:1446 Huawei Technologies Co., Ltd. 

and that is covered in usb_modeswitch

you need to install the latest version, 1.1.2

from here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

it should flip the device and it can be configured as here

"create a mobile broadband connection .."

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

see halfway down page

---

### Post by jre6 on 2010-05-25
> **bumanie said:**
> I had the same issue with huawei E620 (fortunately it works with the latest lucid kernel). There are two things you can try.
1. I found the development mainline kernel [found here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/") allowed the huawei to work. You will only need the image, not the headers as well.
2. Install these two packages - the data one first, I think. As tehy are .deb, you only need to double click them to install them.
usb-modeswitch-data_20100127-1_all.deb
usb-modeswitch_1.1.0-2_i386.deb

Either solution might work. p to you which one you try first.
Is there anything that requires to be done after installing the packages?

Typing lsusb in terminal gives this output:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by pdc on 2010-05-26
if the ID says

> 1446

the device has not changed its ID:

usb_modeswitch file says it should change to 

> 14ac

If you go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

you can download the latest usb_modeswitch;

your system should offer to install it for you, and it should auto-configure and change the ID from 1446 to 14ac; you can check that on lsusb

when it has changed, it should be able to be configured ... as here ..

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

half-way down page ....... create mobile broadband connection ..?

---

### Post by shebaw on 2010-05-26
> Also, does the device work in Ubuntu 10.04(Lucid Lynx)? Please report if anyone has tried using the device on Lucid, as I will upgrade to Lucid if the device is supported.

Ya I'm using the device in Ubuntu Lucid, but I had to install usbmodswitch from Synaptic like the above posters said. The funny thing is, it was working without installing anything on Ubuntu 9.10. And you said it isn't working on Windows XP, did you try to install the drivers? It should mount a CD image of the drivers and you should be able to install the drivers from a "CD Drive".

---

### Post by jre6 on 2010-05-26
> 
you can download the latest usb_modeswitch;
 
 your system should offer to install it for you, and it should  auto-configure and change the ID from 1446 to 14ac; you can check that  on lsusb
 This is where I am having the problem in understanding. Does the change take place without **any** user intervention? Should I install this package with the device connected? Also, is installing with Synaptic necessary, as I do not any other mode of internet browsing except for my dial-up connection(which has simply failed in Ubuntu) which works in Windows?

I do not have a crystal clear understanding of  Linux and so I do not have an understanding of these things. So please clarify the above.

Meanwhile, I was able to install the device in Windows (with much hassle).

---

### Post by alexfish on 2010-05-26
hi if you install the latest pkg's  >=  1.1.0 then if the device is listed then no user intervention should be required , if you are a novice follow the links to the Debian site 
you will need two packages , the modeswitch it's self and then the modeswitch-data .

[Debian Repository]("http://packages.debian.org/usb-modeswitch").

regards 
alexfish

---

### Post by Tatateleserviceslimited on 2010-05-28
> **jre6 said:**
> I recently bought a Huawei EC1261 mobile broadband dongle from Tata Teleservices. Unfortunately,neither does the dongle does not work in Ubuntu 9.04(Jaunty Jackalope) nor in Windows XP. The dongle is rather mounted as a drive and not recognised by NetworkManager as a mobile broadband device. The drive can be accessed with Nautilus as well as terminal like any other USB pen drive and located at "/media/disk". Please help.

Also, does the device work in Ubuntu 10.04(Lucid Lynx)? Please report if anyone has tried using the device on Lucid, as I will upgrade to Lucid if the device is supported.


		 	  	 	 		 			[FONT=Calibri][COLOR=#000000][/COLOR][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Hi,

 request you to visit Authorized service center in this regard[/COLOR][/SIZE][/FONT] 		 	  [SIZE=3]
[/SIZE] [SIZE=3]
[/SIZE] 	 	 [SIZE=3]Thanking you[/SIZE]
 [SIZE=3]Customer Care  [/SIZE]
 [SIZE=3] Tata Teleservices Limited[/SIZE]

---

### Post by novatillasku on 2010-05-28
I have a Huawei E1612 and needs install usb_modeswitch and usb_modeswitch-data.
I have a post in my blog:[Huawei funciona en Ubuntu 10.04]("http://novatillasku.com/2010/05/03/huawei-e1612-funciona-en-ubuntu-10-04/")

---

### Post by jre6 on 2010-05-28
> **Tatateleserviceslimited said:**
> 
Hi,

request you to visit Authorized service center in this regard

Thanking you
Customer Care
Tata Teleservices Limited


**It is very clear that the knowledge of your staff regarding compatibility of mobile broadband devices on Linux-based distributions is unreliable.**

When I had bought this device (Huawei EC1261), your staff at the authorised service centre stated that the device will be compatible with Ubuntu, and did not mention the requirement of installation of packages. The device was connected to Ubuntu and was found to be incompatible (reasons already stated earlier). When I called your staff (at the toll free number), he did not understand what Ubuntu meant. I made the person understand that I was talking about Linux. Then he replied that this modem will not work and would have to replace it with a EPIValley modem. This shows the lack of knowledge of your staff as:
1)The device may be supported in one Linux distro but not in another. By just reference of the name "Linux", this is not understood and hence cannot determine whether to replace the device or not.
2)The statements are contradictory.
3)EPIValley modems do not work in Ubuntu.

However, as this is not a consumer grievance forum, I will restrain from complaining any further.

[B]Please note that I have no intention to abuse Tatateleservices through this post.

[/B]

---

### Post by jre6 on 2010-05-28
Another thing to clarify: Will this device be recognised by NetworkManager after installation of the mentioned packages?

---

### Post by alexfish on 2010-05-28
> **jre6 said:**
> Another thing to clarify: Will this device be recognised by NetworkManager after installation of the mentioned packages?

hi

if the device is recognised by the system then it should connect ,  NM may fail to connect if specific AT codes are require for the device , also may fail to connect if the modem manager returns the wrong enumeration for the device ,that in it's self is not an Ubuntu problem , on the system there is ppp , alternately wvdial or gnomeppp {front end to wvdial} should do the job if the correct init codes are set up

hope this clarifies what you are asking

regards

alexfish

---

### Post by pdc on 2010-05-28
hi jre;

go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

this is the latest usb_modeswitch

download the latest version you can see on this page

open up the directory it has been downloaded into;

right-click on the package for usb_modeswitch you can see and select the top option: open with Gdebi package installer

now plug your modem in 

now right-click on network manager: the most left of the icons at the top right of your Ubuntu screen;

click on mobile broadband; select add; choose your country: India? click on Tata: click on the plans suits you; you get a screen;

as you are CDMA, I suspect you may need to enter a specific password for yourself ............ but I may be wrong ............. 

you need to know how Tata recognises it is you when you dial in: ie does your modem have a SIMCARD in it ..... if it does, that personalises it and they know it is you .....

.. please try the above and let us know how it goes; must be very early morning in India now ..........

---

### Post by jre6 on 2010-05-29
I had to return the device due to various unavoidable circumstances. I have managed to get the older device. However, I would like to thank everybody for their assistance. Although I have no way to test the device now (when *pdc* suggested me to try this out, the device was deactivated by Tata due to lack of some documentary evidences of addresses etc.), I think the above recommendations would work. However, I am not closing the thread to allow further discussions here (if it doesn't work). If anyone knows that this device works, please notify and close the thread.

---

### Post by bihuboliya on 2010-07-28
hi all,

I have bought tata photon plus and I was given the modem Huawei1261. After doing some research I have installed usb-modeswitch-data_20100623-1_all.deb and usb-modeswitch_1.1.3-1_amd64.deb packages. Restarted my machine but still the modem was detected as mass storage. Please help me in connecting.

---

### Post by bihuboliya on 2010-07-28
> **bihuboliya said:**
> hi all,

I have bought tata photon plus and I was given the modem Huawei1261. After doing some research I have installed usb-modeswitch-data_20100623-1_all.deb and usb-modeswitch_1.1.3-1_amd64.deb packages. Restarted my machine but still the modem was detected as mass storage. Please help me in connecting.

the lsusb gave output as "Bus 002 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd" 

I then tried to manually update the fine 12d1:1446 file in /etc/usb_modeswitch.d to include 1446 in the product list. Now the modem is neither detected as modem or mass storage.

---

### Post by bihuboliya on 2010-07-28
> **bihuboliya said:**
> the lsusb gave output as "Bus 002 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd" 

I then tried to manually update the fine 12d1:1446 file in /etc/usb_modeswitch.d to include 1446 in the product list. Now the modem is neither detected as modem or mass storage.

Sometimes the modem is detected now. This happens when "ls /dev/ttyU*" command gives ttyUSB0-2. In other case it shows "ls: cannot access /dev/ttyU*: No such file or directory". How do I make my system detect the modem as ttyUSB?

---

### Post by pdc on 2010-07-28
so you are running 64bit ubuntu, which is why you installed the 64bit usb_modeswitch?

Josh, who oversees the programme, would say to just install the 1.1.3-1 version of the programme; it auto-configures; and NOT to do any manual editing;

I suggest you join his usb_modeswitch forum and seek his advice

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

---

### Post by jre6 on 2010-08-07
Well, it can all be resolved by using Wvdial.

At first, download Wvdial and Gnome-ppp and all the other dependancies using another computer and install them. Then plugging in the modem, go to terminal and type:
```

lsusb

```Then, you get something like this:

```

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 009: ID 12d1:140b Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Notice that there are two parts in the ID seperated by a colon. The first part is the vendor ID and the second part is the product ID. So, in this case the vendor ID for the Huawei modem will be "0x12d1" and the product ID will be "0x140b". So, type the following in the terminal:

```

sudo modprobe usbserial vendor=0x12d1 product=0x140b

```Now, using Gnome-ppp detect the device. Click on Applications > Internet > Gnome PPP and when the dialog box appears, click on Setup. This dialog box will appear:

[IMG]http://polishlinux.org/reviews/three_3g_modem_linux/gnome-ppp.png[/IMG]

Select the type as USB modem and click on detect. The device may appear as "/dev/ttyUSB2" depending on where you connected it.

Then, type in terminal
```
sudo gedit /etc/wvdial.conf
```

Insert the following in the window and save:

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Stupid Mode = 1

Modem Type = USB Modem

ISDN = 0

Phone = type the phone number

New PPPD = yes

Modem = /dev/ttyUSB2 (this will be whatever you saw on Gnome-PPP, for our case it is /dev/ttyUSB2)

Username = type the username

Password = type the password

CBaud = 460800

Close gedit and then type:

```
sudo wvdial
```If the output stops with something like DNS addresses, your connection has been established. Press Ctrl+C when finished browsing to terminate the connection.

**For Karmic (Ubuntu 9.10):**

You need to to these things before you do any of the above:

Copy the following in gedit and save it:

```

#!/bin/sh
#
sudo rmmod -f usb-storage
# EOF.

```Then from System > Preferences > Startup Applications click Add, complete the details (by using any comment/name) and in command, browse to the location where you save the above file, click Save and then click Close.

Those who may think that Gnome-PPP can too be used as it is a frontend to Wvdial, for them, I must say, Gnome PPP miserably fails.

---

### Post by pdc on 2010-08-07
that's a good guide for folks 

instead of 

> gedit /etc/wvdial.conf

you might be better to advise

> **sudo** gedit /etc/wvdial.conf

---

### Post by jre6 on 2010-08-08
Yes, I have corrected that.

---

### Post by aditya.sharma on 2010-10-17
Btw I have a Huawei EC1261 (I got it as part of new Tata Photon+ connection) too, but it seems to be a slightly different model than I have seen elsewhere (see attached image) and the instructions mentioned by other folks did not seem to work. I poured over different forums finally I found these steps to make it work. Posting them here so that other folks can resolve this faster:

[LIST=1]
[*]Since I was on Ubuntu 10.04, I had to install updated versions of usb_modeswitch_data and usb_modeswitch for your architecture (mine was amd64). (See package version links here: [http://www.botskool.com/geeks/how-configure-tata-photon-ec1261-ubuntu-1004-lucid-lynx](http://www.botskool.com/geeks/how-configure-tata-photon-ec1261-ubuntu-1004-lucid-lynx))
[*]The modem was still not detected right, so I went through the next step.
[*]Reboot computer. I think this can be avoided if I knew the right things to restart.
[*]Run this command to make the modeswitch happen:
```
sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1:1446 
```
This time I got the output 
```
-------------------------
Setting up communication with interface 0 ...
Using endpoint 0x08 for message sending ...
Trying to send message 1 to endpoint 0x08 ...
 OK, message successfully sent
Resetting response endpoint 0x87
Resetting message endpoint 0x08
 Error resetting endpoint: -32

Checking for mode switch (max. 20 times, once per second) ...
 Waiting for original device to vanish ...
 Original device can't be accessed anymore. Good.
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Found correct target device

Mode switch succeeded. Bye.
```


[*]Install the Modem using NetworkManager, follow the steps here if you don't know how [http://www.botskool.com/geeks/how-co...004-lucid-lynx](http://www.botskool.com/geeks/how-co...004-lucid-lynx) (I use Gnome, users who don't might have to improvise). This time the modem will be detected.
[/LIST]

---

