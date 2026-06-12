---
title: "Problems connecting to the internet"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by jlae111 on 2011-09-22
Hi,
Completely new to Ubuntu (but love it already!). I've partitioned the HDD on my laptop for pretty much half Windows 7/half Ubuntu (11.10 I think, which ever the latest one was as of 21st of September). So far, everything has gone beautifully.

The only problem I'm having is that I can't get internet connection with my modilbe broadband usb modem. Ubuntu recognises it when I plug it (modem) in, it lists it up in the connection menu, but it just keeps saying disconnected. I've tried re-installing the drivers, I've tried the usually unbeatable "restart", and am now completely at a loss at what to do now. It finds wireless networks and connects to them perfectly, so it has to be something to with the modem/drivers and they're ability to talk to Ubuntu.

If anyone has any soulutions to such problem, I would greatly appreciate your advice.
Thank you

---

### Post by wolfen69 on 2011-09-22
Please post the output of
```
lsusb
```

---

### Post by jlae111 on 2011-09-22
WOW! I was not expecting a reply so quickly. Thank you.
Ok, this is what I got after the lsusb command;

jacob@jacob-Satellite-C665:~$ lsusb  
 Bus 002 Device 003: ID 12d1:140c Huawei Technologies Co., Ltd.  
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 004: ID 10f1:1a34   
 Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp.  
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 
Jibberish to me as I am only just starting with this, but hopefully you can see something. I do, however, know that the Huawei is my modem (if that's any use to you).

---

### Post by wolfen69 on 2011-09-22
I found this: [http://www.initcron.org/uncategorized/how-to-configure-reliance-huawei-modem-with-ubuntu-10-4-lts-lucid-lynx/](http://www.initcron.org/uncategorized/how-to-configure-reliance-huawei-modem-with-ubuntu-10-4-lts-lucid-lynx/)

It's for ubuntu 10.04, but may work for you.

---

### Post by jlae111 on 2011-09-22
Nope, Ubuntu just said that a later version of this mode switch is already installed. I typed the required input into terminal and got;

Reading package lists...
Building dependency tree...
Reading state information...
usb-modeswitch is already the newest version.
usb-modeswitch-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 76 not upgraded.

---

### Post by wolfen69 on 2011-09-22
How old is the modem?

---

### Post by philipballew on 2011-09-22
you installed a beta version that is not officially going to be released for about a month. run a live usb or live cd of 11.04 not 11.10 and see if you have any luck with Internet please and post your success or failure here.

---

### Post by jlae111 on 2011-09-23
My modem is roughly 6 months old.

And my mistake, it is 11.04 that I have installed. I got it from the Ubuntu website.

I've read a bunch of other forums of similar problems, and one thing I noticed that may be similar to the problem I getting is that the APN was slightly different/wrong.

When the new broadband connection wizard opens up, there is no option for pre-paid connection, only the different plans. Again, I am far from an IT expert, but I'm thining this may have something to do with it.

---

### Post by philipballew on 2011-09-23
Can you connect and surf at a starbucks for example?

---

### Post by jlae111 on 2011-09-23
Yeah, if I use wifi, it works fine. I'm pretty sure it has something to do my modem, the software it uses or something like that.

I know when I use the said modem with windows, I actually have to open a program for it to connect. The icon I click on is an .exe file (which I have learnt does not work with linux systems). Could it be something as simple as that? Just needing to open the program somehow to connect?

---

### Post by jlae111 on 2011-09-23
Is there a way of running .exe files? 

Or converting them to an Ubuntu equivalent?

I am starting to think that is the problem. The little connection indicator in the top right corner, when I try to use my usb modem, it flickers from connected to not connected, as if it's trying but something won't let it or is stopping it or needs to be enabled first.

---

### Post by philipballew on 2011-09-23
why are you connecting to the modem. You dont have a router?

---

### Post by jlae111 on 2011-09-23
No, I don't have a router. I have a USB wireless broadband modem that I use on my laptop.

---

### Post by jlae111 on 2011-09-23
This is the modem I can't connect to the Internet and my reason for asking for help.

---

