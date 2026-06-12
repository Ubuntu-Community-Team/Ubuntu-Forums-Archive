---
title: "Huawei EC226 Mobile Broadband (CDMA/EV-DO) Working"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by mingtien on 2009-03-07
Hi Folks,

I am new to Ubuntu (and very impressed!), and thought I would share how I got connected to the Internet using a mobile broadband dongle -- in this case from Hutch in Thailand, the Huawei EC226 (various searches seem to show them in South America, eastern Europe and west Africa).

I was quite excited when I read that Network Manager supported mobile broadband devices out of the box. In using the configuration tool, learned that NM support for these devices is not quite cooked yet (should have ability to enter AT commands, and especially to turn off PIN checking).  Note: I do keep Network Manager for wired and wifi connections (for which it is a great utility!).

A bit of Googling led to a page in Spanish and another (I think!) in Russian that gave me some wvdial configs to experiment with, and after a bit of trial and error, I arrived at the configuration below.  

I did (briefly) see a Polish language GUI utility that seemed quite nice, but have been unable to find the link again -- if someone has the link, I would love to test it out.

So -- how to connect:

1.  sudo vi /etc/wvdial.conf  [replace 'vi' with your favourite editor]

Add the following:

[Dialer Defaults]
Modem = /dev/ttyUSB0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777 [**Put your dial-in number here]

Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = [**Put your username here]
Username = [**Put your password here]
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on

2.  Sudo wvdial


In choosing on a Linux distribution, I have re-installed a few times this week, and can confirm that the above has worked with various Ubuntu variants (gOS, Mint, and Intrepid -- I settled on Intrepid as it is the most complete, and best suited to my work).  Actually I can't think of any reason why it should not work on any system that has wvdial.

If anyone has found other solutions for connecting with these devices (or even better, has got Network Manager working with them), I would be very interested.

---

### Post by mingtien on 2009-03-14
I have tweaked the wvdial.conf file, based on various other pages I've read, and here is the latest one.  Steps above are still valid.

I would still be interested to learn if anyone has got these devices working with Network Manager (it would be nice to have one consistent interface for wifi, ethernet and wireless broadband).


Tags: Huawei EC226, EVDO, CDMA2000, Hutch Thailand mobile broadband

[Dialer Defaults]
Modem = /dev/ttyUSB0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATX0
Phone = #777

Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = hutch
Username = hutch
Auto Reconnect = on
Abort on Busy = off
Carrier Check = no
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
[Dialer shh]
Init3 = ATM0

---

### Post by joeizang on 2009-08-01
Hey,

Nice post it really solved a lot of problems I am sure. Can you help with this one. I got my EC226 to work. It was detected on ttyUSB0 and wvdial auto detected it fine no problem. I got your review of the wvdial.conf file on mine and the strangest thing happens: it dials connects for like 5 seconds and disconnects. I checked the logs and nothing jumps out of it. Any thoughts on where I should be looking?

---

### Post by mingtien on 2009-09-02
HI Joe,

Sorry to take so long to reply -- I've been in Australia on a 5 week training trip, so haven't been able to get online for much  more than quick email checks...

I had that problem initially as well, and I wrote a 3 line script (that I named a rather rude word) to sort it:

```
 
sudo /sbin/rmmod usb-storage
sudo /sbin/modprobe usbserial vendor=0x12d1 product=0x1003
sudo wvdial 

```

Once you upgrade to Ubuntu 9.04 (Jaunty Jackalope) that problem should go away.  You also should not need to bother with wvdial any longer, and your modem should work out of the box with Network Manager. I used quite a number of EVDO modems (different telco providers, different models, and different cities) while visiting Australia, and they all worked well.

Hope this is helpful!

---

### Post by chitragurung on 2009-10-14
I was using above device to connect internet when I was using windows. In my new Dell Inspiron mini I have Ubuntu. Now I want to use same device to connect internet. How can I install driver and set it up ?

---

### Post by mingtien on 2009-10-30
chitragurung: what version of Ubuntu are you running?

---

### Post by markdeblois on 2010-01-23
Hi there,
I had recently tested the EC226 here in Kenya and through the Manager I got it to work without anything special. After a recent upgrade to 9.10 it seems like I cannot get it to work. I have tried adding the conf file as described but I seem to get stuck where the modem actually dials, I keep getting: NO CARRIER detected.

Downgrading to 9.04 seems to not be an advisable thing to do either, is there any hope to get my EC226 to still work right now?!

thanks guys!
M

---

### Post by pdc on 2010-01-23
Hi Mark;

the modem that was described in post #1 is to me essentially a Huawei E220;

the dial number in that wvdial.conf file is to me a CDMA network;

I suspect you may well be connecting to a GSM network, and it will have a different dial number 

eg the wvdial.conf file that works for me on GSM is

> [Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","*whatever.co.country*"
Phone = *99#
Stupid Mode = 1 

obviously I have edited ................ *whatever.co.country* ..............

eg for safari.com it might be

> [Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","web.safaricom.com"
Phone = *99#
Stupid Mode = 1

the value web.safaricom.com is called the APN settings, and each network around the world can be openly googled for the settings;

and after an unsteady start, folks now seem to be using network manager to automate their connections;

eg 

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go halfway down the page to "CReate a mobile broadband connection" to see if an automated response will work for you

---

### Post by markdeblois on 2010-01-24
Hi,
I am using the EC-226 EVDO Huawei modem on the Orange Telkom network. Funny thing is it worked on Ubuntu 9.04, but since I upgraded to 9.10 I seem to be having trouble. 
I have changed the phone to #777 as that is what I need under Windows. I have tried various combinations of username, password (Orangefixed plus, Orange) as well as the more personal one I have been given, including: 
Modem = /dev/ttyUSB2 or Modem = /dev/ttyUSB0 (I see more serial ports included in /var/log/messages. But everytime I get: NO CARRIER DETECTED.
The blue light blinks every 2 seconds, which according to the manual means that no network is detected. But on my Windows machine it does detect. Could this be a kernel issue perhaps?!

Thanks for any pointers!
cheers,
M

---

### Post by markdeblois on 2010-01-24
Oh, and I normally don't need to add apn for Orange (contrary to Safaricom). Using NetworkManager I also get a different interface than if I try the E-220 Safaricom branded modem which does require APN.

cheers,
Mark

---

### Post by Sabonmu on 2010-02-17
> **chitragurung said:**
> I was using above device to connect internet when I was using windows. In my new Dell Inspiron mini I have Ubuntu. Now I want to use same device to connect internet. How can I install driver and set it up ?

Hi, I'm also trying the G-Link CDMA modem ([www.imshkg.com](www.imshkg.com)) with  Linux Helena Mint and so far no joy.
I've tried downloading the latest Wine and the Windows driver but no luck.
I've got an Asus S101 with 16Gb SSD and Windows hogging 6Gb just for this driver so want to get rid.
Any advice will be much appreciated.
Sabonmu

---

### Post by Danxo on 2012-01-12
one way i would recommend is using wvdial which works well if you know some basic commands, another good way to do is to use the gnome-ppp dial tool. i would mostly recommend the latter. For more details you can reach Danson on his business email: [email]danmwaka@yahoo.com[/email]

---

