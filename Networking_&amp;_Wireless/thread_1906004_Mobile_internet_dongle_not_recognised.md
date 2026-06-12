---
title: "Mobile internet dongle not recognised"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by Beaker Boy on 2012-01-08
Guys

I have just got a 3 Mobile Internet dongle.  I have seen several postings on the internet that say it is pretty much plug in and play, but when I connect it, nothing appears to happen.  I have tried configuring it using the Edit Connections option, but it doesn't appear to connect.  I tried using the 'sudo wvdialconf  /etc/wvdial.conf' command as suggested on the forum, and it doesn't appear to be seeing a modem (which I assume is all the dongle is).  I'm running Ubuntu 11.10, but have done nothing apart from the basic upgrade.

Has anyone got any advice?

Many thanks

BB

---

### Post by philinux on 2012-01-08
> **Beaker Boy said:**
> Guys

I have just got a 3 Mobile Internet dongle.  I have seen several postings on the internet that say it is pretty much plug in and play, but when I connect it, nothing appears to happen.  I have tried configuring it using the Edit Connections option, but it doesn't appear to connect.  I tried using the 'sudo wvdialconf  /etc/wvdial.conf' command as suggested on the forum, and it doesn't appear to be seeing a modem (which I assume is all the dongle is).  I'm running Ubuntu 11.10, but have done nothing apart from the basic upgrade.

Has anyone got any advice?

Many thanks

BB

What make and model is the dongle.

---

### Post by Beaker Boy on 2012-01-08
It's a Huawei E353 Dongle for 3 Mobile Internet.

---

### Post by Sijmen on 2012-01-08
When you insert the dongle, does Ubuntu ask for a PIN to unlock the sim?

Can you enable Mobile Broadband? Click on the Network Connections icon  in the notification panel on the menubar. Navigate to 'Enable Mobile  Broadband'. Now you have to make a new configuration to enable the 3G  connection, this should be an option that appears after you enable Mobile Broadband.

Uhm.... the above goes for XFCE

---

### Post by Beaker Boy on 2012-01-08
No, it doesn't ask for anything I'm afraid.

And even with the dongle plugged in it doesn't appear to be giving me an option to Enable Mobile Broadband.  The Enable Wireless and Enable Networking options appear and are ticked.  As you can see from my first post, I tried to make the connection by going into the Edit Connections option, selected the Mobile Internet tab, Clicked Add, selected United Kingdom, 3, and then Internet options, completed and still nothing.

Any ideas?

---

### Post by Sijmen on 2012-01-08
After selecting '3', can you select a plan type? Mine wouldn't work with the default plan that would come up when I selected my ISP. It gave me four options, and the second enabled the 3G connection, the other three did nothing.

---

### Post by Beaker Boy on 2012-01-08
The only options it gives are Internet or Handset.  Should there be something else?

---

### Post by Sijmen on 2012-01-08
My guess is that you have tried 'Internet' already....

