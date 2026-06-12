---
title: "UM175 USB EVDO Rev-A Modem - Issues"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by arch3angel on 2009-02-12
I have an Alltel UM175 USB Modem I am trying to get working in my Ubuntu Intrepid Ibex 8.10 that just don't seem to work.

I have found this [link]("http://www.evdoforums.com/thread9995.html") which states how easy it should be, yet I still fail.

Below is some info related to what I found during my checks when I was trying to get it working:

dmesg Results:
> 
Feb 12 19:44:05 ares kernel: [ 6484.456070] usb 2-2: new full speed USB device using uhci_hcd and address 6
Feb 12 19:44:06 ares kernel: [ 6484.664587] usb 2-2: configuration #1 chosen from 1 choice
Feb 12 19:44:06 ares kernel: [ 6484.716892] scsi6 : SCSI emulation for USB Mass Storage devices
Feb 12 19:44:11 ares kernel: [ 6489.729324] scsi 6:0:0:0: CD-ROM            UM175AL  CD-ROM           2.31 PQ: 0 ANSI: 2
Feb 12 19:44:11 ares kernel: [ 6489.808125] sr0: scsi3-mmc drive: 0x/0x caddy
Feb 12 19:44:11 ares kernel: [ 6489.810023] sr 6:0:0:0: Attached scsi generic sg1 type 5
Feb 12 19:44:11 ares kernel: [ 6490.043346] sr: Sense Key : No Sense [current] 
Feb 12 19:44:11 ares kernel: [ 6490.043355] sr: Add. Sense: No additional sense information
Feb 12 19:44:11 ares kernel: [ 6490.068146] sr: Sense Key : No Sense [current] 
Feb 12 19:44:11 ares kernel: [ 6490.068155] sr: Add. Sense: No additional sense information
Feb 12 19:44:11 ares kernel: [ 6490.331929] usb 2-2: USB disconnect, address 6
Feb 12 19:44:13 ares kernel: [ 6491.808119] usb 2-2: new full speed USB device using uhci_hcd and address 7
Feb 12 19:44:13 ares kernel: [ 6491.999852] usb 2-2: configuration #1 chosen from 1 choice
Feb 12 19:44:13 ares kernel: [ 6492.035050] scsi7 : SCSI emulation for USB Mass Storage devices
Feb 12 19:44:18 ares kernel: [ 6497.045571] scsi 7:0:0:0: Direct-Access     UM175AL  Storage          2.31 PQ: 0 ANSI: 2
Feb 12 19:44:18 ares kernel: [ 6497.064588] sd 7:0:0:0: [sdb] 58880 512-byte hardware sectors (30 MB)
Feb 12 19:44:18 ares kernel: [ 6497.103253] sd 7:0:0:0: [sdb] Write Protect is off
Feb 12 19:44:18 ares kernel: [ 6497.113901] sd 7:0:0:0: [sdb] 58880 512-byte hardware sectors (30 MB)
Feb 12 19:44:18 ares kernel: [ 6497.120579] sd 7:0:0:0: [sdb] Write Protect is off
Feb 12 19:44:18 ares kernel: [ 6497.125062]  sdb:
Feb 12 19:44:18 ares kernel: [ 6497.135775] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Feb 12 19:44:18 ares kernel: [ 6497.137861] sd 7:0:0:0: Attached scsi generic sg1 type 0
Feb 12 19:54:03 ares kernel: [ 7081.650791] usbcore: deregistering interface driver usbserial_generic
Feb 12 19:54:03 ares kernel: [ 7081.652958] usbserial: USB Serial deregistering driver generic
Feb 12 19:54:03 ares kernel: [ 7081.657951] usbcore: deregistering interface driver usbserial


lsusb Results:
> 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 007: ID 106c:3b03 Curitel Communications, Inc.** 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The bold area above is what I believe is the UM175 Modem

When I try to use gnome-ppp application it tells me:

> 
GNOME PPP: STDOUT: Sorry, no modem was detected!  Is it in use by another program?


I have configured wvdial.conf to reflect the following with my information instead of the data displayed here:

> 
[Dialer Defaults]
Stupid Mode = on
Modem Type = Analog Modem
Auto Reconnect = on
Carrier Check = no
Init = ATZ

[Dialer um175]
Modem = /dev/ttyACM0
Baud = 921600
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = [email]8885551212@vzw3g.com[/email]
# replace with your device's actual area code and phone number
Password = vzw
Init1 = ATZ
ISDN = 0 


It appears to not see the USB modem at all and does see it as a mass USB device.  I have tried everything I know and hope that someone here has the solution to get this resolved, I really want the flexibility of this card on my laptop.

Thanks!!!

---

### Post by arch3angel on 2009-02-15
I was sent an email from a buddy and let me say this was a dead on resolution for the issue.  Below is the steps I took to resolve the issue, here are the links that I have:

[Mark Ziesemer's Blog Tutorial]("http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html")

[Jason Costomiris's Tutorial]("http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/")

I downloaded "USB_Modeswitch" from [Here]("http://www.draisberghof.de/usb_modeswitch/") - Take note that there is a .deb file but this failed to install under 8.10 Intrepid Ibex - I edited the configuration to un-comment the following portion of the "usb_modeswitch.conf" file - Example below:

```

########################################################
# UTStarcom UM175 (distributor "Alltel")
#
# Contributor: Mark A. Ziesemer

DefaultVendor=  0x106c
DefaultProduct= 0x3b03

TargetVendor=   0x106c
TargetProduct=  0x3715

MessageEndpoint=0x05
MessageContent="555342431234567824000000800008ff024445564348470000000000000000"

```

The portion of Mark Ziesemer's blog failed to have the "TargetVendor" and "TargetProduct" in his code example, however in the configuration file provided with the current .tar.gz for usb_modeswitch does have this portion and only requires the lines to be un-commented

Once you have extracted the files to the computer simply follow the directions on the usb_modeswitch website - execute "make" then "make install" and it will compile the correct configuration file - Once this is completed you need to execute the following command with the USB Modem already plugged in

```
sudo usb_modeswitch
```

Once you complete this all you should have to do is configure Gnome-PPP or your favorite PPP application with the following information required for the Alltel device:

Alltel Configuration:
> 
**Step 1.** Plug the device in.  Ok, you’re done Step 1.

**Step 2.** Launch gnome-ppp, configure settings, other than the defaults:

    * Modem Tab (Click Auto Detect)
          o Device: /dev/ttyACM0
          o Type: USB Modem or Analog Modem (If Seen As)
          o Speed: 460800
          o Phone Line: Tone
          o Volume: Off

    * Options Tab
          o Minimize: checked
          o Dock in Notification Area: checked

Click Close.  Fill in the fields in the main Gnome PPP window:

    * Username: (10 Digit Phone Number) [email]1234567890@alltel.net[/email]
    * Password: alltel
    * Phone Number: #777

**Step 3.** Click Connect

**Step 4.** There is no step 4.  You’re connected.


Verizon Configuration: - Thanks Jason!
> 
**Step 1.** Plug the device in.  Ok, you’re done Step 1.

**Step 2.** Launch gnome-ppp, configure settings, other than the defaults:

    * Modem Tab (Click Auto Detect)
          o Device: /dev/ttyACM0
          o Type: USB Modem or Analog Modem (If Seen As)
          o Speed: 460800
          o Phone Line: Tone
          o Volume: Off

    * Options Tab
          o Minimize: checked
          o Dock in Notification Area: checked

Click Close.  Fill in the fields in the main Gnome PPP window:

    * Username: (10 Digit Phone Number) [email]1234567890@vzw3g.com[/email]
    * Password: vzw
    * Phone Number: #777

**Step 3.** Click Connect

**Step 4.** There is no step 4.  You’re connected.


Please note that Verizon has purchased Alltel but the Silver UM175 devices sold under the name of the Alltel company are still available and work perfectly fine - The issue surrounding this is that the Alltel device once plugged in creates an auto run CD-Rom to install the software for Windows and Mac

Once I setup "USB_Modeswitch" and Gnome-PPP I was quickly on the internet surfin right along

Hope this solution helps others and thanks to Mark, Jason, and the USB_Modeswitch group for making a confusing process into something of ease!!!

---

### Post by harphauler on 2009-03-17
I'm a complete newbie to Linux and have a question about installing usb_modeswitch.  Am running Ubuntu 8.10 64 bit.  Downloaded usb_modeswitch-0.9.6.tar.bz2 with a manifest of

COPYING
Makefile
README
usb_modeswitch
usb_modeswitch.c
usb_modeswitch.conf
usb_modeswitch.h

On the usb_modeswitch websitesite is the following:

>>Unpack and run "make install". Edit "/etc/usb_modeswitch.conf" according to your hardware (it's heavily commented and should tell you what to do).
>>If you want to compile it for yourself, just delete the binary, then run "make" or type on the shell:
>>$ gcc -l usb -o usb_modeswitch usb_modeswitch.c

Since there's no "make install" file I assume I need to run a terminal window and compile myself.  What is the "binary" referred to that I need to delete?  Actually, step-by-step of what I need to do and type after extracting the files would be most appreciated, if possible.

---

### Post by harphauler on 2009-03-17
Solved install problem of usb_modeswitch.

New problem now.  When trying to dial in, get the following error log from Gnome PPP:

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM0L0DT#777
--> Waiting for carrier.
ATM0L0DT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM0L0DT#777
--> Waiting for carrier.
NO CARRIER
ATM0L0DT#777
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Tue Mar 17 15:53:24 2009

No straight answers for what to do about running /usr/sbin/ppd; specifiying a path in wvdial.conf, etc on the forums.  Can anybody help?

Thanks.

---

### Post by harphauler on 2009-03-17
Solved but clunky, have to run wvdial from the terminal as root.  For whatever reason no GUI dialer will work on my system.

---

