---
title: "Mifi 2352 not detected by Ubuntu"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by bamabaso@gmail.com on 2010-08-01
Hi Guys

I'm a ubuntu linux 10.04 LTS user with a problem. i have been using a vodafone 3G card in South Africa and it has been working correctly. I have used it since Ubuntu 9 and it was correctly detected all the time, so that's great.

But then I got myself a mifi 2352 device (for those who do not know, it is a device that shares a mobile 3G connection to at most 5 users using wifi. it also works in usb mode, like a normal 3G card when you plug it on computer. You can just google the device for more info.

My problem is when i plug in the device through the usb, Ubuntu does not detect, which is very frustrating. I've tried a lot of things, including installing "vodafone-mobile-connect_2.25.01-1_all" with no success.

Is there any reasobn why the mifi 2352 is not detected by Ubuntu?


I would appreciate any help

Thanks
Andy

---

### Post by pdc on 2010-08-01
if you type

> lsusb into a terminal and copy and paste the result

and

copy and paste this command into a terminal

> dmesg | grep tty

and copy and paste the results back here

you may need to install usb_modeswitch from here

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

---

### Post by bamabaso@gmail.com on 2010-08-01
[I][B]Hi, thank you very much for the reply, I appreciate it.

Here are outputs when I type the following on a terminal:[/B][/I]


Typing lsusb:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 003 Device 002: ID 062a:0252 Creative Labs 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 012: ID 1410:7001 Novatel Wireless 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

typing dmesg | grep tty:

 0.000000] console [tty0] enabled
[   11.693573] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[   11.693610] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[   57.218022] type=1503 audit(1280641598.523:16):  operation="open" pid=1913 parent=1911 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0"
[   57.218033] type=1503 audit(1280641598.523:17):  operation="open" pid=1913 parent=1911 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB1"
[  215.215872] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  215.216257] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  332.875441] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[  332.877417] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[26495.520601] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[26495.520905] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[26519.437409] usb 3-3: GSM modem (1-port) converter now attached to ttyUSB0
[26519.438892] usb 3-3: GSM modem (1-port) converter now attached to ttyUSB1
[26547.262303] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB2
[26547.262578] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB3
[26547.262816] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB4
[26547.263050] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB5
[26616.656631] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[26616.656912] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[26665.011535] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[26665.011721] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[26665.011914] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[26665.012087] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[26665.291160] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0
[26665.291329] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1
[26665.291488] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB2
[26665.291744] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB3
[26705.964033] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[26715.350322] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[26720.360299] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[26725.370344] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0




[B][I]I installed package usb-modeswitch from the link that you provided, but i still cannot get Ubuntu to detect the mifi device connected through a usb. 

Hope the information above cab help solve the problem

Many thanks
Andy[/I][/B]

---

### Post by alexfish on 2010-08-01
can try reloading the option module

[B]sudo modprobe option

[/B]then see if the device has configured

[COLOR=Black]Code
[/COLOR][COLOR=Black]ls -al /dev/serial/by-id/usb*

Code:
dmesg | grep tty
[/COLOR][COLOR=Blue]

[/COLOR]

---

### Post by bamabaso@gmail.com on 2010-08-01
Hi Alex Fish

I tried what you suggested but that didn't seem to work.

Interestingly enough, sometimes when I plug in the device, I get this error message:

[B]Unable to mount Vodafone Mobile_
[/B]
Error mounting: mount: block device/dev.sr1 is write-protected, mounting read-only. mount: wrong fs type, bad option, bad superblock on dev/sr1, missing codepage or helper program, or other error

Not sure why it's spitting that info at me, but the device does have an empty sd card slot at the moment...

Regards
Andy

---

### Post by alexfish on 2010-08-02
not sure what is happening , also don't know the device so will have to find where it is on the system 

although reading the previous post it had registered

can you try connecting the device after booting the computer and see if if the drivers are loading
monitor the outputs from the logfile viewer messages

also done a bit of read about this device / at normal config there is no drivers supplied for the device and as far as I am aware there are no linux drivers

if nothing happens
all I can suggest is to unistall VMC / also note there are two versions of vmc one is for debian appended .deb
and also the usb_modeswitch , I can't find your device listed in the conf file

then we can have a fresh look at trying to identify the device
when done try the following codes and see what it comes up with

Codes: to try

