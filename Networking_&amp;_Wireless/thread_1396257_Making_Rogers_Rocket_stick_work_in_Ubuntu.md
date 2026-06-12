---
title: "Making Rogers Rocket stick work in Ubuntu"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by mrpenguin on 2010-02-01
How do I get my Rogers Rocket stick to work in Ubunbtu ? 
Easiest possible way please ;)

---

### Post by hemimaniac on 2010-02-01
[http://ubuntuforums.org/showthread.php?t=1360327&page=2](http://ubuntuforums.org/showthread.php?t=1360327&page=2)

---

### Post by mrpenguin on 2010-02-05
Thanks for the link but none of that explains it properly for a complete newbie to linux .... 
Is there anything out there that explains it properly step by step of a proven way that is working ??

---

### Post by mrpenguin on 2010-02-07
I have been through the search on here and also google but cant find anything that has been accepted to work ... the one or two that claims to work is really bad do not explain how to make it work very well and are assuming everybody knows a lot about linux

---

### Post by mrpenguin on 2010-02-07
I have been through the search on here and also google but cant find anything that has been accepted to work ... the one or two that claims to work is really bad do not explain how to make it work very well and are assuming everybody knows a lot about linux

---

### Post by violatech on 2010-02-24
Hope this helps:

How to set up Rogers ZTE MF668 Rocket Mobile Internet Stick in Ubuntu 9.04

Overview.

There's a lot of helpful but confusing advice floating about (and of course none of it comes from Rogers) 
but after a lot of careful experimentation this may be the simplest effective solution.
 
The ZTE MF668 (Rogers' current offering) is a twofold device. In Windoze it presents as a USB CD drive and "auto"
installs the software from the small amount of built in memory. It then appears as a modem controlled by the Rogers software and as a USB microSD card if an optional
memory card is inserted in the stick. The same functions are available in Ubuntu, of course. The autorun function may or may not work. 
If it does (if you already have Wine running, for example) just cancel any attempt to install and unmount the "CD"  drive.

To be sure that the hardware is recognised type "lsusb" (without the quotes)  into a Terminal. (should give a result "19d2:2000")
That's just the hardware as a whole - remember it is a two part device; microSD and modem.
We need to sort out usb_modeswitch and patch a config file to accommodate our specific hardware.

Method:

Be sure you are running the latest kernel fully updated. This how-to works with 2.6.28-18-generic.

1. Plug in the Rocket Stick. In a terminal, type 

**lsusb**

One of the entries should read  19d2:2000 (this means that the Vendor code is (hex) 0x19d2 and the product ID from that vendor is (hex) 0x2000

You then know that the Rocket Stick is recognized. (However the target ID for the modem element is 0x0017 not 0x2000)

********************************

Choose approach a) or b) now.


2. a) Install usb_modeswitch. Get it here: [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

[Even if you opt for the b) option here I would recommend reading through this webpage for a good background to the issues involved.]

or

2. b) Download it from: [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way) 

[Read through all the directions and follow the process, from the linked pages, of adding source and key to your Software Sources repository). Using this  method avoids compiling from source by hand. (You will modify the mf627 config file in step 3] 

