---
title: "MDC525UPA from ONDA communication"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by giuper on 2009-04-15
Hi,
I am trying to install the MDC525UPA usb modem from ONDA communication with no success. I am using ubuntu 8.10 with kernel 2.6.27-11
The vendor does not provide drivers for ubuntu 8.10 (only up to ubuntu 8.4).
Do you know of any workaround?

Thanks
--pino

---

### Post by openversus on 2010-01-08
Hi to all!
I'm trying to use the same internet key (I use the [Ducati TIM]("http://http://www.tim.it/consumer/c365/i3329/o77171/prodotto.do")) but I have also prolem with it.
Someone can 'help me find the solution?
Thanks and buena vida!
[I][SIZE="1"]

PS: I use Ubuntu 9.10[/SIZE][/I]

---

### Post by pdc on 2010-01-08
looks like this is a ZTE MF638 device

when you plug it into Karmic 9.10 it will likely appear as an icon on the desktop;

if open a terminal and type in

> lsusb

the modem should be mentioned

hint: it should be 0x19d2:0x2000

if you now RIGHT-CLICK on the icon for the modem (on the desktop), and select EJECT from the menu, the icon should disappear

and if you type

> lsusb

into the terminal, the numbers should have changed for the modem

hint: it should be 0x19d2:0x0037

if you now RIGHT-CLICK on network manager (top right)

select EDIT CONNECTIONS

select MOBILE BROADBAND

select ADD

choose your country; provider; accept; close

now LEFT-CLICK on network manager

is your selection there? click: does it connect?

I suspect your device is a ZTE MF638 (aka "Onda MDC525UP")

---

### Post by openversus on 2010-01-11
Hi pdc. Thank you for your reply.
I tried to do what you write me:

doing lsusb: 
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

After this, I cannot find the icon for the modem  to do RIGHT-CLICK on (on the desktop)... where is? I cannot find it...
Then I tried with network manager but no connecion...
I fact I also tried GPPP but no modem is detected.
About device, I installed USB ModeSwitch with ZTE MF638 supported... but it's still not working... :confused:

---

### Post by pdc on 2010-01-11
OK;

you are using the 8.10 version of Ubuntu, so my advice about an icon on the desktop will not work;

you say you have installed usb_modeswitch;

if you have, then the lsusb should not show the 19d2:2000 

instead it should be 19d2:0037

which version of usb_modeswitch did you install please?

Have a read at the final message of this post ie #post106

[http://ubuntuforums.org/showthread.php?t=1147685&page=11](http://ubuntuforums.org/showthread.php?t=1147685&page=11)

George Vitas is very good on mobile broadband

He refers you back to a post #96 he did; in this same post

He reports on Ubuntu 8.10 and usb_modeswitch and a ZTE MF modem, so all very related to your topic;

( I believe your modem is a ZTE638 (happy to be corrected on this)

so your entry in the config file for usb_modeswitch should be 

> # ZTE MF638 (aka "Onda MDC525UP")
#
# Contributor: andylog

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0037

# only for reference and 0.x versions
MessageEndpoint=0x01

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"




I will check back later

---

### Post by openversus on 2010-01-11
I tried again with the instructions in the post quoted  in ubuntu forums italian ([http://www.andreaboscolo.it/2008/03/12/onda-mt512hs-tim/](http://www.andreaboscolo.it/2008/03/12/onda-mt512hs-tim/)) by installing even Kppp. I think it's the same you quote:
now the out come for ONDA mdc525upa is recognized as follows:

[i] lsusb
Bus 002 Device 002: ID 046d: c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2: 2000 ONDA Communication SpA
Bus 001 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub

tail-f / var / log / syslog
Yoda Jan 11 23:02:35 wpa_supplicant [1726]: CTRL-EVENT-SCAN-RESULTS
Yoda Jan 11 23:02:37 kernel: [1124.404449] usb 1-4: USB disconnect, address 3
Yoda Jan 11 23:03:30 kernel: [1177.860060] usb 1-4: new full speed USB device using uhci_hcd and address 4
Yoda Jan 11 23:03:30 kernel: [1178.003391] usb 1-4: configuration # 1 chosen from 1 choice
Yoda Jan 11 23:03:35 wpa_supplicant [1726]: CTRL-EVENT-SCAN-RESULTS
Yoda Jan 11 23:04:35 wpa_supplicant [1726]: CTRL-EVENT-SCAN-RESULTS
Yoda Jan 11 23:05:35 wpa_supplicant [1726]: CTRL-EVENT-SCAN-RESULTS
Yoda Jan 11 23:06:31 udevd [433]: Worker [1661] returned unexpectedly with status 0x0100
Yoda Jan 11 23:06:31 udevd [433]: Worker [1661] failed while handling '/ devices/pci0000: 00/0000: 00:1 d.7/usb1/1-4/1-4: 1.0' [/ i]

But the result is' always the same: both GPPP that on kppp modem is not recognized ....
Need help ... >: (

---

### Post by openversus on 2010-01-11
PS: I use 9.10

---

### Post by pdc on 2010-01-11
Yes you use 9.10; that was why I initially said to look for an icon;

and then I was misled by the first post from last April !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

anyway, back on track now ............................

we need to ensure two things:

1) "flip" the device so it is no longer seen as a virtual storage device
2) having done that, connect

your lsusb shows you have NOT flipped the device; it is still seen as a CD-ROM storage device (I believe);

If you are using Karmic 9.10

1) turn your computer on; look carefully at the screen; see what icons are there 
2) plug the modem in; now has anything changed ...
3) surely you get an icon on your desktop .... (meaning the starting screen your computer shows when it has finished booting up)

