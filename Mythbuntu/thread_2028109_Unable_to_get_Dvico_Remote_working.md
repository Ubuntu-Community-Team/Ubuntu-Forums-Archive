---
title: "Unable to get Dvico Remote working"
date: 2012-07-17
forum: Mythbuntu
---

### Post by rxm307 on 2012-07-17
I previously had this working under mythdora

[http://www.pccasegear.com/images/remotemce3.jpg](http://www.pccasegear.com/images/remotemce3.jpg)

Here are my previously working config files from fedora

[http://www.mythdora.com/?q=node/3734](http://www.mythdora.com/?q=node/3734)

I really want to move over to unbuntu for the nightly builds and ease of dist updating

---

### Post by rxm307 on 2012-08-13
Please can someone post some suggestions on getting this working with the new lirc?

---

### Post by Lester_Burnham on 2012-08-14
Hi,

Have you selected the remote in mythbuntu control centre?
After that give us a look at your hardware.conf and lsusb
Do you see a /dev/usb/hiddev0 or something like that in /dev folder.
With older dvico remotes I used to have to change my /etc/lirc/hardware.conf intro from /dev/lirc0 to above.
Make sure it exists in /dev before just changing anything.

Lester

---

### Post by rxm307 on 2012-08-14
Yes that is the first thing I did

Have tried changing the hardware.conf as you suggested however still no good, please see below

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="DViCO USB Remote"
REMOTE_MODULES=""
REMOTE_DRIVER="dvico"
#REMOTE_DEVICE="/dev/lirc0"
REMOTE_DEVICE="/dev/usb/hiddev0"
REMOTE_SOCKET="/var/run/lirc/lircd"
REMOTE_LIRCD_CONF="dvico/lircd.conf.fusionHDTV"
REMOTE_LIRCD_ARGS=""



$ ls -al /dev/usb/hiddev*
crw------- 1 root root 180, 96 Aug 15 01:52 /dev/usb/hiddev0

---

### Post by Lester_Burnham on 2012-08-15
Hi,

Try having a look [here]("http://forum.xbmc.org/showthread.php?tid=104541") down just after section 2.1
You might just need the ir-lirc-codec and below it to send across to lirc.

I have seen pages with a single command to convert kernel-ir to lirc, but I can't find them now.

Lester

---

### Post by rxm307 on 2012-08-15
Nope that doesn't work either, seems there are alot of articles about the rc6 mce remotes but not many about the Dvico remotes under the new lirc

$ sudo modprobe ir-lirc-codec

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0fe9:9010 DVICO


$ ir-keytable -p LIRC
Couldn't find any node at /sys/class/rc/rc*.

---

### Post by Lester_Burnham on 2012-08-15
Hi,

What does this below give you
```
dmesg | grep lirc
dmesg | grep DVICO
```
Try lower case too maybe. See if we can see a module loaded for dvico.
If so, maybe hardware.conf is the problem. Might need to use an event ID in there?

I'm still waiting for some one in the know to chime in :)

Lester

---

### Post by nickrout on 2012-08-15
> **Lester_Burnham said:**
> Hi,

What does this below give you
```
dmesg | grep lirc
dmesg | grep DVICO
```
Try lower case too maybe. See if we can see a module loaded for dvico.
If so, maybe hardware.conf is the problem. Might need to use an event ID in there?

I'm still waiting for some one in the know to chime in :)

Lester


To check upper or lower case use grep -i (case Insensitive).

-i also works with locate.

---

### Post by rxm307 on 2012-08-15
dmesg | grep -i lirc
[69904.537681] lirc_dev: IR Remote Control driver registered, major 250
[69904.576688] IR LIRC bridge handler initialized

$ dmesg | grep -i DVICO
[    1.286519] generic-usb 0003:0FE9:9010.0001: hiddev0,hidraw0: USB HID v1.10 Device [DVICO DVICO USB HID Remocon V1.00] on usb-0000:00:1d.1-2/input0

by event ID do you mean one of these?
$ ls -al /dev/input/
total 0
drwxr-xr-x  3 root root    240 Aug 15 01:52 .
drwxr-xr-x 16 root root   4240 Aug 15 12:19 ..
drwxr-xr-x  2 root root    120 Aug 15 01:52 by-path
crw-r-----  1 root root 13, 64 Aug 15 01:52 event0
crw-r-----  1 root root 13, 65 Aug 15 01:52 event1
crw-r-----  1 root root 13, 66 Aug 15 01:52 event2
crw-r-----  1 root root 13, 67 Aug 15 01:52 event3
crw-r-----  1 root root 13, 68 Aug 15 01:52 event4
crw-r-----  1 root root 13, 69 Aug 15 01:52 event5
crw-r-----  1 root root 13, 70 Aug 15 01:52 event6
crw-r-----  1 root root 13, 63 Aug 15 01:52 mice
crw-r-----  1 root root 13, 32 Aug 15 01:52 mouse0

---

### Post by Lester_Burnham on 2012-08-16
Hi,

Yeah, something the likes of this
REMOTE_DEVICE="/dev/input/by-id/usb-Philips_eHome_Infrared_Transceiver_PH00Q7WZ-event-if00"
Or if you can find which /dev/input/event* it is.

It's just something else to try. Have you tried other dvico remotes in the MCC?
Otherwise you can install ir-keytable and go the kernel ir route.
If you do, run the following commands
```
sudo ir-keytable        # shows the supported protocols
sudo ir-keytable -t      # press some buttons
```
If it works, you'll then need some devinput files.

Lester

---

### Post by rxm307 on 2012-08-16
Thats just it I dont have any /dev/input/by-id

$ ls -al /dev/input/by-path/
total 0
drwxr-xr-x 2 root root 120 Aug 15 01:52 .
drwxr-xr-x 3 root root 240 Aug 15 01:52 ..
lrwxrwxrwx 1 root root   9 Aug 15 01:52 platform-i8042-serio-0-event-kbd -> ../event3
lrwxrwxrwx 1 root root   9 Aug 15 01:52 platform-i8042-serio-1-event-mouse -> ../event5
lrwxrwxrwx 1 root root   9 Aug 15 01:52 platform-i8042-serio-1-mouse -> ../mouse0
lrwxrwxrwx 1 root root   9 Aug 15 01:52 platform-thinkpad_acpi-event -> ../event6

$ sudo ir-keytable
Couldn't find any node at /sys/class/rc/rc*.

Really appreciate all the help and ideas by the way

---

### Post by Lester_Burnham on 2012-08-16
Hi,

No problems. It seems there's no others hanging out here with this remote.
You need to install ir-keytable first.
```
sudo apt-get install ir-keytable
```
From memory you need to stop lirc while testing.
```
sudo service lirc stop
```

Lester

Ps: just a quick stupid question. You know the batteries in the remote are good. No silly coindicences going on :)

---

### Post by rxm307 on 2012-08-16
Yep brand new batteries

ir-keytable is already installed

I read somewhere that removing lirc may also work on recent kernels so I may also try this

worse case I can always reinstall

---

### Post by Lester_Burnham on 2012-08-16
Hmmm. So when you stop lirc, does ir-keytable respond?

Lester

---

### Post by rxm307 on 2012-08-16
Nope :(

same message 

/sys/class/rc/: No such file or directory

$ ls -al /sys/class/
total 0
drwxr-xr-x 49 root root 0 Aug 16 22:39 .
drwxr-xr-x 12 root root 0 Aug 16 22:39 ..
drwxr-xr-x  2 root root 0 Aug 16 22:39 ata_device
drwxr-xr-x  2 root root 0 Aug 16 22:39 ata_link
drwxr-xr-x  2 root root 0 Aug 16 22:39 ata_port
drwxr-xr-x  2 root root 0 Aug 16 22:39 backlight
drwxr-xr-x  2 root root 0 Aug 16 22:39 bdi
drwxr-xr-x  2 root root 0 Aug 16 22:39 block
drwxr-xr-x  2 root root 0 Aug 16 22:41 bluetooth
drwxr-xr-x  2 root root 0 Aug 16 22:39 bsg
drwxr-xr-x  2 root root 0 Aug 16 22:39 devfreq
drwxr-xr-x  2 root root 0 Aug 16 22:39 dma
drwxr-xr-x  2 root root 0 Aug 16 22:39 dmi
drwxr-xr-x  2 root root 0 Aug 16 22:40 drm
drwxr-xr-x  2 root root 0 Aug 16 22:39 firmware
drwxr-xr-x  2 root root 0 Aug 16 22:39 gpio
drwxr-xr-x  2 root root 0 Aug 16 22:39 graphics
drwxr-xr-x  2 root root 0 Aug 16 22:39 hidraw
drwxr-xr-x  2 root root 0 Aug 16 22:39 hwmon
drwxr-xr-x  2 root root 0 Aug 16 22:39 i2c-adapter
drwxr-xr-x  2 root root 0 Aug 16 22:40 ieee80211
drwxr-xr-x  2 root root 0 Aug 16 22:39 input
drwxr-xr-x  2 root root 0 Aug 16 22:39 leds
drwxr-xr-x  2 root root 0 Aug 16 22:39 mdio_bus
drwxr-xr-x  2 root root 0 Aug 16 22:39 mem
drwxr-xr-x  2 root root 0 Aug 16 22:39 misc
drwxr-xr-x  2 root root 0 Aug 16 22:39 mmc_host
drwxr-xr-x  2 root root 0 Aug 16 22:39 net
drwxr-xr-x  2 root root 0 Aug 16 22:39 pci_bus
drwxr-xr-x  2 root root 0 Aug 16 22:40 pcmcia_socket
drwxr-xr-x  2 root root 0 Aug 16 22:39 power_supply
drwxr-xr-x  2 root root 0 Aug 16 22:40 ppdev
drwxr-xr-x  2 root root 0 Aug 16 22:39 ppp
drwxr-xr-x  2 root root 0 Aug 16 22:40 printer
drwxr-xr-x  2 root root 0 Aug 16 22:39 regulator
drwxr-xr-x  2 root root 0 Aug 16 22:39 rfkill
drwxr-xr-x  2 root root 0 Aug 16 22:39 rtc
drwxr-xr-x  2 root root 0 Aug 16 22:39 scsi_device
drwxr-xr-x  2 root root 0 Aug 16 22:39 scsi_disk
drwxr-xr-x  2 root root 0 Aug 16 22:39 scsi_generic
drwxr-xr-x  2 root root 0 Aug 16 22:39 scsi_host
drwxr-xr-x  2 root root 0 Aug 16 22:40 sound
drwxr-xr-x  2 root root 0 Aug 16 22:39 spi_master
drwxr-xr-x  2 root root 0 Aug 16 22:39 thermal
drwxr-xr-x  2 root root 0 Aug 16 22:39 tty
drwxr-xr-x  2 root root 0 Aug 16 22:39 usb
drwxr-xr-x  2 root root 0 Aug 16 22:39 usbmon
drwxr-xr-x  2 root root 0 Aug 16 22:39 vc
drwxr-xr-x  2 root root 0 Aug 16 22:39 vtconsole

---

### Post by Lester_Burnham on 2012-08-17
Not looking good here :)
Is the receiver USB or plugged into the DVB card?  I'm guessing USB, withe the /dev/usb/hiddev0

Lester

Edit: have you tried removing "/var/run/lirc/lircd" fom socket in hardware.conf
My mce remote doesn't have that line filled out.

Also, does the path to this file "lircd.conf.fusionHDTV" exist in your lircd.conf and in the actual directory that it's meant to be in?

---

### Post by Lester_Burnham on 2012-08-18
Well it seems there is something weird going on with mythbuntu 12.04 (64bit).
I just did a re-install because my SSD on a play system was not aligned correctly. It's an ION2 based zbox ID41.

I'm seeing all the same problems, as the OP but with a MCE USB remote (old type). I tried devinput and lirc!
The only thing I did differently to normal was not having the receiver plugged in when I installed and setup the system.

Might even try the 32bit version unless someone can suggest the correct path for trouble shooting.
Time for a search :)

