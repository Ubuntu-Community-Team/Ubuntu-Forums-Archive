---
title: "Has anyone got the Huawei E586 working on ubuntu 11.10?"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by Hugh Mulqueen on 2011-11-04
Just got my new Huawei E586 Mywifi device. Does anybody have this working when the device is plugged in via the USB port. Just wondering does anyone have a driver or a port. It says on the three website that it works with linux. So it shouldn't have any problems connecting. I have the latest linux kernel 3.08 installed.
Anyone have any ideas?:confused:

---

### Post by cariboo on 2011-11-04
Moved to Networking & Wireless, as this is a support question, not something you'd ask in the Cafe.

---

### Post by praseodym on 2011-11-04
Hi,

please show the outputs of

```
lsusb
lsmod
usb-devices
```

---

### Post by Hugh Mulqueen on 2011-11-05
Sorry should have put this in the networking section I suppose...
I'm on this fourm long enough now to know the difference. 

Here's my output anyway:

```
Output for lsusb:
lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1c4f:0003 SiGma Micro HID controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 12d1:1c1f Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Output for lsmod:
lsmod
Module                  Size  Used by
nls_utf8                1405  1 
fuse                   63903  5 
vboxnetadp              5833  0 
vboxnetflt             18047  0 
vboxdrv              1792317  2 vboxnetadp,vboxnetflt
sunrpc                203677  1 
ipv6                  290970  33 
cpufreq_ondemand        6044  1 
powernow_k8            21808  1 
freq_table              5054  2 cpufreq_ondemand,powernow_k8
mperf                   1433  1 powernow_k8
uinput                  7378  0 
tuner_simple           11573  1 
tuner_types            18715  1 tuner_simple
tuner                  15504  1 
ir_lirc_codec           4310  0 
lirc_dev               13060  1 ir_lirc_codec
tvaudio                25488  0 
ir_sony_decoder         2109  0 
tda7432                 4450  0 
ir_jvc_decoder          2308  0 
msp3400                25293  0 
nvidia              11901801  30 
snd_hda_codec_realtek   322924  1 
snd_hda_intel          23961  2 
ir_rc6_decoder          2763  0 
ir_rc5_decoder          2138  0 
bttv                  112890  0 
i2c_algo_bit            5022  1 bttv
videobuf_dma_sg         8438  1 bttv
snd_hda_codec          83855  2 snd_hda_codec_realtek,snd_hda_intel
videobuf_core          16012  2 bttv,videobuf_dma_sg
btcx_risc               3690  1 bttv
ir_nec_decoder          2596  0 
snd_bt87x              10614  1 
rc_core                17117  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,bttv,ir_nec_decoder
snd_hwdep               6312  1 snd_hda_codec
tveeprom               13481  1 bttv
v4l2_common             6889  5 tuner,tvaudio,tda7432,msp3400,bttv
videodev               72719  6 tuner,tvaudio,tda7432,msp3400,bttv,v4l2_common
snd_seq                53033  0 
snd_seq_device          5977  1 snd_seq
snd_pcm                80006  3 snd_hda_intel,snd_hda_codec,snd_bt87x
v4l2_compat_ioctl32     7537  1 videodev
cdc_ncm                11676  0 
usbnet                 24141  1 cdc_ncm
ppdev                   7556  0 
snd_timer              19419  2 snd_seq,snd_pcm
snd                    63813  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_bt87x,snd_hwdep,snd_seq,snd_seq_device,snd_pcm,snd_timer
r8169                  39060  0 
edac_core              40516  0 
mii                     4367  2 usbnet,r8169
parport_pc             21271  0 
parport                31258  2 ppdev,parport_pc
i2c_piix4              10518  0 
i2c_core               25952  12 tuner_simple,tuner,tvaudio,tda7432,msp3400,nvidia,bttv,i2c_algo_bit,tveeprom,v4l2_common,videodev,i2c_piix4
soundcore               6377  1 snd
snd_page_alloc          7367  3 snd_hda_intel,snd_bt87x,snd_pcm
edac_mce_amd           13234  0 
pcspkr                  1926  0 
k8temp                  3651  0 
floppy                 57190  0 
wmi                     9129  0 
pata_acpi               3435  0 
firewire_ohci          26287  0 
ata_generic             3651  0 
firewire_core          49719  1 firewire_ohci
usb_storage            46063  1 
crc_itu_t               1547  1 firewire_core
pata_atiixp             4157  0 

Output for usb-devices:
$ usb-devices
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.8 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.5
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c1f Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0d Prot=00 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.8 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.8 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1c4f ProdID=0003 Rev=01.10
S:  Manufacturer=SIGMACH1P
S:  Product=U+P Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.8 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.8 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.8 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.4
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```

