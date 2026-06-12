---
title: "Zoom 3095 Not connecting"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Malcolm Waterman on 2010-07-21
Hello, I'm using Ubuntu 10.04 with wvdial and Gnome PPP, but I am unable to connect to the internet with my Zoom 3095 USB Modem. I tried several times and got similar results. I have got the connection log attached along with all of the mentions of pppd and all other lines in the file /var/log/messages from the first mention of pppd to the end of the file.

---

### Post by alexfish on 2010-07-21
did you do a fresh install of ubuntu or did you upgrade

---

### Post by Malcolm Waterman on 2010-07-22
I believe it was a fresh install. I got a nearby PC store to add a second hdd and install Ubuntu onto that new hdd.

---

### Post by alexfish on 2010-07-22
Hi
 

 have a look here
 

 [http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
 

 see post #6  by George Vita
 Ubuntu **10.04** includes **wvdial** and dependencies but are NOT installed!
To install them read [wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790")
 

  you could also try ppp :
 

 also can you post  details of the wvdial.conf for your provider, here

---

### Post by Malcolm Waterman on 2010-07-23
I'm not sure if you understood. I've got Gnome PPP and wvdial installed. I downloaded them from the Ubuntu repositories and they're apparently installed fine. Though my Zoom USB modem won't connect.

---

### Post by pdc on 2010-07-24
I notice in your logs

> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: *Could not modify /etc/ppp/chap-secrets*: **Permission denied**
--> --> CHAP (Challenge Handshake) may be flaky.

Peter Curtis is very knowledgable on this

[http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets](http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets)

see if what he writes helps you;

I would suspect if you can remove the above error message, things may flow more smoothly for you

---

### Post by pdc on 2010-07-24
how is coming along out there Malcolm?

What Peter was suggesting is open a terminal and copy and paste into it

> gksudo nautilus

that opens nautilus, which allows you to see the folders on your system

....... that gives you root powers ..

You then navigate to folder /etc/ppp 

and **right click** on pap-secrets -> Properties -> Permissions tab 

then select **dip** from the drop down menu for Group 

and then select read and write under Access. 

Repeat for chap-secrets. 

Peter says "*The annoying warning messages should now disappear*."

Is this any help?

this comes from here

[http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets](http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets)

---

### Post by Malcolm Waterman on 2010-07-26
Unfortunately, it doesn't seem to have worked. Perhaps if I could contact Peter Curtis directly or if he could look at this feed, he might know something you don't?  
 
:confused:Although, I didn't get any annoying warning messages when I was following the instructions ??:confused:

Though, I do have some additional information about my modem to add which may or may not help. I got the information from the windows based modem information called LstMdm and also from the Linux scanModem tools.

---

### Post by Malcolm Waterman on 2010-07-26
Computer didn't manage to add attachment. The relevant part of attachment is pasted below:
=====================================================================
=              RESULT OF MODEM QUERY                                =
=====================================================================
NUMBER OF MODEMS FOUND = 1

MODEM #1:
  PCI CONFIGURATION INFORMATION READ:
     VENDOR ID              : 14F1
     DEVICE ID              : 2F30
     SUBVENDOR ID           : 14F1
     SUBDEVICE ID           : 2003
     REVISION ID            : 01

  DEDUCED INFORMATION:
     VENDOR NAME            : CONEXANT
     DEVICE NAME            : UNKNOWN
     SUBVENDOR NAME         : ACTIONTEC                   -- [HTTP://WWW.ACTIONTEC.COM/](HTTP://WWW.ACTIONTEC.COM/)
     MODEM TYPE             : HSF
     WINXP INBUILD SUPPORT  : NO

---

### Post by Malcolm Waterman on 2010-07-30
I've tried installing the deb from the archive from this site: [http://www.linuxant.com/drivers/dgc/archive/dgcmodem-1.13/dgcmodem_1.13_k2.6.31_17_generic_ubuntu_i386.deb.zip](http://www.linuxant.com/drivers/dgc/archive/dgcmodem-1.13/dgcmodem_1.13_k2.6.31_17_generic_ubuntu_i386.deb.zip), but it doesn't appear to have helped. I'm also going to put this additional information from my latest attempt to get the internet to work. During this attempt, I used the additional software from the link above and I also used a different ISP. The different ISP seems to have been a big factor in the success of this attempt. The log information is attached

---

### Post by Malcolm Waterman on 2010-08-13
I've tried installing the gnome-network-admin package which was suggested in Ubuntu's official documentation on this URL: 
[https://help.ubuntu.com/10.04/internet/C/modem-connect.html](https://help.ubuntu.com/10.04/internet/C/modem-connect.html). That hasn't made the problem go away, though I have noticed that the internet seems to connect for a few seconds during which I can tell Synaptic Package Manager or Update Manager to download up to date information and it can then download up to file 9 at which point it says it can't find any more files. The symbol indicating that the internet is connected remains for several more seconds before ending. There is also some changes in the logs I've uploaded. I'm going to upload the new versions.
 
I did notice that in the var/log/messages file I did see this line
*"Warning - secret file /etc/ppp/pap-secrets has world and/or group access"*
Do I need to change the access settings again? I'll check that they were correctly reset according to what My Curtis said.

---

### Post by alexfish on 2010-08-13
hi

best  I can suggest is to look at the /etc/ppp/options using gedit 

search and find with gedit  lcp look at the options available

if you need to alter the settings

make a backup of the file then

Code:

sudo gedit /etc/ppp/options

---

### Post by Malcolm Waterman on 2010-08-14
Thanks for all of your assistance and effort. I seem to have sorted it out, with some help from you lot. So thanks.
Now, for the zoom 3095, you need to install the software on the URL below (I think, I've got it installed at least:) 
[http://www.zoom.com/files/dial_up/3095_Linux-x86-106.zip](http://www.zoom.com/files/dial_up/3095_Linux-x86-106.zip)
It will download a zip archive. To install just:

[LIST=1]
[*]Extract the archive
[*]Plug in the USB Modem
[*]Go to the debian folder and install
[/LIST]
If you're using a different model to the Zoom 3095 USB, then try the manufacturer's website.

You will also need to install Gnome PPP and wvdial. Gnome PPP will appear in the Applications menu under Internet. To install Gnome PPP without a internet connection you need to (modified this can be used for any other package):

[LIST=1]
[*]Open up the Synaptic PackageManager
[*]Search for Gnome PPP
[*]Mark "gnome-ppp" for installation. It will probably ask you to confirm several dependencies.
[*]Go to File -> Generate Download Script. Then save it somewhere.
[*]This script will work with Ubuntu and potentially other versions of Linux. Though, it will not work straight away with Windows. To download in Windows all that you have to do is open the file and locate the URLs (it's actually easier to make a list before and save it using Windows line ending and a txt extension)
[*]Go to the Linux computer with the downloads on a memory stick or similar and either install by double clicking on the file names or open terminal and enter in:
[/LIST]
[CENTER][SIZE=1]sudo spkg -i[/SIZE] PACKAGE NAME
[/CENTER]
             for each package
Then just:

[LIST=1]
[*]Open Gnome PPP (Applications -> Internet -> GNOME PPP
[*]Go to Seup
[*]Make sure modem is plugged in
[*]Click detect. It should register you're modem.
[*]Make sure that the following settings are set like this
[/LIST]

[LIST]
[*]The Type setting under Modem is as it was set by Gnome
[*]"Ignore Terminal strings (stupid mode)" is ticked (that was the main thing stopping me before)
[/LIST]
These are my other settings:
"Wait for dial tone" under Modem -> Phone options is not ticked
Networking area is left alone
Options:

[LIST=1]
[*]"Minimize" is unticked
[*]"Dock in notification area" is unticked
[*]"Auto reconnect" is unticked
[*]"Abort connecting if line is bust" is ticked
[*]"Abort connecting if no dial tone" is ticked
[*]"Check carrier line" is ticked
[*]"Check default route" is ticked
[*]"Send custom reply" is unticked
[*]Idle time is 0
[/LIST]
Those settings are what I've got set up. For other opinions see the rest of this thread and any other sources you can find



Thank you again and good luck for anyone who's trying this method

---

### Post by alexfish on 2010-08-15
hi

great news , looking good 

I had a look at some of the info in the 3095 files

The Read Me file list the following devices

This package contains Linux drivers for Conexant USB hardware modems
with a software Digital Call Progress interface.
The latest version and related information are available
at [http://www.linuxant.com](http://www.linuxant.com) on the web.

This driver officially requires a 2.6.19 or newer kernel. It might work under
some older versions but various issues may be encountered.

The following modem devices are recognized by the driver:

    USB ID 0572:1320
    USB ID 0572:1321
    USB ID 0572:1322
    USB ID 0572:1323
    USB ID 0572:1324
    USB ID 0572:1328
    USB ID 0572:1329
    USB ID 0572:1340
    USB ID 0803:3095

Many vendors have shipped modems based on Conexant modem chipsets.
If you have a modem based on the same chipset but with different device IDs,
please contact [EMAIL="modem.support@linuxant.com"]modem.support@linuxant.com[/EMAIL]. If supported, your device could
be added to the list and automatically recognized in future versions of this
driver.

See the INSTALL file for installation instructions.

Bug reports are welcome. (see section "REPORTING PROBLEMS" in INSTALL file)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
End of read me

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
to find usb ID's open up a terminal 

Code:

lsusb

to find usage of lsusb

man lsusb


regards

alexfish

---

