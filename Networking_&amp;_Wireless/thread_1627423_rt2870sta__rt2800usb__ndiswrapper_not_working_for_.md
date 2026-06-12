---
title: "rt2870sta / rt2800usb / ndiswrapper not working for: Sitecom 300N Wireless(WL-324)"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by Y_Ernst on 2010-11-21
Hi,
does anybody know how to use the Sitecom WL-324 usb stick with ubuntu (10.10)?   
(It works with windows.)


lsusb | grep Ralink
```
Bus 002 Device 004: ID 148f:2878 Ralink Technology, Corp. 
```

Im using Ubuntu 10.10 x64 with a Phenom(tm) II X6 System


My results so far:
sudo modprobe rt2870sta  (or rt2800usb)

result (rt2870sta) :

lsmod | grep rt28
```
rt2870sta             445182  0 
crc_ccitt               1699  1 rt2870sta
```

dmesg

```
[ 5377.578303] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 5377.588122] rtusb init --->
[ 5377.588168] usbcore: registered new interface driver rt2870
```


result (rt2800usb):

lsmod | grep rt28

```
rt2800usb               9955  0 
rt2800lib              31970  1 rt2800usb
rt2x00usb              11316  2 rt2800usb,rt2800lib
rt2x00lib              31575  2 rt2800lib,rt2x00usb
crc_ccitt               1699  1 rt2800usb
```

dmesg

 ```
4793.985419] usbcore: registered new interface driver rt2800usb
[ 5137.231764] usbcore: deregistering interface driver rt2800usb
[ 5149.007270] cfg80211: Calling CRDA to update world regulatory domain
[ 5149.020203] cfg80211: World regulatory domain updated:
[ 5149.020209]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5149.020215]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5149.020221]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5149.020226]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5149.020231]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5149.020236]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5149.037525] usbcore: registered new interface driver rt2800usb

```

sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                   [ OK ] 

```

iwconfig for **both** 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

I've got the same result with the ndiswrapper:

The original inf File from windows:
```
[Version]
Signature       = "$Chicago$"
Class           = Net
ClassGUID       = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider        = %Ralink%
Compatible      = 1
DriverVer       = 02/12/2010, 3.01.00.0000
CatalogFile     = rt2870.cat            
WHQL certified
```

ndiswrapper -l
```
rt2870 : driver installed
```



demsg

```
[10599.122755] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[10599.149972] usbcore: registered new interface driver ndiswrapper
```

lsmod | grep  ndis
```
ndiswrapper           245044  0 
```

sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                                   [ OK ] 
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.
```

---

### Post by chili555 on 2010-11-21
> The original inf File from windows:From where? the original driver CD that came with the device? 64-bit? Windows XP?

Neither rt2870sta nor rt2800usb will drive your device because the usb.id is not recognized. > Bus 002 Device 004: ID [COLOR="Red"]148f:2878[/COLOR] Ralink Technology, Corp.```
modinfo rt2870sta | grep 2878
modinfo rt2800usb | grep 2878
:~$ 
```When grep comes up blank, it means the requested text does not appear.

Do you feel lucky? Well, do ya?

Would you like to try Agent Chili's super-secret highly-experimental method to trick the driver into recognizing the usb.id? It often, but not always works.

I'll bet the Windows .inf file also lacks the usb.id. You could check:```
cat rt2870.inf | grep 2878
```We could experimentally modify it, too.

My experimental methods can be reversed easily if they don't work.

---

### Post by chili555 on 2010-11-21
Did the .sys file get installed in /etc/ndiswrapper?

---

### Post by Y_Ernst on 2010-11-21
You are absolutly correct.
The id is missing in the inf-file.

Tell me your super-secret method!

---

### Post by Y_Ernst on 2010-11-21
> **chili555 said:**
> Did the .sys file get installed in /etc/ndiswrapper?

Yes:

ls netr28ux.*
netr28ux.inf  netr28ux.sys

---

### Post by chili555 on 2010-11-21
Try this. Remove the device and in a terminal, do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="2878", RUN+="/sbin/modprobe -qba rt2870sta"

```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
Add one long single line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "148f 2878" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rt2870sta
```Post back and let the searchers and me know the result.

---

### Post by Y_Ernst on 2010-11-21
I had no luck with the modifications.

modinfo rt2870sta | grep 2878
:~$ 


I also tried to patch the inf-file for the ndiswrapper.
(I copied the win x64 driver from the device storage)

I added the line:

```
%Sitecom_2878.DeviceDesc%   = RTWLAN.ndi,           USB\VID_148f&PID_2878 

