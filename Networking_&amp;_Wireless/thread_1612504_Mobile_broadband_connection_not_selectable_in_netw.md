---
title: "Mobile broadband connection not selectable in network manager"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by karamu on 2010-11-03
Hi, I am having problems with my 3 dongle- when I connect it to my netbook it flashes green so it detects a 3G network. However there is nothing in network manager enabling me to choose the mobile broadband so I can't use it. I know there should be an entry "mobile broadband" after the wireless networks listed.

I know the dongle works because I have previously used it successfully- I was using Linux Mint 8 and have now updated to version 9 and when I have tried to use it have been unable to do so.

I have gone into the connections and my 3 connection is present but there is no way for me to select it in network manager.

Any ideas??

---

### Post by karamu on 2010-11-04
I just tried on my wife's netbook and the same thing happened- no entry in the network manager list.... She is running Ubuntu 8.04 (the Dell remix for their minis).

Any suggestions anyone?

---

### Post by halj32 on 2010-11-04
have you tried installing usb-modeswitch
worked for me even though you shouldnt need it
the number should be
*99#
APN 3Connect
also give the connection a name..

have a look here
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

goodluck

---

### Post by karamu on 2010-11-05
OK, thanks, I'll give it a try.

---

### Post by joe5000 on 2010-11-05
Mobile broadband option is available
in network manager applet in new versions of Ubuntu. 09 or 10
When u right click on net manager icon on top left of speaker
you should see edit connections,
And there 
wired
wireless
mobile broadband
vpn
=====

But it takes up to 40-50 seconds Ubuntu to discover yr device.
it is not as fast as inserting usb flash disk,

---

### Post by cedricf on 2010-11-05
I have the same issue. The Mobile Broadband option is not available in network manager. I am using Ubuntu 10.04. If I right click and select edit connections, I can click on the mobile broadband tab to create a connection which I have done, but no option to 'activate it? Left click also allows me to enable networking and wireless, no option to enable mobile broadband though (not sure if it should be there?). usb-modeswitch and usb-modeswitch-data has been installed.

Any help would be appreciated please?

Thanks

---

### Post by zerubbabel on 2010-11-05
It could be that your USB mobile broadband device is first being recognized as a CD drive. Go to System>Administration>Disk Utility, and if there is an extra "CD drive", dismount it, then wait a minute and your mobile broadband connection should appear in the network manager.

---

### Post by fredmlay on 2010-11-05
> **zerubbabel said:**
> It could be that your USB mobile broadband device is first being recognized as a CD drive. Go to System>Administration>Disk Utility, and if there is an extra "CD drive", dismount it, then wait a minute and your mobile broadband connection should appear in the network manager.

Nothing happen..

---

