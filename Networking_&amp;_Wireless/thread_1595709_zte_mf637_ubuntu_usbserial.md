---
title: "zte mf637 ubuntu usbserial"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by bulsoft on 2010-10-13
Help me please solve it ....

~$ uname -a
Linux bulsoft-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

~$ lsusb
Bus 001 Device 005: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636

~$ dmesg
[ 2533.552021] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 2533.689719] scsi5 : usb-storage 1-3:1.2
[ 2533.716222] usbserial: `0×19d2' invalid for parameter `vendor'
[ 2533.728888] usbserial: `0×19d2' invalid for parameter `vendor'
[ 2533.734815] usbserial: `0×19d2' invalid for parameter `vendor'
[ 2534.689998] scsi 5:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2534.690822] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 2534.699736] sd 5:0:0:0: [sdc] Attached SCSI removable disk

~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
FATAL: Error inserting usbserial (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

on another PC and same OS this modem works.

---

### Post by alexfish on 2010-10-13
Hi

maybe driver modules are already attached to the device or the device is showing a different ID

From the terminal use the following code

Code:

usb-devices

locate the section that contains the device and post only those parts


alexfish

---

### Post by bulsoft on 2010-10-14
> **alexfish said:**
> 
Code:
usb-devices
locate the section that contains the device and post only those parts
alexfish

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=P673A3ZTED010000
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

---

### Post by alexfish on 2010-10-14
hi

the info shows the drivers have not loaded ( don't know why , have check you kernel version , serial driver is in kernel)

T: Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=19d2 ProdID=0031 Rev=00.00
S: Manufacturer=ZTE,Incorporated
S: Product=ZTE WCDMA Technologies MSM
S: SerialNumber=P673A3ZTED010000
C: #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Blue]Driver=(none)[/COLOR]
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Blue]Driver=(none)[/COLOR]
I: If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff[COLOR=Blue] Driver=(none)[/COLOR]

Note " [COLOR=Blue]Driver=(none) "[/COLOR]

From the terminal try this 

Code:

[COLOR=Blue]sudo modprobe option[/COLOR]

enter your system password

wait a for 5 sec's

Code:

[COLOR=Blue]usb-devices[/COLOR]

What happens

alexfish

---

### Post by bulsoft on 2010-10-14
> **alexfish said:**
> 
[COLOR=Blue]sudo modprobe option[/COLOR]


~$ sudo modprobe option
WARNING: Error inserting usb_wwan (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usb_wwan.ko): Invalid argument
FATAL: Error inserting option (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/option.ko): Invalid argument


dmesg writes
0×19d2

i`m print
0x19d2

where it may may be ?

---

### Post by alexfish on 2010-10-14
hi

can you search  your system

from your menus select places/search for files

option.ko
usbserial.ko

alexfish

---

### Post by bulsoft on 2010-10-14
> **alexfish said:**
> 
can you search  your system
from your menus select places/search for files
option.ko
usbserial.ko


hi,
/lib/modules/2.6.32-25-generic/kernel/drivers/usb/serial/option.ko 76.1k
/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/option.ko 66.0k

/lib/modules/2.6.32-25-generic/kernel/drivers/usb/serial/usbserial.ko 54.6k
/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko 54.0k

/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usb_wwan.ko 19.4k

/lib/modules/2.6.32-25-generic/kernel/drivers/usb/serial/option.ko 76.1k
/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/option.ko 66.0k

---

### Post by alexfish on 2010-10-14
Perhaps cleaning up the system may help , but can,t say  ( if  already done let me know and by which method )

you can use 

Computer janitor

or try ubuntu tweak ( I think this gives safer options) but I leave it to you 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Please read help info etc if either option is used

alexfish

added can you check for further updates

if met with failure and 
if working in  earlier kernel  , try booting into that kernel

---

### Post by bulsoft on 2010-10-14
cleaning my system 2 progs, reboot, dmesg

[  123.689098] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  123.903868] Initializing USB Mass Storage driver...
[  123.904224] scsi2 : usb-storage 1-3:1.2
[  123.904609] usbcore: registered new interface driver usb-storage
[  123.904615] USB Mass Storage support registered.
[  123.937691] usbserial: `0×19d2' invalid for parameter `vendor'
[  123.943694] usbserial: `0×19d2' invalid for parameter `vendor'
[  123.947078] usbserial: `0×19d2' invalid for parameter `vendor'
[  124.909377] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[  124.910225] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  124.922259] sd 2:0:0:0: [sdc] Attached SCSI removable disk