---

### Post by openversus on 2010-01-12
Ok... 
I do what you write pdc, 
but I dont' see any icon on desktop.
I also install the latest [usb_modeswitch]("http://http://www.draisberghof.de/usb_modeswitch/") and after this I see some changement that I show you:

[I] tail -f /var/log/syslog 
Jan 12 17:19:48 Yoda wpa_supplicant[1800]: CTRL-EVENT-SCAN-RESULTS 
Jan 12 17:20:15 Yoda kernel: [ 1153.628054] usb 1-4: new high speed USB device using ehci_hcd and address 10
Jan 12 17:20:15 Yoda kernel: [ 1153.771419] usb 1-4: configuration #1 chosen from 1 choice
Jan 12 17:20:15 Yoda kernel: [ 1153.778335] scsi9 : SCSI emulation for USB Mass Storage devices
Jan 12 17:20:15 Yoda kernel: [ 1153.778551] usb-storage: device found at 10
Jan 12 17:20:15 Yoda kernel: [ 1153.778556] usb-storage: waiting for device to settle before scanning[/I]

So it seems there's something new... but modem is not detected...](*,)

---

### Post by alexfish on 2010-01-12
hi

from the terminal try

Code:

lsusb

---

### Post by openversus on 2010-01-12
this is the output:

[I]lsusb
Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 024: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

nothing new...](*,)

---

### Post by pdc on 2010-01-12
so alex asked you for the lsusb and it confirms that your system still sees this device as a CD-ROM storage device;

you need to flip it;

can we just check which kernel you are running?

Can you type 

> uname -r

in a terminal and tell us the result please

---

### Post by openversus on 2010-01-13
that's the kernel:

uname -r 
2.6.31-17-generic

---

### Post by pdc on 2010-01-14
well; you need to flip the device

all I do is post this again

> If you are using Karmic 9.10

1) turn your computer on; **_look carefully at the screen; see what icons are there _**
2) plug the modem in; **_now has anything changed_** ...
3) surely you get an icon on your desktop .... (meaning the starting screen your computer shows when it has finished booting up)

---

### Post by openversus on 2010-01-14
real sorry but I try a lot of time and I dont' see any icon on dektop :-(

---

### Post by pdc on 2010-01-14
OK;

I think you need to do two things:

1) flip the device, so it is no longer seen as a storage device
2)connect

if we follow the advice of George Vitas in post #104 here

[http://ubuntuforums.org/showthread.php?t=1147685&page=11](http://ubuntuforums.org/showthread.php?t=1147685&page=11)

one creates a udev rule as he advises:

> sudo gedit /etc/udev/rules.d/zte_eject.rules


and paste in the line he quotes: my computer won't let me copy it for some reason ......

save; close; turn off computer; start again with modem plugged in

type > lsusb and tell us what you get
]

---

### Post by openversus on 2010-01-15
That's what I get after file creation and reboot with key: after grub I received this message...

[I]Ubuntu 9.10 MyPC tty1

MyPC login * nmbd is running
				[120.634766] hub 1-0:1.0: port 4 disabled by hub (EMI?). re-enabilng
[121.114151] hub 1-0:1.0: port 4 disbled by hub (EMI?). re-enabilng
[121.584667] hub 1-0:1.0: port 4 disbled by hub (EMI?). re-enabilng
[121.055182] hub 1-0:1.0: port 4 disbled by hub (EMI?). re-enabilng
[121.525820] hub 1-0:1.0: port 4 disbled by hub (EMI?). re-enabilng
[121.360035] usb 1-4: device descripter read/64. error -71[/I]