### Post by cedricf on 2010-11-05
Did not work for me as well :(

---

### Post by Hippytaff on 2010-11-05
What is the output of
```

lsusb

```
with the dongle plugged in?
also what does
```

rfkill list

```
show?

---

### Post by cedricf on 2010-11-05
> **Hippytaff said:**
> What is the output of
```

lsusb

```with the dongle plugged in?
also what does
```

rfkill list

```show?

Output from lsusb:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Output from rfkill list:

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by Hippytaff on 2010-11-05
ok Huawei Technologies is the name of the usb chipset thing. And you've tried
 
```

usb_modeswitch -H -p 1446 -v 12d1 -W

```
 
I'm not at my linux box now, but someone might be able to jump in here - you can check to see if the driver is installed with modprobe, but can't remember the command and can't faff around in a terminal to find it. Might just be
```

modprobe

```

---

### Post by cedricf on 2010-11-05
> **Hippytaff said:**
> ok Huawei Technologies is the name of the usb chipset thing. And you've tried
 
```

usb_modeswitch -H -p 1446 -v 12d1 -W

```I'm not at my linux box now, but someone might be able to jump in here - you can check to see if the driver is installed with modprobe, but can't remember the command and can't faff around in a terminal to find it. Might just be
```

modprobe

```

Getting the following:

Taking all parameters from the command line


 * usb-modeswitch: handle USB devices with multiple modes
 * Version 1.1.0 (C) Josua Dietze 2010
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1446
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=1
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
usb_os_find_busses: Found 008
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 008
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 007
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 006
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 005
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 002 on 004
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 004
error obtaining child information: Operation not permitted
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 003
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 002
error obtaining child information: Operation not permitted
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 008 on 001
usb_os_find_devices: couldn't get connect info
usb_os_find_devices: Found 001 on 001
error obtaining child information: Operation not permitted
error obtaining child information: Operation not permitted

Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 0a5c:2145
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 12d1:14ac
   found matching vendor ID
  searching devices, found USB ID 1d6b:0002
 No default device found. Is it connected? Bye.

---

### Post by Hippytaff on 2010-11-05
Sorry, try
```

sudo usb_modeswitch -H -p 0x12d1 -v 0x14ac -W

```
had wrong vendor infor etc (you might need to put sudo infrom - I didn't think you had to but...)

---

### Post by karamu on 2010-11-05
[QUOTE=joe5000;10074881]Mobile broadband option is available
in network manager applet in new versions of Ubuntu. 09 or 10
When u right click on net manager icon on top left of speaker
you should see edit connections,
And there 
wired
wireless
mobile broadband
vpn
=====

Yes, that's exactly what I expected to find- it was the case previously but nothing is there this time.

---

### Post by Hippytaff on 2010-11-05
> **Hippytaff said:**
> ok Huawei Technologies is the name of the usb chipset thing. And you've tried
 
```

lsusb

```
```

sudo usb_modeswitch -H -p 0x12d1 -v 0x14ac -W

```
 
I'm not at my linux box now, but someone might be able to jump in here - you can check to see if the driver is installed with modprobe, but can't remember the command and can't faff around in a terminal to find it. Might just be
```

modprobe

```
 
What about you karimu? replacing 0x12d1 and 0x14ac with the correct ones from your lsusb output

---

### Post by karamu on 2010-11-05
> **halj32 said:**
> have you tried installing usb-modeswitch
worked for me even though you shouldnt need it
the number should be
*99#
APN 3Connect
also give the connection a name..

have a look here
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

goodluck

I just installed usb-modeswitch and it has worked! Mobile broadband is now listed under network manager! For reference, the dongle is a 3 Huawei 1550.

---

### Post by cedricf on 2010-11-08
> **Hippytaff said:**
> Sorry, try
```

sudo usb_modeswitch -H -p 0x12d1 -v 0x14ac -W

```had wrong vendor infor etc (you might need to put sudo infrom - I didn't think you had to but...)

Thanks for you assistance so far. I tried the new command ... here is the output:

Taking all parameters from the command line


 * usb-modeswitch: handle USB devices with multiple modes
 * Version 1.1.0 (C) Josua Dietze 2010
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x14ac
DefaultProduct= 0x12d1
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=1
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
usb_os_find_busses: Found 008
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 008
usb_os_find_devices: Found 001 on 007
usb_os_find_devices: Found 001 on 006
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 003 on 004
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 004
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 003 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 001

Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 0a5c:2145
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 12d1:14ac
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 1d6b:0002
 No default device found. Is it connected? Bye.

I am using the E1820 usb modem for reference. Thanks.

---

### Post by Hippytaff on 2010-11-08
Doesn't look like ubuntu can see the usb dongle.
 
Try lsusb again with it plugged in.
and
```

lsmod | grep E1820

```
if the above command returns nothing post the results of just
```

lsmod

```

---

### Post by alexfish on 2010-11-08
hi cedricf

from your info the device has already switched

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=Blue]Bus 001 Device 008: ID[/COLOR] [COLOR=Red]12d1:14ac[/COLOR] [COLOR=Blue]Huawei Technologies Co., Ltd.[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

from your listing the device has switched

check file.

Code:

[COLOR=Blue]cat /etc/usb_modeswitch.d/12d1:1446[/COLOR]

from the terminal find out the state of the device to see if the drivers have loaded

If Ubuntu version 10.04 or 10.10 try

Code:

[COLOR=Blue]usb-devices
[/COLOR]
locate the lines which indicate the device and post only those lines

or try

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]

Post the results

alexfish

---

### Post by cedricf on 2010-11-08
> **Hippytaff said:**
> Doesn't look like ubuntu can see the usb dongle.
 
Try lsusb again with it plugged in.
and
```

lsmod | grep E1820

```if the above command returns nothing post the results of just
```

lsmod

```

Hello Hippotaff ... thanks for the help so far ... lsmod with grep yielded nothing .. here is lsmod on its own:

Module                  Size  Used by
usblp                  10481  0 
ppp_deflate             3682  0 
zlib_deflate           19568  1 ppp_deflate
bsd_comp                4811  0 
ppp_async               6734  0 
crc_ccitt               1339  1 ppp_async
nls_utf8                1069  1 
isofs                  29250  1 
option                 19686  0 
usbserial              33019  1 option
usb_storage            39553  1 
binfmt_misc             6587  1 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
ipt_LOG                 4542  2 
ipt_REJECT              1928  1 
iptable_nat             4414  0 
nf_nat                 15735  1 iptable_nat
nf_conntrack_ipv4      10672  5 iptable_nat,nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_filter          2271  1 
ip_tables               9991  2 iptable_nat,iptable_filter
ip6t_LOG                4669  2 
xt_limit                1382  4 
ip6t_REJECT             2604  1 
xt_tcpudp               2011  72 
ip6t_ah                  993  1 
nf_conntrack_ipv6      10447  2 
xt_state                1098  4 
ip6table_filter         2343  1 
ip6_tables             11227  3 ip6t_LOG,ip6t_ah,ip6table_filter
x_tables               14299  11 ipt_LOG,ipt_REJECT,iptable_nat,ip_tables,ip6t_LOG,xt_limit,ip6t_REJECT,xt_tcpudp,ip6t_ah,xt_state,ip6_tables
vmnet                  40983  13 
ppdev                   5259  0 
parport_pc             25962  0 
vmblock                10766  1 
vsock                  37367  0 
vmci                   52974  1 vsock
vmmon                  62872  0 
dm_crypt               11331  0 
arc4                    1153  2 
snd_hda_codec_conexant    22641  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
iwlagn                106815  0 
iwlcore               106050  1 iwlagn
nf_conntrack_ftp        5381  0 
thinkpad_acpi          68083  0 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_hwdep               5412  1 snd_hda_codec
snd_rawmidi            19056  1 snd_seq_midi
snd_pcm_oss            35308  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_mixer_oss          13746  1 snd_pcm_oss
nf_conntrack           61615  6 iptable_nat,nf_nat,nf_conntrack_ipv4,nf_conntrack_ipv6,xt_state,nf_conntrack_ftp
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      7060  0 
mac80211              205402  2 iwlagn,iwlcore
joydev                  8708  0 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
parport                32635  3 ppdev,parport_pc,lp
snd                    54180  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,thinkpad_acpi,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
btusb                  10957  2 
psmouse                63245  0 
cfg80211              126528  3 iwlagn,iwlcore,mac80211
soundcore               6620  1 snd
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
led_class               2864  2 iwlcore,thinkpad_acpi
tpm_tis                 7422  0 
nvram                   6203  1 thinkpad_acpi
tpm                    13484  1 tpm_tis
tpm_bios                5266  1 tpm
serio_raw               3978  0 
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  286079  3 
drm_kms_helper         29297  1 i915
ohci1394               26950  0 
intel_agp              24119  2 i915
drm                   162409  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
e1000e                119856  0 
ieee1394               81181  1 ohci1394
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video

---

### Post by cedricf on 2010-11-08
> **alexfish said:**
> hi cedricf

from your info the device has already switched

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=Blue]Bus 001 Device 008: ID[/COLOR] [COLOR=Red]12d1:14ac[/COLOR] [COLOR=Blue]Huawei Technologies Co., Ltd.[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

from your listing the device has switched

check file.

Code:

[COLOR=Blue]cat /etc/usb_modeswitch.d/12d1:1446[/COLOR]

from the terminal find out the state of the device to see if the drivers have loaded

If Ubuntu version 10.04 or 10.10 try

Code:

[COLOR=Blue]usb-devices
[/COLOR]
locate the lines which indicate the device and post only those lines

or try

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]

Post the results

alexfish

Hi alexfish .. thanks for assisting .. here is the cat output:

########################################################
# Huawei, newer modems

DefaultVendor= 0x12d1
DefaultProduct=0x1446

TargetVendor=  0x12d1
TargetProductList="1001,1406,140b,140c,1412,141b,14ac"

CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

Here is the ls output:

lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB3

Thanks

---

### Post by Hippytaff on 2010-11-08
I've only had a quick look, but I'd say you need to install the driver...with ndiswrapper
 
Edit -> pending 

> 

[COLOR=blue]usb-devices
[/COLOR]
locate the lines which indicate the device and post only those lines

or try

Code:

[COLOR=blue]ls -al /dev/serial/by-id/usb*[/COLOR]

Post the results


---

### Post by alexfish on 2010-11-08
hi cedricf

from the info

lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0 ->  ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB3

these lines indicate the modem and the drivers have configured

will the device configure with the network manager


if not it will help if you could post details of 

Code:

[COLOR=Blue]usb-devices[/COLOR]

this will help determine the data port

sure the above command available in 10.04

alexfish

---

### Post by cedricf on 2010-11-08
Hi alexfish .. here is the output for the command usb-devices :

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ac Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=2145 Rev=03.99
S:  Manufacturer=Lenovo Computer Corp
S:  Product=ThinkPad Bluetooth with Enhanced Data Rate II
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
cedricf@cedricf-laptop:~$ usb-devices | grep e1820
cedricf@cedricf-laptop:~$ usb-devices | grep 1820
cedricf@cedricf-laptop:~$ usb-devices | grep huw
cedricf@cedricf-laptop:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ac Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=2145 Rev=03.99
S:  Manufacturer=Lenovo Computer Corp
S:  Product=ThinkPad Bluetooth with Enhanced Data Rate II
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
cedricf@cedricf-laptop:~$ clear

cedricf@cedricf-laptop:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ac Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=2145 Rev=03.99
S:  Manufacturer=Lenovo Computer Corp
S:  Product=ThinkPad Bluetooth with Enhanced Data Rate II
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

Thanks for your assistance.

---

### Post by Hippytaff on 2010-11-08
```

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ac Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```
I don't think mode-switch has worked :-)

---

### Post by alexfish on 2010-11-08
Hi cedicf

from your info

T: Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 8 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=14ac Rev=00.00
S: Manufacturer=Huawei Technologies
S: Product=HUAWEI Mobile
C: #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I: [COLOR=Blue]If#= 0[/COLOR] Alt= 0 #[COLOR=Blue]EPs= 3[/COLOR] Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: [COLOR=Blue]If#= 1[/COLOR] Alt= 0 #[COLOR=Blue]EPs= 3[/COLOR] Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-[COLOR=Blue]if00[/COLOR]-port0 ->  ../../[COLOR=Blue]ttyUSB0[/COLOR]
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-[COLOR=Blue]if01[/COLOR]-port0 -> ../..[COLOR=Blue]/ttyUSB1[/COLOR]

lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB3


there appears to be two data ports on this device highlighted in blue Note the EPs=3
it would be normal to assume the correct Data Port would be ttyUSB0
and the associated driver is option / 

so as far as Linux system is concerned the device is recognized , so depending on the connection manager you should be able to connect

I had requested does the network manager recognize the device / I am assuming not

but looking through your post your system is 10.04 / the modem-manager to which network manager depends on for mobile connections,
may not be seeing the device for several reasons, to in depth to go into at present

If your connection is 3g then I suggest 

confirm Network Manager can not connect with this device
or check if modem-manager is installed

Code:

[COLOR=Blue]which modem-manager[/COLOR]

post the results

for ease of use try Sakis3g ,

from  

**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBkQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=wmvYTK25B5uS4gajiNziBw&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**


let us know of any progress

Sakis also has a forum;

[SIZE=2][Forum]("http://forum.sakis3g.org/")[/SIZE]

alexfish

---

### Post by cedricf on 2010-11-09
Hi alexfish .... the command which modem-manager gave nothing, so I checked synaptic and it was not installed!! Installed it and it works! ... Thank you for help!

---

### Post by Hippytaff on 2010-11-09
Glad it's sorted. Remeber to mark the thread as solved in the thread tools at the top of the page so others can see how you fixed it. :-)

---

### Post by cedricf on 2010-11-09
> **Hippytaff said:**
> Glad it's sorted. Remeber to mark the thread as solved in the thread tools at the top of the page so others can see how you fixed it. :-)

Karamu originally created the thread ... I just piggybacked off it. No option in thread tools for me to close it ... hopefully Karamu will see this and close :)    ... Thanks for all your assistance.

---

### Post by karamu on 2010-11-09
> **cedricf said:**
> Karamu originally created the thread ... I just piggybacked off it. No option in thread tools for me to close it ... hopefully Karamu will see this and close :)    ... Thanks for all your assistance.

OK, I will mark it as solved- glad we could both resolve our issues! I'm happy that my thread was the spark to help someone else out! (Typing from my mobile connection right now!)

---

### Post by leonbravo on 2012-10-07
> **alexfish said:**
> hi cedricf

from the info

lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0 ->  ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-11-08 16:07 /dev/serial/by-id/usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB3

these lines indicate the modem and the drivers have configured

will the device configure with the network manager


if not it will help if you could post details of 

Code:

[COLOR=Blue]usb-devices[/COLOR]

this will help determine the data port

sure the above command available in 10.04

alexfish

Hi, I'm in the process of solving a similar problem under ubuntu 12.4.

I use the command ls as described but doesn't find  anything on /serial/

ls: cannot access /dev/serial/by-id/usb*: No such file or directory

This is my output for:

[COLOR=Blue]usb-devices[/COLOR]

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1446 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


Please, post me with any instructions...

---

