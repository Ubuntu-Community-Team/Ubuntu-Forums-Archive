---
title: "Vista MCE Remote clone and LIRC"
date: 2008-08-01
forum: Mythbuntu
---

### Post by tenguzori on 2008-08-01
Hi Guys,

I guys I have purchased a cheap Vista MCE clone remote.

I can not get this remote to work. I suspect it is becuase it is not yet supported by LIRC. 

This is how the device is reported.
lsusb
Bus 002 Device 003: ID 05a4:9881 Ortek Technology, Inc.

Mythbunto version - 8.04

Please let me know if you agree this is currently unsuported. Howdifficult would it be to hack LIRC to support this, any info or apointer on how to do this would be greatfully recieved.

Also I also have a wireless keyboard as well as this MCE clone. I have found some reports on issues with having both the wireless keyboard/mouse and IR MCE remote connected at the same time. Some detail on this would also be great.

Thanks for the help - Matthew.

---

### Post by superm1 on 2008-08-01
Hi Matthew:

Hacking LIRC to add support usually isn't too bad.  Start out by installing lirc-modules-source.  This package depends upon dkms and will be used to rebuild all your modules for you.

Next grab the lirc_mceusb2.c source file from LIRC CVS.  Drop it in the appropriate directory in /usr/src.  I want to say it's /usr/src/lirc-0.8.3~pre1/lirc_mceusb2.

Now issue these commands:
```
dkms -m lirc -v 0.8.3~pre1 build
dkms -m lirc -v 0.8.3~pre1 install
```

Remove and reload the module
```
rmmod lirc_mceusb2
modprobe lirc_mceusb2
```

Restart lirc to try it (assuming that it has been configured for a mceusb2 properly)
```
/etc/init.d/lirc restart
```

If that works, you are done.  If it doesn't, then you can start poking around that source file to add identifiers for your remote (which can be found via lsusb)

---

### Post by tenguzori on 2008-08-02
Hi Superm1,

Thanks for getting back to me and giving the commands.

After modifying the driver .c file, dkpm compains that the mod has allready been built. It sugest first using the remove option - so I did - then it complained lirc-0.8.3~pre1 did not exist in the dkpm tree. (removed the lirc-modules-source package and reinstalled, and tried again with the dkms uninstall witht he same result).

If you could give me some further advice on how to get past this, I woudl be greatfull.

Thanks - Matthew.


sudo dkms -m lirc -v 0.8.3~pre1 build
Error! This module/version has already been built on: 2.6.24-19-generic
Directory: /var/lib/dkms/lirc/0.8.3~pre1/2.6.24-19-generic/x86_64
already exists.  Use the dkms remove function before trying to build again.


 sudo dkms remove -m lirc -v 0.8.3~pre1 --all
...


sudo dkms -m lirc -v 0.8.3~pre1 build

Error! DKMS tree does not contain: lirc-0.8.3~pre1
Build cannot continue without the proper tree.

diff lirc_mceusb2.c lirc_mceusb2.c.org
133d132
< #define VENDOR_JMICRON                0x152d
174,175d172
<       /* JMicron Technology Corp */
<       { USB_DEVICE(VENDOR_JMICRON, 0x152d) },


lsusb:
Bus 002 Device 006: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp.

uname -a
Linux tengu3 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

---

### Post by superm1 on 2008-08-03
issue a dkms add -m lirc -v 0.8.3~pre1 and then another rebuild.  Hopefully should take care of it.

---

### Post by tenguzori on 2008-08-03
Hi Superm1,

