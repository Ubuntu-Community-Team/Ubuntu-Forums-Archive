---
title: "Dial up Modem is not detected !!!!!"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by arjun2504 on 2010-01-01
[I]I use ubuntu 9.10 and PCI connected Conexant CX11252 Modem.
My GNOME PPP doesn't detects my modem. How can I create a connection? Is there any way to detect my modem and connect ? or ubuntu is fit only for broadband? I think most of the activities in ubuntu depends on internet. I can't do any work. Please reply more suitable result.I am losing my money in Internet Cafe. Broadband is even not available in my resident area. Therefore. please find me a solution to connect internet via my dial up modem !!
:(:(:(
[/I]

---

### Post by ubuncha on 2010-01-07
I'd like to bump this post...
I also live in an area in which I can only recieve connection to the net via 56k dial-up.
  I have ubuntu installed on another computer and was trying to find where my modem was listed so I could get the details of it for this post, I couldn't find it listed, does ubuntu support dial-up modems? 
Thanks.

---

### Post by alexfish on 2010-01-08
hi

the only info I have on these devices is here : it may help until someone sees your post

[http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html)

[http://forums.windrivers.com/showthread.php?t=78402](http://forums.windrivers.com/showthread.php?t=78402)

[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)

[SIZE=2][COLOR=Blue][Conexant Soft Modems]("http://www.pcurtis.com/ubuntu-mobile.htm#softmodem")

please read  carefully  and take note of how these devices connect ; it also provides   links to other sites and how to avoid problems 

 also the rest of the page is worth reading

[COLOR=Black]alexfish[/COLOR]
[/COLOR][/SIZE]

---

### Post by Adi100 on 2010-01-08
hi ubuncha,
Dial up modems are not detected in UBUNTU. however there is a complete description on How to for Dial up modems in Official UBUNTU documention. please refer to them.
 
Adi

---

### Post by ubuncha on 2010-01-08
Thanks guys for the replies. 

The above links refer to Conexant/Rockwell modems, I'm not even sure if this is the type of my device, as I have already wiped windows of my system and cannot check devices that way, I also can't find the documentation of my laptop either (argh!).

This may be a silly question, but what the heck!

Where can I find the official Ubuntu documentation??? (I have downloaded the pocketguide, but there is no mention of dial-up.)

Thanks.

---

### Post by ubuncha on 2010-01-08
Ah yes! found it!

[http://ubuntuforums.org/archive/index.php/t-493780.html](http://ubuntuforums.org/archive/index.php/t-493780.html)

The joys of google.

---

### Post by AFarris01 on 2010-01-09
Actually... a better link to follow would be here:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

or more generally: [https://help.ubuntu.com/](https://help.ubuntu.com/)

I've followed that walk through before to set up a dial-up connection for a friend who doesn't have broadband available out where he's at.... Unfortunately, it does require the internet to set up properly....and at current time, the only built-in ubuntu tool for configuring Dial-up appears to have been removed. In it's stead, I've used gnome-ppp where necessary, and I've been very happy with it.

Good luck!

---

### Post by ubuncha on 2010-01-09
Thanks very much for the help ppl, I think from the looks of this link I should be on my way! :)

---

### Post by Bartender on 2010-01-09
OpenSUSE and Puppy provide far better modem support than Ubuntu.

As a long-time dial-up user, the best course of action IMO:

#1  Make sure you have an ISP that uses no proprietary software.  Juno, PeoplePC, etc. are on the "Do Not Use" list.  Copper.net, frys.com, BasicISP and many others will work.

#2 Shop around for a used USR 5686 56K external serial modem.  If your PC has no serial port get a Sabrent USB-to-serial adapter cable or similar.  A serial external modem will be found on tty/S0 or tty/S1 (serial) or if using a serial-to-USB adapter it'll be tty/ACM0 or some sort of tty/usb variant.

#3 Ubuntu doesn't even come with wvdial installed anymore so you'll have to start out with pppconfig, get online, then download wvdial and gnomeppp if you want a GUI interface.

---

### Post by alexfish on 2010-01-11
> **Bartender said:**
> OpenSUSE and Puppy provide far better modem support than Ubuntu.

As a long-time dial-up user, the best course of action IMO:

#1  Make sure you have an ISP that uses no proprietary software.  Juno, PeoplePC, etc. are on the "Do Not Use" list.  Copper.net, frys.com, BasicISP and many others will work.

#2 Shop around for a used USR 5686 56K external serial modem.  If your PC has no serial port get a Sabrent USB-to-serial adapter cable or similar.  A serial external modem will be found on tty/S0 or tty/S1 (serial) or if using a serial-to-USB adapter it'll be tty/ACM0 or some sort of tty/usb variant.

#3 Ubuntu doesn't even come with wvdial installed anymore so you'll have to start out with pppconfig, get online, then download wvdial and gnomeppp if you want a GUI interface.

Hi

Nice to see these pointed out  Hope Canonical is reading These posts here

---

### Post by GeorgeVita on 2010-01-11
> **Bartender said:**
> ...As a long-time dial-up user, the best course of action IMO:
#2 Shop around for a used USR 5686 56K external serial modem.  If your PC has no serial port get a Sabrent USB-to-serial adapter cable or similar.  A serial external modem will be found on tty/S0 or tty/S1 (serial) or if using a serial-to-USB adapter it'll be tty/ACM0 or some sort of tty/usb variant.
#3 Ubuntu doesn't even come with wvdial installed anymore so you'll have to start out with pppconfig, get online, then download wvdial and gnomeppp if you want a GUI interface.

Just to hear the 'connection tones' I used my old **Zoom Modem V.92 Ext** (RS232) with a USB to RS232 adapter cable and got connected!

Total 6-7 minutes, 5 to unpack and connect psu and usb/rs232/telephone jacks. 1-2 minutes to configure gnome-ppp, >>> connected!
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: AT&F
AT&F
OK
--> Sending: ATX3
ATX3
OK
--> Modem initialized.
--> Sending: ATM1L3DT8012001010
--> Waiting for carrier.
ATM1L3DT8012001010
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jan 11 14:16:45 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 3677
--> Using interface ppp0
--> local  IP address 213.170.204.169
--> remote IP address 213.170.204.1
--> primary   DNS address 213.170.194.164
--> secondary DNS address 213.170.192.14

```

(Baudrate shown is for the USB adapter not the actual for the modem!)

Regards,
George

---

### Post by bkratz on 2010-01-11
Just saw this link!

[http://ubuntuforums.org/showthread.php?t=1377619](http://ubuntuforums.org/showthread.php?t=1377619)

---

### Post by Bartender on 2010-01-14
Hi, bkratz -
I'm glad to see someone spotted my latest endeavor.  I just don't see any way around it - dial-up is never going to be fun, but at least we can help each other to make it tolerable.

After reading hundreds of posts from people lost in the wilderness with their winmodems, I've come to the conclusion that for me and Linux, there is no better option than a USR serial external.  I'm not gonna waste my time with anything else.  The USR's are faster than anything I've ever tried in Windows, so it only makes sense to me that they'll be faster in Linux too once you have them set up correctly.

I know it's frustrating to be told you gotta go out and buy some funky old-school modem to get online that you didn't need in Windows, but AFAIK there's no better option that's going to "just work".  

It's frustrating for me to know that many people in other parts of the world can't go out and buy a USR external.

GeorgeVita knows more than me about this dial-up stuff, so when you see him post pay attention!  I've heard good things about the old Zoom modems that he mentions, so if a person comes across one of those for the right price I'd say grab it.

---