Going on info from this thread, is your 10.04 up to date? 
[http://ubuntuforums.org/showthread.php?t=1799524](http://ubuntuforums.org/showthread.php?t=1799524)

Edit: even with updates it might not fix problem...

---

### Post by Beaker Boy on 2012-01-08
That was my first check, and luckily I did select Internet! 

Despite my profile (which I seem unable to update) I am actually running Ubuntu 11.10.

---

### Post by mörgæs on 2012-01-08
Moved to the networking forum.

---

### Post by Sijmen on 2012-01-08
Can you check in Synaptic if the following packages are installed:

usb-modeswitch
usb-modeswitch-data

---

### Post by Beaker Boy on 2012-01-08
Yes, both files are there.

Out of interest, how do/did you get the Mobile Internet to connect.  Did you just plug in the dongle and then it gave you the option to enable Mobile Broadband?

---

### Post by Sijmen on 2012-01-08
I use a 904 with 11.10 from a Dutch provider. I was hoping it was just a setup issue. But searching shows a there are bunch of threads on this problem:

[http://ubuntuforums.org/showthread.php?t=1800877](http://ubuntuforums.org/showthread.php?t=1800877)
[http://ubuntuforums.org/showthread.php?p=11072539](http://ubuntuforums.org/showthread.php?p=11072539)
[http://ubuntuforums.org/showthread.php?t=1805826](http://ubuntuforums.org/showthread.php?t=1805826)
[http://ubuntuforums.org/showthread.php?t=1799524](http://ubuntuforums.org/showthread.php?t=1799524)

Non have sufficient info about how to get it working, though. 

This site might do the trick: [http://www.sakis3g.org/](http://www.sakis3g.org/)

The installation guide:
**Ubuntu**
sudo bash apt-get install ppp
cd /usr/bin
wget '[http://www.sakis3g.org/versions/latest/sakis3g.gz']("http://www.sakis3g.org/versions/latest/sakis3g.gz%27")
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
**You should see:** sakis3g.gz: OK
gunzip sakis3g.gz
chmod +x sakis3g

Let's see if I can run it.

---

### Post by Sijmen on 2012-01-08
The wget command doesn't retrieve the package. So I download manually. 
Installation worked as described. I had to sudo the chmod command.
./sakis3g ran the script nicely.

---

### Post by Beaker Boy on 2012-01-08
I tried running the sakis3g shell script, and interestingly, I don't think it is able to see the modem despite one of the options being a Huawei modem connected via a USB.  I'm getting well outside my knowledge zone now.  Is there a network manager or modem manager I haven't got installed???

---

### Post by Sijmen on 2012-01-08
I think we're getting to the point where we needed to start from: is the E353 being recognized by Ubuntu.
I'm trying to figure out with what command I can show the active USB ports. Found it.

type: lsusb

It shows something like this:

```

james@Bond:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0af0:d057 Option 
Bus 002 Device 002: ID 04f2:b064 Chicony Electronics Co., Ltd 

```This is my 904, Option being the manufacturer:
Bus 001 Device 004: ID 0af0:d057 Option

---

### Post by Beaker Boy on 2012-01-08
You read my mind as I did just that and got:

alex@alex-laptop:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 002 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552 (HSPA modem)


So it is seeing the modem but just not doing anything about it.

---

### Post by Sijmen on 2012-01-08
All right, let's see if we can get some extra information on that particular device. Can you run 'dmesg' and look for the USB lines:

```

[  119.440283] usb 1-2: new high speed USB device number 4 using ehci_hcd
[  119.637244] hso: /build/buildd/linux-3.0.0/drivers/net/usb/hso.c: Option Wireless
[  119.642951] hso 1-2:1.5: Not our interface
[  119.642985] usbcore: registered new interface driver hso
[  119.682537] usbcore: registered new interface driver hdj_mod


```

---

### Post by Beaker Boy on 2012-01-08
That generates quite a few pages of script, is it possible to view it a page at a time?

---

### Post by Beaker Boy on 2012-01-08
Although I did just find this:

[ 6259.824100] usb 2-1: new high speed USB device number 5 using ehci_hcd
[ 6259.978829] scsi9 : usb-storage 2-1:1.0
[ 6259.979429] scsi10 : usb-storage 2-1:1.1
[ 6260.162837] usb_modeswitch_[14830]: segfault at 0 ip 080494fa sp bf922cf0 error 4 in usb_modeswitch_dispatcher[8048000+8000]
[ 6260.977640] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 6260.977814] scsi: killing requests for dead queue
[ 6260.978134] scsi 10:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2

Does this give us any clues?

---

### Post by Sijmen on 2012-01-08
Found this: [http://wiki.georgweiss.de/Hardware/UMTS-Usbstick_HUAWEI_E1552](http://wiki.georgweiss.de/Hardware/UMTS-Usbstick_HUAWEI_E1552)

My guess is, it's not made for 11.10, since it asks to add lines to /etc/modules.d/ which now seems to be etc/modules

---

### Post by Sijmen on 2012-01-08
Check this:

[https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/824147](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/824147)

Post #16 and onward might be the solution.

Edit: Checking my usb_modeswitch shows the exact same line as the fix they suggested.

---

### Post by Sijmen on 2012-01-08
As the report states: This bug was fixed in the package usb-modeswitch - 1.1.9-1ubuntu3

Which is what is installed:
```
james@Bond:$ usb_modeswitch -e

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.9 (C) Josua Dietze 2011
 * Based on libusb0 (0.1.12 and above)

```

---

### Post by Sijmen on 2012-01-08
To come back to your question. The E353 has two functions; one being a  USB storage device and the other being the USB modem. For some reason  Ubuntu isn't able to make the modem part of the device work.


> **Sijmen said:**
> Found this: [http://wiki.georgweiss.de/Hardware/UMTS-Usbstick_HUAWEI_E1552](http://wiki.georgweiss.de/Hardware/UMTS-Usbstick_HUAWEI_E1552)

My guess is, it's not made for 11.10, since it asks to add lines to /etc/modules.d/ which now seems to be etc/modules

This could work, if we could find out which 'product' is being used so that name can be added to the ' TargetProductList' and the modules file. But that would mean the module for this particular chip exists, which is something we don't know.... yet :)

---

### Post by Beaker Boy on 2012-01-08
I'm afraid my computer still won't see the modem.  It doesn't seem to be able to look for it. As seen below.  

alex@alex-laptop:~$ usb_modeswitch -c /etc/usb_modeswitch.conf
No default vendor/product ID given. Aborting.

I'm guessing there should be some text in usb_modeswitch.conf.

---

### Post by Beaker Boy on 2012-01-08
Sijmen

Thankyou so much for all your help this afternoon.  We may not have solved the problem but I think I have learnt some new techniques for diagnosing problems.  I've got to shoot off now but if you get any more ideas I would love to hear them.  I think the answer should be quite simple, like configuration file or something but I'm al bit too inexpereinced to know what it is.

Anyway, many thanks

BB

---

### Post by Sijmen on 2012-01-08
You're welcome.

Did another search on the specs of the dongle. Huawei states that the E353 is the first plug&play dongle; no software required, but it has to be supported by the OS. And the OS's are Windows and OSX. The chipset is uses is the Qualcomm MSM8200. I can't find any info whether the linux kernel supports this chipset.

---

### Post by alexfish on 2012-01-08
hi Beaker Boy

can post the results of lsub command from the terminal

```
lsusb
```

this will indicate if in modem mode or switched mode

depending on the ID's of the Device

I suspect this device is unstable or or problematic device for linux

if so . sakis3g , possible best bet , try using sakis3g from the terminal with the nostorage option

ie
```
sakis3g -nostorage
```

---

