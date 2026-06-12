---
title: "Fonic UMTS USB-Stick Huawei e1550  Ubuntu 10.4 LTS install"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by Knutsch on 2010-07-02
A few days ago I ordered a UMTS USB-stick from Fonic and I received a  Huawei model E1550. Win and Mac install files are on the stick, but  nothing for Linux. I found for the USB Modeswitch "drivers" at [www.draisberghof.de/usb_modeswitsch/]("http://www.draisberghof.de/usb_modeswitsch/")  (nothing about the program source on the producers web page -  strange),  but the install gave me a lot of errors, and after a while, I  decide to find another "approach".

I think you might find this useful. This is my approach for Ubuntu 10.4  LTS.

Open your terminal and type:

 #  sudo apt-get install udev-extras

and add a new udev rule:
#   gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules

In the pop-up window make the rule like this:

SUBSYSTEM=="usb",
SYSFS{idProduct}=="1446",
SYSFS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type  option-zerocd"

Save and close.

To setup you mobile broadband connection go to

System / Preferences / Network Connections, (or type in terminal ~$ nm-connection-editor)

select the Mobile Broadband Tab, Add new and follow the assistent. The only changes I made, are the country of the provider, and the provider. (In my case Germany, Fonic)
If you have to type in the settings yourself for Fonic, visit  [www.fonic.de/html/handy-einstellungen.html#internet]("http://www.fonic.de/html/handy-einstellungen.html#internet") 

(APN pinternet.interkom.de)


If the device is plugged, it will connect after a few seconds.


;) have fun
greets

---

### Post by axi.torvalds on 2010-07-23
Hello, I have a problem in adding a new udev rule:
#   gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules
No pop up window appeared.
Please help me, Thank's anyways.

---

### Post by pdc on 2010-07-24
OK

perhaps you first of all type in a terminal

> lsusb

and copy and paste the results back to us; (this will help us understand how your device is currently being seen by linux)


then to do what Knutsch suggests, do copy and paste into a terminal

> sudo gedit /etc/udev/rules.d/15-huawei-e1550.rules

the system will ask you for your sudo password; type that in and hit the ENTER key: the text editor called gedit should open;

you should have a BLANK file

into that **copy and paste**

> SUBSYSTEM=="usb",
SYSFS{idProduct}=="1446",
SYSFS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

SAVE: CLOSE: REBOOT

hopefully your system will now switch your modem as you wish

to help us confirm this, please again type

> lsusb

into a terminal and copy and paste the results back here please

---

### Post by axi.torvalds on 2010-07-24
Thank's man it works.
The problem is that I added the #'s into the terminal first time.

---

### Post by pdc on 2010-07-24
great! enjoy

on other linux distros, where you get root powers by typing 

> su

and then entering your password, 

your new prompt after doing that starts with 

> #

to signify root powers; 

so Knutsch was sort of using shorthand for being root .... I think ...

---

### Post by sportscliche on 2010-11-04
I have found a much easier way to do this...simply download and run this excellent program:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

It will provide a simple GUI that allows configuration and use of a USB wireless.  I have installed it on two laptops (a vintage Thinkpad and new Dell) and in both cases it worked immediately.  It automatically takes care of dependencies and loads programs like usb-modeswitch, for example.  You may have to disable wireless and especially mobile broadband in the Ubuntu Network Manager applet.   In my experience, you do not need to boot the OS along with the USB modem...you can plug it in and out at your convenience.

I am in (southern) Germany and have some experience with the available services.  USB wireless modems are called surf-sticks and can be purchased at places like Median Markt or on the provider websites for around 40&#8364;.  At the time of this writing (Fall 2010) the three popular services are Klarmobil, O2, and Fonic.  They are all pretty much the same.  Klarmobil offers a flat fee monthly data transfer of 5 Gb for around 30&#8364;.  You have to acquire a SIM card separately, however, and they will ask you for all kinds of personal information including a passport number.  This is done on the phone or on their website.  

O2 and Fonic have daily rates of around 2-3&#8364;, maxing out at 25&#8364;/month.  You'll need one of their SIM cards as well, but as far as I know any SIM card will work in any of the other modems, ie. SIM cards are not hardware specific.  It is important to point out that neither O2 or Fonic has unlimited data transfer.  You are limited to 500 Mb per day and 5 Gb per calendar month.  If you exceed either of those limits, your bandwidth will slow to a crawl and act like an old dial-up connection.  None of the three providers offers Linux support, so you'll be on your own but as I said, Sakis3g makes it very easy.  You will have to arrange for some sort of payment using a personal German bank account.

---