As you can see its not really recognised in lsusb or lsmod. and in usb-devices its only recognised as a Mass storage device.
We'll see what we can do sure. Its a pretty new device anyway.
I might have to mess about wvdial.

---

### Post by pdc on 2011-11-05
I am assuming that you believe that you have to plug this device into your laptop, for it to work............

my assumption was that this device functions as a router; has a battery in it;

and transmits a wifi signal so that up to 5 laptops sitting close by;

so the signal comes into it as 3G mobile broadband;

but it then transmits a wifi signal out from itself;

so you need the wireless receiver on your laptop to be working;

eg see this video

[http://www.three.co.uk/Devices/Huawei/E586](http://www.three.co.uk/Devices/Huawei/E586)

so I would suggest it is wireless you need to connect to it......

---

### Post by praseodym on 2011-11-06
Try to switch to modem modus (copy/paste these lines):

```
sudo usb_modeswitch -v 12d1 -p 1c1f -M '55534243123456780000000000000011062000000100000000000000000000'
sudo modprobe option
echo "12d1 1c1f" | sudo tee /sys/bus/usb-serial/drivers/option1/new_id 
```
Did you install USB-modeswitch?

---

### Post by pdc on 2011-11-06
I am assuming that you believe that you have to plug this device into your laptop, for it to work............

***in contrast***.............my assumption was that this device functions as a **wifi** router; has a battery in it;

and transmits a **wifi** signal so that up to 5 laptops sitting close by can receive the **wifi** signal;

so the signal comes into it as 3G mobile broadband;

but it then transmits a **wifi** signal out from itself;

so you need the **wireless** receiver on your laptop to be working;

eg see this video

[http://www.three.co.uk/Devices/Huawei/E586](http://www.three.co.uk/Devices/Huawei/E586)

---

### Post by Hugh Mulqueen on 2011-11-07
I'm plugging it in using a USB port. Its not a laptop its a desktop that I have with no Wifi card. So until I can pecure one ill use USB port. And no I dont have usb-modeswitch installed thanks for the tipps. I'll run those commands as soon as possible.

---

### Post by IJHarvey on 2011-11-07
I've got one of these and as far as I can make out it only functions as a USB device under windows.  (I've used it under XP).  Under Ubuntu I've had it running nicely as a wifi connection on one PC (11.04) but not on another (11.10) as well as a couple of Android tablets.  I haven't been able to get it working as a usb device on either Ubuntu machines. (but then again I haven't tried that hard :P)
Take care
Ian

---

### Post by alexfish on 2011-11-08
> **IJHarvey said:**
> I've got one of these and as far as I can make out it only functions as a USB device under windows.  (I've used it under XP).  Under Ubuntu I've had it running nicely as a wifi connection on one PC (11.04) but not on another (11.10) as well as a couple of Android tablets.  I haven't been able to get it working as a usb device on either Ubuntu machines. (but then again I haven't tried that hard :P)
Take care
Ian

hi

according to the list the drivers have not loaded

```
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c1f Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
[COLOR=Blue]I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)[/COLOR]
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
[COLOR=Blue]I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0d Prot=00 Driver=(none)[/COLOR]
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```
suggest going to the working system 11.04 and list the devices with the usb-devices command
```
usb-devices
```this will show the drivers

the main driver if fully working could be listed at

[COLOR=Blue]I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0d Prot=00 Driver=<driver>[/COLOR]

if not fully functional the a default driver may show up at

[COLOR=Blue]If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=<driver>[/COLOR]

can try and load the drivers in 11.10 with
```
sudo modprobe <driver>
```
alexfish

---

### Post by alexfish on 2011-11-11
Hi Hugh Mulqueen

assuming this is the device listing from the info posted

```
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c1f Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0d Prot=00 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")

Have a look at  Posts  #[**59**]("http://ubuntuforums.org/showpost.php?p=11443633&postcount=59")  and   #[**60 **]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60")

this shows examples of how to find a suitable driver module and how to load it

if stuck post back here

ADDED:

if have read the thread 

then should have these



grep with "ip00" 
```

alias usb:v07B4p0F02d*dc*dsc*dp*ic02isc06ip00* cdc_ether
```

then grep the modules with "p12d1" it should come up with this

```
alias usb:v12D1p*d*dc*dsc*dp*ic02isc06ipFF* cdc_ether
```

can post the results of the modalias to confirm


alexfish

---

### Post by Hugh Mulqueen on 2011-11-28
Thank you alexfish for the help. Very informitive. I'll give that a go soon. I was just wondering what module would I load for the modem sierra or something else? After a lot of fiddling I got the wifi working on my system. It took the whole weekend. but I got there eventually.:p I'd still like to know if its possible to get this yoke working though. So any help on which module to load would be great. 

Thanks, Hugh.

---

### Post by alexfish on 2011-11-28
the code
to modprobe driver
```
sudo modprobe cdc_ether
```then list the device with
```
usb_devices
```from listing can tell if driver has bound to the device then
to see if ports have registered in the devs
```
ls -al /dev/serial/by-id
```or ```
ls /dev/ttyACM*
```will also have to see if the ether port is established , normally seen in usb0, and possible see if the device has mac address use the lsusb -v option
```
lsusb -v
```alexfish

ADDED:
added there is also another possible driver
modprobe with
```
sudo modprobe qcaux
```

if all fails will post further to get the modalias listings , then possible add the device to the new_id of suitable driver

---

### Post by Eug48 on 2011-12-27
I've managed to get the serial interface connecting. Basically, the device (Huawei E586Bs-2) starts out at 12d1:14fe and usb_modeswitch already has a rule for it. The existing rule switches it to 12d1:1c1e and I had to add 1c1e to usb_modeswitch's TargetProductList (placed attached file into /etc/usb_modeswitch.d/) After doing this, the id is added to the option driver and I get three interfaces:

/dev/ttyUSB0
/dev/ttyUSB1
/dev/ttyUSB2

Running "screen /dev/ttyUSB1" I'm able to send AT commands. However, I'm not having much luck with wvdial. I don't know the config to use... My best attempt has been:

> 
~# cat .wvdialrc
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Check Def Route = on
Phone = *99#
Modem Type = Analog Modem
Stupid Mode = 1
Baud = 9600
Dial Command = ATDT
Dial Attempts = 3
Modem = /dev/ttyUSB1
ISDN = 0
Password = dummy
Username = dummy

[Dialer connect]
Init2 = ATZ
#Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
Init4 = AT+CGDCONT=1,"IP","yesinternet"
ISDN = 0
Modem = /dev/ttyUSB1
Modem Type = Analog Modem
Baud = 460800
~# wvdial connect
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","yesinternet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Dec 27 22:47:52 2011
--> Pid of pppd: 4162
--> Using interface ppp0
--> pppd: &#65533;[
--> [08]&#65533;\
--> [08]
--> pppd: &#65533;[
--> [08]&#65533;\
--> [08]
--> pppd: &#65533;[
--> [08]&#65533;\
--> [08]
--> pppd: &#65533;[
--> [08]&#65533;\
--> [08]
--> pppd: &#65533;[
--> [08]&#65533;\
--> [08]
--> Disconnecting at Tue Dec 27 22:48:22 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
--> Disconnecting at Tue Dec 27 22:48:44 2011




Any help would be much appreciated  :)

---

### Post by praseodym on 2011-12-27
Hi,

have a look here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by Eug48 on 2011-12-27
Thanks, I had a look but everything in that checklist looks OK. The device works on a Windows XP laptop.

---

### Post by praseodym on 2011-12-27
Can you try this:

```
sudo usb_modeswitch -v 12d1 -p 14fe -M '55534243123456780000000000000011062000000100000000000000000000'
```
It switches to modem mode, too. Then load the driver with the _new_ ID from "lsusb":

```
sudo modprobe usbserial vendor=0x[COLOR="Red"]12d1[/COLOR] product=0x[COLOR="Red"]1506[/COLOR]
```
Maybe in your case **1506** is **1c1e**
Check:
```
lsusb
lsmod
usb-devices
dmesg | egrep 'option|ppp0|tty|usb'
```

---

### Post by Eug48 on 2011-12-28
That part is already working for me - it's already switching fine with that same "5553..." message and the serial driver is loading. Do you mean I should try usbserial instead of option?

---

### Post by praseodym on 2011-12-28
Yes, if its working...You can add an UDEV-rule:

```
sudo apt-get install unzip
wget [ftp://ftp.heise.de/pub/ct/listings/1116-134.zip](ftp://ftp.heise.de/pub/ct/listings/1116-134.zip)
unzip 1116-134.zip
sudo mv 70-usb_modeswitch.rules /etc/udev/rules.d/
sudo service udev reload
```

---

### Post by Eug48 on 2011-12-29
It's working that far, but I can't actually make a 3G connection..

---

### Post by Eddison on 2012-01-11
Looks like the only solution to this is to buy a cheap netword card or usb network dongle =0|

---

### Post by aidani on 2012-01-14
I too am trying to get Huawei E586 working on Ubuntu 11.10 - but no joy.

Whether I plug it into USB port or not the E586 is detected, and listed  as an available wireless network named with the correct SSID of my  device "3MobileWiFi-3bc9" (both by Wicd and by the network manager tool that comes standard  with Ubuntu 11.10)

When I try to connect it asks for the password (saying authentication required by wireless network, which I believe is correct) and i enter  the 8 digit wifi key which came with the device and then it fails to  connect and asks again for the password as it retries...

The trace from /var/log/syslog (attached - top and bottom of file most interesting, rest is just repetition upon retries to establish connection) shows:
eth1: Lucent/Agere firmware doesn't support manual roaming 
... and I have no clue what this is referring to or where to go from here. 

Has anyone gotten the E586 working with any version of Ubuntu or other Linux?

---

### Post by alexfish on 2012-02-03
Hi all

have been looking further into Huawei E586 , this device may have several usb ID's
depending on original Unswitch ID and the Switched ID

looking at the info available , drivers are binding to specific parts of the device , due to the info given by the
modalias , Drivers for these type of devices appears to be on going , unless some one knows different

Refer to Post              #[**60  foot of page**]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60")


**Feel free to post any info or links to driver patches** HERE : [COLOR=#980101]****[/COLOR] 			 			[E586 huawei (mobile wifi router )]("http://ubuntuforums.org/showthread.php?t=1881919")

regards
alexfish

---

### Post by chris.dietrich on 2013-01-20
Hello I have been following this thread for a while and last night by accident I managed to get my E586 fully working under my ubuntu system, just like it behaves under windows.

Huawei released linux drivers for their data cards on the 19 Dec 2012 the direct link to the download page is [http://www.huaweidevice.com/worldwide/downloadCenter.do?method=toDownloadFile&flay=software&softid=NDcwMzU=]("http://www.huaweidevice.com/worldwide/downloadCenter.do?method=toDownloadFile&flay=software&softid=NDcwMzU=")


the steps i took to make this work on my ubuntu 12.10 3.5.0-22-generic was:-

-download the drivers from the above site
-made a new folder under my home directory 'mkdir ~/huawei'
-unziped the driver folder to ~/huawei
-then in a term, as superuser (sudo -i), i did 'cd /home/{USER}/huawei/driver' followed by ./install /home/{USER}/huawei


I think you need gcc and kernel header to compile properly.


I hope this helps someone out there it had me looking for a year now


Chris

---

### Post by shadowslider on 2013-06-12
followed these steps on Ubuntu 12.04 64Bit desktop and all works well even under VMWare

---

