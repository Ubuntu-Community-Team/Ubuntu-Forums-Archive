---
title: "Help PLZ!!! Ubuntu 10.04 broadband connection!!!"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by lifes2short on 2011-05-09
I installed Ubuntu 10.04 on my D drive & tried it for the first time in my life & I said WaW:D in my first boot on it but soon I was disappointed:mad: that I can't connect to the internet using my USB Huawei HDM ec122 I googled my problem & was surprised of the solutions as a new user can't understand most of the stuff there
People are talking about wvdial, modeswitch, code changes in the terminal, gnome package..,
Plz! I need a step by step guide for dummies..,
I tried to follow the steps myself but can't find wvdial or modeswitch & much stuff to install..,
Where can I find such stuff & packages???

Country: Morocco
Modem: Huawei HDM ec122
Operator: Inwi

---

### Post by Jordanbadangayon on 2011-05-09
Modeswitch is already installed by default in 10.10. Therefore it should recognize your modem. You have to wait for a moment after plugging your modem because its recognition is not instant. After the indicator light of your modem is set right, you can try to check if it was recognized in the Network indicator at the right of the top panel.

---

### Post by lifes2short on 2011-05-09
Thanx 4 ur reply but there is a misunderstanding here I have Ubuntu 10.04 already insatalled & I'm satisfied with it I'm looking for a solution to my problem in this version not to upgrade to another version..,

---

### Post by Jordanbadangayon on 2011-05-09
sorry, i did not read carefully...

---

### Post by lifes2short on 2011-05-09
I understood from ur last reply that the only solution for my problem is to connect to the internet in Ubuntu to install the missing packages..,
I can't get access to the internet in Ubuntu but can use my USB modem in Windows..,
Any link suggestions to download these packages???

---

### Post by lifes2short on 2011-05-09
How come that this version is considered as the most stable version with such a huge problem???
My modem is detected with the driver in it but can't install it or do anything with it!!!
We have always to depend on the Windows lazy bum???
Why developers of ubuntu missed the broadband topic???

---

### Post by Jordanbadangayon on 2011-05-09
By the way, you can access Terminal by going to: Applications > Accessories > Terminal... You can easily search and install modeswitch and wvdial by going to the Ubuntu Software Center. However, you need to be connected to the internet to do this.

---

### Post by lifes2short on 2011-05-09
What's the use of a very performant system without the internet..,
Ubuntu 10.04 ](*,) :-#

---

### Post by jtarin on 2011-05-09
> **lifes2short said:**
> How come that this version is considered as the most stable version with such a huge problem???
My modem is detected with the driver in it but can't install it or do anything with it!!!
We have always to depend on the Windows lazy bum???
Why developers of ubuntu missed the broadband topic???
This [link]("http://gongled.ru/426.html") is in Russian. You can use Google to translate. Basically the same modem....you'll have to play around with the settings.Your problems are not with Ubuntu it's your modem....it's a Windows modem.

---

### Post by compmodder26 on 2011-05-09
Okay, so you are obviously on a computer with a working net connection now.  So a solution would be for you to download the packages to that computer and transfer them to the other computer (via a flash drive, etc.).  

So the package you are looking for is located here:

[http://packages.ubuntu.com/lucid/usb-modeswitch](http://packages.ubuntu.com/lucid/usb-modeswitch)

The download link is at the bottom of the page (amd64 or i386).  

After you get that package on your computer, you should be able to double click on it to attempt an install.  If the install fails and tells you that some packages are missing, make a note of which packages it tells you, then follow the same instructions above for those packages.  Install them first and once all dependencies are satisfied, try to install the usb-modeswitch package again.  Assuming you've installed all the packages it depends on, it should install correctly for you.

---

### Post by Jordanbadangayon on 2011-05-09
You can download the modeswitch and modeswitch data from here:

[http://www.draisberghof.de/usb_modeswitch/#intro](http://www.draisberghof.de/usb_modeswitch/#intro)

however, i'm not sure on how to install the tar.bz2 files

but you can try this that i found from
[http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/](http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/)
1.Extract USB Modeswitch
2. Run Terminal and Type : sudo cp /*usbmodeswitch location /usr/sbin
3.Then Make File Executable:sudo chmod u+x /usr/sbin/usb_modeswitch

*To find location of files: copy file and paste in terminal. Result is the file location

:)

---

### Post by Jordanbadangayon on 2011-05-09
> **compmodder26 said:**
> Okay, so you are obviously on a computer with a working net connection now.  So a solution would be for you to download the packages to that computer and transfer them to the other computer (via a flash drive, etc.).  

So the package you are looking for is located here:

[http://packages.ubuntu.com/lucid/usb-modeswitch](http://packages.ubuntu.com/lucid/usb-modeswitch)

The download link is at the bottom of the page (amd64 or i386).  

After you get that package on your computer, you should be able to double click on it to attempt an install.  If the install fails and tells you that some packages are missing, make a note of which packages it tells you, then follow the same instructions above for those packages.  Install them first and once all dependencies are satisfied, try to install the usb-modeswitch package again.  Assuming you've installed all the packages it depends on, it should install correctly for you.
this is a better solution than my post... ;)

---

### Post by compmodder26 on 2011-05-09
> **Jordanbadangayon said:**
> You can download the modeswitch and modeswitch data from here:

[http://www.draisberghof.de/usb_modeswitch/#intro](http://www.draisberghof.de/usb_modeswitch/#intro)

however, i'm not sure on how to install the tar.bz2 files

but you can try this that i found from
[http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/](http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/)
1.Extract USB Modeswitch
2. Run Terminal and Type : sudo cp /*usbmodeswitch location /usr/sbin
3.Then Make File Executable:sudo chmod u+x /usr/sbin/usb_modeswitch

*To find location of files: copy file and paste in terminal. Result is the file location

:)

Eh, it's probably easiest for him/her to install the official package(s) for that.  Getting them from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and simply installing them with gdebi (for 10.04 all it takes is a double click to use it) will be more user friendly.

EDIT: Jordanbadangayon beat me to it.

---

### Post by jtarin on 2011-05-09
I didn't know about usbmode-switch.....I've been doing it manually for over a year.

---

### Post by lifes2short on 2011-05-09
Thank u!
I did all what u said & still can't get access to the internet..,
I first downloaded modeswitch to install it I needed modeswitch data I installed both I configured my connection settings I was happy that my PC detected my usb modem in the settings I choosed country & typed num & pass then the network loaded for a while & just in vain still sth missing in the puzzle now I'll give wvdial a try too..,

---

### Post by lifes2short on 2011-05-09
I installed all important packages & still not working..,
Nobody had the same problem before???!!!

---

### Post by jtarin on 2011-05-09
Yes I had the problem before it was a problem and followed instructions similar to the ones in the link I gave you. I didn't use any additional software other than Gnome PPP dialer.

---

### Post by 3rdalbum on 2011-05-09
Usually, the SIM card has the access password already in it, so most of the time you DON'T put anything into the "password" field.

---

### Post by Jordanbadangayon on 2011-05-09
> **lifes2short said:**
> Thank u!
I did all what u said & still can't get access to the internet..,
I first downloaded modeswitch to install it I needed modeswitch data I installed both I configured my connection settings I was happy that my PC detected my usb modem in the settings I choosed country & typed num & pass then the network loaded for a while & just in vain still sth missing in the puzzle now I'll give wvdial a try too..,
call your network provider if they can help...

---

### Post by moersalin on 2011-06-29
Hi lifes2short,

I was having the same problem with Inwi modem before (yes, I'm residing in Morocco too), but after some trials and errors have finally managed to get the Huawei EC122 modem to work.

I will come back ASAP with step by step guides ;)

---

### Post by jtarin on 2011-06-29
[Easy Peasy]("http://translate.google.com/translate?hl=en&twu=1&u=http://gongled.ru/426.html").....still with the problems?

---

### Post by moersalin on 2011-06-29
Okay, as promised before, here is the step-by-step guide for your Inwi's Huawei EC122 USB modem.

1. Install ppp, setserial, wvdial, and usb-modeswitch packages

a. Go to any cafe with free wifi connection and write down these commands on your Ubuntu terminal:

```
~$ sudo apt-get install ppp setserial wvdial usb-modeswitch
```

b. Alternative way is to download the .deb packages using your Windows and save them to a USB storage stick. Download them here (choose the nearest mirror to download):

> [http://packages.ubuntu.com/lucid/i386/ppp/download](http://packages.ubuntu.com/lucid/i386/ppp/download)
[http://packages.ubuntu.com/lucid/i386/setserial/download](http://packages.ubuntu.com/lucid/i386/setserial/download)
[http://packages.ubuntu.com/lucid/i386/wvdial/download](http://packages.ubuntu.com/lucid/i386/wvdial/download)
[http://packages.ubuntu.com/lucid/i386/usb-modeswitch/download](http://packages.ubuntu.com/lucid/i386/usb-modeswitch/download)

Once you've download them, open them from inside of your Ubuntu and install them (simply by double clicking on each deb package), or you can use the dpkg -install command.

2. Plug in Inwi's Huawei EC122 USB Modem 
 
3. Type in the terminal

```
~$ lsusb
``` 

Bus 002 Device 004: ID **12d1:1446** Huawei Technologies Co., Ltd.  
Bus 002 Device 003: ID 1bcf:0007 Sunplus Innovation Technology Inc.  
Bus 002 Device 002: ID 8087:0020   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 0461:4db6 Primax Electronics, Ltd  
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard  
Bus 001 Device 002: ID 8087:0020   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

That's an example of my lsusb. Here we get vendor id (**12d1**) and product id (**1446**) of Huawei EC122 modem. However product id as 1446 means that the modem acts as a storage device rather than as a modem. 
 
4. Another command

```
~$ sudo nano /etc/usb_modeswitch.conf
``` 

By the end of the config file, add the following lines: 

> # Huawei EC122 
….. 
DefaultVendor= 0x12d1 
DefaultProduct= 0x1446 
…… 
TargetVendor= 0x12d1 
TargetProduct= 0x1001 
…… 
MessageContent="55534243123456780000000000000011060000000000000000000000000000" 
 
Save the change (Ctrl-O > Enter > Ctrl-X)

5. These commands will do the trick for your Huawei modem (option **-H** stands for **H**uawei)

```
~$ sudo usb_modeswitch **-H** -c /etc/usb_modeswitch.conf
``` 

If succesfull, you will get some messages like these: 
 
> Looking for target devices ... 
 No devices in target mode or class found 
Looking for default devices ... 
 Found devices in default mode or class (1) 
Accessing device 004 on bus 002 ... 
Using endpoints 0x08 (out) and 0x87 (in) 
Using endpoints 0x08 (out) and 0x87 (in) 
Inquiring device details; driver will be detached ... 
Looking for active driver ... 
 OK, driver found ("usb-storage") 
 OK, driver "usb-storage" detached 
 
SCSI inquiry data (for identification) 
------------------------- 
  Vendor String: HUAWEI   
   Model String: Mass Storage     
Revision String: 2.31 
------------------------- 
 
USB description data (for identification) 
------------------------- 
Manufacturer: HUA&#65533;WEI TECHNOLOGIES 
     Product: HUAWEI Mobile 
  Serial No.: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; 
------------------------- 
Setting up communication with interface 0 ... 
Using endpoint 0x08 for message sending ... 
Trying to send message 1 to endpoint 0x08 ... 
 OK, message successfully sent 
Resetting response endpoint 0x87 
Resetting message endpoint 0x08 
 Error resetting endpoint: -32 
-> Run lsusb to note any changes. Bye. 
  
6. Confirm whether product id changed from 1446 to 1001: 

```
~$ lsusb
``` 
 
> Bus 002 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem 
Bus 002 Device 003: ID 1bcf:0007 Sunplus Innovation Technology Inc.  
Bus 002 Device 002: ID 8087:0020   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 0461:4db6 Primax Electronics, Ltd  
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard  
Bus 001 Device 002: ID 8087:0020   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 
Note: if the product id is not changed, then unplug the Huawei EC122 device and re-plug it and execute the command again. 
 
7. ```
~$ sudo modprobe usbserial vendor=0x12d1 product=0x1001
``` 
 
8. ```
~$ sudo wvdialconf 
```
 
9. Now you have to edit the content of wvdial config file:

```
~$ sudo nano /etc/wvdial.conf
``` 

Insert  these lines on the config file:
 
> [Dialer HDM] 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Modem Type = Analog Modem 
Phone = #777 
ISDN = 0 
Username = wana
Init1 = ATZ 
Password = wana 
Modem = /dev/ttyUSB0 
Baud = 9600 
 
Save the changes (Ctrl-O > Enter > Ctrl-X)
 
10. Ready to connect?

```
~$ sudo wvdial HDM
``` 
 
Done. You'll be connected now. 
To disconnect the Modem, just press inside the terminal Ctrl+C

:guitar:

---

### Post by createdcreature on 2011-06-29
Dial-up, mobile broadband, and 'Speed Touch' type modems never work with Ubuntu, use Windows, or get a Wi-Fi network.

---

### Post by jtarin on 2011-06-29
> **Robert Moyse said:**
> Dial-up, mobile broadband, and 'Speed Touch' type modems never work with Ubuntu, use Windows, or get a Wi-Fi network.You don't have the slightest clue about Linux....do you?:P

---

### Post by pavlushka on 2011-07-10
> **moersalin said:**
> Okay, as promised before, here is the step-by-step guide for your Inwi's Huawei EC122 USB modem.

1. Install ppp, setserial, wvdial, and usb-modeswitch packages

a. Go to any cafe with free wifi connection and write down these commands on your Ubuntu terminal:

```
~$ sudo apt-get install ppp setserial wvdial usb-modeswitch
```b. Alternative way is to download the .deb packages using your Windows and save them to a USB storage stick. Download them here (choose the nearest mirror to download):



Once you've download them, open them from inside of your Ubuntu and install them (simply by double clicking on each deb package), or you can use the dpkg -install command.

2. Plug in Inwi's Huawei EC122 USB Modem 
 
3. Type in the terminal

```
~$ lsusb
```Bus 002 Device 004: ID **12d1:1446** Huawei Technologies Co., Ltd.  
Bus 002 Device 003: ID 1bcf:0007 Sunplus Innovation Technology Inc.  
Bus 002 Device 002: ID 8087:0020   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 0461:4db6 Primax Electronics, Ltd  
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard  
Bus 001 Device 002: ID 8087:0020   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

That's an example of my lsusb. Here we get vendor id (**12d1**) and product id (**1446**) of Huawei EC122 modem. However product id as 1446 means that the modem acts as a storage device rather than as a modem. 
 
4. Another command

```
~$ sudo nano /etc/usb_modeswitch.conf
```By the end of the config file, add the following lines: 

 
 
Save the change (Ctrl-O > Enter > Ctrl-X)

5. These commands will do the trick for your Huawei modem (option **-H** stands for **H**uawei)

```
~$ sudo usb_modeswitch **-H** -c /etc/usb_modeswitch.conf
```If succesfull, you will get some messages like these: 
 
 
  
6. Confirm whether product id changed from 1446 to 1001: 

```
~$ lsusb
``` 
 
Note: if the product id is not changed, then unplug the Huawei EC122 device and re-plug it and execute the command again. 
 
7. ```
~$ sudo modprobe usbserial vendor=0x12d1 product=0x1001
```8. ```
~$ sudo wvdialconf 
```9. Now you have to edit the content of wvdial config file:

```
~$ sudo nano /etc/wvdial.conf
```Insert  these lines on the config file:
 

 
Save the changes (Ctrl-O > Enter > Ctrl-X)
 
10. Ready to connect?

```
~$ sudo wvdial HDM
```Done. You'll be connected now. 
To disconnect the Modem, just press inside the terminal Ctrl+C

:guitar:
But it still says

--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
everytime with huawei ec122 modem

---