``` 


The Result:

ndiswrapper -l
```
rt2870 : driver installed
	device (148F:2878) present
```



cat /etc/modprobe.d/ndiswrapper.conf | grep 2870
alias usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip* ndiswrapper

typo:
cat /etc/modprobe.d/ndiswrapper.conf | grep 2878
alias usb:v148Fp2878d*dc*dsc*dp*ic*isc*ip* ndiswrapper


dmesg

[ 1026.363297] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1026.403514] usbcore: registered new interface driver ndiswrapper

But iwconfig didn't find a wireless device.

---

### Post by chili555 on 2010-11-21
>  had no luck with the modifications.

modinfo rt2870sta | grep 2878
:~$ That doesn't really tell us much; the intent is to add the usb.id to the driver after it's loaded; not permanently to the driver file. I believe that would involve a tedious process like recompiling the driver and the kernel. 

Let's have a gander at:```
sudo modprobe rt2870sta
dmesg | grep rt2
```Thanks.

---

### Post by Y_Ernst on 2010-11-21
Of course. Here comes the dmesg result: 

[  102.852632] <--- rtusb exit
[  124.635223] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  124.644501] rtusb init --->
[  124.645191] usbcore: registered new interface driver rt2870

---

### Post by chili555 on 2010-11-21
And not a peep from:```
iwconfig
```What is the result of:```
ls /etc/Wireless/RT2870STA/
```

---

### Post by Y_Ernst on 2010-11-22
Nothing.

I added the missing file: 
/etc/Wireless/RT2870STA/RT2870STA.dat

Should I try to install the **2.4.0.1** driver?

```
#The word of "Default" must not be removed
Default
CountryRegion=1
CountryRegionABand=1
CountryCode=DE
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
```

---

### Post by chili555 on 2010-11-22
Something is very wrong. The Power of the Grey Beard is dimming! Let's do a full diagnostic work-up. We are going to create a text document that I and others can examine to pin down the problem. Please shut the computer completely down. Detach the ethernet cable. Insert the Sitecom. Boot up and run:```
sudo modprobe rt2870sta > ernst.txt
iwconfig >> ernst.txt
lsusb >> ernst.txt
dmesg >> ernst.txt
zip ernst.zip ernst.txt
```You will find a zip file in your home directory called ernst.zip. Please attach it to your reply using the paperclip above the reply box.

---

### Post by Y_Ernst on 2010-11-22
Hi,
I have added the zip file.
I hope the list is complete.

---

### Post by chili555 on 2010-11-22
I have never indulged in adult beverages at 10:00am, but I may start. Before I reach for my tanto, please confirm that the required firmware is in place:```
ls /lib/firmware | grep rt2
```We are looking for rt2870.bin.

Next, please proofread the files we created above; is every character and space exactly correct?

Next, open:```
sudo tail -f /var/log/messages
```Remove the device, count to twenty and plug it back in. Are there any informative messages that appear? If so, you can copy and paste them from the terminal into a text document to post here.> Should I try to install the **2.4.0.1** driver?Does your usb.id appear in usb_main_dev.c? We can add it if not.

I notice you used the Vist64 driver in ndiswrapper. It is designed to use the XP drivers, although sometimes Win2000 and other drivers work. From *man ndiswrapper-1.9*:> ndiswrapper - Linux kernel module and user space tool to load and run Windows XP drivers for wireless cardsWe may, as a Plan C, try the XP driver.

---

### Post by Y_Ernst on 2010-11-22
I'm feeling guilty :(

I checked the files:
/etc/udev/rules.d/network_drivers.rules
/etc/modprobe.d/network_drivers.conf

they are ok.

the firmware is available:

:~$ ls /lib/firmware | grep rt2
-rw-r--r--  1 root root    4096 2010-08-16 21:02 rt2870.bin

in /var/log/messages only the device-storage appears:   

Nov 22 16:31:43 hope kernel: [ 6295.672961] usb 2-1: USB disconnect, address 3

Nov 22 16:33:04 hope kernel: [ 6377.140086] usb 2-1: new high speed USB device using ehci_hcd and address 4
Nov 22 16:33:04 hope kernel: [ 6377.308961] scsi9 : usb-storage 2-1:1.0
Nov 22 16:33:05 hope kernel: [ 6378.304534] scsi 9:0:0:0: CD-ROM            Ralink   Wireless 11n     1.00 PQ: 0 ANSI: 0 CCS
Nov 22 16:33:05 hope kernel: [ 6378.307632] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Nov 22 16:33:05 hope kernel: [ 6378.307994] sr 9:0:0:0: Attached scsi generic sg2 type 5

**usb_main_dev.c** doesn't support 2878

(Also the driver doesn't compile under 10.10)

I already tried the WINXP and the old WINXP2K driver.
I had no luck with them.

---

### Post by chili555 on 2010-11-22
Oh my heavens!!!!!!!!

I just noticed this: [http://www.sitecom.com/wireless-usb-adapter-300n-xr-self-installing/p/713](http://www.sitecom.com/wireless-usb-adapter-300n-xr-self-installing/p/713)> Simply plug this Wireless USB Adapter 300N XR - Self Installing into your desktop PC or notebook, and it will install all the necessary software automatically.I wonder if there are, in effect or actuality, two partitions on the device; a software bundle and the wireless radio. When you load the USB device in Ubuntu, it sees a software package and stops; nothing refers it on to the wireless radio.> scsi 9:0:0:0: CD-ROM Ralink Wireless 11n 1.00 PQ: 0 ANSI: 0 CCSIt evidently emulates a CDROM.

I would be very interested to see:```
sudo fdisk /dev/sr1
```Does a device get created in /media, perhaps something like /media/SITECOM? If you right-click it, can you browse the contents?

I have not encountered these before, we are learning together.

I am sliding the tanto back in the sheath...

---

### Post by Y_Ernst on 2010-11-22
Yes, windows adds two devices if you connect it.

You can also see a "cd-rom" in /media

ls /media/Sitecom\ WL-324/
AutoInst.exe  Autorun.inf  setup.exe


sorry, the fdisk output is in german:

sudo fdisk /dev/sr1


Platte /dev/sr1: 8 MByte, 8255488 Byte
255 Köpfe, 63 Sektoren/Spur, 0 Zylinder
Einheiten = Zylinder von 16065 × 2048 = 32901120 Bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0xe7c0f6f2

    Gerät  boot.     Anfang        Ende     Blöcke   Id  System

---

### Post by chili555 on 2010-11-22
I think the Windows software somehow jumps from, in effect, the CDROM over to the wireless radio. I haven't any idea how to do that in Ubuntu. I have only two suggestions. First, email Sitecom and tell them of our problem and ask them for directions. Feel free to refer them to our discussions here. They may say that they don't support Linux and have no solutions. 

The other suggestion is to try another device.

I am not sure I have any better ideas, but please post back if I can help.

---

### Post by Y_Ernst on 2010-11-22
Thank you for your help.

Perhaps the [USB_ModeSwitch]("http://www.draisberghof.de/usb_modeswitch/") package for usb-flipflop devices could solve this problem?

---

### Post by chili555 on 2010-11-22
I think it is worth a try. Please note that the package is included in the Ubuntu repositories; i.e. Synaptic. I'd install it and try it out. Please see:```
man usb_modeswitch
```You will notice:>  -v --default-vendor NUM
                 Vendor  ID  to  look  for (mandatory), usually given as hex number (example: 0x12d1).  Each USB device is
                 identified by a number officialy assigned to the vendor by the USB  association  and  a  number  for  the
                 respective model (product ID) chosen by the vendor

       -p --default-product NUM
                 Product ID to look for (mandatory).
In your case, I believe, this would be:```
sudo usb_modeswitch -v 0x148f -p 0x2878
```There may be other options required.

We are learning together. Please let all of us know.

---

### Post by Y_Ernst on 2010-11-23
usb_modeswitch seems to work but now my system freezes after several seconds.

~$ lsusb | grep Ralink
Bus 002 Device 002: ID 148f:2878 Ralink Technology, Corp

~$ usb-devices
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=148f ProdID=2878 Rev=00.01
S:  Manufacturer=Ralink
S:  Product=802.11 n WLAN
S:  SerialNumber=1.0
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=450mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

~$ sudo usb_modeswitch -v 0x148f -p 0x2878 -w 100 -n -W -D
```
Taking all parameters from the command line

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.4 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x148f
DefaultProduct= 0x2878
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
MessageEndpoint=  not set
MessageContent=""
NeedResponse=1
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled
System integration mode enabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 008
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Couldn't open /dev/bus/usb/008/001
usb_os_find_devices: Found 001 on 007
usb_os_find_devices: Found 001 on 006
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 002 on 004
skipped 1 class/vendor specific interface descriptors
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 004
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 006 on 001
usb_os_find_devices: Found 005 on 001
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 004 on 001
skipped 4 class/vendor specific interface descriptors
skipped 2 class/vendor specific interface descriptors
skipping descriptor 0x25
skipped 1 class/vendor specific endpoint descriptors
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 046d:c316
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 148f:2878
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 0c0b:b159
  searching devices, found USB ID 046d:c01e
  searching devices, found USB ID 045e:00f5
  searching devices, found USB ID 05e3:0660
  searching devices, found USB ID 1d6b:0002
 Found devices in default mode or class (1)