Lester

---

### Post by rxm307 on 2012-08-19
This is also a 32bit system, I dont currently have a 64bit capable test system although I could bring up a VM

---

### Post by Lester_Burnham on 2012-08-19
It might be to do with this [lirc bug]("http://ubuntuforums.org/showthread.php?t=2039065") 
I'm installing again now and will try the suggested fixes.

Lester

EDIT: I just did an install of 12.04 64bit without updates and lirc works OK!
Downside, now I might be stuck with some of the issues from early on in 12.04 :)

---

### Post by rxm307 on 2012-08-26
Unfortunantly I cant do a fresh 32bit install as the old laptop I'm testing on doesn't support PAE :(

I'll continue trying to test this in a 64bit VM

---

### Post by LarryBari on 2012-09-04
Hi,

I too have a DViCO USB Remote (for DViCO Fusion HDTV Lite DVB) and cannot lirc to work with it 12.04. I did have it working with 12.04 32 bit but recently I did a fresh install with 64 bit and updated hardware.

Not a huge issue as I do have a wireless keyboard, but I've still got all the keys from the Dvico remote mapped to my learning Yamaha receiver remote.

Anyway, I've got the same configuration settings as you guys and am also happy to try things. I dont get any joy out of irw and am unsure as to the correct settings in /etc/lirc/hardware.conf and /etc/lirc/lircd.conf.  Settings are as follows

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="DVICO"
REMOTE_MODULES=""
REMOTE_DRIVER="dvico"
REMOTE_DEVICE="/dev/usb/hiddev0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="dvico/lircd.conf.fusionHDTV"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

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

```

and /usr/share/lirc/remotes/dvico/lircd.conf.fusionHDTV

```
# contributed by  Chris Pascoe
#
# brand:                       DVICO
# model no. of remote control: DVB-T
# devices being controlled by this remote:
#

begin remote

  name  DVICO
  bits            32
  eps             0
  aeps            0

  one             0     0
  zero            0     0
  pre_data_bits   32
  pre_data 0x10046
  gap          195755
  post_data_bits  0
  toggle_bit     0

``` etc

Just not sure what I'm doing wrong. 
Cheers, Larry

---