then arrive the login screen.
After login in the terminal lsusb:

[I]lsusb
Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]


That's all... and no modem is found in my system... :roll:

---

### Post by alexfish on 2010-01-15
hi

do you have any versions of usb modeswitch installed

---

### Post by pdc on 2010-01-15
usb_modeswitch is a programme to "flip" a device from being seen as CD-ROM to being seen as modem

I saw this description of how to install usb_modeswitch on their forum

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=284](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=284)

it is the post by sakis, from Athens: post #2

He says

> There is now a better way to install usb_modeswitch with more benefits: 
* You do not need to edit any file for your modem to appear. 
This new mode is called "integrated" install. 

**To install usb_modeswitch using the new method, unplug your modem (if plugged) and try the following**: 

I thought it was very helpful; copy and paste the commands

[B][I][U]since that posting: 1.0.7 is the latest programme, so I have inserted 1.0.7 in the commands below
[/U][/I][/B]
open a terminal

> cd /tmp

> wget  http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.7.tar.bz2"

> tar -xjvf usb_modeswitch-1.0.7.tar.bz2

> cd usb_modeswitch-1.0.7

> sudo modprobe -r -v usbserial

> sudo make integrated_install 

that should get it installed, and follow further guidance from the above posting

---

### Post by openversus on 2010-01-16
I installed before usb_modeswich with synaptic... so after your reply I remove it and a re-installed with the same commands on your post.
But no way to find modem:
this is the situation:

[I]
lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

and when I plug the key:

[I]tail -f /var/log/syslog 
Jan 16 10:57:26 MyPc kernel: [  536.840055] usb 1-4: new high speed USB device using ehci_hcd and address 7
Jan 16 10:57:26 MyPc kernel: [  536.983479] usb 1-4: configuration #1 chosen from 1 choice
Jan 16 10:57:26 MyPc kernel: [  536.991662] scsi6 : SCSI emulation for USB Mass Storage devices
Jan 16 10:57:26 MyPc kernel: [  536.991877] usb-storage: device found at 7
Jan 16 10:57:26 MyPc kernel: [  536.991882] usb-storage: waiting for device to settle before scanning
Jan 16 10:57:26 MyPc kernel: [  537.086965] usbcore: registered new interface driver usbserial
Jan 16 10:57:26 MyPc kernel: [  537.086979] USB Serial support registered for generic
Jan 16 10:57:26 MyPc kernel: [  537.086993] usbcore: registered new interface driver usbserial_generic
Jan 16 10:57:26 MyPc kernel: [  537.086995] usbserial: USB Serial Driver core
Jan 16 10:57:31 MyPc kernel: [  541.989867] usb-storage: device scan complete
Jan 16 10:57:31 MyPc kernel: [  541.991487] scsi 6:0:0:0: CD-ROM            ONDA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
Jan 16 10:57:31 MyPc kernel: [  542.011688] sr1: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
Jan 16 10:57:31 MyPc kernel: [  542.011919] sr 6:0:0:0: Attached scsi CD-ROM sr1
Jan 16 10:57:31 MyPc kernel: [  542.015603] sr 6:0:0:0: Attached scsi generic sg2 type 5
Jan 16 10:57:31 MyPc usb_modeswitch: switching 19d2:2000 (ONDA,  Incorporated: ONDA CDMA Technologies MSM)
Jan 16 10:57:31 MyPc kernel: [  542.151186] scsi 6:0:0:0: rejecting I/O to dead device
Jan 16 10:57:31 MyPc usb_id[3355]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr1'

[/I]

so nothing new...

---

### Post by pdc on 2010-01-16
your last log shows 

> MyPc **usb_modeswitch: switching 19d2:2000** (ONDA, Incorporated: ONDA CDMA Technologies MSM)

you do not say when you ran the lsusb command

............ the log suggests usb_modeswitch is working

**_repeat the lsusb command after you get the above message_**

............. tell us what it says .............

---

### Post by openversus on 2010-01-17
yes, it seems that the module is working... But the modem is still not found. With lsusb there's no changement after this log:

[I]tail -f /var/log/syslog  
Jan 17 10:10:00 MyPc wpa_supplicant[1672]: CTRL-EVENT-SCAN-RESULTS 
Jan 17 10:10:21 MyPc kernel: [ 2465.936034] usb 1-4: new high speed USB device using ehci_hcd and address 3
Jan 17 10:10:21 MyPc kernel: [ 2466.079405] usb 1-4: configuration #1 chosen from 1 choice
Jan 17 10:10:22 MyPc kernel: [ 2466.260144] Initializing USB Mass Storage driver...
Jan 17 10:10:22 MyPc kernel: [ 2466.261631] scsi2 : SCSI emulation for USB Mass Storage devices
Jan 17 10:10:22 MyPc kernel: [ 2466.261775] usbcore: registered new interface driver usb-storage
Jan 17 10:10:22 MyPc kernel: [ 2466.261779] USB Mass Storage support registered.
Jan 17 10:10:22 MyPc kernel: [ 2466.267986] usb-storage: device found at 3
Jan 17 10:10:22 MyPc kernel: [ 2466.267989] usb-storage: waiting for device to settle before scanning
Jan 17 10:10:27 MyPc kernel: [ 2471.265476] usb-storage: device scan complete
Jan 17 10:10:27 MyPc kernel: [ 2471.267958] scsi 2:0:0:0: CD-ROM            ONDA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
Jan 17 10:10:27 MyPc kernel: [ 2471.287062] sr1: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
Jan 17 10:10:27 MyPc kernel: [ 2471.287180] sr 2:0:0:0: Attached scsi CD-ROM sr1
Jan 17 10:10:27 MyPc kernel: [ 2471.287256] sr 2:0:0:0: Attached scsi generic sg2 type 5
Jan 17 10:10:27 MyPc usb_modeswitch: switching 19d2:2000 (ONDA,  Incorporated: ONDA CDMA Technologies MSM)
Jan 17 10:10:27 MyPc usb_id[3634]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host2/target2:0:0/2:0:0:0/block/sr1'
Jan 17 10:10:27 MyPc kernel: [ 2471.424483] scsi 2:0:0:0: rejecting I/O to dead device[/I]

then lsusb:
[I]lsusb
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/I]

so there's still a problem
... I also read in italian ubuntu forum that someone has solved problem using onda [this driver given by onda]("http://www.ondacommunication.com/site/index.php?page=shop.getfile&file_id=301&product_id=115&option=com_virtuemart&Itemid=21")... ??? 
Now I'm confused... and unlucky? :(

---

### Post by pdc on 2010-01-17
from here: 

[http://ubuntuforums.org/showthread.php?t=1147685&page=11](http://ubuntuforums.org/showthread.php?t=1147685&page=11)

post #104

try

> sudo eject sr1 ... as I believe sr1 is your modem/device

and pause and then

> lsusb

any joy?

If not ...........

I think you need to join the usb_modeswitch forum 

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

join; tell them your woes; seek their help

---

### Post by openversus on 2010-01-18
I probably find a solution in _[italian ubuntu forum]("http://forum.ubuntu-it.org/index.php/topic,347775.msg2738981.html#msg2738981")_, _[installing files]("http://www.ondacommunication.com/site/index.php?page=shop.getfile&file_id=301&product_id=115&option=com_virtuemart&Itemid=21")_ given by TIM mobile operator in CD you find with that product.
I will share how we find the solution, but I don't know if is good for everyone that use MDC525UPA. This software's also in english language and for linux but for this italian product...
It seems to work fine without usb_modemswitch: I uninstall it.
There is a problem installing linuxdriveronda... but it works:
I show you the message I receive installing linuxdriveronda1.0.1 (you find in the package):
 
[I]me@MyPC:~/home/linuxdriveronda1.0.1$ sudo make
[sudo] password for me:
make -C /lib/modules/2.6.31-17-generic/build M=/home/linuxdriveronda1.0.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/linuxdriveronda1.0.1/onda.o
/home/linuxdriveronda1.0.1/onda.c:179: error: unknown field ‘num_interrupt_in’ specified in initializer
/home/linuxdriveronda1.0.1/onda.c:179: error: ‘NUM_DONT_CARE’ undeclared here (not in a function)
/home/linuxdriveronda1.0.1/onda.c:180: error: unknown field ‘num_bulk_in’ specified in initializer
/home/linuxdriveronda1.0.1/onda.c:181: error: unknown field ‘num_bulk_out’ specified in initializer
/home/linuxdriveronda1.0.1/onda.c:183: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:184: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:185: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:186: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:187: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:188: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:189: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:190: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:191: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:192: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:193: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:194: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c:196: error: unknown field ‘shutdown’ specified in initializer
/home/linuxdriveronda1.0.1/onda.c:196: warning: initialization from incompatible pointer type
/home/linuxdriveronda1.0.1/onda.c: In function ‘onda_init’:
/home/linuxdriveronda1.0.1/onda.c:243: error: implicit declaration of function ‘info’
/home/linuxdriveronda1.0.1/onda.c: In function ‘onda_indat_callback’:
/home/linuxdriveronda1.0.1/onda.c:419: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/linuxdriveronda1.0.1/onda.c:429: error: ‘struct usb_serial_port’ has no member named ‘open_count’
/home/linuxdriveronda1.0.1/onda.c: In function ‘onda_instat_callback’:
/home/linuxdriveronda1.0.1/onda.c:483: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/linuxdriveronda1.0.1/onda.c:483: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/linuxdriveronda1.0.1/onda.c:485: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/linuxdriveronda1.0.1/onda.c: In function ‘onda_open’:
/home/linuxdriveronda1.0.1/onda.c:590: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/linuxdriveronda1.0.1/onda.c: In function ‘onda_close’:
/home/linuxdriveronda1.0.1/onda.c:624: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/linuxdriveronda1.0.1/onda.c: In function ‘onda_send_setup’:
/home/linuxdriveronda1.0.1/onda.c:692: error: ‘struct usb_serial_port’ has no member named ‘tty’
make[2]: *** [/home/linuxdriveronda1.0.1/onda.o] Error 1
make[1]: *** [_module_/home/linuxdriveronda1.0.1] Error
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [modules] Error 2[/I]

But it's not a problem... 
it works with networkmanager and GPPP: and you can find the complete _**[package here]("http://www.ondacommunication.com/site/index.php?page=shop.getfile&file_id=301&product_id=115&option=com_virtuemart&Itemid=21").**_
Hoping could be useful to someone.
Thank you!

Buena vida ;)