Accessing device 002 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Ralink  
   Model String: Wireless 11n    
Revision String: 1.00
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Ralink
     Product: 802.11 n WLAN
  Serial No.: 1.0
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.
```

And now:

~$ usb-devices
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=148f ProdID=2878 Rev=00.01
S:  Manufacturer=Ralink
S:  Product=802.11 n WLAN
S:  SerialNumber=1.0
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=450mA
I:  I**f#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)**


Than I configured the ndiswrapper with x64 Driver

~$ dmesg

```
[  545.546091] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  545.703428] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[  545.898190] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[  545.903802] ndiswrapper: driver rt2870 (Ralink Technology, Corp.,10/29/2008, 1.02.04.0000) loaded
[  546.811295] wlan0: ethernet device 00:0c:f6:8a:77:ee using NDIS driver: rt2870, version: 0x0, NDIS version: 0x501, vendor: 'IEEE 802.11 Wireless Card.', 148F:2878.F.conf
[  546.811332] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  546.811434] usbcore: registered new interface driver ndiswrapper
[  546.828085] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  547.423609] BUG: unable to handle kernel paging request at ffffc900133dd000
[  547.423620] IP: [<ffffc900130ac766>] 0xffffc900130ac766
[  547.423631] PGD 11fc15067 PUD 11fc16067 PMD 73890067 PTE 0
[  547.423640] Oops: 0002 [#1] SMP 
[  547.423646] last sysfs file: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/uevent
[  547.423651] CPU 4 
[  547.423654] Modules linked in: ndiswrapper nls_utf8 isofs nls_iso8859_1 nls_cp437 vfat fat binfmt_misc vboxnetadp vboxnetflt vboxdrv parport_pc ppdev snd_hda_codec_realtek snd_usb_audio snd_usbmidi_lib snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd fglrx(P) gspca_sonixj gspca_main videodev v4l1_compat v4l2_compat_ioctl32 psmouse serio_raw soundcore edac_core edac_mce_amd snd_page_alloc k10temp i2c_piix4 xhci_hcd shpchp lp parport usb_storage usbhid hid r8169 ahci pata_atiixp libahci mii
[  547.423721] 
[  547.423728] Pid: 4493, comm: ntdriver Tainted: P            2.6.35-22-generic #35-Ubuntu 880GXH/USB3/To Be Filled By O.E.M.
[  547.423734] RIP: 0010:[<ffffc900130ac766>]  [<ffffc900130ac766>] 0xffffc900130ac766
[  547.423743] RSP: 0018:ffff880073f3f6a8  EFLAGS: 00010287
[  547.423747] RAX: 0000000000000000 RBX: ffff880073f916e0 RCX: 0000000000000800
[  547.423752] RDX: ffffc900133dc800 RSI: 726576697264746e RDI: 0000000000000282
[  547.423756] RBP: ffff880073f3fee0 R08: ffffc90013399000 R09: 0000000028008d80
[  547.423761] R10: ffffffffa069a850 R11: dead000000100100 R12: ffffc900130b3040
[  547.423766] R13: ffffc90013156000 R14: ffff88009c68d820 R15: 0000000000000000
[  547.423772] FS:  00007f6546a2d8e0(0000) GS:ffff880001f00000(0000) knlGS:0000000000000000
[  547.423777] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  547.423781] CR2: ffffc900133dd000 CR3: 00000000ceb37000 CR4: 00000000000006e0
[  547.423786] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  547.423791] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  547.423797] Process ntdriver (pid: 4493, threadinfo ffff880073f3e000, task ffff880073f916e0)
[  547.423801] Stack:
[  547.423804]  ffffc90000000800 ffffc90013399000 ffffc900133dc800 0000000000000282
[  547.423811] <0> 726576697264746e ffffc9001309f114 ffffc900133dc800 ffffc90013399000
[  547.423820] <0> ffff880100002800 ffff880073f3f740 ffff880073f3f730 ffff8800c5ed8540
[  547.423828] Call Trace:
[  547.423840]  [<ffffffff814219dc>] ? ehci_urb_enqueue+0x9c/0x110
[  547.423876]  [<ffffffffa06a8335>] ? wrap_process_nt_urb+0x1f5/0x4f0 [ndiswrapper]
[  547.423885]  [<ffffffff815891ff>] ? _raw_spin_lock_irqsave+0x2f/0x40
[  547.423898]  [<ffffffff810700bc>] ? lock_timer_base+0x3c/0x70
[  547.423932]  [<ffffffffa06a86f5>] ? wrap_submit_irp+0xc5/0x250 [ndiswrapper]
[  547.423963]  [<ffffffffa069e996>] ? pdoDispatchDeviceControl+0x16/0x40 [ndiswrapper]
[  547.423993]  [<ffffffffa069ceef>] ? IoAllocateIrp+0x6f/0x80 [ndiswrapper]
[  547.424025]  [<ffffffffa06a88a7>] ? win2lin2+0xe/0x11 [ndiswrapper]
[  547.424055]  [<ffffffffa069bf91>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[  547.424084]  [<ffffffffa069bfbd>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[  547.424091]  [<ffffffff81589439>] ? _raw_spin_unlock_bh+0x19/0x20
[  547.424120]  [<ffffffffa069bf91>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[  547.424151]  [<ffffffffa06a88a7>] ? win2lin2+0xe/0x11 [ndiswrapper]
[  547.424160]  [<ffffffff8117cb01>] ? __find_get_block+0xb1/0x200
[  547.424168]  [<ffffffff812be669>] ? put_dec+0x59/0x60
[  547.424174]  [<ffffffff812be99e>] ? number+0x32e/0x360
[  547.424181]  [<ffffffff81049964>] ? scale_rt_power+0x24/0x70
[  547.424189]  [<ffffffff81050a0a>] ? find_busiest_group+0x67a/0xa00
[  547.424197]  [<ffffffff812c1006>] ? vsnprintf+0x416/0x5a0
[  547.424204]  [<ffffffff81050ae7>] ? find_busiest_group+0x757/0xa00
[  547.424211]  [<ffffffff81049769>] ? wake_affine+0x2a9/0x310
[  547.424218]  [<ffffffff8104eb08>] ? enqueue_sleeper+0x158/0x230
[  547.424226]  [<ffffffff8104ed12>] ? enqueue_entity+0x132/0x1b0
[  547.424234]  [<ffffffff81029601>] ? native_smp_send_reschedule+0x41/0x60
[  547.424241]  [<ffffffff81049ae6>] ? resched_task+0x76/0x90
[  547.424247]  [<ffffffff81056438>] ? try_to_wake_up+0xc8/0x400
[  547.424254]  [<ffffffff81056782>] ? default_wake_function+0x12/0x20
[  547.424260]  [<ffffffff81048d89>] ? __wake_up_common+0x59/0x90
[  547.424289]  [<ffffffffa0697bd4>] ? ntdriver_thread+0x74/0xb0 [ndiswrapper]
[  547.424317]  [<ffffffffa0697ba7>] ? ntdriver_thread+0x47/0xb0 [ndiswrapper]
[  547.424345]  [<ffffffffa0697b60>] ? ntdriver_thread+0x0/0xb0 [ndiswrapper]
[  547.424353]  [<ffffffff8107f0b6>] kthread+0x96/0xa0
[  547.424360]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[  547.424366]  [<ffffffff8107f020>] ? kthread+0x0/0xa0
[  547.424372]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[  547.424376] Code: 00 00 00 eb 08 8b 04 24 ff c0 89 04 24 8b 44 24 40 39 04 24 73 1a 8b 04 24 8b 0c 24 48 8b 54 24 10 4c 8b 44 24 08 41 0f b6 04 00 <88> 04 0a eb d5 48 83 c4 28 c3 cc cc cc cc cc cc cc cc cc cc cc 
[  547.424433] RIP  [<ffffc900130ac766>] 0xffffc900130ac766
[  547.424441]  RSP <ffff880073f3f6a8>
[  547.424445] CR2: ffffc900133dd000
[  547.424450] ---[ end trace e074263f73742a90 ]---
```

The wlan-device is recognized but than the system freezes :(

Also the rt2870sta doesn't work:

~$ dmesg
....
[  439.967012] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3c28
[  439.967016] 	Request Value=0x0000!
[  439.972748] #
[  439.982745] #
[  439.992743] #
[  440.002740] #
[  440.012738] #
[  440.022736] #
[  440.032733] #
[  440.042731] #
[  440.052729] #
[  440.062602] #

There is now a new entry in net rules
:~$ ls /etc/udev/rules.d/70-persistent-net.rules 

# USB device 0x148f:0x2878 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:f6:8a:77:ee", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

---

### Post by chili555 on 2010-11-23
We are making progress! At last, the device is recognized as a wireless device and not a CDROM. The ndiswrapper driver, at least, grabs the device and creates a wireless interface:> [  545.546091] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  545.703428] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[  545.898190] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[  545.903802] ndiswrapper: driver rt2870 (Ralink Technology, Corp.,10/29/2008, 1.02.04.0000) loaded
[  546.811295] wlan0: ethernet device 00:0c:f6:8a:77:ee using NDIS driver: rt2870, version: 0x0, NDIS version: 0x501, vendor: 'IEEE 802.11 Wireless Card.', 148F:2878.F.conf
[  546.811332] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  546.811434] usbcore: registered new interface driver ndiswrapper
[  546.828085] ADDRCONF(NETDEV_UP): wlan0: link is not ready
We have a new problem now:> [  547.423609] BUG: unable to handle kernel paging request at ffffc900133dd000This is, evidently, a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/635125](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/635125)

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/613796](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/613796)

[http://ubuntuforums.org/showthread.php?t=1546409](http://ubuntuforums.org/showthread.php?t=1546409)

I am doing some more reading and suggest you do the same. I will report back soon.

---

### Post by chili555 on 2010-11-23
Just to be sure that method #1 is not fighting ndiswrapper, I suggest you stop the files we created in post #6 from loading.```
sudo mv /etc/udev/rules.d/network_drivers.rules /etc/udev/rules.d/network_drivers.rules.bak
sudo mv /etc/modprobe.d/network_drivers.conf /etc/modprobe.d/network_drivers.conf.bak
```Then I'd unload and reload ndiswrapper and check dmesg for improvement.```
sudo rmmod -f ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n20
```

---

### Post by Y_Ernst on 2010-11-23
the output looks like this:

:$ dmesg | tail -n20

[ 2591.780871]  [<ffffffff81049769>] ? wake_affine+0x2a9/0x310
[ 2591.780878]  [<ffffffff8104eb08>] ? enqueue_sleeper+0x158/0x230
[ 2591.780885]  [<ffffffff8104ed12>] ? enqueue_entity+0x132/0x1b0
[ 2591.780894]  [<ffffffff81029601>] ? native_smp_send_reschedule+0x41/0x60
[ 2591.780900]  [<ffffffff81049ae6>] ? resched_task+0x76/0x90
[ 2591.780907]  [<ffffffff81056438>] ? try_to_wake_up+0xc8/0x400
[ 2591.780913]  [<ffffffff81056782>] ? default_wake_function+0x12/0x20
[ 2591.780920]  [<ffffffff81048d89>] ? __wake_up_common+0x59/0x90
[ 2591.780949]  [<ffffffffa0692bd4>] ? ntdriver_thread+0x74/0xb0 [ndiswrapper]
[ 2591.780977]  [<ffffffffa0692ba7>] ? ntdriver_thread+0x47/0xb0 [ndiswrapper]
[ 2591.781005]  [<ffffffffa0692b60>] ? ntdriver_thread+0x0/0xb0 [ndiswrapper]
[ 2591.781012]  [<ffffffff8107f0b6>] kthread+0x96/0xa0
[ 2591.781019]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[ 2591.781026]  [<ffffffff8107f020>] ? kthread+0x0/0xa0
[ 2591.781032]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[ 2591.781036] Code: 00 00 00 eb 08 8b 04 24 ff c0 89 04 24 8b 44 24 40 39 04 24 73 1a 8b 04 24 8b 0c 24 48 8b 54 24 10 4c 8b 44 24 08 41 0f b6 04 00 <88> 04 0a eb d5 48 83 c4 28 c3 cc cc cc cc cc cc cc cc cc cc cc 
[ 2591.781092] RIP  [<ffffc900130ac766>] 0xffffc900130ac766
[ 2591.781100]  RSP <ffff88008136d6a8>
[ 2591.781103] CR2: ffffc900133e1000
[ 2591.781108] ---[ end trace 5452532dd192ab4d ]---

The system froze shortly after clicking on the network icon.

I will try to find out something about this message:

Nov 23 19:05:05 hope NetworkManager[964]: <error> [1290535505.125740] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)

---

### Post by pdc on 2010-11-23
I plugged a ZTE MF636 modem into an EEE running 10.10 Ubuntu yesterday; all newly configured and unused; the ZTE configured up nicely; and it then auto-connected to the network when I pressed OK for the settings; in doing that,the screen froze; I think it was CTL-ALT_Backspace that gave a "do you want to leave" message; I pressed cancel to that and was back to a working screen; I will try it again and see what happens; I remember trying a liveCD of Fedora 14; and having a curious freeze of the screen there too after attempting to open firefox; I think the same on Fedora13; so a couple of freezes seen recently; I guess I attempt to capture the freeze again today with dmesg; the Eee was for travelling so not a regular

---

### Post by Y_Ernst on 2010-11-24
I think the ndiswrapper doesn't work along with the rt2870sta 64Bit driver.

It just freezes the system after the first request:

syslog:

Nov 24 07:16:19 hope kernel: [  464.931810]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Nov 24 07:16:29 hope NetworkManager[1015]: <warn> Could not get scan request result: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Is it hard to write a kernel module? 	;-)

---

### Post by Reliant39 on 2010-11-28
I have followed this thread with great interest. 

I am running Xubuntu 10.10 on my desktop PC (dual booting with Windows XP), and I rely for my Internet connection for that box on the self-same Sitecom WL-324 USB adapter (with Ralink chipset) that the OP uses. I have tried to install the XP drivers again and again using Ndiswrapper; the driver installs, but the device itself is not detected, despite using modprobe and the device being listed properly as a wireless thingy. 

It doesn't help that I have only managed to find the RT2870.sys file in my Windows directory, and had to get the RT2870.inf file from elsewhere on my drive (the adapter auto-installs, as managed earlier, and I'm not exactly sure where it sticks the .inf-file).  

So has there been any progress with the OP's problem? I imagine some sort of solution is close at hand, but I cannot, for the life of me, get this thing to work properly. Any further insight would be appreciated by this lurker!

---

### Post by Y_Ernst on 2010-12-02
I've tried to contact Ralink about this issue (because the vendor-id is 148f) and I'm still waiting for an answer.

Meanwhile I downloaded and patched the device driver 2010_0709_RT2870_Linux_STA_v2.4.0.1 from the vendors website.
(I found some instructions on gentoos wiki) and added the missing device id.

The device is now listed by the module:

alias:          usb:v148Fp2878d*dc*dsc*dp*ic*isc*ip* 

But there seems to be a strange entanglement between wlan-kernel modules and the network-manager.(The driver is ok, but the nm still crashes.) 

Until the inconsistencies in the linux device management aren't solved I stopped working on this problem.

---

### Post by Y_Ernst on 2010-12-02
Finally I managed to use the WL-324 usb-stick with the Ralink 2010_0709_RT2870_Linux_STA_v2.4.0.1 module.

I hope the list is complete:

- blacklist the rt2800usb driver.

- in rtusb_dev_id.c add the line:
  {USB_DEVICE(0x0DF6,0x003D)}, /* Sitecom */

- activate HAS_NATIVE_WPA_SUPPLICANT_SUPPORT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT in config.mk

- modify RT2870STA.dat for your country.

- Follow the gentoo wiki instructions: 
[http://en.gentoo-wiki.com/wiki/Ralink_RT2870#How_to_fix]("http://en.gentoo-wiki.com/wiki/Ralink_RT2870#How_to_fix")

- remove the old rt2870sta modules from the kernel.

- compile and install the driver.

- reboot

The tool usb-modeswitch doesn't work for me. But you can eject the storage device.  
 
Thank you for your help.

---

### Post by Y_Ernst on 2010-12-22
A small update for the new kernel version 2.6.35-24-generic.

I think the [rt2x00 project]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page") is far away from creating usable kernel drivers for rt2870 usb devices.   

For example the Sitec device id:0df6:003d was submitted a long time ago but 
it is still not recognized by the module :( 

Meanwhile I have patched the original Ralink driver (v2.4.0.1) to handle the new kernel device messages. Otherwise you get an endless list of error messages in your syslog.

---

### Post by Y_Ernst on 2011-01-29
2.6.35-25 + Ralink rt2870: 

rt2x00usb: doesn't work
rt2800usb: doesn't work + system lock

The wlan backport doesn't work for rt2870. 

:confused:


The old solution still works:

- Download the latest driver from ralink.
- Patch the device id
- patch the return codes
- patch the system messages

make; make install; remove the buggy driver from the kernel; restart

---

### Post by derxen on 2011-02-06
I want to try this too, but I have no idea how to modify modify RT2870STA.dat for my own country. Does anyone know how to do this for the Netherlands?

---

### Post by ilna on 2011-02-09
> **Y_Ernst said:**
> Meanwhile I have patched the original Ralink driver (v2.4.0.1) to handle the new kernel device messages. Otherwise you get an endless list of error messages in your syslog.I have installed v.2.4.0.1. 'iwlist scan' does find my access point, but when I try (with wicd-gtk) to connect to the access point, I get "Bad password", and the system immediately halts. At such situation it is rather difficult to play with configuration to find needed config(s) variant. syslog contains info about wicd segfaulting.

So I'm interested in this your patch - what do you mean exactly?

Also, if somebody uses wicd, which WPA Supplicant driver must be selected? wext? ralink_legacy? nl80211?

---

### Post by Y_Ernst on 2011-03-02
A small update for the latest kernel: 2.6.35-27-generic

There is a small improvement for the "rt2x00usb" module.
It doesn't immediately crash your system any more. Now you have enough time to reboot your Ubuntu and install the original ralink module: RT2870_Linux_STA_v2.4.0.1   

To patch your device, for example:
ID 0df6:003d Sitecom Europe B.V. WL-324 Wireless USB Adapter 300N
add the id to the file: common/rtusb_dev_id.c 

The last few steps are discussed above.

---

### Post by Y_Ernst on 2011-03-18
Update for the latest 10.10 kernel: 2.6.35-28-generic

Despite the fact that Ralink open-sourced and donated their driver to

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) 

the "maintained" linux driver still won't work for the Sitecom 300N usb device.

Nonetheless you can still use the old drivers mentioned above with the described patches.

---

### Post by Y_Ernst on 2011-04-16
Update for Ubuntu 10.10 2.6.35-28-generic #50-Ubuntu SMP  x86_64

The distro rt2870 and 28xxUSB drivers don't work with the the Sitecom 200N device.

Follow the instructions above to use your device.

---

