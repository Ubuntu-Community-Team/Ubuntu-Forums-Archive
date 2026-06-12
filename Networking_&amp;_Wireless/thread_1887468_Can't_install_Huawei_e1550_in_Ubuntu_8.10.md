---
title: "Can't install Huawei e1550 in Ubuntu 8.10"
date: 2011-11-27
forum: Networking &amp; Wireless
---

### Post by moossa on 2011-11-27
hi, am a newbie into Ubuntu world, just installed ubuntu 8.10 yesterday.
My problem is, i can't connect to internet using my huawei e1550 usb stick. It works fine with xp and vista.
I searched all over the net (i believe so) for a easy-to-follow guide. Sad to say, i couldn't find any. I tried lots of codes from here and there. Nothing works. 
Huawei usb stick is showing as a storage device, i can see the files in there.
When i used 'sudo wvdial', it shows as,
WvDial:  Internet dialer version 1.60
Cannot open /dev/ttyUSB2: no such file or directory.
Cannot open /dev/ttyUSB2: No such file or directory
Cannot open /dev/ttyUSB2: No such file or directory.

Don't know why it repeated 3 times.

Can anyone give me an easy guide for installing huawei e1550 for me.

Note: i don't have any other way to use internet from my PC, right now am with mobile.

Hope someone will help.

Thanks in advance

---

### Post by T.exe on 2011-11-27
Have you put the correct VendorID and ProductID for your device in the wvdial configuration file?

I am running an Olive VME101 via wvdial in 11.10

---

### Post by moossa on 2011-11-27
> **T.exe said:**
> Have you put the correct VendorID and ProductID for your device in the wvdial configuration file?

I am running an Olive VME101 via wvdial in 11.10

Thanks for the reply,
But am really zero in Ubuntu. can you please give me the code to add product & vendor id.
I know my product & vendor id by using lsusb.
I want to know how&where to add these ids into conf file.

thanks

---

### Post by T.exe on 2011-11-27
Sorry for the bad interpretation.. i regret my bad english, I wanted to know if you know your ProductID and VendorID. Since i had to load modules for my device into the kernel before making a dial using wvdial.

But, my way might not work for your device.

