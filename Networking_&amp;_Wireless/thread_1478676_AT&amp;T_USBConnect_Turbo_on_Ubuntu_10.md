---
title: "AT&amp;T USBConnect Turbo on Ubuntu 10"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by chrisjgilmore on 2010-05-10
OK so I'm trying and have been trying for a couple of days to get my new AT&T laptop connect card working on my new Ubuntu install of 10.04.  Below are the excerpts of my lsusb query, wvdial.conf and contents of my /dev directory. It appears to me (I'm a novice) that the proper file is not referenced in the wvdial.conf but i can't figure out which one should be referenced.... Can anyone offer some help?

_**lsusb query response**_
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
***Bus 002 Device 003: ID 1004:613f LG Electronics, Inc. ***
Bus 002 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 17ef:1004 Lenovo 
Bus 001 Device 002: ID 13fe:2240 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

_**wvdial.conf**_
[Dialer 3G]
Modem = ***/dev/ttyACM0***
Init = ATZ
Init1 = AT+CGDCONT=1,"IP","proxy"
Stupid mode = 1
phone= *99#
Baud = 921600
Username = [email]ISPDA@CINGULARGPRS.COM[/email]
Password = CINGULAR1
Init1 = ATZ 
Auto Reconnect = on 
Carrier Check = no

_**/dev contents**_
adsp             loop6               random      tty10  tty41    usbmon1
agpgart          loop7               rfkill      tty11  tty42    usbmon2
audio            mapper              root        tty12  tty43    usbmon3
block            mcelog              rtc         tty13  tty44    usbmon4
bsg              mem                 rtc0        tty14  tty45    usbmon5
bus              mixer               scd0        tty15  tty46    usbmon6
cdrom            net                 scd1        tty16  tty47    usbmon7
cdrom1           network_latency     sda         tty17  tty48    usbmon8
cdrw             network_throughput  sda1        tty18  tty49    v4l
char             null                sda2        tty19  tty5     vboxdrv
console          nvram               sda5        tty2   tty50    vboxnetctl
core             oldmem              sdb         tty20  tty51    vcs
cpu_dma_latency  pktcdvd             sdb1        tty21  tty52    vcs1
disk             port                sdc         tty22  tty53    vcs2
dri              ppp                 sdc1        tty23  tty54    vcs3
dsp              psaux               sequencer   tty24  tty55    vcs4
dvd              ptmx                sequencer2  tty25  tty56    vcs5
dvdrw            pts                 sg0         tty26  tty57    vcs6
ecryptfs         ram0                sg1         tty27  tty58    vcs7
fb0              ram1                sg2         tty28  tty59    vcsa
fd               ram10               sg3         tty29  tty6     vcsa1
full             ram11               sg4         tty3   tty60    vcsa2
fuse             ram12               shm         tty30  tty61    vcsa3
hidraw0          ram13               snapshot    tty31  tty62    vcsa4
hpet             ram14               snd         tty32  tty63    vcsa5
input            ram15               sndstat     tty33  tty7     vcsa6
kmsg             ram2                sr0         tty34  tty8     vcsa7
log              ram3                sr1         tty35  tty9     vga_arbiter
loop0            ram4                stderr      tty36  ttyS0    video0
loop1            ram5                stdin       tty37  ttyS1    zero
loop2            ram6                stdout      tty38  ttyS2
loop3            ram7                tty         tty39  ttyS3
loop4            ram8                tty0        tty4   urandom
loop5            ram9                tty1        tty40  usbmon0


Like I said any help is appreciated this is what is keeping me from getting off M$ for not only my home but also my work computer.

---

### Post by Charles07 on 2010-05-19
Bump.

---

### Post by Charles07 on 2010-05-19
This appears to be the one from LG.

---

### Post by pdc on 2010-05-20
these devices need to be seen as a modem; (some are seen initially as a virtual CD-ROM device);

I think this is your device

[http://www.netbooktech.com/2010/03/08/atts-two-new-laptopconnect-cards-lg-turbo-and-option-velocity/](http://www.netbooktech.com/2010/03/08/atts-two-new-laptopconnect-cards-lg-turbo-and-option-velocity/)

from the ID you give

> ID 1004:613f LG Electronics, Inc. 

that looks very like the ID of a device that has not flipped; meaning it is seen as a virtual CD-ROM device and I quote it here

> # LG HDM-2100 (EVDO Rev.A USB modem)
#
# Contributor: Jérôme Oufella

;DefaultVendor= 0x1004
;**DefaultProduct**=0x**607f**


....... I know it is not the ID of your device, but is close;

so if you tell us what 

> dmesg | grep tty says when you copy and paste this command and type it into a terminal

if it says 

> ttyACM0 you can use wvdial

but if it does not, the device still needs to be flipped ........

..... also ...... where did you get the wvdial script from? Just wondering if it is all correct .......

---

### Post by trippinnik on 2010-06-18
Any luck getting this to work?  My boss just gave me one of these, and I'm going on vacation.  I don't want to drag one of the big Windows PCs with me just to use this card.

I had a Mercury from Sierra and it worked about a year ago, just plugged it in and connected.  I've tried making a new connection with NetworkManager but no go.  

Anyone have any success?

---

### Post by pdc on 2010-06-18
see what

> dmesg | grep tty 

gives you .......... as above ...............

---

### Post by trippinnik on 2010-06-18
[    0.000000] console [tty0] enabled
[    4.232633] tty tty10: hash matches


I guess I need to "flip" it? I saw something about a script that does this, is that right? And I have to use wvdial to connect, not NetworkManager?

---

### Post by pdc on 2010-06-18
yes;

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

is the home for usb_modeswitch

they send you here for the debian package

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

1.1.2 seems the latest

it should autoconfigure

reboot after install

try dmesg again; hopefully you will see new data

---

### Post by trippinnik on 2010-06-18
I installed those packages but dmesg |grep tty:
[    0.000000] console [tty0] enabled

---

### Post by trippinnik on 2010-06-18
I think it's just not installed right yet (install is apparently broken in live system atm) I will try again on the PC I actually have Ubuntu installed on at home.

---

### Post by alexfish on 2010-06-18
hi

the device does not appear to be listed in the usb modeswitch data

when the device is connected do any icons appear on the desktop

if so try right click and eject or safely remove commands from the menu , or use the disk utility from the menu

see if any changes in the ID's check with  the lsusb command from the terminal

if there are any changes in the ID's try the modprobe command from the terminal

Code:

sudo modprobe usbserial vendor=0xID  product=0xID

Example:

sudo modprobe usbserial vendor=0x19d2  product=0x0063


regards

alexfish

---

### Post by trippinnik on 2010-06-19
I did see a thread on the usb_modeswitch forum that ejecting the device might work.

I've tried "Safely Remove" and "Eject" but the usb id doesn't change. I'm going to dive into the info on the usb_modeswitch site about manual doing the flip since it's a new device maybe it's not on the list yet.

---

### Post by pdc on 2010-06-21
join their forum; Josh runs the forum and oversees usb_modeswitch;

seek his help; he is very helpful and knowledgable;

google on the usb_modeswitch; google will give it to you

---

### Post by trippinnik on 2010-06-22
Cool got it working.  I found this thread over there: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=412](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=412) so I built the latest source which has the device added and now it's working.

---

### Post by pdc on 2010-06-22
great work! well done

somewhere; you can add SOLVED to the thread; you can then claim the credit for it

---

### Post by Charles07 on 2010-06-22
Thanks!

---

### Post by trippinnik on 2010-06-23
Solved.

---

