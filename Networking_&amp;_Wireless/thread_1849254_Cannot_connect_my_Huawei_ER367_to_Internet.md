---
title: "Cannot connect my Huawei ER367 to Internet"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by suomalainen on 2011-09-24
Ubunteros,

I have a Huawei E367 Mobile Broadband USB stick which I cannot seem to get to connect to the Internet.

The attached pics show what I've attempted thus far.

You help is appreciated. Thanks!

---

### Post by gandaran on 2011-09-24
you modem is supported (usb-modeswitch) on ubuntu 11.04 (cant check other versions as I only have 11.04 installed) so it should work with network manager.
or try with [Sakis3G]("http://www.sakis3g.org/")
also usb-modeswitch isn't installed by default on ubuntu 10.04, you have to install the packages, (not needed if you use Sakis3G)

---

### Post by suomalainen on 2011-09-24
I have usb-modeswitch installed but when I run commands in terminal nothing happens.

I ran in terminal the following code:

* sudo aptitude install usb-modeswitch
* sudo gedit /etc/udev/rules.d/Huawei_eject.rules
SYSFS{idVendor}=="12d1", SYSFS{idProduct}=="14ac", RUN+="/usr/bin/eject %k",
OPTIONS+="last_rule"


and when I rebooted my machine the "zeroCD" disappeared but in Network manager my device was not listed.

Would you happen to know what I need to do?

---

### Post by technosysind on 2011-09-24
you need to check if it is Linux compatible or not ?

---

### Post by suomalainen on 2011-09-24
that kinda goes w/o saying...................

---

### Post by Silvertones on 2011-09-24
A little long winded but should help you get there.
[Huawei e220 USB modem for beginners - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=843973")

---

### Post by suomalainen on 2011-09-24
Ubunteros,

The back of my laptop has 3 usb ports. Whenever, my huawei stick is in one of these ports it is unable to be detected and I cannot establish connection to Internet via my operators network.

I have a free PCMCIA slot. I also have a PCMCIA card that proves me with 4 additional usb ports. When the stick is in one of these ports that are on the PCMCIA card it is identified and I can make internet connection. However, I'd prefer to use one of the 3 ports in back of my laptop.

Any advice what I can do? Thank you very much!!!

---

### Post by Silvertones on 2011-09-24
It'll eventually get you here. Something I discovered.
[http://ubuntuforums.org/showthread.php?t=1375907](http://ubuntuforums.org/showthread.php?t=1375907)

---

### Post by suomalainen on 2011-09-24
Thanks for all the info but I really need to be using Network Manager. GNOME PPP can be last resort.

But now as it appears and like I noted above, I think the problem now is getting the stick identified on one of the 3 ports on my laptop.

---

### Post by gandaran on 2011-09-24
[try this]("http://ubuntuforums.org/showpost.php?p=7496646&postcount=3"), it's for the E1550 but just change the vendor serial (vendor=0x12d1 product=0x1446) to your modem model

---

### Post by suomalainen on 2011-09-24
Just realised that if the stick is in one of the 3 ports upon boot up no connection to the Internet can be made. BUT upon boot up I can pull the stick out and then back in again and NOW network manager will connect to Internet... Strange isn't it? What can I do to solve this?

---

### Post by suomalainen on 2011-09-25
Good Morning everyone!

I have my Huawei E367 working but not the way it's suppose to!

When I boot up my laptop I have the stick in the usb port. Once the O/S has loaded, I must pull the stick out and then place it back in again to the usb port. Now it connects to INTERNET automatically.

What can I do so that I don't need to do this each and every time?

Thank you!

suomalainen

---

### Post by suomalainen on 2011-09-25
Can someone tell me what this means please.

top:~$ sudo modprobe usbserial vendor=0x12d1 product=0x14ac
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.


Is this good or bad? Is it correctable?


Thank you!

---

### Post by suomalainen on 2011-09-25
Ubunteros,

I got this strange problem with my Huawei E367 stick and have been going in circles last couple of days.

I have attached two pictures to hopefully explain/clarify my situation for you.

Please consider the following.

When I boot up my laptop with the Huawei USB broadband stick in the USB port found at the back of the machine, see pic "Direct Connection", then my connection does not automatically connect. HOWEVER, if I quickly remove the stick and then place it back into the usb port then a connection is automatically made via Network Manager.

I have also a PCMCIA slot and have bought a 4 port usb card for it. As you can see in the picture labeled "PCMCIA" the broadband stick can also be placed here too. If the laptop is booted and the Huawei stick is in the USB port on the card then an Internet connection is made automatically. Yea.

F.Y.I.:

1) Under both these scenarios the ZeroCD stuff is present on desktop

2) I can also access the micro 2GB card on the stick as well

3) I use Ubuntu 10.04 LTS

I would like to have my broadband stick plugged into the back of my laptop. But pulling the stick in and out all day long isn't piratical either. So the question is how can I trouble shoot this situation I find myself in? 

The ideal outcome for me is to have the Huawei stick in the back of the laptop and automatically connect to the Internet each time I boot up. 

Any offers for assistance will be greatly appreciated.

Thanks!

---

### Post by mörgæs on 2011-09-25
Please don't create multiple threads on the same subject. Threads merged.

---

### Post by mörgæs on 2011-09-25
First I would recommend installing 11.04. Lubuntu is in a fast development, and one year matters a lot.

Second, a brief googling yields for example

[https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch-data/+bug/776959](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch-data/+bug/776959)
[http://ubuntuforums.org/showthread.php?p=10735664](http://ubuntuforums.org/showthread.php?p=10735664)
[http://ubuntuforums.org/showthread.php?t=1820017](http://ubuntuforums.org/showthread.php?t=1820017)

After installing 11.04 using wired internet access, you could try posting in one of these threads.

---

### Post by suomalainen on 2011-09-26
As a Ubuntu user I have the ability to choose which LTS versions of Ubuntu I would like to stick with. Especially since support for such versions is offered into the future. 2015!!!!!!

Please do not re-invent my problem for me or tell me to use a non LTS version of Ubuntu. I stated my experiences and problem and sticking with 10.04LTS I'd like to find a solution. That simple.

Thank you for the links you provided. However, as you read through them you will notice the solutions offered apply to people who haven't got there stick to work. I noted in a past thread that my stick does work and outlined the situation in which it fully operates/functions. However, that thread was consolidated and buried into another thread which was believed to have been similar but wasn't.

I'm going to wait a couple of days w/o saying a word and see what answers I get to my question posted in another thread but then was consolidated into this one. If nobody is able to answer, then I will re-list that question again as a separate thread. Thanks for your understanding. 

Thanks for your understanding.

Suomalainen

---

