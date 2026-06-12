---
title: "T-Mobile Web Connect USB Stick Huawei UMG181"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by jmurrayil on 2009-02-24
Does anyone know if the new T-Mobile Web Connect USB Stick, mobile broadband 3G device for laptops, a Huawei UMG181, (goes on sale in US on March 25, 2009) will be compatible with Ubuntu?

---

### Post by tevang on 2009-04-04
Good question. I've asked at a T-mobile store and after calling the technical support they told me that the current model is compatible only with Windows. They are working on resolving compatibility with Mac and Linux and they will launch that version soon. However I found the following interesting thread:

[http://news.cnet.com/t-mobile-debuts-webconnect-usb-laptop-stick/](http://news.cnet.com/t-mobile-debuts-webconnect-usb-laptop-stick/)

If someone has experience on broadband internet please reply.

---

### Post by djrakun on 2009-04-23
does not work with wine.  I got the software installed but it crashes on startup.  I installed msxml3 using winetricks as suggested by the wine community but at this point no avail.

you can track this bug by the following link.  if this is resolved i think you'll be able to use the webconnect stick

[http://bugs.winehq.org/show_bug.cgi?id=18084](http://bugs.winehq.org/show_bug.cgi?id=18084)

---

### Post by Fatman22 on 2009-06-15
Working Solution !
 
Ok, I have made some progress with this to the point by following this thread.
[http://ubuntuforums.org/archive/index.php/t-482420.html](http://ubuntuforums.org/archive/index.php/t-482420.html)
 
Which had me first open a terminal and do all kinds of fun..
 
 
 
1. "sudo gedit /etc/modprobe.d/blacklist
 
this opened up text editor where I put a comment
 
"#Disabling module for USB-dongle..." (hard return)
"module"
 
Save and close the file.
 
2. Got Data about the USB modem from the system via
 
Terminal --> "lsusb"
which will give a list of what is plugged into your usb ports.
Look for Huawei Tech and save the data on this line.
 
Mine replied
"BUS 001 Device 002: ID 12d1:1414 Huawei Technologies Co., Ltd."
 
12d1 is the Vendor ID.
1414 is the product ID. (You will need these shortly)
 
3. Use the modprobe & ls commands from a terminal window to see where the device was created on your system.
"modprobe usbserial vendor=12d1 product=0x1414" 
now type "ls -la /dev/ttyU*" 
 
BTW that "*" is supposed to be there!!!
 
You will get a list like this
 
crw-rw---- 1 root dialout 188, 0 2009-06-15 15:53: /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2009-06-15 15:53: /dev/ttyUSB1
etc
 
 
 
Finally we can edit wvdial.conf
 
4. "sudo gedit /etc/wvdial.conf"
 
This opens up the modem connection files.
Next I inserted # signs in front of all of the default dialing info in case I want to recover it later.
 
;Note - i am not sure if this is the correct speed )-:
 
I then created new Dialer Defaults:
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","internet2.voicestream.com".
 
Now part of this came from [http://ubuntuforums.org/showthread.php?t=1119373](http://ubuntuforums.org/showthread.php?t=1119373)
but this works!
 
 
Now, honestly, looking through the thread linked to above, it seems I may have some extra uneccessary steps in my method, and my personal Init2 & Init3 use different options but I wanted to you all a prefered method rather than random config.
 
Enjoy!
 
Edit: There may be some room for play in the baud settings so you can experiment there.
Also; it should be noted that you have to open a terminal window and type "sudo wvdial" to get this working.
Sites other than "internet2.voicestream.com"

---

### Post by djrakun on 2009-06-16
"#Disabling module for USB-dongle..." (hard return)
"module"
 

Sorry, but what exactly did you put in for the "module"?  From what I understand, the syntax in the blacklist file is usually the word 'blacklist' followed by the driver name, for example

```
blacklist de4x5
```

do you happen to know what module name to put in this line? just a hunch based on what i got from lshw -C storage

```
blacklist usb-storage
```

the modprobe command works when this is blacklisted however there are no directories named /dev/ttyU

---

### Post by djrakun on 2009-06-24
FWIW, I found this link that seems like an easy solution as well

[http://www.spsc.tugraz.at/people/alumni/marian-kepesi/t-mobile-webnwalk-on-ubuntu-using-the-huaewi-e220-hsdpa-3g-umts-modem/](http://www.spsc.tugraz.at/people/alumni/marian-kepesi/t-mobile-webnwalk-on-ubuntu-using-the-huaewi-e220-hsdpa-3g-umts-modem/)

It seems like I have a very fundamental problem:  /dev/ttyUSB0 does not get created by my OS when I insert the usb device.  In fact, there are no ttyUSB* modules at all.  I created /dev/ttyUSB0 manually but probably no surprise that a blank document with that name is not sufficient.

i see a few bugs in launchpad ( 386251 and 435266 ) that appear verry related, but I'm not even at the stage where I'm putting the AT commands into the wvdialer.conf.  Maybe it is just a different way of describing the same thing, but if so this dates back to Hardy Heron because that's what i'm running on this particular pc.  The bug reports are in Intrepid and Jaunty

---

### Post by djrakun on 2009-06-24
i created a ttyUSB0 and 1 using mknod

```

mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB1 c 188 1

```

although i probably only need USB0.  I can complete your walkthrough with this step however wvdial barfs trying to upen ttyUSB0

--> Cannot open /dev/ttyUSB0: No such device

---

### Post by djrakun on 2009-07-02
jmurrayil, use the thread tools to mark this thread as 'solved' unless you dont think this issue is closed.  Thanks!

---

### Post by Fatman22 on 2009-07-04
My revised wvdial.conf file

[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Phone = *99*#
Stupid Mode = 1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","internet2.voicestream.com"
New PPPD = yes



#[OLD Dialer Defaults]
#Phone = 
#Username = 
#Password = 
#New PPPD = yes
#Baud = 115200

I have found that the faster setting of 460800 for baud works very well. PDQ even with TOR (-:

---

### Post by petrockthief on 2009-10-25
Thanks FM I really appreciate this thread. I just seem to be stuck on something here for the last bit of it.

I'm using Kubuntu and I just started up again after four years and I need to know what to put in lieau of

Modem = /dev/ttyUSB0


I'm told that that device cannot be found. So I tried:

/dev/bus/usb/001/001


********. So where do I look? Otherwise T-Mobile has been like a gift from God! If only to get it to run on my Kubuntu 6.06 D computer.

---

### Post by twright on 2009-10-26
> **petrockthief said:**
> Thanks FM I really appreciate this thread. I just seem to be stuck on something here for the last bit of it.

I'm using Kubuntu and I just started up again after four years and I need to know what to put in lieau of

Modem = /dev/ttyUSB0


I'm told that that device cannot be found. So I tried:

/dev/bus/usb/001/001


********. So where do I look? Otherwise T-Mobile has been like a gift from God! If only to get it to run on my Kubuntu 6.06 D computer.
Are you sure you are running Kubuntu 6.06, if you are running something this old I recommend you try upgrading to something newer. I know that Ubuntu Karmic now works out of the box for most mobile broadband though I am not sure about kubuntu.

anyway, you could try lsdev to find valid devices.

---

### Post by HeavyHaulTrucker on 2009-12-23
**[SIZE=2]Making The T-Mobile UMG181 WebConnect Laptop Stick Work In Linux[/SIZE]**

I am running Ubuntu Linux v9.04 (Jaunty) and recently purchased this USB mobile broadband stick.  I sort of had my doubts about it working on my laptop since I was not running Windows.

My fears were un-warranted.  I figured that I had 14 days to make it work or I would just send it back and cancel the service.  Actually, it took me only 15 minutes to have it up and running -- in fact, I am using it as I write this!  So I figured that I would post some instructions for those of you who need to get it running on your Linux box.

First of all, you have to realize that this stick is manufactured for T-Mobile (and others) by Huawei Technologies Co., Ltd. -- and there is a little bit of info on the web.  Unfortunately, the instructions I have seen make the task of getting it to work seem much too complicated -- I was able to do the same job with just 3 or 4 terminal commands and a couple of minor file edits.

First, insert your Laptop Stick into an open USB port.  Then open a terminal window and type the command:[INDENT] "lsusb"
[/INDENT]this will give you an output something like this:[INDENT]Bus 001 Device 003: ID 12d1:1414 Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/INDENT]Now, in the same terminal window, type the command:[INDENT]"modprobe usbserial vendor=0x12d1 product=0x1414".
[/INDENT]Next, type the command "ls -la /dev/ttyU*" and make sure that you put the * at the end or you won't get the right info.  You will get a response something like this:[INDENT]crw-rw---- 1 root dialout 188, 0 2009-12-23 18:17 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2009-12-23 18:17 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2009-12-23 18:17 /dev/ttyUSB2
crw-rw---- 1 root dialout 188, 3 2009-12-23 18:17 /dev/ttyUSB3
[/INDENT][SIZE=1]**** Making sure it works every time you re-boot:**[/SIZE]

In a terminal window, issue the command:[INDENT]"sudo gedit /etc/modules"
[/INDENT]When GEdit has opened the file, simply add the line[INDENT]"usbserial vendor=0x12d1 product=0x1414"
[/INDENT]to the file and save it.  Now, every time you boot up, the same 4 usb ports will be allocated & assigned and your Laptop Stick will be there like it should.

[SIZE=1]****Configuration For Different Connection Methods:**[/SIZE]

_**WVDIAL:**_

Now that you have all the basic information that you need, you can edit your /etc/wvdial.conf file as shown, adding the following block of code to it:[INDENT][T-Mobile]
Modem = /dev/ttyUSB0  # Adjust this for your particular port
Modem Type = Analog Modem
ISDN = 0
Baud = 7200000
Username = voicestream
Password = voicestream
Phone = *99#
Stupid Mode = 0
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","epc.tmobile.com"
[/INDENT]Save & close the /etc/wvdial.conf file.  If you did everything correctly, you can issue the command "wvdial T-Mobile" in the terminal window and you should get connected lickety-split.

_**GNOMEPPP:**_

You can also use the GnomePPP GUI to do the dialing (I do), simply use the info from your /etc/wvdial.conf file to set it up to dial.

_**GNOME NETWORK MANAGER APPLET:**_

If you would like to use the Ubuntu "NetworkManager" applet, edit your /etc/wvdial.conf file as shown above then simply set up a Mobile Broadband connection named "T-Mobile" using the same information you used for the /etc/wvdial.conf file.  ***Note:** Make sure that you disable all authentication in the "PPP Settings" tab or it will not connect.*

---

### Post by AndyP79 on 2009-12-24
Threads from the deep! It's been awhile since I saw this. 

I am not sure about Ubuntu, but in Linux Mint 7 and 8, this USB works great. All you do, it plug it in and choose. It is automatically recognized. At least on my computer it was. When I originally asked about this, it was not too long before the next release came out, and when I loaded it, viola! It just worked. I did not have to do any configureation. I just choose the broadband in the network and chose T-Mobile Internet, and bada-bing! 

Good Luck, and glad to hear someone alse is using the same things as me.

Merry Christmas and Happy New Year!

---

### Post by ieee488 on 2010-05-09
> **jmurrayil said:**
> Does anyone know if the new T-Mobile Web Connect USB Stick, mobile broadband 3G device for laptops, a Huawei UMG181, (goes on sale in US on March 25, 2009) will be compatible with Ubuntu?

**Once you follow HeavyHaulTrucker's steps...**

Go to the Gnome Network Manager Applet.
Choose Mobile Broadband.
Click on Add.
Choose Huawei.
Choose USA.
Choose T-Mobile.
Choose Internet for the plan.
Leave everything else at default.
Change APN to epc.tmobile.com

---

### Post by Nick_Jinn on 2010-07-07
> **AndyP79 said:**
> Threads from the deep! It's been awhile since I saw this. 

I am not sure about Ubuntu, but in Linux Mint 7 and 8, this USB works great. All you do, it plug it in and choose. It is automatically recognized. At least on my computer it was. When I originally asked about this, it was not too long before the next release came out, and when I loaded it, viola! It just worked. I did not have to do any configureation. I just choose the broadband in the network and chose T-Mobile Internet, and bada-bing! 

Good Luck, and glad to hear someone alse is using the same things as me.

Merry Christmas and Happy New Year!


Awesome...I was hesitant to buy one after reading that people had problems, but I am going to go ahead and get it now.

---

### Post by ieee488 on 2010-07-07
I have found that it helps to have the device plugged in before turning on the PC.

---