Notes: Check that you have done the following. 
Download and save the key file. 
Add the [deb [http://ppa.launchpad.net/liamgh/ppa/ubuntu](http://ppa.launchpad.net/liamgh/ppa/ubuntu) jaunty main] to Third Party Software Sources
Add the [deb-src [http://ppa.launchpad.net/liamgh/ppa/ubuntu](http://ppa.launchpad.net/liamgh/ppa/ubuntu) jaunty main] to Third Party Software Sources
Import the Key on the Authentication tab  
The sources will be updated

run **sudo apt-get install zte-mf627-switch** in a terminal.


3. a) In terminal, type **sudo gedit /etc/usb_modeswitch.conf**

This will bring up the editor.  Replace the contents of the file with the following (do not include the ----- ):  (this info is from [http://www.draisberghof.de/usb_modeswit](http://www.draisberghof.de/usb_modeswit) &#8230; =1895#1895 )

----------------
DefaultVendor=0x19d2
DefaultProduct=0x2000

TargetVendor=0x19d2
TargetProduct=0x0017

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
---------------

3. b) If you used the version from [www.greenhughes.com]("http://www.greenhughes.com"), in a terminal type 
**sudo gedit /etc/usb_modeswitch_zte_mf627.conf**

edit to look like this (my working config file)

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF
#
# Also applies to MF668 (Rogers Canada)

DefaultVendor=0x19d2
DefaultProduct=0x2000

TargetVendor=0x19d2
TargetProduct=0x0017

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"


4. (may not be necessary) Reboot with the Rocket Stick plugged in and it will appear in the Network Manager
Double check by typing in the terminal **lsusb** and you should see 19d2:0017

This means that the Rocket Stick is recognised as a modem.

TO CREATE A CONNECTION

If you have not yet created a profile connection:

Go to Network Manager
Edit Connections
Mobile Broadband
Add
Select Country: Canada
Select Provider: Rogers
and you're good to go. 

Having two Rogers Mobile Broadband connections in the Network Manager seems to be normal. If you end up with four, i.e. two sets of entries just connect and disconnect to and from the internet and delete the version that has not been used when you recheck the Network Manager settings for Mobile Broadband.


This process has been tested on two different MSI Wind U100s with Ubuntu 9.04. Connect and Disconnect appear to work correctly and simply. When the modem is unplugged it disappears as an option in the Network Manager

---

### Post by hanzj on 2010-06-21
violatech,
thanks for your helpful post.
it was what I used to guide me in making a Rogers Internet stick rocket USB work on my Ubuntu 10.04.

I made it work on Saturday, June 19, using the greenhughes files (option B in your post). When I first got it working, 

I installed zte-mf627-switch_0.2-1_all.deb (from greenhughes.com, I believe) and usb-modeswitch (version 1.1.0-2), and usb-mode-switch-data (version 20100127-1). Things worked on Saturday, June 19, and this morning (morning of Monday June 21). But this afternoon, it doesn't work anymore.


my lsusb currently has:

"Bus 001 Device 004: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA"

I think it should be 19d2:0017, according to your step 4.

When I click on the Network Connection Manager applet on the panel, I no longer see "Rogers Mobile Broadband" as an option.

Please help.

---

### Post by alexfish on 2010-06-22
Hi

There are two possibilities 

1. the usb_modeswitch is not required for this device so you try un-installing the modeswitch

2. also the usb_modeswitch is not the latest version checkout the below site : 

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by hanzj on 2010-06-22
I can try the newest version of usb-modeswitch, but is that the issue? With the older version of usb-modeswitch, I was able to make my Rogers stick work in ubuntu on day 1.

---

### Post by alexfish on 2010-06-22
Hi

If the Kernel is clean then most ZTE devices will work out of the box ,IE the recognition of some ZTE devices is built into the Kernel , if the modeswitch is installed then it has to be later version the the one supplied from the site mentioned , I could be proved wrong, but the latest usb_modeswitch overcomes the problem of switching some  ZTE device twice, the one done by the kernel , then the one done by the modeswitch , when this event occurs the ZTE device will reset , and only be recognised as the CD or mass storage device 

the ID's are

DefaultVendor=0x19d2
DefaultProduct=0x2000

the latest usb modeswitch package needs to be 1.1.2

Debian Packages are available here

 [    Debian Repository]("http://packages.debian.org/usb-modeswitch").

both usb_modeswitch and the usb modeswitch DATA pkg need to be installed

please read info and details at the site

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

regards

alexfish

---

### Post by mrpenguin on 2010-06-22
Holy crap that is confusing !!!

I dont understand why I all of a sudden need to be a linux super user to make this work if it was so damn easy in 9.10 ???


I dont understand any of the previous posts and even less what is one the modeswitch page :confused:

---

### Post by alexfish on 2010-06-23
> **mrpenguin said:**
> Holy crap that is confusing !!!

I dont understand why I all of a sudden need to be a linux super user to make this work if it was so damn easy in 9.10 ???


I dont understand any of the previous posts and even less what is one the modeswitch page :confused:

Hi

Yes it can be confusing , but a little reading and digesting what you read helps

as said some devices work out of the box and some require the Modeswitch

At the end of the day what is inside the device is a modem and in some cases a mass storage device that configures as a cdrom , the sofware on the cd is usually windows drivers , When in windows the user installs the software and makes the rules for the device and also installs the software to operate the device , also remember that each device has its own software to run it. With Linux this is not possible Since what you have is a Windows Compatible device.

for that please read the info a the site mentioned

also please have a look here

[How To : Mobile Broadband Connections  [  Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

also on these forum be aware of the type of language and terminology of your replies
it could result in offending other members who would normally be only to willing to help.

regards

alexfish

---

### Post by hanzj on 2010-06-23
I tried installing usb-modeswitch-1.1.2 by unpacking the tar.bz2, and then  "sudo make install". 

Here's the log:

gcc -o usb_modeswitch usb_modeswitch.c -Wall -l usb
usb_modeswitch.c:66:17: error: usb.h: No such file or directory
usb_modeswitch.c: In function â&#8364;&#732;mainâ&#8364;&#8482;:
usb_modeswitch.c:359: warning: implicit declaration of function â&#8364;&#732;usb_initâ&#8364;&#8482;
usb_modeswitch.c:362: warning: implicit declaration of function â&#8364;&#732;usb_set_debugâ&#8364;&#8482;
usb_modeswitch.c:364: warning: implicit declaration of function â&#8364;&#732;usb_find_bussesâ&#8364;&#8482;
usb_modeswitch.c:365: warning: implicit declaration of function â&#8364;&#732;usb_find_devicesâ&#8364;&#8482;
usb_modeswitch.c:408: error: dereferencing pointer to incomplete type
usb_modeswitch.c:409: error: dereferencing pointer to incomplete type
usb_modeswitch.c:411: warning: implicit declaration of function â&#8364;&#732;usb_openâ&#8364;&#8482;
usb_modeswitch.c:411: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:418: error: dereferencing pointer to incomplete type
usb_modeswitch.c:420: error: dereferencing pointer to incomplete type
usb_modeswitch.c:422: error: dereferencing pointer to incomplete type
usb_modeswitch.c:570: warning: implicit declaration of function â&#8364;&#732;usb_closeâ&#8364;&#8482;
usb_modeswitch.c: In function â&#8364;&#732;deviceDescriptionâ&#8364;&#8482;:
usb_modeswitch.c:584: error: dereferencing pointer to incomplete type
usb_modeswitch.c:585: warning: implicit declaration of function â&#8364;&#732;usb_get_string_simpleâ&#8364;&#8482;
usb_modeswitch.c:585: error: dereferencing pointer to incomplete type
usb_modeswitch.c:594: error: dereferencing pointer to incomplete type
usb_modeswitch.c:595: error: dereferencing pointer to incomplete type
usb_modeswitch.c:604: error: dereferencing pointer to incomplete type
usb_modeswitch.c:605: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function â&#8364;&#732;deviceInquireâ&#8364;&#8482;:
usb_modeswitch.c:637: warning: implicit declaration of function â&#8364;&#732;usb_claim_interfaceâ&#8364;&#8482;
usb_modeswitch.c:642: warning: implicit declaration of function â&#8364;&#732;usb_clear_haltâ&#8364;&#8482;
usb_modeswitch.c:644: warning: implicit declaration of function â&#8364;&#732;usb_bulk_writeâ&#8364;&#8482;
usb_modeswitch.c:650: warning: implicit declaration of function â&#8364;&#732;usb_bulk_readâ&#8364;&#8482;
usb_modeswitch.c:677: warning: implicit declaration of function â&#8364;&#732;usb_release_interfaceâ&#8364;&#8482;
usb_modeswitch.c: In function â&#8364;&#732;resetUSBâ&#8364;&#8482;:
usb_modeswitch.c:693: warning: implicit declaration of function â&#8364;&#732;sleepâ&#8364;&#8482;
usb_modeswitch.c:695: warning: implicit declaration of function â&#8364;&#732;usb_resetâ&#8364;&#8482;
usb_modeswitch.c: In function â&#8364;&#732;switchConfigurationâ&#8364;&#8482;:
usb_modeswitch.c:761: warning: implicit declaration of function â&#8364;&#732;usb_set_configurationâ&#8364;&#8482;
usb_modeswitch.c: In function â&#8364;&#732;switchAltSettingâ&#8364;&#8482;:
usb_modeswitch.c:777: warning: implicit declaration of function â&#8364;&#732;usb_set_altinterfaceâ&#8364;&#8482;
usb_modeswitch.c: In function â&#8364;&#732;switchHuaweiModeâ&#8364;&#8482;:
usb_modeswitch.c:794: warning: implicit declaration of function â&#8364;&#732;usb_control_msgâ&#8364;&#8482;
usb_modeswitch.c:794: error: â&#8364;&#732;USB_TYPE_STANDARDâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:794: error: (Each undeclared identifier is reported only once
usb_modeswitch.c:794: error: for each function it appears in.)
usb_modeswitch.c:794: error: â&#8364;&#732;USB_RECIP_DEVICEâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:794: error: â&#8364;&#732;USB_REQ_SET_FEATUREâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c: In function â&#8364;&#732;switchSonyModeâ&#8364;&#8482;:
usb_modeswitch.c:880: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c: In function â&#8364;&#732;detachDriverâ&#8364;&#8482;:
usb_modeswitch.c:914: warning: implicit declaration of function â&#8364;&#732;usb_get_driver_npâ&#8364;&#8482;
usb_modeswitch.c:930: warning: implicit declaration of function â&#8364;&#732;usb_detach_kernel_driver_npâ&#8364;&#8482;
usb_modeswitch.c: In function â&#8364;&#732;checkSuccessâ&#8364;&#8482;:
usb_modeswitch.c:1020: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:1026: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1026: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function â&#8364;&#732;search_devicesâ&#8364;&#8482;:
usb_modeswitch.c:1134: warning: implicit declaration of function â&#8364;&#732;usb_get_bussesâ&#8364;&#8482;
usb_modeswitch.c:1134: warning: assignment makes pointer from integer without a cast
usb_modeswitch.c:1134: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1136: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1136: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1138: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1138: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1139: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1160: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1167: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1167: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1169: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1179: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1188: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1190: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1193: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1194: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1220: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1220: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function â&#8364;&#732;find_first_bulk_output_endpointâ&#8364;&#8482;:
usb_modeswitch.c:1242: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1245: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1246: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1247: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1247: error: â&#8364;&#732;USB_ENDPOINT_TYPE_MASKâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:1247: error: â&#8364;&#732;USB_ENDPOINT_TYPE_BULKâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:1248: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1248: error: â&#8364;&#732;USB_ENDPOINT_DIR_MASKâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:1249: error: dereferencing pointer to incomplete type
usb_modeswitch.c: In function â&#8364;&#732;find_first_bulk_input_endpointâ&#8364;&#8482;:
usb_modeswitch.c:1260: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1263: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1264: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1265: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1265: error: â&#8364;&#732;USB_ENDPOINT_TYPE_MASKâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:1265: error: â&#8364;&#732;USB_ENDPOINT_TYPE_BULKâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:1266: error: dereferencing pointer to incomplete type
usb_modeswitch.c:1266: error: â&#8364;&#732;USB_ENDPOINT_DIR_MASKâ&#8364;&#8482; undeclared (first use in this function)
usb_modeswitch.c:1267: error: dereferencing pointer to incomplete type
make: *** [usb_modeswitch] Error 1

---

### Post by PBrn46 on 2010-06-24
Before making modeswitch, you'll need to get some dependencies first.

Try:
sudo apt-get build-dep usb-modeswitch

---

### Post by alexfish on 2010-06-24
Hi all the same usb mode switch is available at the debian repos

 [    Debian Repository]("http://packages.debian.org/usb-modeswitch").

this will self install ,ensure to install the modeswitch data pkg as well

regards

alexfish

---

### Post by hanzj on 2010-07-05
hello, all.

seems that the rogers internet stick on ubuntu  is temperamental. sometimes I see "Rogers Default" under "Mobile Broadband heading" when clicking on the applet. Sometimes, I don't.


Please help everyone!!!

---

### Post by Devo66 on 2010-09-24
I'm having this issue on a new netbook with Lucid Netbook Edition installed.  My Rocket stick was working fine on the old netbook which had eeebuntu running.  Not a modeswitch issue, as it switches to 19d2:0017 in lsusb, however, Network Manager does not recognize any mobile broadband modems attached.  I can use the clunky wvdial system, so I know the Rocketstick is working, but I'd rather use network manager.  Is this an issue with Lucid?  Should I go back to eeebuntu?  I like the look and feel of NBE better, but I've always liked the fact that eeebuntu just works.

---

### Post by alexfish on 2010-09-26
hi

can you post detail of these commands from the terminal

Code:

[COLOR=Blue]which modem-manager[/COLOR]

Code:

[COLOR=Blue]dmesg | grep -e "modem" -e "tty"[/COLOR]

---

