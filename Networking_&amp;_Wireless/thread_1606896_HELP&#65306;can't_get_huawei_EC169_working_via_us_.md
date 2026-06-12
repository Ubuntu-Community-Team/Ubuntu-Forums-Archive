---
title: "HELP&#65306;can't get huawei EC169 working via us_modeswitch()"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by yyyoabc on 2010-10-27
[COLOR=Navy][COLOR=Black] [COLOR=Navy]I get &#12288;HUAWEI&#12288;EC169&#12288;work well with Mobile Partner. It's known to us all  that 3G
card can be used with the help of usb_modeswitch  and wvdial. But when i try to use EC169 this way ,i got problems .I tried many solutions ,still can’t do. Anybody help? Many ,many thanks!
My environment is :

Kernel: 2.6.24-19-generi  Ubuntu 8.04
Usb_modeswitch:  usb-modeswitch-1.1.4   usb-modeswitch-data-20100826 
When i first plug in ,it runs as a CD-ROM,and pop up a auto-run dialog,i shut it ,and run follows.[/COLOR] [/COLOR]

[COLOR=Black]lee1@lee1-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem[/COLOR][/COLOR]
Bus 001 Device 002: ID 0e0f:0002
Bus 001 Device 001: ID 0000:0000

[COLOR=Black]I[COLOR=Navy]t seems that EC169 has only one address, 12d1&#65306;1001.
then i check the info in the log messages:[/COLOR]

[/COLOR]Oct 29 09:40:42 lee1-desktop kernel: [ 4261.011259] usb 1-1: new full speed USB device using uhci_hcd and address 5
Oct 29 09:40:43 lee1-desktop kernel: [ 4261.573638] usb 1-1: configuration #1 chosen from 1 choice
Oct 29 09:40:43 lee1-desktop kernel: [ 4261.626068] option 1-1:1.0: GSM modem (1-port) converter detected
Oct 29 09:40:43 lee1-desktop kernel: [ 4261.626272] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
Oct 29 09:40:43 lee1-desktop kernel: [ 4261.720286] usbcore: registered new interface driver libusual
Oct 29 09:40:43 lee1-desktop kernel: [ 4261.727035] Initializing USB Mass Storage driver...
Oct 29 09:40:43 lee1-desktop kernel: [ 4261.727100] usbcore: registered new interface driver usb-storage
Oct 29 09:40:43 lee1-desktop kernel: [ 4261.727103] USB Mass Storage support registered.
Oct 29 09:40:54 lee1-desktop kernel: [ 4282.139883] usb 1-1: USB disconnect, address 5
Oct 29 09:40:54 lee1-desktop kernel: [ 4282.263714] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Oct 29 09:40:54 lee1-desktop kernel: [ 4282.263728] option 1-1:1.0: device disconnected
Oct 29 09:41:04 lee1-desktop kernel: [ 4291.707779] usb 1-1: new full speed USB device using uhci_hcd and address 6
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.458634] usb 1-1: configuration #1 chosen from 1 choice
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.628065] option 1-1:1.0: GSM modem (1-port) converter detected
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.628169] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.634117] option 1-1:1.1: GSM modem (1-port) converter detected
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.634229] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.641952] option 1-1:1.2: GSM modem (1-port) converter detected
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.642081] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.651243] option 1-1:1.3: GSM modem (1-port) converter detected
Oct 29 09:41:05 lee1-desktop kernel: [ 4292.651372] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3 
[COLOR=Navy]
[/COLOR] [COLOR=Navy]It seems that sth like ttyUSB&#65290; has already come into being, Then i tried this:[/COLOR]

lee1@lee1-desktop:~$ dmesg | grep -e "modem" -e "tty"
[ 6.678459] console [tty0] enabled
[ 8.423191] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 8.423743] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 8.424558] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 8.425176] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 56.267489] audit(1288018969.154:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5461 profile="/usr/sbin/cupsd" namespace="default"
[ 424.369470] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[ 424.369710] option 1-1:1.0: GSM modem (1-port) converter detected
[ 424.370021] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 424.370156] option 1-1:1.1: GSM modem (1-port) converter detected
[ 424.370318] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 424.370442] option 1-1:1.2: GSM modem (1-port) converter detected
[ 424.370607] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[ 424.370739] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[ 656.470024] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 656.470399] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 656.596217] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 660.244778] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial deregistering driver GSM modem (1-port)
[ 660.269181] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[ 660.269490] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[ 670.397873] option 1-1:1.0: GSM modem (1-port) converter detected
[ 670.397980] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 670.405878] option 1-1:1.1: GSM modem (1-port) converter detected
[ 670.405987] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 670.418661] option 1-1:1.2: GSM modem (1-port) converter detected
[ 670.418774] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2