lsusb
grep . /sys/bus/usb/devices/*/tty*/port_number
cat /proc/modules | grep "^usbhid"
ls -al /dev/disk/by-id/*
ls /dev/serial/by-path/*
sudo cat /proc/tty/driver/usbserial

---

### Post by bamabaso@gmail.com on 2010-08-02
Hi Guys


Thanks again for the replies...
I'm getting a little frustrated at this problem, but nonetheless I will not rest until it has been resolved, well until Friday anyway.

The Job sent me away from the office for the week, so I will only try out the codes on Friday when I come back :-(

Crumbs!!

---

### Post by bamabaso@gmail.com on 2010-08-06
Hi Guys

I'm back from my travels...

to get back to this problem, any help appreciated...

AlexFish, I tried some of the codes that you suggested. I also removed VMC software from the computer...


lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 003 Device 002: ID 062a:0252 Creative Labs 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1410:5041 Novatel Wireless 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




typing cat /proc/modules | grep "^usbhid"
usbhid 41084 0 - Live 0xffffffffa0039000
+++++++++++++++++++++++++++++++



typing ls -al /dev/disk/by-id/*

rwxrwxrwx 1 root root  9 2010-08-06 08:10 /dev/disk/by-id/ata-ST3500418AS_9VM30R3X -> ../../sda
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/ata-ST3500418AS_9VM30R3X-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/ata-ST3500418AS_9VM30R3X-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/ata-ST3500418AS_9VM30R3X-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/ata-ST3500418AS_9VM30R3X-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/ata-ST3500418AS_9VM30R3X-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/ata-ST3500418AS_9VM30R3X-part8 -> ../../sda8
lrwxrwxrwx 1 root root  9 2010-08-06 08:10 /dev/disk/by-id/scsi-SATA_ST3500418AS_9VM30R3X -> ../../sda
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/scsi-SATA_ST3500418AS_9VM30R3X-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/scsi-SATA_ST3500418AS_9VM30R3X-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/scsi-SATA_ST3500418AS_9VM30R3X-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/scsi-SATA_ST3500418AS_9VM30R3X-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/scsi-SATA_ST3500418AS_9VM30R3X-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/scsi-SATA_ST3500418AS_9VM30R3X-part8 -> ../../sda8
lrwxrwxrwx 1 root root  9 2010-08-06 08:36 /dev/disk/by-id/usb-NVTL_Mass_Storage_358204020369111-0:0 -> ../../sr1
lrwxrwxrwx 1 root root  9 2010-08-06 08:10 /dev/disk/by-id/wwn-0x5000c50015a4d44c -> ../../sda
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/wwn-0x5000c50015a4d44c-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/wwn-0x5000c50015a4d44c-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/wwn-0x5000c50015a4d44c-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/wwn-0x5000c50015a4d44c-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/wwn-0x5000c50015a4d44c-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-08-06 08:10 /dev/disk/by-id/wwn-0x5000c50015a4d44c-part8 -> ../../sda8

Anyway, I will try some things today and will post it back here if I succeed...

---

### Post by bamabaso@gmail.com on 2010-08-06
[I]Hi guys

**I have managed to solve this problem, and possibly for every other MIFI device Ubuntu user out there. The solution is quite simple actually. Funny enough, this is possible the only post on the internet, or one of very few, dealing with a mifi device and a linux distro... **[/I]

[LIST=1]
[*]Firstly, if you have the VMC software on your Ubuntu, remove it. (Thanks for the tip AlexFish)
[*]Second, you need a software package (also developed by Betavine, an R&D group of Vodafone) called Betavine Connection Manager (BCM).
[*] You can find the BMC software here: [https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76)
[*] Download bcm_2.99.11-1_all.deb
             python-messaging_0.5-1_all.deb
             usb-modeswitch-data_20100623-1betavine1_all.deb
             wader-core_0.5.4_all.deb
[*]You might have dependecy issues, but nothing that you shouldn't be able to sort out.
[*]Install those 4 files, and resolve any dependency issues..

[/LIST]

[B][I]And that's it, Ubuntu's Network Manager should now be able to detect your MIFI device, and plus you've got a really cool connection manager where you can send/receive sms's, amongst other things...

So the crux of the matter is, in order to use your MIFI device with Ubuntu, you need the BCM software, and not the VMC software... The BCM is just a later version of the VMC, with a name change.

Alright, Thanks everyone!!!![/I][/B]

---

### Post by alexfish on 2010-08-09
HI all

 Just one last word on this VMC : BMC .

** Install this software at your own risk**

you have read this post .even installing the BMC version is of risk

please read 

[VMC software from Betavine{ vodafone mobile  connect re:Betavine Connection Manager}]("http://ubuntuforums.org/showthread.php?t=1548553")

---

### Post by bamabaso@gmail.com on 2010-08-09
AlexFish, I'm afraid you are right!!! The software is terribly unstable. After I installed the software a week ago, everything worked well for a while, but then all of a sudden I could not pick up the device anymore when I connect via USB. I initially thought there was something wrong with the device but in windows it works. After seeing your post here it just confirms it to me

When I plugged in my device and started the BCM software, all my USB devices became unresponsive, and also the BCM could not pick up the device. I have now competely removed the BCM software, and the network manager can pick up the mifi device.

So for anyone else that encountered a problem with the software after reading this post, then pleas go to synaptic and mark the 'bcm' soft. for complete removal. Please let me know if your network manager can still pick up the device...


hmmmmm, someone needs to update Ubuntu's Network Manager to accommodate all devices....

---

### Post by alexfish on 2010-08-09
Hi

All again there a safer way to achieve this 

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

if you read the thread in detail you will realise it is not a Network Manager issue

and where ever possible use the Network Manager for your connection ,it has a lot of protection features built in to which most users are not aware of

---

### Post by bamabaso@gmail.com on 2010-08-09
Thanks AlexFish

---

### Post by alexfish on 2010-08-09
> **bamabaso@gmail.com said:**
> AlexFish, I'm afraid you are right!!! The software is terribly unstable. After I installed the software a week ago, everything worked well for a while, but then all of a sudden I could not pick up the device anymore when I connect via USB. I initially thought there was something wrong with the device but in windows it works. After seeing your post here it just confirms it to me

When I plugged in my device and started the BCM software, all my USB devices became unresponsive, and also the BCM could not pick up the device. I have now competely removed the BCM software, and the network manager can pick up the mifi device.

So for anyone else that encountered a problem with the software after reading this post, then pleas go to synaptic and mark the 'bcm' soft. for complete removal. Please let me know if your network manager can still pick up the device...


hmmmmm, someone needs to update Ubuntu's Network Manager to accommodate all devices....

Hi

could you give a complete account of the un-install of this software 

I think for some systems the standard methods of un-install will still be rendering part of the system useless

At present trying to debug a system  , and hopefully have a complete solution that this irresponsible piece of software has caused . It's Not giving Linux a good name

one can only but feel sorry for the end user .

regards

alexfish

---

### Post by bamabaso@gmail.com on 2010-08-09
Hi

sudo apt-get --purge remove bcm

That will remove the package and all it's associated files...

I'm not sure if there's any reason to remove the other packages that were installed with it (like usb modeswitch), in order to start afresh.....?

Hope that helps..., but maybe you already knew that

---

### Post by bamabaso@gmail.com on 2010-08-09
Like I said, I only removed the BCM software... and my problems seem to have disappeared...

---

### Post by alexfish on 2010-08-09
what happened with  the modem manager , this is one of reason NM can't see the modem

also there are some devices which do not require usb modeswitch { if installed they will be reset to storage mode } then to also it will not
be seen by the modem manager/ also recommend installing this type of software from safe sources IE through the debian repo's or ubuntu

---

### Post by bamabaso@gmail.com on 2010-08-12
Hi Alex , sorry for the late reply...

I'm not entirely sure of what you are asking me.

The modemmanager is still there, and I have not removed. I've got the latest version from the Ubuntu repos.

dpkg -s  modemmanager
Package: modemmanager
Status: install ok config-files
Priority: optional
Section: net
Installed-Size: 620
Maintainer: Ubuntu Network Manager Team <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.3-0ubuntu2
Config-Version: 0.3-0ubuntu2
Depends: libc6 (>= 2.7), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libglib2.0-0 (>= 2.18.0), libgudev-1.0-0 (>= 147)
Conffiles:
 /etc/dbus-1/system.d/org.freedesktop.ModemManager.conf 4832ca750119cc4126f0835a78df32ef
Description: D-Bus service for managing modems
 Provides a D-Bus interface to communicate with mobile broadband (GSM, CDMA,
 UMTS, ...) cards. Implements a loadable plugin interface to add work-arounds
 for non standard devices. Also provides patches to use networkmanager (and
 the applet) with modem manager.
 .
 Git Repository: [http://cgit.freedesktop.org/ModemManager/ModemManager/](http://cgit.freedesktop.org/ModemManager/ModemManager/)

I hope that is the answer you were looking for?

---

### Post by alexfish on 2010-08-12
hi

there has been a reply from pmarti one delelopers for betavine
at the thread mentioned above Re: VMC software from Betavine{ vodafone mobile connect re:Betavine Connection Manager}#[**10**]("http://ubuntuforums.org/showpost.php?p=9697253&postcount=10")

interesting comments, some of which , worth noting

---

### Post by bamabaso@gmail.com on 2010-08-13
Thanks, I'll have a look at it

---

