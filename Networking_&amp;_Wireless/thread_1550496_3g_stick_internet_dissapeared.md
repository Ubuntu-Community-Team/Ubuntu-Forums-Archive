---
title: "3g stick internet dissapeared?"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by ELD on 2010-08-11
After applying updates the other day my wireless 3g stick from 3 (UK) has dissapeared from my network list, if i edit connections it is listed but it doesn't list it in the panel so i can't connect to it?

It is working as i'm using it right now in Win7 but want to get it working again in ubuntu, odd for it to just dissapear.

---

### Post by dineshs on 2010-08-11
There is a chance that `Available to all users' is not ticked in the configured connection

---

### Post by ELD on 2010-08-11
That is ticked, it simply will not show up in the network list anymore so i can't connect to it :\

---

### Post by dineshs on 2010-08-11
I am not sure ,perhaps this link may help you
[http://ubuntuforums.org/showthread.php?t=1549395](http://ubuntuforums.org/showthread.php?t=1549395)

---

### Post by ELD on 2010-08-12
I can't use that as you have to add PPA's and download stuff, i don't have the net on Ubuntu without it.

It shows up in my connections manager when i go to edit connections, but it just won't show up in gnome panel list to connect to it anymore

---

### Post by alexfish on 2010-08-12
hi can you post the results of these codes from the terminal

Code:
dmesg | grep -e "modem" -e "tty"

Code:
ls -al /dev/serial/by-id/usb*

Code:
lsusb -t

---

### Post by ELD on 2010-08-12
Odd i actually tried to enter them manually and failed (copying from my phone by hand), booting into windows to copy them to a text file so i could just copy them properly...booted into Ubuntu again and my stick shows up and i'm typing from Ubuntu now.

---

### Post by alexfish on 2010-08-12
It may be windows leaving it in modem mode /

if it happens again can you post the results

regards alexfish

---

### Post by ELD on 2010-08-12
If it got left in modem mode why wouldn't it work as a modem under ubuntu?

---

### Post by alexfish on 2010-08-12
not absolutely sure but have seen post where they boot into windows first then into
Ubuntu , can only assume the auto mount cd is switched off , or it still thinks its connected to the system IE usb ports are always live

so on a cold boot to Ubuntu it will be set to auto cd

there is a way to disable this on some modems

also some devices when attached on cold boot will self configure and connect to the net 
you can check this in the system monitor look for pppd . when in this state modem manager can't see it , kill the pppd

this will leave 4 things to look at

1. is the device ID's . can list  with

Code:
lsusb -t 

this will list the device and the state of the drivers this will indicate 

2. find the port orientation 

Code:
[COLOR=Black]ls -al /dev/serial/by-id/usb*[/COLOR]

3. try to determine the state of the [COLOR=Blue][COLOR=Black]CTS,DCD and DSR lines[/COLOR][/COLOR]
 the only way I now of checking this is to install statserial
 if installed

usage 

Code:

statserial ttyX 

where X is the out put of the ttyports issued by the "[COLOR=Black]ls -al /dev/serial/by-id/usb*" command

4. the drivers are not loading for this you need to know if connection is 3g or cdma hso etc you will be able to get that from the "lsusb -t" command next time you are connected, make a note

to ensure the driver is loaded

Code:

sudo modprobe <driver>

posting the the listings when the device is not recognised will indicate as what to do next

if you can't install statserial it don't matter as an assumption could be made from the the other info , it just helps to confirm . but a handy tool for checking the modem status

[/COLOR][COLOR=Black]regards
alexfish[/COLOR]

---

### Post by ELD on 2010-08-13
Thanks for all the help, i'm getting the internet turned on Monday via Sky anyway so i will cope for the weekend :)

---

### Post by manish671 on 2011-12-16
I am new to Ubuntu and presently with 10.04. First time I connected the 3G stick it got configured very easily with Network manager, but latter-on it disappeared from Network Manager. I tried many things. “lsusb” indicates it’s product ID switched properly to 1404 but of no avail to me.

Presently I am using Mobile Partner for Linux 21.003.28.00.03. I found it best till date. It lacks USSD and voice call but gives option of sending and receiving message. Earlier I had downloaded Videotron package combining Windows-Mac-Linux in 52 MB but this does not have facility for sending the message.

However I have problem of speed. I am using 2G SIM with Huawei UMG1831 model. We know that mobile partner keeps on switching between WCDMA EDGE HSPA etc. I noticed that when it connects to HSPA, speed is good but when it switches to EDGE or WCDMA speed dies to zero.  Same switching happens in XP also but then it does not affect the speed.  I hope some one will come up with some solution.

When working with Network Manager Speed was good. If someone can give step by step procedure to connect with Network Manager, for a beginner it will be really helpful.

Manish

---