---

### Post by pdc on 2010-01-18
....... so it is working for you ?????????

if so, well done;

I see it creates a udev rule ? amongst other things; quite a linux package there

> #
# udev rules file for supported cameras
#
#

#SUBSYSTEM!="usb_device", GOTO="phone_rules_end"
#ACTION!="add", GOTO="phone_rules_end"KERNEL=="sr*",SUBSYSTEMS=="scsi"
#ACTION!="remove", GOTO="phone_rules_end",KERNEL=="scd*",NAME="%k", ACTION=="add",
BUS=="usb",KERNEL=="sr[0-9]*", GROUP="cdrom",SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000",SYMLINK+="MODEMCONNECTION",MODE="0666", RUN+=""


LABEL="phone_rules_end"


---

### Post by openversus on 2010-01-25
Hi pdc!!!
I confirm... it works for me.
In fact I have to say that is especially for italian user: the connection works with _[their (TIM mobile operator) software]("http://www.ondacommunication.com/site/index.php?page=shop.getfile&file_id=301&product_id=115&option=com_virtuemart&Itemid=21")_ without using network-manager. If I try to connect with network-manager I cannot and then I have also problem with this software provided by TIM mobile operator... there's probably a conflict, I suppose...
The good news is that a major telecom operator in Italy has started to provide software for Linux ... plus working ....
Here's a link translated to italian forum posts:
[http://translate.google.ch/translate?js=y&prev=_t&hl=it&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C347775.0.html&sl=it&tl=en](http://translate.google.ch/translate?js=y&prev=_t&hl=it&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C347775.0.html&sl=it&tl=en)

Buena Vida!

---

### Post by alexfish on 2010-01-25
> **openversus said:**
> Hi pdc!!!
I confirm... it works for me.
In fact I have to say that is especially for italian user: the connection works with _[their (TIM mobile operator) software]("http://www.ondacommunication.com/site/index.php?page=shop.getfile&file_id=301&product_id=115&option=com_virtuemart&Itemid=21")_ without using network-manager. If I try to connect with network-manager I cannot and then I have also problem with this software provided by TIM mobile operator... there's probably a conflict, I suppose...
[SIZE=3][COLOR=Navy]The good news is that a major telecom operator in Italy has started to provide software for Linux ... plus working ....
Here's a link translated to italian forum posts:[/COLOR][/SIZE]
[http://translate.google.ch/translate?js=y&prev=_t&hl=it&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C347775.0.html&sl=it&tl=en](http://translate.google.ch/translate?js=y&prev=_t&hl=it&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C347775.0.html&sl=it&tl=en)

Buena Vida!

Hi 

Just Hi-lighting  The good news is  

Hoping Other ISP companies taking note

If  I had a Choice  [SIZE=3][COLOR=Navy]"software for Linux ... plus working ....[/COLOR][/SIZE]"

---

### Post by pdc on 2010-01-25
Hi openversus;

delighted to hear your modem is working, and you have specially written software from your provider

---

### Post by openversus on 2010-01-26
I'm happy to see that it is a really good news...
I have to report that the package is provided from ONDA (in thier website) and not directly from ISP TIM... but it doesn't matter :D

Buena vida!

---