what else ?

---

### Post by alexfish on 2010-10-14
Hi

Since the problem may have started after upgrading or updating

suggest starting new thread at

Installation & Upgrades

possible head up with title something like " driver modules not loading after updates "

explain in detail the problem and also provide a reference back to this thread

hopefully someone with more Knowlege on these matters will help

alexfish

---

### Post by bulsoft on 2010-10-14
[QUOTE=alexfish;9971231]
Since the problem may have started after upgrading or updating
[QUOTE=alexfish;9971231]

NO. 

I have another PC with the same OS, but there`s no problem.

~$ sudo modprobe usbserial
FATAL: Error inserting usbserial (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

~$ dmesg
[ 4681.366359] usbserial: `0×19d2' invalid for parameter `vendor'

where is module usbserial take `0×19d2' ?
and what is the simb after zero ?

---

### Post by alexfish on 2010-10-14
> **bulsoft said:**
> [QUOTE=alexfish;9971231]
Since the problem may have started after upgrading or updating
[QUOTE=alexfish;9971231]

NO. 

I have another PC with the same OS, but there`s no problem.

~$ sudo modprobe usbserial
FATAL: Error inserting usbserial (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

~$ dmesg
[ 4681.366359] usbserial: `0×19d2' invalid for parameter `vendor'

where is module usbserial take `0×19d2' ?
and what is the simb after zero ?

should be "0x19d2" 

thanks did not spot that keyboard  "789 0"  : "Zz Xx Cc" then " 0x"

check type of keyboard and language

also check " @ ' $ £  etc etc are correct as may have other problems when scripting or programming

added just checked back through some of your post / 

the symbols  

on the system there are numbers which are represented by hexadecimal , the symbol for this is "0x" then the number in hex IE 19d2 

the dmseg is reporting back how it prints its representation of hex number "0×" then the number IE 19d2

so as to what is wrong don't know

it would have been  helpful,   if  you check on the other system what the dmesg shows, in hex

other than that I am fishing in the dark

added
also wondering if character encoding utf8 maybe a problem

Check the settings in the terminal

---

### Post by bulsoft on 2010-10-15
1. output only inserting modem:
~$ dmesg
[58375.493036] usb 1-3: new high speed USB device using ehci_hcd and address 4
[58375.629597] scsi3 : usb-storage 1-3:1.2
[B][58376.015579] usbserial: `0×19d2' invalid for parameter `vendor'
[58376.021516] usbserial: `0×19d2' invalid for parameter `vendor'
[58376.029529] usbserial: `0×19d2' invalid for parameter `vendor'[/B]
[58376.630168] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[58376.631022] sd 3:0:0:0: Attached scsi generic sg3 type 0
[58376.635776] sd 3:0:0:0: [sdc] Attached SCSI removable disk

simb are wrong

2. ~$ sudo modprobe usbserial
FATAL: Error inserting usbserial (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

~$ dmesg
**[58477.299075] usbserial: `0×19d2' invalid for parameter `vendor'**

new message in log
simb are wrong
i am not print anything

3. ~$ sudo modprobe usbserial vendor=**0x19d2** product=0x0031 <- i print this 'x'
FATAL: Error inserting usbserial (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

new message in log
~$ dmesg
[58477.299075] usbserial: `0×19d2' invalid for parameter `vendor'
**[58703.078836] usbserial: `0×19d2' invalid for parameter `vendor'**

simb are wrong

4. ~$ sudo modprobe option
WARNING: Error inserting usb_wwan (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usb_wwan.ko): Invalid argument
FATAL: Error inserting option (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/option.ko): Invalid argument

new message in log
~$ dmesg
[58477.299075] usbserial: `0×19d2' invalid for parameter `vendor'
[58703.078836] usbserial: `0×19d2' invalid for parameter `vendor'
**[59062.698300] usbserial: `0×19d2' invalid for parameter `vendor'**

where is modules option and usbserial take `0×19d2'?
who are transcode it ?

on the PC where it works i recover no **usbserial: `0×19d2' invalid for parameter `vendor'**
there is only than new interface ttyUSB(0,1,2)

---

### Post by bulsoft on 2010-10-15
coolsmiley   2funny

sudo grep -R '0×19d2' /etc -> /etc/modprobe.d/zte636.conf
options usbserial vendor=0×19d2 product=0×0031
rewrite options usbserial vendor=0x19d2 product=0x0031

BIG thanks, all good !!! there was an error

---