Thanks for you help. Thelast command you gave did look to help as I was able to run the build and install. remote however is still not working. Some further info below on what I have found (/dev/lirc0 missing. Please could you let me know what may be causing this and what I may have done wrong? (I install lircd by simply using the mythbuntu control centre  gui and anbling the microsoft mce remote (new).

Thanks again for this help - Matthew

message log following start of lircd:

Aug  3 20:18:45 tengu3 kernel: [   57.072052] lirc_dev: IR Remote Control driver registered, major 61
Aug  3 20:18:45 tengu3 kernel: [   57.086088] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
Aug  3 20:18:45 tengu3 kernel: [   57.087749]
Aug  3 20:18:45 tengu3 kernel: [   57.087753] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
Aug  3 20:18:45 tengu3 kernel: [   57.087756] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
Aug  3 20:18:45 tengu3 kernel: [   57.124594] usbcore: registered new interface driver lirc_mceusb2

do I need to be worried about the Kernel Tainted message?

I have noticed that following boot, no lircd proc is running


following execution of lircd init script:
 ps -ef | grep lircd
root      6660     1  0 20:39 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0

Lircd dies after running irw:

irw
matthew@tengu3:~$ ps -ef | grep lircd
matthew   6688  6521  0 20:40 pts/0    00:00:00 grep lircd
matthew@tengu3:~$


notably, the file/device /dev/lirc0 does not exist

 ls -altr | grep -i lirc
srw-rw-rw-   1 root   root           0 2008-08-03 20:39 lircd


Is this missing device file only created which it sucessfully detects the correct USB identifier (in my case 05a4). or is their some other problem which is cuasing this device file to be missing.


lsusb
Bus 002 Device 002: ID 05a4:9881 Ortek Technology, Inc.

 diff lirc_mceusb2.c lirc_mceusb2.c.org
133d132
< #define VENDOR_ORTEK          0x05a4
174,175d172
<       /* Ortek Technology */
<       { USB_DEVICE(VENDOR_ORTEK, 0x05a4) },

---

### Post by webwalker on 2008-08-07
Throw me in as a 'me too!' here. I also have the Ortek (which is actually a very nice remote) and am having identical problems.

Hopefully, this problem will be worked out.

---

### Post by superm1 on 2008-08-07
> **tenguzori said:**
> Hi Superm1,

Thanks for you help. Thelast command you gave did look to help as I was able to run the build and install. remote however is still not working. Some further info below on what I have found (/dev/lirc0 missing. Please could you let me know what may be causing this and what I may have done wrong? (I install lircd by simply using the mythbuntu control centre  gui and anbling the microsoft mce remote (new).

Thanks again for this help - Matthew

message log following start of lircd:

Aug  3 20:18:45 tengu3 kernel: [   57.072052] lirc_dev: IR Remote Control driver registered, major 61
Aug  3 20:18:45 tengu3 kernel: [   57.086088] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
Aug  3 20:18:45 tengu3 kernel: [   57.087749]
Aug  3 20:18:45 tengu3 kernel: [   57.087753] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
Aug  3 20:18:45 tengu3 kernel: [   57.087756] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
Aug  3 20:18:45 tengu3 kernel: [   57.124594] usbcore: registered new interface driver lirc_mceusb2

do I need to be worried about the Kernel Tainted message?

I have noticed that following boot, no lircd proc is running


following execution of lircd init script:
 ps -ef | grep lircd
root      6660     1  0 20:39 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0

Lircd dies after running irw:

irw
matthew@tengu3:~$ ps -ef | grep lircd
matthew   6688  6521  0 20:40 pts/0    00:00:00 grep lircd
matthew@tengu3:~$


notably, the file/device /dev/lirc0 does not exist

 ls -altr | grep -i lirc
srw-rw-rw-   1 root   root           0 2008-08-03 20:39 lircd


Is this missing device file only created which it sucessfully detects the correct USB identifier (in my case 05a4). or is their some other problem which is cuasing this device file to be missing.


lsusb
Bus 002 Device 002: ID 05a4:9881 Ortek Technology, Inc.

 diff lirc_mceusb2.c lirc_mceusb2.c.org
133d132
< #define VENDOR_ORTEK          0x05a4
174,175d172
<       /* Ortek Technology */
<       { USB_DEVICE(VENDOR_ORTEK, 0x05a4) },
If you aren't getting a /dev/lirc0 created, then your device ID probably isn't being recognized.  I think you did that patch wrong.  Shouldn't it be USB_DEVICE(VENDOR_ORTEK, 0x9881) ?

---

### Post by ozybushwalker on 2008-08-09
I bought a couple of supposed Windows MCE remote controls (usb IDs immediately following)
> 
myth@mythbox:~$ lsusb
Bus 003 Device 003: ID 04b4:0100 Cypress Semiconductor Corp.
Bus 003 Device 002: ID 1241:e000 Belkin
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
myth@mythbox:~$ 

because I have not been able to get the remote for my Winfast DTV2000 H nor the remote for my Winfast DTV1000 T working reliably. I'm stuck on 7.10 because, despite spending many hours, I've been unable to get 8.04 working on either of my two systems. I've lodged reports on my problems with 8.04 but they haven't been given any obvious attention.

If I'm to use mythTV as the family TV I'll really have to have a working "TV like" remote control for it to gain acceptance. If I can get a remote working in the next couple of weeks and show the significant decision makers that it works and give them a chance to play with a mythTV system I'll probably get funds to get a new system otherwise they'll go out and buy a TV.

Thats the context to my question: How can I rebuild the lirc_mceusb2 driver to recognise either or both of the remotes I have? Based on an earlier reply I attempted to install lirc-modules-src by
> 
myth@mythbox:~$ sudo apt-get install lirc-modules-src
[sudo] password for myth:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lirc-modules-src
myth@mythbox:~$

I have poked around the sources of a number of Linux and FreeBSD device drivers adding USB and PCI ids to their tables of recognised devices so I don't anticipate any issues with that aspect. I do have a system where I have downloaded 7.10 kernel sources and built kernels.

---

### Post by sidrit on 2008-08-10
On hardy , Lirc from the repos solved tha matter for me.
The remote is a MCE one, Philips.

Afterward i as able to configure it with Elisa.

In this miniguide i wrote about it, the 1st part should be able to help you.

[http://sidrit.wordpress.com/2008/08/09/configuring-windows-media-center-remote-control-for-elisa-on-ubuntu-804/]("http://sidrit.wordpress.com/2008/08/09/configuring-windows-media-center-remote-control-for-elisa-on-ubuntu-804/")

best regards
sid

---

### Post by Hayesio on 2008-08-11
> I bought a couple of supposed Windows MCE remote controls (usb IDs immediately following)

Quote:
myth@mythbox:~$ lsusb
Bus 003 Device 003: ID 04b4:0100 Cypress Semiconductor Corp.
Bus 003 Device 002: ID 1241:e000 Belkin
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
myth@mythbox:~$  

because I have not been able to get the remote for my Winfast DTV2000 H nor the remote for my Winfast DTV1000 T working reliably. I'm stuck on 7.10 because, despite spending many hours, I've been unable to get 8.04 working on either of my two systems. I've lodged reports on my problems with 8.04 but they haven't been given any obvious attention.

If I'm to use mythTV as the family TV I'll really have to have a working "TV like" remote control for it to gain acceptance. If I can get a remote working in the next couple of weeks and show the significant decision makers that it works and give them a chance to play with a mythTV system I'll probably get funds to get a new system otherwise they'll go out and buy a TV.

Thats the context to my question: How can I rebuild the lirc_mceusb2 driver to recognise either or both of the remotes I have? Based on an earlier reply I attempted to install lirc-modules-src by

Quote:
myth@mythbox:~$ sudo apt-get install lirc-modules-src
[sudo] password for myth:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lirc-modules-src
myth@mythbox:~$  

I have poked around the sources of a number of Linux and FreeBSD device drivers adding USB and PCI ids to their tables of recognised devices so I don't anticipate any issues with that aspect. I do have a system where I have downloaded 7.10 kernel sources and built kernels. 

ozybushwalker,

I recently purchased a remote from Jaycar which responds with the same ID as one of yours:
```
Bus 003 Device 002: ID 1241:e000 Belkin
```
Is it Digitech brand?  If so, its good news! After this thing drove me insane, i found a post somewhere on the net that said the device is not actually a "mce remote" at all but rather a keyboard! I went back to myth frontend key settings to set the keys and found every button was giving a square at the end of the binding.  It turned out that i just needed to push the button on the remote really hard to get it to register the full binding! Every key on the device is now working.

Hope this helps you.

---

### Post by tenguzori on 2008-08-13
Hi Superm1,

fixed the bug in my code you picked up however after ameding the code and re-runnig through the build/install I am still not getting the /dev/lirc0 device created.

>>If you aren't getting a /dev/lirc0 created, then your device ID probably isn't being recognized. I think you did that patch wrong. Shouldn't it be USB_DEVICE(VENDOR_ORTEK, 0x9881) ? 


Aug 13 20:35:58 tengu3 lircd-0.8.3pre1[6810]: lircd(userspace) ready
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: accepted new client on /dev/lircd
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: could not get file information for /dev/lirc0
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: default_init(): No such file or directory
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: caught signal


 diff lirc_mceusb2.c lirc_mceusb2.c.org
133d132
< #define VENDOR_ORTEK          0x05a4
174,175d172
<       /* Ortek Technology */
<       { USB_DEVICE(VENDOR_ORTEK, 0x9881) },

If you could give any further help, it would be much appreciated. 

Thanks - Matthew

---

### Post by superm1 on 2008-08-13
> **tenguzori said:**
> Hi Superm1,

fixed the bug in my code you picked up however after ameding the code and re-runnig through the build/install I am still not getting the /dev/lirc0 device created.

>>If you aren't getting a /dev/lirc0 created, then your device ID probably isn't being recognized. I think you did that patch wrong. Shouldn't it be USB_DEVICE(VENDOR_ORTEK, 0x9881) ? 


Aug 13 20:35:58 tengu3 lircd-0.8.3pre1[6810]: lircd(userspace) ready
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: accepted new client on /dev/lircd
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: could not get file information for /dev/lirc0
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: default_init(): No such file or directory
Aug 13 20:36:38 tengu3 lircd-0.8.3pre1[6810]: caught signal


 diff lirc_mceusb2.c lirc_mceusb2.c.org
133d132
< #define VENDOR_ORTEK          0x05a4
174,175d172
<       /* Ortek Technology */
<       { USB_DEVICE(VENDOR_ORTEK, 0x9881) },

If you could give any further help, it would be much appreciated. 

Thanks - Matthew
Matthew,
That looks right.  Did you make sure to rmmod the lirc_mceusb2 module and reload it?  If not, did you reboot?

---

### Post by webwalker on 2008-08-15
Mario,

I've gotten the same behavior following the same steps. I'm also working with Matt over at CommandIR to get this working with my CommandIR unit.

The remote is the Ortek VRC-1100
[http://www.ortek.com/prod_detail.asp?pid=127&cname=Mobility%3E%3ERemote%20Control%3E%3EVRC-1100&ppid=103&id=140]("http://www.ortek.com/prod_detail.asp?pid=127&cname=Mobility%3E%3ERemote%20Control%3E%3EVRC-1100&ppid=103&id=140")

Attached is the irrecord raw mode dump of the keys.

Anything that can be done to integrate this going forward would be deeply appreciated. Do you have a contact with LIRC who handles their intake of new devices? Heck, I'll send the device over to someone if they can get it working...my whole rig is dead in the water until it is working.

M

---

### Post by tenguzori on 2008-08-21
Hi Superm1/webwalker,

To confirm I did load and re-load the driver ( and no reboot) with no success.

One bit info I did not give b4: I also have wireless kbd/mouse drivers loaded. keys on the remote which correspond to actual keys (eg "1" and lt/rt/up/dwn cursor keys) are received by this driver. However special keys like "pause" do not work. this is not processed by lircd - as lircd is dead.

If you want me to include any info, please let me know. Otherwise Thanks for all the help you are giving.

Cheers - Matthew.

---

### Post by kingmoffa on 2008-09-09
I also have a mce usb remote clone:

Bus 003 Device 003: ID 04b4:0100 Cypress Semiconductor Corp. 


Has anyone had any luck getting lirc to work with it?

---

### Post by skypher on 2008-09-10
I have an Auvisio remote that uses this chip, too.

It looks like the HID driver grabs the device so you get the behaviour of a... HID device. :)

How does one tell the HID driver to release a device (or not grab it at all)?

  Leslie

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-30
> **kingmoffa said:**
> I also have a mce usb remote clone:

Bus 003 Device 003: ID 04b4:0100 Cypress Semiconductor Corp. 


Has anyone had any luck getting lirc to work with it?

I have the same one no luck yet...

---

### Post by skypher on 2008-12-01
Hi guys,

maybe this will help you: [http://blog.viridian-project.de/2008/10/02/hid-remotes-and-lirc/](http://blog.viridian-project.de/2008/10/02/hid-remotes-and-lirc/)

---

### Post by kowivo on 2009-01-24
Did anyone solved the problem in the meantime?

My Remote is not working, there's no /dev/lirc0.

**Status Quo:**
System: Mythbuntu 8.10
Remote: ID 05a4:9881 Ortek Technology, Inc. (VRC-1100)
Lirc Version: 0.8.3
Modificated and recompiled lirc_mceusb2.c with

[I]#define VENDOR_ORTEK            0x05a4
 /* Ortek Technology */
        { USB_DEVICE(VENDOR_ORTEK, 0x9881) },
[/I]

Modificated /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi 

[I]<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="HID 05a4:9881">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>
[/I]

cat /proc/bus/input/devices

[I]Bus=0003 Vendor=05a4 Product=9881 Version=0110
N: Name="HID 05a4:9881"
P: Phys=usb-0000:00:0b.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input2
U: Uniq=
H: Handlers=kbd event2
B: EV=120013
B: KEY=e080ffdf 1cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=05a4 Product=9881 Version=0110
N: Name="HID 05a4:9881"
P: Phys=usb-0000:00:0b.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.1/input/input3
U: Uniq=
H: Handlers=kbd mouse1 event3
B: EV=17
B: KEY=1f0000 0 2020000 3878 d801d001 1e0000 0 0 0
B: REL=103
B: MSC=10
[/I]

Did "run an lircd instance for both"
[I]#!/bin/sh
 
sudo lircd -Hdev/input -d/dev/input/event2 -o/dev/lircd1 \
  --pidfile=/var/run/lircd1.pid --listen
 
sudo lircd -Hdev/input -d/dev/input/event3 -o/dev/lircd \
  --pidfile=/var/run/lircd.pid --connect=localhost:8765[/I]

**lircd.conf and hardware.conf with dpkg-reconfigure lirc**

[I]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
TRANSMITTER="None"

/etc/lirc/lircd.conf
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb[/I]

Output with lircd --nodaemon
*lircd-0.8.3[7407]: lircd(userspace) ready*

output with irw
[I][I]lircd-0.8.3[7407]: accepted new client on /dev/lircd
lircd-0.8.3[7407]: could not get file information for /dev/lirc0
lircd-0.8.3[7407]: default_init(): No such file or directory
lircd-0.8.3[7407]: caught signal
[/I][/I]

ls -l /dev/lirc*
[I]srw-rw-rw- 1 root root 0 2009-01-24 14:48 /dev/lircd
srw-rw-rw- 1 root root 0 2009-01-24 14:20 /dev/lircd1
prw-r--r-- 1 root root 0 2009-01-24 13:52 /dev/lircm[/I]

Something forgotten?
I hope you can help me - thanks in advance 

Volker

---

### Post by jdoggman on 2009-02-02
I have this same remote, seems nice and is of good quality.  I am also having trouble getting it to function properly.  

The post at [http://blog.viridian-project.de/2008/10/02/hid-remotes-and-lirc/](http://blog.viridian-project.de/2008/10/02/hid-remotes-and-lirc/) helps in identifying the initial problem (it being seen as multiple devices) but the fix has not worked for me. 

XBMC (on hardy) seem to be the closest I've seen [http://xbmc.org/forum/showthread.php?p=245159](http://xbmc.org/forum/showthread.php?p=245159) .  I still am unable to get this to work for me but it looks to have addressed all the components of the issue. 

Any help on this matter would be greatly appreciated as I am to the point of pulling my hair out over this.

---

### Post by rich_is_bored on 2009-02-12
I just got the VRC-1100 and found that LIRC will be of no use with it.

The Ortek remote doesn't pass IR codes onto the operating system so LIRC will never have any codes to interpret. The receiver seems to do all the interpretation and for most of the buttons it emulates keyboard input. This thing is pretty much a wireless keyboard/mouse combo packaged in a remote controlled shaped case.

I found an interesting thread on another forum that talks about why some buttons work as key presses and others don't...

[http://forum.melloware.com/viewtopic.php?f=1&t=6287](http://forum.melloware.com/viewtopic.php?f=1&t=6287)

So for buttons that work, the IR receiver is sending key codes. For the buttons that don't it's sending USB HID data.

You can monitor the HID data by finding the mount points for the remote. In my case the device mounts itself at /dev/input/event4 and /dev/input/event5. If you monitor the output of those locations using the cat command and then press the non-functional buttons, you'll see garbage characters spewed out as output.

Getting all the buttons to work is just a matter of interpreting the HID data correctly. Unfortunately I don't have much experience with Linux so I don't know if a device driver is in order or if there is some pre-existing daemon that will do the job.

---

### Post by lpearson on 2009-05-31
The Ortek remote can be made fully functional.  The dev/input module for lirc is for exactly this kind of remote, and Mythbuntu's lirc setup even has an option for it.  The only trick with the Ortek chipset remotes is to hack /etc/init.d/lirc to start two communicating lirc processes that will talk to each other, since the remote uses multiple HID devices for various buttons. 

I'll post later with more information about the details involved in getting it working.

---

### Post by My Name on 2009-06-01
oooooo please do as I have been struggling to get a remote to work !!!

---

### Post by thedaver on 2009-09-13
Sorry to bump an old message, but I've found myself in the same situation with the Ortek VRC 1100...  did this get resolved?  I'm having trouble finding closure on Ubuntu or Mythbuntu forums.  THANKS!

---

### Post by dnlallred on 2009-10-27
What version of ubuntu are you using.  My vrc-1100 works great. I had to use the xmodmap to get it to work. If anyone needs help just let me know and I will try and walk you through it. I am not using lirc at all by the way.

---

### Post by Lampje on 2009-11-01
Hello,
 

 I just started using mythbuntu 9.4 for my media center.
 And I have the same problem with my remote control.
 I have a ms-tech case with a windows media center compatible remote. Incl. Usb-ir receiver.
 

 This is my output of lsusb:
 

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 005 Device 002: ID 1130:6604 Tenx Technology, Inc.  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 And .cat /proc/bus/input/devices
 
I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1130 Product=6604 Version=0110
N: Name="MCE-IR-Receiver"
P: Phys=usb-0000:00:1d.3-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=e080ffdf 1cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1130 Product=6604 Version=0110
N: Name="MCE-IR-Receiver"
P: Phys=usb-0000:00:1d.3-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input5
U: Uniq=
H: Handlers=kbd mouse1 event5 
B: EV=17
B: KEY=1f0000 0 2020000 3878 d801d001 1e0000 0 0 0
B: REL=103
B: MSC=10

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0005 Version=0051
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse2 event7 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

---

### Post by dnlallred on 2009-11-05
Does any of your buttons work. If you just plug it in. Because most of mine just worked the few that didn't work is what xmodmap is for.
run xev at the command line and see what output you get from each button press.

---

### Post by Lampje on 2009-11-08
> **dnlallred said:**
> Does any of your buttons work. If you just plug it in. Because most of mine just worked the few that didn't work is what xmodmap is for.

Nothing works

> **dnlallred said:**
> run xev at the command line and see what output you get from each button press.

When I run xev nothing happens only wen I move the mouse    	 	 	 	 	or type on the keyboard.

---

### Post by chadparry on 2009-11-15
> **dnlallred said:**
> What version of ubuntu are you using.  My vrc-1100 works great. I had to use the xmodmap to get it to work. If anyone needs help just let me know and I will try and walk you through it. I am not using lirc at all by the way.

DNLAllred, I have been working with my VNC-1100 for weeks and I still don't have all the keys working. Could you please post your xmodmap, and any hints that you think I might have missed? Since you've got a working recipe, I think it would probably help out a lot of people for you to post it here.

Do you mind also clarifying whether any of the following behaviors work for you:

[LIST]
[*]The Play and Pause buttons are interpreted as separate buttons; (my system can never distinguish them).
[*]The hash (#) key is mapped to the correct character; (mine produces a combination of numbers).
[*]Volume continues to change when a volume key is held down; (mine requires me to repeatedly press the volume key).
[*]Multimedia keys are not intercepted by the window manager; (I had to use custom application shortcuts just to get the volume keys to propagate to an application).
[*]Mute button toggles mute once; (mine frequently repeats the key press, toggling it back to its original state).
[/LIST]
 Thanks!

---

### Post by anton610 on 2009-11-19
Yes please give us a walkthrou!

Thanks!

---

### Post by anton610 on 2009-12-03
Here is the solution:
 
[http://xbmc.org/forum/showthread.php?t=63152](http://xbmc.org/forum/showthread.php?t=63152)
 
 
reagards

---

### Post by fuzzyworbles on 2010-01-28
the above link works for 9.10 if you add the suggested line mentioned at the bottom of the post. now i just have to figure out how to make it work with mythtv.

---