[http://ubuntuforums.org/showthread.php?t=1193355&page=4](http://ubuntuforums.org/showthread.php?t=1193355&page=4)

Check page 4, there is a working solution to connect your e1550 in 8.10

---

### Post by T.exe on 2011-11-27
This is as far as i can help mate! Hope it works! I am a newbie too...

---

### Post by moossa on 2011-11-27
> **T.exe said:**
> Sorry for the bad interpretation.. i regret my bad english, I wanted to know if you know your ProductID and VendorID. Since i had to load modules for my device into the kernel before making a dial using wvdial.

But, my way might not work for your device.

[http://ubuntuforums.org/showthread.php?t=1193355&page=4](http://ubuntuforums.org/showthread.php?t=1193355&page=4)

Check page 4, there is a working solution to connect your e1550 in 8.10

I checked that page, but do you know how to check whether usb-modeswitch is in my pc or not?

Thanks

---

### Post by T.exe on 2011-11-27
_Type in the terminal:_
**man usb_modeswitch**

If a usb_modeswitch manual page shows up in the terminal, then usb_modeswitch is installed in your system otherwise you have to install it. 

Or, type *usb_modeswitch* in synaptic. And check if the usb_modeswitch package that appears has a green tick/dot near it (then its installed).

If not installed then..

_Install it by typing:_
**sudo apt-get install usb-modeswitch**

You might consider upgrading your system to 10.04+ because 8.10 is no longer supported.

---

### Post by moossa on 2011-11-27
> **T.exe said:**
> _Type in the terminal:_
**man usb_modeswitch**

If a usb_modeswitch manual page shows up in the terminal, then usb_modeswitch is installed in your system otherwise you have to install it. 

Or, type *usb_modeswitch* in synaptic. And check if the usb_modeswitch package that appears has a green tick/dot near it (then its installed).

If not installed then..

_Install it by typing:_
**sudo apt-get install usb-modeswitch**

You might consider upgrading your system to 10.04+ because 8.10 is no longer supported.

i removed it and re-installed windows7, still, i would like to use it, but before i want to know these 2 things,

# how to use huawei e1550?

# is it possible to install photoshop in ubuntu? (using wine or any...) (btw, am a PSD to HTML coder)

i will go to an internet caffe tomorrow, and will download latest ubuntu (11.10) in my USB.

is the installation of huawei usb stick is different from in the latest one?

btw, i heard that internet connection is needed to install ubuntu 11.10. is it true?

guys, help me pls, i really wanted to use ubuntu.

hope i too can join the ubuntu family soon :)

thanks
-saeed

---

### Post by T.exe on 2011-11-28
You can perform offline installation of Ubuntu however for updating your system, internet connection is mandatory.

I am using my data card by modeswitching and it automatically gets detected in my 11.10 system.

For detailed information on running Photoshop in Wine, check this link:
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

Here are the applications supported by Wine (Do give it a read):
[URL="http://appdb.winehq.org/objectManager.php?sClass=category&iId=0&sAction=view&sTitle=Browse+Applications"]http://appdb.winehq.org/objectManager.php?sClass=category&iId=0&sAction=view&sTitle=Browse+Applications 
[/URL]

---

### Post by moossa on 2011-11-28
> **T.exe said:**
> You can perform offline installation of Ubuntu however for updating your system, internet connection is mandatory.

I am using my data card by modeswitching and it automatically gets detected in my 11.10 system.

For detailed information on running Photoshop in Wine, check this link:
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

Here are the applications supported by Wine (Do give it a read):
[URL="http://appdb.winehq.org/objectManager.php?sClass=category&iId=0&sAction=view&sTitle=Browse+Applications"]http://appdb.winehq.org/objectManager.php?sClass=category&iId=0&sAction=view&sTitle=Browse+Applications 
[/URL]

thanks for the links.

but i have a cracked copy of Photoshop, will it work in Ubuntu? that site says it will not work.

anyone tried it? 

i fear that i have to stick with windows :(

---

### Post by mörgæs on 2011-11-28
Before looking at applications you should get a working Ubuntu. 

There is a chance that 11.10 will work without internet access, but by far the best is to have wired internet while installing. Can't you move the computer to a place with access during installation?

---

### Post by moossa on 2011-12-01
> **mörgæs said:**
> Before looking at applications you should get a working Ubuntu. 

There is a chance that 11.10 will work without internet access, but by far the best is to have wired internet while installing. Can't you move the computer to a place with access during installation?

sorry for the late reply,

i don't have any way to use wired internet in my PC. all i have is a huawei e1550 with a little slow connection.

btw, i still couldn't find time to download the 11.10, am still playing with this (8.10). am re-installing it again, and can you give me an easy guide to use huawei e1550 in 8.10?

T.exe said i should have usb-modeswitch, i will install it. now, i want to know where to add my idvendor and idproduct ?

would be great if anyone can reply me within 10-15 mints.

(still with windows to use the internet)

thanks
-saeed

---

### Post by moossa on 2011-12-01
hi, i re-installed ubuntu (8.10) again.

and when i add "sudo apt-get install usb-modeswitch"
I got result like below,

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package usb-modeswitch

What is the problem here? and how do i get that usb-modeswitch in my pc?

Pls help

thanks for your efforts
-saeed

---

### Post by mörgæs on 2011-12-01
> **moossa said:**
> can you give me an easy guide to use huawei e1550 in 8.10?

No. I believe that it is anything but easy, if it is possible at all.

8.10 is three years old, and it is not worth the struggle to try to get the dongle running on such an old system. Might work in first attempt under 11.10.

---

### Post by moossa on 2011-12-01
> **mörgæs said:**
> 8.10 is three years old, and it is not worth the struggle to try to get the dongle running on such an old system. Might work in first attempt under 11.10.

OK, i will download the new version, and will test it.

thanks

---

### Post by moossa on 2011-12-14
ya, it worked. i just installed ubuntu 11.10, and it worked with ease.

thanks
-saeed

---

### Post by mörgæs on 2011-12-14
Good, then please mark the thread 'solved'.

---

