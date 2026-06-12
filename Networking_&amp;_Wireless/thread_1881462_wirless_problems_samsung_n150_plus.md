---
title: "wirless problems samsung n150 plus"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by fidelandche on 2011-11-15
Hi all,

I have a Samsung N150 plus netbook which is having problems connecting to a wireless hub. What happens is the wireless indicator just keeps showing it is trying to connect to the hub, until the dialogue box appears saying you are now disconnected from wireless networks, you then click on the wireless indicator and then I can connect to the wireless network. I have removed the wireless connection and then re-added it, but the problem still exists.

Running Ubuntu 11.04 as the only OS, this problem has only appeared in the last few weeks.Using BT Home hub 2.0

Specs of the netbook [http://www.samsung.com/uk/consumer/pc-peripherals/notebook-computers/netbook/NP-N150-JP07UK-spec]("http://www.samsung.com/uk/consumer/pc-peripherals/notebook-computers/netbook/NP-N150-JP07UK-spec")

---

### Post by deltacomp on 2011-11-15
Hello, have you ever been able to connect through the wireless?

Please post the output of

lspci -nn

iwconfig

---

### Post by praseodym on 2011-11-15
Hi,

please show additionally:
```
lsmod
lsusb
usb-devices
hciconfig --all
rfkill list
sudo iwlist scan
```

---

### Post by fidelandche on 2011-11-16
@ deltacomp, yes I have been able to connect before wirelessly.

---

### Post by fidelandche on 2011-11-16
Output from all the commands
 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]

---

### Post by fidelandche on 2011-11-16
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:203  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

 lsmod
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
easy_slow_down_manager    12985  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rfcomm                 38125  8 
i915                  451033  3 
snd_seq_midi_event     14475  1 snd_seq_midi
sco                    17827  2 
bnep                   17785  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
acpi_cpufreq           13167  1 
snd_timer              28659  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17203  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
btusb                  18160  2 
wl                   2642531  0 
samsung_backlight      13487  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                73312  0 
uvcvideo               66851  0 
serio_raw              12990  0 
drm                   184164  4 i915,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0

---

### Post by fidelandche on 2011-11-16
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:219c Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by fidelandche on 2011-11-16
usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0ac8 ProdID=c33f Rev=01.00
S:  Manufacturer=Namuga.
S:  Product=WebCam SCB-0340N
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=128mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=219c Rev=06.00
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom BCM2070 Bluetooth Device
S:  SerialNumber=001BB111E446
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by fidelandche on 2011-11-16
hciconfig --all
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1B:B1:11:E4:46  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING PSCAN 
	RX bytes:687 acl:0 sco:0 events:25 errors:0
	TX bytes:594 acl:0 sco:0 commands:25 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'millie-N150P-N210P-N220P-0'
	Class: 0x4a0100
	Service Classes: Networking, Capturing, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 3.0 (0x5)  Revision: 0x258
	LMP Version: 3.0 (0x5)  Subversion: 0x4203
	Manufacturer: Broadcom Corporation (15)

---

### Post by fidelandche on 2011-11-16
rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by fidelandche on 2011-11-16
however I am  unable to post the outcome from the last command as I get the error that there are too many images? In the post.

---

### Post by praseodym on 2011-11-16
Direct the outcome directly into a text file:

```
sudo iwlist scan >> wlan.txt
```

You are using mixed WPA/WPA2 encryption? The network-manager often makes problems with that, better change to WPA2 only

---

### Post by fidelandche on 2011-11-17
here is the output;


millie@millie-N150P-N210P-N220P:~$ sudo iwlist scan >> wlan.txt
[sudo] password for millie: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

millie@millie-N150P-N210P-N220P:~$

---

### Post by fidelandche on 2011-11-17
> **praseodym said:**
> Direct the outcome directly into a text file:


You are using mixed WPA/WPA2 encryption? The network-manager often makes problems with that, better change to WPA2 only

that is the only option there is.

---

### Post by praseodym on 2011-11-17
Try Wicd instead:
```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Those encryption templates are pretty good for that. Choose **eth1** as interface name and **wext** as driver. You may need to uninstall the networkmanager completely.

---

