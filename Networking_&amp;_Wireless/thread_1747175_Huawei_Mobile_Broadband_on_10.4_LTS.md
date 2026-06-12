---
title: "Huawei Mobile Broadband on 10.4 LTS"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by SLIREAND on 2011-05-02
I am new to Linux. I have recently installed the Ubuntu 11.4 LTS Distro that comes with the Haynes Linux Manual (which I heartily recommend to new users).

     For the Internet I have a Huawei E1550 dongle on the 3 network in the UK which I'm currently using with Windows XP on my desktop to post this thread.

     After some initial fumbling, I'm unable to use the dongle with Ubuntu.

     Can any fellow user advise me with the installation?

     Many thanks in advance of your replies.

---

### Post by IPEX-731BA5DD06 on 2011-05-02
I've got the same provider and mobile brand, but in Australia.

Basically similar procedure.

Right click on the wireless icon in the top right hand corner, it'll open up a page with selections. Choose edit connections.

5 tab selection opens up, choose mobile broadband.

Now you either have a selection for mobile, choose edit for that, or add new service.

follow through the selections, ie country, provider, plan, and it should connect.

This is assuming that you have service to connect too. (huge problem in Australia, with 3 and Vodafone merging) 

It should automatically connect now. Choose the options, connect automatically, etc and it'll just load up on booting assuming you have service.

P.S. don't worry about the tag that say's "never used", I use mine every day, and it still says that

---

### Post by SLIREAND on 2011-05-03
Thank you, IPEX-731BA5DD06, for your response.

This follows the advice given in the Haynes Manual. Unfortunately, the dongle is still not recognised and I am still at a loss as to how to proceed.

Have you any further suggestions?

Thanks again.

---

### Post by alexfish on 2011-05-05
Hi

just to note
> **Huawei Mobile Broadband on [COLOR=Blue]10.4 LTS[/COLOR]**I am new to Linux. I have recently installed the Ubuntu [COLOR=Blue]11.4 LTS[/COLOR] Distro can confirm which version installed.

can open up a terminal 
if ubuntu 11.04 can log in (classic) if can't find the terminal in unity menus ( I have not found this a problem, but some have.
post results of this command
```
usb-devices
```

---

### Post by SLIREAND on 2011-05-07
Thank you, Alexfish.

I've used the command but it is not recognised.

Following the Haynes Manual, I've used the command "dmesg" after inserting the dongle and I attach a Screenshot of the result.

Will this be of service?

I look forward to your reply,

Regards, Slireand[ATTACH]

191458[/ATTACH]

---

### Post by alexfish on 2011-05-07
not sure why usb-devices command not working ( missing)

can post results of 
```
uname -r
```the "dmesg" command its fine if looking for a switched modem 
but need to know the ID's of the device
also notice there is a cd rom mounting on the system sr1
open up first terminal and enter this code ( this will minitor the syslog in real time)
```
tail -f /var/log/syslog 
```open up a second terminal
Now connect the device and wait till the device settles list the device ID's with
```
lsusb
```post the results
can try ejecting the device with
```
eject sr1
```check to see if the device ids have changed with the lsusb command ( not all huawei change there id's)
if the modem has switch then you will see it in the messages from the syslog 
post results of the syslog

if the modem has not registered then will post further on what to do

can you confirm this device works in windows or another OS ,not sure what the last line means (dead device)

---

### Post by SLIREAND on 2011-05-09
Thanks, alexfish. 

I attach four screenshots showing the results of the commands that you suggested.

The following may be of use:-

1.  I am using the dongle with Windows XP on my desktop to make this post.

2.  The dongle has a 2GB Mocro SD card installed.

3.  The Haynes Manual that I'm using contains 8 commands but only the "dmesg" command is recognised.

4.  I've looked at the root directory and there is no "syslog" folder under /var/log.

I hope that this further information will be useful.

Regards, Slireand[ATTACH]191643[/ATTACH]

[ATTACH]191641[/ATTACH]

[ATTACH]191642[/ATTACH]

[ATTACH]191640[/ATTACH]

---

### Post by alexfish on 2011-05-09
Hi

from the info uname -r , system looks like 10.04 , part of op indicates 11.04 

can see from the info your making typo errors

anyhow from the rest of the info

noted from the lsusb id's shows this device needs usb_modeswitch ( a program for switching the device from cd storage to modem mode) , this program is not installed at default on 10.04 , but are in Ubuntu 11.04 and 10.10 
so may run out of the box in the two later versions of Ubuntu

here are your options

can download these two files usb_modeswitch and usbmodeswitch data (put them an a usb stick)
[http://packages.debian.org/sid/i386/usb-modeswitch/download](http://packages.debian.org/sid/i386/usb-modeswitch/download)
[http://packages.debian.org/sid/all/usb-modeswitch-data/download](http://packages.debian.org/sid/all/usb-modeswitch-data/download)
then when in Ubuntu clicking on the files will automatically start the installer , install both files , then reboot the computer and connect the device , see what happens


if your fairly new to Ubuntu can suggest downloading latest Ubuntu 11.04, hopefully your device may work out of the box
the desktop is more akin to latest desktops, you may feel more at ease , you can only try

if your only method of network connection is via windows then can download Ubuntu in windows and put onto a usbstick
via this program

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

if you need further assistance with any of the above feel free to post

regards

alexfish

---

### Post by SLIREAND on 2011-05-10
Dear alexfish.

I've followed your advice and installed Ubuntu 11.4 as directed.

I'm delighted to tell you that the dongle has been recognised in this distro and I'm using it to make this post.

May I once more extend my heartfelt gratitude for your help in resolving this.

Kindest regards, Slireand.

---

