---
title: "SLVR L7 and Linux?"
date: 2008-08-24
forum: Multimedia Software
---

### Post by csall on 2008-08-24
Does anyone know a way to tranfer music to a Motorola SLVR L7. I have tried floola and gtkpod w/ no avail. Any help would be appreciated!

---

### Post by ferrarix on 2008-08-24
You need to use Moto4Lin.

Hop to [www.modmymoto.com](www.modmymoto.com) and visit the [Linux section]("http://www.modmymoto.com/forums/forumdisplay.php?f=33").

I'm the moderator "ferrarix" over there and I assure you that you will find all the help you would need for your Moto, together with tons of modifications that you can put on it ;).

---

### Post by csall on 2008-08-24
Ferrarix, some of the threads seemed outdated. So, I thought I'd post it here as well hoping you'd see it. Here's the issue, if you decide to post back to response on your moto4lin site just let me know by leaving a post here. thank you!

I just installed moto4lin on kubuntu hardy heron.

$ sudo apt-get install moto4lin

Okay there. Furthermore, I run:

$ sudo moto4lin

The GUI pops up, conveniently telling me my phone is not connected.

I then probe my usb devices to find the vendor ID and what not:

$ lsusb
Bus 005 Device 003: ID 13b1:0020 Linksys
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 22b8:4810 Motorola PCS Triplet GSM Phone (storage)
Bus 001 Device 001: ID 0000:0000


Okay so:

Vendor ID=22b8
Product ID=4810

Go through the steps in the guide. I get an error that my phone was not found. Check vendor and product ID. I come to find out that moto4lin is not looking in the right place for my phone, according to the lsusb output. So i edit moto4linrc.

$ cd $HOME/.qt
$ sudo nano moto4linrc

The edited as follows:

[device]
cfgACMdevice=/dev/bus/usb/001/002
cfgATproduct=4810
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=4810
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=1
cfgGoLastFolder=0
cfgLoadList=0

Then I make a script in home directory to load the module and launch moto4lin.

$ cd $HOME
$ sudo nano motorola

This will be the script:

$ sudo modprobe cdc_acm

$ sudo moto4lin

And allow permission to execute script:

$ chmod 700 motorola

And then, Finally run the script:

$ ./motorola


So, now moto4lin GUI opens up and I get this error message now:

[info] Switching device /dev/bus/usb/001/002 to P2K mode...
[error] Unable to open device
[error] Please check preferences

I also notice that when I unplug the phone I get this output as well:

[info] Phone is unpluged


So, I assume the phone is being seen as connected?

I am at a standstill on this. Any help greatly appreciated. Hate using Windows and iTunes!

---

### Post by csall on 2008-08-24
Okay, well I still would like to be able to use moto4lin because it has other features than just the ability to transfer music. However, I have now gotten Amarok to work with my Motorola SLVR L7 with iTunes. I can now successfully transfer and delete mp3's or acc's. If anyone can still help me to get moto4lin to work.. keep postin!

---

### Post by ferrarix on 2008-08-25
Open Moto4Lin, go to Preferences, and set the following:

_ACM Device:_ /dev/ttyACM0
_AT Vendor ID:_ 22b8
_AT Product ID:_ 4902
_P2k Vendor ID:_ 22b8
_P2k Product ID:_ 4901

I think that should get it working.

---

### Post by csall on 2008-09-02
Yeah, I did not change my phone from storage media to data. So, then the original slvr vendor id etc worked properly. Now a few new skins and transferring music w/ amarok. Nice. If anyone has an really good skins for slvr please let me know.

---