[COLOR=Black]Al[COLOR=Navy]so ,It seems that  there are already info of related ttyUSB*. but when i check in the /dev [/COLOR][/COLOR].

root@lee1-desktop:~# ls /dev/ttyU*
/dev/ttyUSB3           /dev/ttyUSB_utps_modem
/dev/ttyUSB_utps_diag  /dev/ttyUSB_utps_pcui

[COLOR=Black] [COLOR=Navy]This time there is a ttyUSB3.:) I remember last time it is a ttyUSB0 and sometime there is just none except the other  three. That's so odd!
The other three are the automatically products of &#12288;HUAWEI&#12288; Mobile Partner&#65292;cause it runs automatically when it detects ec 169. Then I test whether ttyUSB3 is a modem like this:[/COLOR][/COLOR]

root@lee1-desktop:~# wvdialconf /etc/wvdialconf
Editing `/etc/wvdialconf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB_utps_diag<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB_utps_diag<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB_utps_diag<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB_utps_modem<*1>: ATQ0 V1 E1 -- OK
ttyUSB_utps_modem<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB_utps_modem<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB_utps_modem<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB_utps_modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB_utps_modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB_utps_modem<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: HUAWEI TECHNOLOGIES CO., LTD
ttyUSB_utps_modem<*1>: Speed 9600: AT -- OK
ttyUSB_utps_modem<*1>: Max speed is 9600; that should be safe.
ttyUSB_utps_modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB_utps_pcui<*1>: ATQ0 V1 E1 -- OK
ttyUSB_utps_pcui<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB_utps_pcui<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB_utps_pcui<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB_utps_pcui<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB_utps_pcui<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB_utps_pcui<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: HUAWEI TECHNOLOGIES CO., LTD
ttyUSB_utps_pcui<*1>: Speed 9600: AT -- OK
ttyUSB_utps_pcui<*1>: Max speed is 9600; that should be safe.
ttyUSB_utps_pcui<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB_utps_modem.
Modem configuration written to /etc/wvdialconf.
ttyUSB_utps_modem<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB_utps_pcui<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

[COLOR=Black][COLOR=Navy]Obiviously it was not,:( Only the product of MP was seen as a modem.
Then I try usb_modeswitch.. I write the file usb_modeswitch.conf.
I tried HuaweiMode and later DetachStorageOnly,both has the same result.[/COLOR]

[/COLOR]# Huawei E169
# Contributor: Dale Lane
DefaultVendor= 0x12d1
DefaultProduct=0x1001
TargetClass=0xff
CheckSuccess=20
DetachStorageOnly=1
#HuaweiMode=1
EnableLogging=1

[COLOR=Black]and run follows &#65306;[/COLOR]

root@lee1-desktop:~# usb_modeswitch -W 
 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.4 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  not set
DefaultProduct= not set
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
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled
System integration mode disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 006 on 001
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
No default vendor/product ID given. Aborting.

[COLOR=Navy]I am confused , why it doesn't read the config file,cause i see others running the command and the first output is&#65306;Reading config file:&#65290;&#65290;&#65290;&#65290;&#65290;&#65288;filename&#65289;.Then i tried this :[/COLOR]

root@lee1-desktop:~# usb_modeswitch -W -c /etc/usb_modeswitch.conf
Reading config file: /etc/usb_modeswitch.conf
 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.4 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1001
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    0xff
TargetProductList=""

DetachStorageOnly=1
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
MessageEndpoint=  not set
MessageContent=""
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check enabled, max. wait time 20 seconds
System integration mode disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 006 on 001
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
  searching devices, found USB ID 0000:0000
  searching devices, found USB ID 12d1:1001
   found matching vendor ID
   found matching product ID
   target class ff matching
   adding device
  searching devices, found USB ID 0e0f:0002
  searching devices, found USB ID 0000:0000
 Found devices in target mode or class (1)
Looking for default devices ...
  searching devices, found USB ID 0000:0000
  searching devices, found USB ID 12d1:1001
   found matching vendor ID
   found matching product ID
   target class ff matching
   not adding device as default
  searching devices, found USB ID 0e0f:0002
  searching devices, found USB ID 0000:0000
 No devices in default mode or class found. Nothing to do. Bye.

[COLOR=Navy]Still can't do ,though it got the configurations, my PC is UBUNTU 8.04 under a VMare.Caould anybody help? 
Another strange thing is that I turn on logging in /etc/usb_modeswitch.conf; plug again and after a while have a look in /var/log. There is no file named "usb_modeswitch_<something>.log".
 Info from google says that it maybe due to the lack of tcl, so I test as follows:[/COLOR]

root@lee1-desktop:~# tclsh
%
[COLOR=Navy]It seems I have already got tcl. And I found that there are two in /usr/bin: tcl and tcl8.4, I wonder if they would conflict which may causes they don’t work well. [/COLOR]
[COLOR=Navy]Also info can be seen from the next code ? I just put them here.[/COLOR]

root@lee1-desktop:~# lsmod 
Module                  Size  Used by
ppp_async              13312  0 
crc_ccitt               3072  1 ppp_async
ppp_generic            29588  1 ppp_async
slhc                    7040  1 ppp_generic
[COLOR=Navy]usb_storage            73664  0 [/COLOR]
libusual               19108  1 usb_storage
option                 11520  0 
[COLOR=Navy]usbserial              35816  1 option[/COLOR]
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
vmblock                17956  3 
vsock                  42656  0 
vmmemctl               12988  0 
acpiphp                26128  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  1 acpiphp
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
vmhgfs                 45312  1 
lp                     12324  0 
evdev                  13056  3 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0 
psmouse                40336  0 
pcspkr                  4224  0 
snd_ens1371            27168  3 
gameport               16008  1 snd_ens1371
snd_ac97_codec        101028  1 snd_ens1371
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm
container               5632  0 
ac                      6916  0 
i2c_piix4               9612  0 
button                  9232  0 
vmci                   33828  1 vsock
i2c_core               24832  1 i2c_piix4
shpchp                 34452  0 
intel_agp              25492  1 
pci_hotplug            30880  2 acpiphp,shpchp
agpgart                34760  1 intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sd_mod                 30720  3 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
floppy                 59588  0 
pcnet32                34820  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
mii                     6400  1 pcnet32
[COLOR=Navy]usbcore               146028  7 usb_storage,libusual,option,usbserial,ehci_hcd,uhci_hcd[/COLOR]
mptspi                 22280  2 
mptscsih               37376  1 mptspi
mptbase                78308  2 mptspi,mptscsih
scsi_transport_spi     25472  1 mptspi
ata_piix               19588  0 
pata_acpi               8320  0 
ata_generic             8324  0 
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  8 [COLOR=Navy]usb_storage,sd_mod,sg,sr_mod,mptspi,mptscsih,scsi_transport_spi,libata[/COLOR]
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
vmxnet                 19972  0 



root@lee1-desktop:~# lsusb -v

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:02:03.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1001 E620 USB Modem
  bcdDevice            0.00
  iManufacturer           1 HUA&#65533;WEI TECHNOLOGIES
  iProduct                2 HUAWEI Mobile
  iSerial                 4 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 002: ID 0e0f:0002  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x0e0f 
  idProduct          0x0002 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 VMware Virtual USB Hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          1 VMware Virtual USB Hub
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              1 VMware Virtual USB Hub
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             7
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xfe
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:02:00.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

root@lee1-desktop:~# modprobe -v -r usbserial
FATAL: Module usbserial is in use.
root@lee1-desktop:~# modprobe -v -r option
rmmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/option.ko
rmmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko
root@lee1-desktop:~# modprobe -v option
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/option.ko

---

### Post by pdc on 2010-10-27
go here

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

Join the usb_modeswitch forum

Josh oversees the programme and the forum;

tell him all of this

when you get it sorted, tell us

---

### Post by yyyoabc on 2010-10-28
[SIZE=2]Hi,pdc


Thanks for your advice. Actually ,i registerd several times in that forum ,but  my mai-box just can get the active mail. I don't know why.  All my  mail-boxs can't receive any mails from the forum. I tried yahoo ,gmail,126 ,,none of them worked.

That means i can't have my problems checked by Josh,Could anybody help ? Or any good advices? (Can ianybody help borrow me a account for use?)

My email-addr is :liliying87@gmail.com

Thanks in advance.[/SIZE]

---

### Post by yyyoabc on 2010-10-28
> **pdc said:**
> go here

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

Join the usb_modeswitch forum

Josh oversees the programme and the forum;

tell him all of this

when you get it sorted, tell us
   

I just can't receive active mails from the  [http://www.draisberghof.de/usb_modeswitch/bb](http://www.draisberghof.de/usb_modeswitch/bb) and i got no active account.:(
 Can  anybody help me put a thread on the forum? I couldn't thanks too much.

---

