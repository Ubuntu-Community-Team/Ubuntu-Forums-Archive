---
title: "Hauwei E156G modeswitch problem."
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by solitaire on 2010-04-16
Ive installed 10.04 and ever since I can't get my USB 3G dongle to work correctly.

every time I plug it in it keeps going to USB storage rather than a 3G modem.

I've installed ozerocdoff and usb_modeswitch from the repos and it's still not switching from cd mode to modem mode...

It worked fine in 09.10 and my copy of Win7

lsusb:
```
$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 019: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

usb_modeswitch
```

$ usb_modeswitch -W
Reading config file: /etc/usb-modeswitch.conf

 * usb-modeswitch: handle USB devices with multiple modes
 * Version 1.1.0 (C) Josua Dietze 2010
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x0000
DefaultProduct= 0x0000
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
MessageEndpoint= not set
MessageContent= not set
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled
System integration mode disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 006
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 005
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 004
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 003
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 021 on 002
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 002
error obtaining child information: Operation not permitted
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 001
error obtaining child information: Operation not permitted
No default vendor/product ID given. Aborting.

```
Any ideas of how to get modeswitch to work?

---

### Post by alexfish on 2010-04-16
looking at the output the usb modeswitch is set to enquire mode , also the Default id's have not been set in the conf file I would assume these have to be entered. also same for the the targets.  info from the site says the conf file is for setting up new devices , seen as per your outputs. Also the new file name for device info is called usb_modeswitch.setup and is now only used as a reference point. possibly the E156G should work when the usb modeswitch is set to system integrated is enabled , assuming the installation is correct


also
the latest debian package is now 1.1.1-1 from here

                                 
[LIST]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package     ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[/LIST]
 
from source ;

                                 
[LIST]
[*][SIZE=2]**Latest Download     from **[/SIZE][SIZE=2] / If you are a Novice Please Seek     Help

The latest release version is [/SIZE][SIZE=2]**1.1.1**[/SIZE][SIZE=2].     The tar archive contains the source and a i586 binary (32 bit, GCC     4.4.1). I used libusb-0.1.12 but the "compat" library from     libusb-1.0 is now working smoothly too.Changes and updates to the     config database may happen more often than new releases; most of the     valuable knowledge about devices is contained in these files. So you     better use the latest version linked here if it is newer than the     latest program release.[/SIZE]
[/LIST]
 
[LIST]
[*]Download     [usb-modeswitch-1.1.1.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.1.1.tar.bz2"),     dated from 2010-03-17; a Debian (Xandros/Ubuntu) package should be     available soon at the [Debian     Repository]("http://packages.debian.org/usb-modeswitch"). Many architectures are supported there (like amd64     or ia64).
[*]Load the latest     [usb-modeswitch-data]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20100322.tar.bz2")     package (2010-03-22). It contains the device database and the rules     file, including full paths. Use this version only with releases from     1.1.0 upward !
[*]The latest [usb_modeswitch.setup]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup")     (formerly known as usb_modeswitch.conf, 2010-03-16); this is a     reference to all device setups and contributors; you can use it as a     starting point if you want to make a new device working.
[*]Don't forget [libusb]("http://libusb.wiki.sourceforge.net/")     if you don't have it. In your distribution, there is most likely a     package named "libusb-dev" or "libusb-devel".     Choose the legacy version (0.1.12) or the compatible package from     libusb-1.0, at the time of writing it had the version number 0.1.13.
[/LIST]
for the above Please read
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

 there should be no need to install libusb with Ubuntu


I suggest this ,Totaly remove the existing usb modeswitch and the ozerocdoff check to see if the device works,if not then install the latest usb modeswitch, it may work without the need for further configuration

regards

alexfish

---

### Post by solitaire on 2010-04-16
I did download and install 1.1.1 it was the same 
(well it found the Vender / Product id's but not the target class)

I removed 1.1.1 and installed 1.1.0 from the repos to see if it was a problem with the latest or the stable one.

After a lot of googleing i've got a work around

```
sudo rmmod usb-storage && sudo modprobe usbserial vendor=0x12d1 product=0x1003
```

That seems to work but if i remove the dongle I have to reboot and run the commands again for it to be seen...

---

### Post by pdc on 2010-04-16
what about posting here

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

it's the lucid lynx development forum;

surely best to report issues on it there ??????????/

---

### Post by solitaire on 2010-04-16
I've already tacked my problem on to another Hauwei thread in that forum...

[http://ubuntuforums.org/showthread.php?t=1454283](http://ubuntuforums.org/showthread.php?t=1454283)

I'm going to leave it till the full release since there's a workaround and it's not a Major issue for me at the present.
I plan to do a clean install of the final 10.04 rather than keep this upgraded install...

if others have a problem i'll chip in where I can...

---

### Post by pdc on 2010-04-16
it's so tragic you are having these issues

> 12d1:1003

is the ID of the older Huawei E220

I plug one of those into my computer and I get

> 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

I am mint 8 at present, and this older Huawei is just fine;

and it worked two years ago perfectly on various editions of Ubuntu 8.04 !

so if you plug your modem in and type

> dmesg | grep tty

you don't get any ttyUSB results?

I downloaded an alpha of lucid lynx and was pleasantly surprised that my vodafone K3765-Z was auto-flipped from an id of 19d2:2000 to 19d2:0063 by the system; (I know not how);

and I could dial up straight away; I had hoped that would auger better things for 10.04; as you say, best wait a month; there is much feverish activity sorting before the 29th April deadline

---

### Post by solitaire on 2010-04-16
Something has changed between 9.10 and 10.04 so some Hauwei devices don't plug'n'play for a lot of people.

It worked fine in 9.10 As I said it's not big deal for me! since I can use the the workaround if desperate.

Since I'm on an upgrade it's safe to say there's probably something small left over from the upgrade that's causing a problem.

Until I do a clean install I can't be 100% sure it's just not my setup being the problem...

---

### Post by alexfish on 2010-04-17
Hi

for problematic devices you could try using the below, but can't say if it will work here,but worth a try

                                 [SIZE=2]Sakis3G:[/SIZE]
[SIZE=2]
[/SIZE] 
 [SIZE=2]This Method is also worth trying[/SIZE] { Read the Two Links thoroughly before hand } { Also has usb_modeswitch and a couple of fixes for zte devices ,also probes the modem ports so may be a better tool if you have problematic devices IE : multiple ports registering on the system which makes life hard for the Network Manager. Check out the script file , its is easy to enter your provider info}


Check it out at Sakis' blog [ToDo Forever]("http://sakis.tel4u.gr/blog/sakis3g/")


[http://sakis.tel4u.gr/blog/sakis3g/#features](http://sakis.tel4u.gr/blog/sakis3g/#features)

[http://sakis.tel4u.gr/blog/2010/01/2...nown-operator/]("http://sakis.tel4u.gr/blog/2010/01/26/sakis3g-unknown-operator/")

Reminder " Read the script file " and the how to identify the devices etc this is after the long list of ISP's

If done with Ubuntu the " sakis3g " script should be in the " user/bin " it is easy to add to the menu go to edit menu's and add new item , then locate the script , also give it a name


regards


alexfish

---

