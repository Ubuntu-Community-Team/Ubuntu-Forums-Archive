---
title: "Mobile Broadband - Huawei BM-358 on Lubuntu-GNOME-13.04."
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by Sean Moran on 2013-05-01
I bought a Vividwireless 4G Huawei BM-358 mobile broadband stick from **** Smith's in Fremantle Western Australia on Friday, and haven't had any luck getting it to light up yet.

With my apologies if I may have overlooked the answer, wherever I've searched: vividwireless, linuxquestions, huawei, mint, here, the most I can gather is that the lsusb and modprobe commands are what you're supposed to use to configure a driver, (I did the realtek driver for this laptop from source code last year), but nowhere could I find a link where I might be able to download a .TAR.GZ or maybe a .DEB file to get that driver.

The best solution I found was one fellow who ran Windows in VM box to make use of the Vividwireless 4G facilities, and I'd rather not have to jump to such conclusions.

For what it is worth, I have listed some hardware specs and the lsusb, lspci, lsmod readouts, and would like to take this opportunity to beg anyone who has managed to get a Vividwireless Huawei BM-358 mobile broadband stick to run on Ubuntu 13.04 to give me a hint on how you ever did it.  I'll be forever in your debt. 
(I might have to go offline for a few days next week otherwise.)

**HARDWARE**
Computer:  Toshiba U840W Ultrabook.
Processor:  4x Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
Memory:    6105MB (305MB used)
OpSystem: Luuntu 13.04 running GNOME Fallback (No effects)
Kernel:      Linux 3.8.0-19-generic (i686)

**LSUSB:**
```

tos@tos:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
[COLOR=#008000]**Bus 003 Device 006: ID 12d1:380b Huawei Technologies Co., Ltd. WiMAX USB modem(s)**[/COLOR]
Bus 003 Device 002: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b2f9 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0930:021d Toshiba Corp. 
Bus 003 Device 003: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 003 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 003 Device 005: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
tos@tos:~$ 

```

**LSPCI:**
```

tos@tos:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.6 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 7 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
03:00.0 Ethernet controller: Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)
tos@tos:~$ 

```

**LSMOD:**
```

tos@tos:~$ lsmod
Module                  Size  Used by
cdc_ether              13245  0 
ppp_deflate            12806  0 
zlib_deflate           26445  1 ppp_deflate
bsd_comp               12785  0 
ppp_async              17205  1 
crc_ccitt              12627  1 ppp_async
bnep                   17669  2 
rfcomm                 37420  16 
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_realtek    63791  1 
binfmt_misc            17260  1 
uvcvideo               71279  0 
qmi_wwan               12771  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
option                 29746  2 
cdc_wdm                17663  1 qmi_wwan
usb_wwan               14830  1 option
usbserial              27423  7 option,usb_wwan
usbnet                 26567  2 qmi_wwan,cdc_ether
arc4                   12543  2 
coretemp               13131  0 
rtl8723ae              81059  0 
rtlwifi                69015  1 rtl8723ae
snd_hda_intel          38307  3 
kvm_intel             126842  0 
mac80211              526519  1 rtlwifi
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
kvm                   376505  1 kvm_intel
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              436177  2 mac80211,rtlwifi
snd_rawmidi            25114  1 snd_seq_midi
joydev                 17097  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
aesni_intel            18156  0 
snd                    56485  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
aes_i586               16995  1 aesni_intel
soundcore              12600  1 snd
i915                  535507  2 
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
btusb                  17986  0 
cryptd                 15613  1 ablk_helper
drm_kms_helper         47545  1 i915
bluetooth             202069  22 bnep,btusb,rfcomm
drm                   228750  3 i915,drm_kms_helper
psmouse                81038  0 
toshiba_acpi           18270  0 
sparse_keymap          13658  1 toshiba_acpi
mac_hid                13037  0 
serio_raw              13031  0 
microcode              18286  0 
wmi                    18590  1 toshiba_acpi
toshiba_bluetooth      12748  0 
video                  18894  1 i915
i2c_algo_bit           13197  1 i915
lpc_ich                16925  0 
mei                    36197  0 
lp                     13299  0 
parport                40753  1 lp
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  0 
atl1c                  36175  0 
ahci                   25507  4 
libahci                26108  1 ahci
tos@tos:~$ 

```

---

### Post by praseodym on 2013-05-01
Please show also:

```
usb-devices
```
Is the package "usb-modeswitch" installed?

---

### Post by Sean Moran on 2013-05-01
> **praseodym said:**
> Please show also:

```
usb-devices
```
Is the package "usb-modeswitch" installed?

Thank you for your prompt reply, Praseodym.    Could it be possible that the driver/s I am after for 13.04 are hard to find on google because 13.04 already has them?  I admit I was searching and testing on 12.04 until Monday afternoon.  13.04 has the realtek internal wifi drivers that 12.04 doesn't.

Indeed, the usb-modeswitch is installed.  I should history back through the weekend's searches and try some new tricks with usb_modeswitch on 13.04.   Otherwise, what do you reckon I should type in the terminal to configure the usb stick with it?

**NOTE: Readout from USB-DEVICES listed below.**  
(it's just beyond my threshold of confusion)  

**USB_MODESWITCH:**
```

tos@tos:~$ usb_modeswitch
Usage: usb_modeswitch [<params>] [-c filename]
 -h, --help                    this help
 -v, --default-vendor NUM      vendor ID of original mode (mandatory)                                     [COLOR=#008000]((( 12d1 ??? )))[/COLOR]
 -p, --default-product NUM     product ID of original mode (mandatory)                                    [COLOR=#008000]((( 380b ??? )))[/COLOR]
 -V, --target-vendor NUM       target mode vendor ID (optional)
 -P, --target-product NUM      target mode product ID (optional)
 -C, --target-class NUM        target mode device class (optional)
 -b, --busnum NUM              system bus number of device (for hard ID)                                   [COLOR=#008000]((( 003 ??? )))[/COLOR]
 -g, --devnum NUM              system device number (for hard ID)                                            ((( 006 ??? )))
 -H, --huawei-mode             apply a special procedure                                                                 [COLOR=#008000]???[/COLOR]
 -W, --verbose                 print all settings and debug output                                                     [COLOR=#008000]Yes / ON[/COLOR]
 -c, --config-file <filename>  load long configuration from file                                                       [COLOR=#008000]???[/COLOR] 
 -i, --interface NUM           select initial USB interface (default 0)
 -u, --configuration NUM       select USB configuration
 -a, --altsetting NUM          select alternative USB interface setting
 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.2.3 (C) Josua Dietze 2012
 * Based on libusb0 (0.1.12 and above)
 ! PLEASE REPORT NEW CONFIGURATIONS !
tos@tos:~$ sudo usb_modeswitch -H
No default vendor/product ID given. Aborting.                                                              [COLOR=#ff8c00]((( Halfway There !!! )))[/COLOR]
tos@tos:~$ 

```


**USB-DEVICES:**  (note the error with the Huawei WIMAX 12d1-380d culprit halfway down the listing)
```

tos@tos:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-19-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b2f9 Rev=36.72
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=TOSHIBA Web Camera
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0930 ProdID=021d Rev=02.00
S:  Manufacturer=Realtek
S:  Product=RT Bluetooth Radio
S:  SerialNumber=00e04c000001
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-19-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-19-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

[COLOR=#ff0000]T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=380b Rev=00.01
S:  Manufacturer=HUAWEI Communications
S:  Product=HUAWEI WiMAX USB Stick
cat: serial: No such file or directory
S:  SerialNumber=
cat: bNumInterfaces: No such file or directory
cat: bConfigurationValue: No such file or directory
cat: bmAttributes: No such file or directory
cat: bMaxPower: No such file or directory
C:  #Ifs= 0 Cfg#= 0 Atr= MxPwr=
cat: /sys/bus/usb/devices/usb3/3-1/3-*:?.*/bInterfaceNumber: No such file or directory
cat: /sys/bus/usb/devices/usb3/3-1/3-*:?.*/bAlternateSetting: No such file or directory
cat: /sys/bus/usb/devices/usb3/3-1/3-*:?.*/bNumEndpoints: No such file or directory
cat: /sys/bus/usb/devices/usb3/3-1/3-*:?.*/bInterfaceClass: No such file or directory
cat: /sys/bus/usb/devices/usb3/3-1/3-*:?.*/bInterfaceSubClass: No such file or directory
cat: /sys/bus/usb/devices/usb3/3-1/3-*:?.*/bInterfaceProtocol: No such file or directory
/usr/bin/usb-devices: line 79: printf: (none): invalid number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=() Sub= Prot= Driver=

[/COLOR]T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  2 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03eb ProdID=0902 Rev=01.00
S:  Product=USB 2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=140c Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a81 ProdID=0101 Rev=01.10
S:  Manufacturer=CHESEN
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=03 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52f Rev=22.00
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.08
S:  Manufacturer=Linux 3.8.0-19-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
tos@tos:~$ 


```

---

### Post by praseodym on 2013-05-02
Is the package "modemmanager" installed?

---

### Post by bmork on 2013-05-02
> **Sean Moran said:**
> ```

[COLOR=#ff0000]T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=380b Rev=00.01
S:  Manufacturer=HUAWEI Communications
S:  Product=HUAWEI WiMAX USB Stick
cat: serial: No such file or directory
S:  SerialNumber=
cat: bNumInterfaces: No such file or directory
cat: bConfigurationValue: No such file or directory
cat: bmAttributes: No such file or directory
cat: bMaxPower: No such file or directory
C:  #Ifs= 0 Cfg#= 0 Atr= MxPwr=
[/COLOR]
```
Someone should really rewrite that script....

Anyway, the C: line is the only interesting one here.  Configuration #0 means that the USB core has failed to configure this device at all.  No need to look for drivers, mode switching or ModemManager yet.  You need to find out what happened when the kernel tried to set up this device.  dmesg output right after plugging it in might give some clues.

---

### Post by Sean Moran on 2013-05-02
Thanks again for your replies on this gnarly business.  I realise that the chances of anyone actually having succeeded in this endeavour with this exact Huawei BM-358 USB stick on 13.04 are slim, and greatly appreciate your expertise in helping me to learn how to find an original solution.

In reply, firstly modem-manager is installed.  Overall, I'm using a standard Lubuntu 13.04 with the additional 'apt-get install gnome', and most of the general user applications for both Lubuntu and the GNOME set, (eg. AbiWord and LibreOffice), removed to keep the .ISO down to CD size and reduce the build time until the main system and devices are all firing the way they should.

I will post the readouts for both 'modem-manager' and 'dpkg -l' below in code tags if that latter will help to determine what is actually installed in this morning's build. 

=============================================================================
=============================================================================
=============================================================================

Thanks again, Bmork.  We maybe getting to the core of this problem.
A readout for the 'dmesg' command is coded below.  The HUAWEI WIMAX part is down at the very bottom of the listing if that might help negotiation of such a large readout.

I have also persevered with the usb_modeswitch command, just to test my luck on complicated operations I know very little about, and have included the readout for:

usb_modeswitch -H -v 12d1 -p 380b -u 3 -b 3 -d 6

even though I don't really know what I am actually doing at this part.

I hope that somewhere in all these codings of readouts there is an answer or at least a hint on how to get this USB stick up and running, especially because I'm now down to 425Mb remaining on my quota for the other 3G mobile broadband stick, but that's not something to request support on the Ubuntu forums for. 
 
**MODEM-MANAGER:**
```

tos@tos:~$ modem-manager
modem-manager[2086]: <info>  ModemManager (version 0.6.0.0) starting...
modem-manager[2086]: <warn>  Could not acquire the org.freedesktop.ModemManager service.
  Message: 'Connection ":1.48" is not allowed to own the service "org.freedesktop.ModemManager" due to security policies in the configuration file'
tos@tos:~$ sudo modem-manager
[sudo] password for tos: 
modem-manager[2131]: <info>  ModemManager (version 0.6.0.0) starting...
modem-manager[2131]: <warn>  Could not acquire the org.freedesktop.ModemManager service as it is already taken. Return: 3
tos@tos:~$ 

```

**DMESG:**
```

tos@tos:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-19-generic (buildd@panlong) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 (Ubuntu 3.8.0-19.29-generic 3.8.8)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000091bff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000091c00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000aaabefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aaabf000-0x00000000aaebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aaebf000-0x00000000aafbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000aafbf000-0x00000000aaffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000aafff000-0x00000000aaffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ab000000-0x00000000af9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffd80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001cf5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: TOSHIBA Satellite U840W/Type2 - Board Product Name1, BIOS 1.10 07/06/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x1cf600 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0AB000000 mask FFF000000 uncachable
[    0.000000]   3 base 0AC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0B0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 1CF600000 mask FFFE00000 uncachable
[    0.000000]   8 base 1CF800000 mask FFF800000 uncachable
[    0.000000]   9 base 1D0000000 mask FF0000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [c00fe1b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c008d000] 8d000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x361e6000-0x370eafff]
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT aaffe210 000A4 (v01 TOSQCI TOSQCI00 00000001      01000013)
[    0.000000] ACPI: FACP aaffb000 0010C (v05 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT aafea000 0DBB1 (v01 TOSQCI TOSQCI00 00000000 ACPI 00040000)
[    0.000000] ACPI: FACS aafba000 00040
[    0.000000] ACPI: UEFI aaffd000 00236 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! aaffc000 000A5 (v32 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: HPET aaffa000 00038 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: APIC aaff9000 0008C (v03 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG aaff8000 0003C (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC aafe9000 00176 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: WDAT aafe8000 00224 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT aafe6000 01068 (v01 INSYDE CR CRB   00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT aafe4000 00028 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT aafdf000 00034 (v07 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: MSDM aafde000 00055 (v03 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT aafdc000 00044 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT aafdb000 008CD (v01 INSYDE CR CRB   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT aafda000 00A92 (v01 INSYDE CR CRB   00003000 ACPI 00040000)
[    0.000000] ACPI: DMAR aafd9000 000B8 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6522MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xcf5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00090fff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xaaabefff]
[    0.000000]   node   0: [mem 0xaafff000-0xaaffffff]
[    0.000000]   node   0: [mem 0x00000000-0xcf5fffff]
[    0.000000] On node 0 totalpages: 1547840
[    0.000000] free_area_init_node: node 0, pgdat c18f6100, node_mem_map f27f6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3937 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 221990 pages, LIFO batch:31
[    0.000000]   HighMem zone: 13045 pages used for memmap
[    0.000000]   HighMem zone: 1307084 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000091000 - 0000000000092000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] e820: [mem 0xafa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7b7a000 s35008 r0 d22336 u57344
[    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1533011
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=d0809264-03c7-4ea5-bf6e-9ce952d4edf2 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 15183744 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001cf600)
[    0.000000] Memory: 6089512k/7591936k available (6251k kernel code, 101848k reserved, 2973k data, 784k init, 5280516k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1903000 - 0xc19c7000   ( 784 kB)
[    0.000000]       .data : 0xc161ad30 - 0xc19023c0   (2973 kB)
[    0.000000]       .text : 0xc1000000 - 0xc161ad30   (6251 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1696.205 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3392.41 BogoMIPS (lpj=6784820)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000041] Security Framework initialized
[    0.000052] AppArmor: AppArmor initialized
[    0.000054] Yama: becoming mindful.
[    0.000107] Mount-cache hash table entries: 512
[    0.000330] Initializing cgroup subsys cpuacct
[    0.000332] Initializing cgroup subsys memory
[    0.000339] Initializing cgroup subsys devices
[    0.000341] Initializing cgroup subsys freezer
[    0.000343] Initializing cgroup subsys blkio
[    0.000345] Initializing cgroup subsys perf_event
[    0.000348] Initializing cgroup subsys hugetlb
[    0.000382] CPU: Physical Processor ID: 0
[    0.000384] CPU: Processor Core ID: 0
[    0.000390] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000390] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001494] mce: CPU supports 7 MCE banks
[    0.001509] CPU0: Thermal monitoring enabled (TM1)
[    0.001516] process: using mwait in idle threads
[    0.001524] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.001524] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.001524] tlb_flushall_shift: 1
[    0.001974] Freeing SMP alternatives: 24k freed
[    0.004887] ACPI: Core revision 20121018
[    0.004890] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.004993] ACPI: Forced DSDT copy: length 0x0DBB1 copied locally, original unmapped
[    0.031111] ftrace: allocating 26115 entries in 52 pages
[    1.092537] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    1.092973] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.132613] smpboot: CPU0: Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz (fam: 06, model: 3a, stepping: 09)
[    1.132622] TSC deadline timer enabled
[    1.132627] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.
[    1.132636] ... version:                3
[    1.132638] ... bit width:              48
[    1.132639] ... generic registers:      4
[    1.132641] ... value mask:             0000ffffffffffff
[    1.132643] ... max period:             000000007fffffff
[    1.132644] ... fixed-purpose events:   3
[    1.132646] ... event mask:             000000070000000f
[    1.133941] CPU 1 irqstacks, hard=f7524000 soft=f7526000
[    1.144220] Initializing CPU#1
[    1.148227] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    1.133944] smpboot: Booting Node   0, Processors  #1
[    1.148334] CPU 2 irqstacks, hard=f75fc000 soft=f75fe000
[    1.158688] Initializing CPU#2
[    1.148336]  #2
[    1.162660] CPU 3 irqstacks, hard=f7642000 soft=f7644000
[    1.173014] Initializing CPU#3
[    1.162663]  #3
[    2.069972] Brought up 4 CPUs
[    2.069976] smpboot: Total of 4 processors activated (13569.64 BogoMIPS)
[    2.074783] devtmpfs: initialized
[    2.074989] EVM: security.selinux
[    2.074991] EVM: security.SMACK64
[    2.074992] EVM: security.capability
[    2.075085] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)
[    2.076131] regulator-dummy: no parameters
[    2.076192] NET: Registered protocol family 16
[    2.076332] EISA bus registered
[    2.076442] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    2.076444] ACPI: bus type pci registered
[    2.076515] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    2.076519] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    2.076521] PCI: Using MMCONFIG for extended config space
[    2.076523] PCI: Using configuration type 1 for base access
[    2.077665] bio: create slab <bio-0> at 0
[    2.077785] ACPI: Added _OSI(Module Device)
[    2.077788] ACPI: Added _OSI(Processor Device)
[    2.077790] ACPI: Added _OSI(3.0 _SCP Extensions)
[    2.077793] ACPI: Added _OSI(Processor Aggregator Device)
[    2.080645] ACPI: EC: Look up EC in DSDT
[    2.083655] ACPI: Executed 1 blocks of module-level executable AML code
[    2.088574] ACPI: SSDT aabde018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    2.089315] ACPI: Dynamic OEM Table Load:
[    2.089318] ACPI: SSDT   (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    2.089645] ACPI: SSDT aabdfa98 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    2.090423] ACPI: Dynamic OEM Table Load:
[    2.090426] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    2.090578] ACPI: SSDT aabddd98 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    2.091308] ACPI: Dynamic OEM Table Load:
[    2.091311] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    2.092164] ACPI: Interpreter enabled
[    2.092178] ACPI: (supports S0 S3 S4 S5)
[    2.092203] ACPI: Using IOAPIC for interrupt routing
[    2.097905] ACPI: EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    2.098341] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    2.098351] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.098690] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    2.098693] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.098978] \_SB_.PCI0:_OSC invalid UUID
[    2.098979] _OSC request data:1 8 1f 
[    4.541827] PCI host bridge to bus 0000:00
[    4.541832] pci_bus 0000:00: root bus resource [bus 00-fe]
[    4.541835] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    4.541838] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    4.541841] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    4.541844] pci_bus 0000:00: root bus resource [mem 0xafa00000-0xfeafffff]
[    4.541855] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    4.541910] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    4.541926] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    4.541936] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    4.541943] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
[    4.542033] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    4.542073] pci 0000:00:14.0: reg 10: [mem 0xc0600000-0xc060ffff 64bit]
[    4.542206] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    4.542246] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    4.542287] pci 0000:00:16.0: reg 10: [mem 0xc0614000-0xc061400f 64bit]
[    4.542420] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    4.542482] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    4.542783] pci 0000:00:1a.0: reg 10: [mem 0xc0619000-0xc06193ff]
[    4.544505] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    4.544551] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    4.544582] pci 0000:00:1b.0: reg 10: [mem 0xc0610000-0xc0613fff 64bit]
[    4.544722] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    4.544765] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    4.544910] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    4.544957] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    4.545105] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    4.545156] pci 0000:00:1c.6: [8086:1e1c] type 01 class 0x060400
[    4.545305] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    4.545356] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    4.545656] pci 0000:00:1d.0: reg 10: [mem 0xc0618000-0xc06183ff]
[    4.547380] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    4.547419] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    4.547613] pci 0000:00:1f.2: [8086:282a] type 00 class 0x010400
[    4.547653] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
[    4.547667] pci 0000:00:1f.2: reg 14: [io  0x4094-0x4097]
[    4.547682] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
[    4.547699] pci 0000:00:1f.2: reg 1c: [io  0x4090-0x4093]
[    4.547716] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
[    4.547732] pci 0000:00:1f.2: reg 24: [mem 0xc0617000-0xc06177ff]
[    4.547834] pci 0000:00:1f.2: PME# supported from D3hot
[    4.547870] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    4.547901] pci 0000:00:1f.3: reg 10: [mem 0xc0615000-0xc06150ff 64bit]
[    4.547944] pci 0000:00:1f.3: reg 20: [io  0x4040-0x405f]
[    4.548077] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    4.548229] pci 0000:02:00.0: [10ec:8723] type 00 class 0x028000
[    4.548277] pci 0000:02:00.0: reg 10: [io  0x3000-0x30ff]
[    4.548331] pci 0000:02:00.0: reg 18: [mem 0xc0500000-0xc0503fff 64bit]
[    4.548586] pci 0000:02:00.0: supports D1 D2
[    4.548588] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    4.553250] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    4.553257] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    4.553263] pci 0000:00:1c.2:   bridge window [mem 0xc0500000-0xc05fffff]
[    4.553440] pci 0000:03:00.0: [1969:2062] type 00 class 0x020000
[    4.553546] pci 0000:03:00.0: reg 10: [mem 0xc0400000-0xc043ffff 64bit]
[    4.553600] pci 0000:03:00.0: reg 18: [io  0x2000-0x207f]
[    4.554111] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    4.561259] pci 0000:00:1c.6: PCI bridge to [bus 03]
[    4.561265] pci 0000:00:1c.6:   bridge window [io  0x2000-0x2fff]
[    4.561272] pci 0000:00:1c.6:   bridge window [mem 0xc0400000-0xc04fffff]
[    4.561307] pci_bus 0000:00: on NUMA node 0
[    4.561340] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    4.561384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    4.561428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    4.561547] \_SB_.PCI0:_OSC invalid UUID
[    4.561549] _OSC request data:1 1f 1f 
[    4.561554]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    4.561556]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    4.562311] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    4.562371] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    4.562423] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    4.562475] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    4.562527] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    4.562580] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    4.562631] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    4.562684] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    4.562802] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    4.562807] vgaarb: loaded
[    4.562809] vgaarb: bridge control possible 0000:00:02.0
[    4.563028] SCSI subsystem initialized
[    4.563031] ACPI: bus type scsi registered
[    4.563075] libata version 3.00 loaded.
[    4.563096] ACPI: bus type usb registered
[    4.563116] usbcore: registered new interface driver usbfs
[    4.563126] usbcore: registered new interface driver hub
[    4.563154] usbcore: registered new device driver usb
[    4.563256] PCI: Using ACPI for IRQ routing
[    4.571245] PCI: pci_cache_line_size set to 64 bytes
[    4.571338] e820: reserve RAM buffer [mem 0x00091c00-0x0009ffff]
[    4.571341] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    4.571343] e820: reserve RAM buffer [mem 0xaaabf000-0xabffffff]
[    4.571346] e820: reserve RAM buffer [mem 0xab000000-0xabffffff]
[    4.571348] e820: reserve RAM buffer [mem 0x1cf600000-0x1cfffffff]
[    4.571444] NetLabel: Initializing
[    4.571446] NetLabel:  domain hash size = 128
[    4.571447] NetLabel:  protocols = UNLABELED CIPSOv4
[    4.571458] NetLabel:  unlabeled traffic allowed by default
[    4.571564] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    4.571573] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    4.573586] Switching to clocksource hpet
[    4.581579] AppArmor: AppArmor Filesystem Enabled
[    4.581611] pnp: PnP ACPI init
[    4.581624] ACPI: bus type pnp registered
[    4.581661] pnp 00:00: [dma 4]
[    4.581685] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    4.581709] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    4.581814] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    4.581855] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    4.581903] system 00:04: [io  0x0680-0x069f] has been reserved
[    4.581906] system 00:04: [io  0x1100-0x110f] has been reserved
[    4.581909] system 00:04: [io  0xffff] has been reserved
[    4.581912] system 00:04: [io  0xffff] has been reserved
[    4.581915] system 00:04: [io  0x0400-0x0453] has been reserved
[    4.581918] system 00:04: [io  0x0458-0x047f] has been reserved
[    4.581921] system 00:04: [io  0x0500-0x057f] has been reserved
[    4.581924] system 00:04: [io  0x164e-0x164f] has been reserved
[    4.581928] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    4.581958] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    4.582012] system 00:06: [io  0x0454-0x0457] has been reserved
[    4.582016] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    4.582074] pnp 00:07: Plug and Play ACPI device, IDs TOS1102 PNP0303 (active)
[    4.582108] pnp 00:08: Plug and Play ACPI device, IDs TOS1100 PNP0f13 (active)
[    4.582251] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    4.582254] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    4.582257] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    4.582260] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    4.582264] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    4.582267] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    4.582270] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    4.582273] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    4.582276] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    4.582279] system 00:09: [mem 0xafa00000-0xafa00fff] has been reserved
[    4.582283] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    4.582609] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    4.582613] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    4.582616] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    4.582697] pnp: PnP ACPI: found 11 devices
[    4.582699] ACPI: ACPI bus type pnp unregistered
[    4.582702] PnPBIOS: Disabled by ACPI PNP
[    4.619183] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    4.619204] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    4.619209] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    4.619217] pci 0000:00:1c.2:   bridge window [mem 0xc0500000-0xc05fffff]
[    4.619231] pci 0000:00:1c.6: PCI bridge to [bus 03]
[    4.619236] pci 0000:00:1c.6:   bridge window [io  0x2000-0x2fff]
[    4.619244] pci 0000:00:1c.6:   bridge window [mem 0xc0400000-0xc04fffff]
[    4.619292] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    4.619295] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    4.619298] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    4.619300] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
[    4.619303] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    4.619306] pci_bus 0000:02: resource 1 [mem 0xc0500000-0xc05fffff]
[    4.619309] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    4.619311] pci_bus 0000:03: resource 1 [mem 0xc0400000-0xc04fffff]
[    4.619351] NET: Registered protocol family 2
[    4.619506] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    4.619526] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    4.619542] TCP: Hash tables configured (established 8192 bind 8192)
[    4.619557] TCP: reno registered
[    4.619561] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    4.619566] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    4.619622] NET: Registered protocol family 1
[    4.619635] pci 0000:00:02.0: Boot video device
[    4.649577] PCI: CLS 64 bytes, default 64
[    4.649623] Trying to unpack rootfs image as initramfs...
[    5.032382] Freeing initrd memory: 15380k freed
[    5.034792] dmar: Host address width 36
[    5.034795] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    5.034812] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    5.034814] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    5.034821] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    5.034824] dmar: RMRR base: 0x000000aae8f000 end: 0x000000aaeaefff
[    5.034826] dmar: RMRR base: 0x000000ab800000 end: 0x000000af9fffff
[    5.034907] Simple Boot Flag at 0x44 set to 0x1
[    5.035300] Initialise module verification
[    5.035351] audit: initializing netlink socket (disabled)
[    5.035367] type=2000 audit(1367547563.644:1): initialized
[    5.067619] bounce pool size: 64 pages
[    5.067637] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    5.069492] VFS: Disk quotas dquot_6.5.2
[    5.069545] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.070122] fuse init (API version 7.20)
[    5.070210] msgmni has been set to 1610
[    5.070723] Key type asymmetric registered
[    5.070727] Asymmetric key parser 'x509' registered
[    5.070773] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    5.070806] io scheduler noop registered
[    5.070808] io scheduler deadline registered (default)
[    5.070816] io scheduler cfq registered
[    5.071138] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    5.071154] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    5.071215] intel_idle: MWAIT substates: 0x21120
[    5.071217] intel_idle: v0.4 model 0x3A
[    5.071218] intel_idle: lapic_timer_reliable_states 0xffffffff
[    5.071369] ACPI: AC Adapter [ACAD] (on-line)
[    5.071508] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    5.071514] ACPI: Power Button [PWRB]
[    5.071553] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    5.071582] ACPI: Lid Switch [LID]
[    5.071625] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    5.071629] ACPI: Power Button [PWRF]
[    5.071728] ACPI: Requesting acpi_cpufreq
[    5.076164] GHES: HEST is not enabled!
[    5.076200] ACPI: Battery Slot [BAT1] (battery absent)
[    5.076230] isapnp: Scanning for PnP cards...
[    5.076267] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    5.078003] Linux agpgart interface v0.103
[    5.079506] brd: module loaded
[    5.080275] loop: module loaded
[    5.080642] libphy: Fixed MDIO Bus: probed
[    5.080711] tun: Universal TUN/TAP device driver, 1.6
[    5.080712] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.080757] PPP generic driver version 2.4.2
[    5.080800] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.080802] ehci-pci: EHCI PCI platform driver
[    5.080837] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    5.080842] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    5.080848] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    5.080867] ehci-pci 0000:00:1a.0: debug port 2
[    5.084760] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    5.084779] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc0619000
[    5.093006] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    5.093037] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    5.093041] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.093046] usb usb1: Product: EHCI Host Controller
[    5.093049] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    5.093051] usb usb1: SerialNumber: 0000:00:1a.0
[    5.093178] hub 1-0:1.0: USB hub found
[    5.093183] hub 1-0:1.0: 2 ports detected
[    5.093324] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    5.093329] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    5.093334] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    5.093352] ehci-pci 0000:00:1d.0: debug port 2
[    5.097257] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    5.097274] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc0618000
[    5.108986] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    5.109009] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    5.109013] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.109017] usb usb2: Product: EHCI Host Controller
[    5.109022] usb usb2: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    5.109025] usb usb2: SerialNumber: 0000:00:1d.0
[    5.109136] hub 2-0:1.0: USB hub found
[    5.109141] hub 2-0:1.0: 2 ports detected
[    5.109253] ehci-platform: EHCI generic platform driver
[    5.109261] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.109276] uhci_hcd: USB Universal Host Controller Interface driver
[    5.109323] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    5.109327] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    5.109332] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    5.109432] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    5.109505] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    5.109563] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    5.109566] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.109568] usb usb3: Product: xHCI Host Controller
[    5.109571] usb usb3: Manufacturer: Linux 3.8.0-19-generic xhci_hcd
[    5.109573] usb usb3: SerialNumber: 0000:00:14.0
[    5.109661] xHCI xhci_add_endpoint called for root hub
[    5.109663] xHCI xhci_check_bandwidth called for root hub
[    5.109687] hub 3-0:1.0: USB hub found
[    5.109695] hub 3-0:1.0: 4 ports detected
[    5.110027] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    5.110031] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    5.110055] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    5.110058] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.110060] usb usb4: Product: xHCI Host Controller
[    5.110063] usb usb4: Manufacturer: Linux 3.8.0-19-generic xhci_hcd
[    5.110065] usb usb4: SerialNumber: 0000:00:14.0
[    5.110149] xHCI xhci_add_endpoint called for root hub
[    5.110151] xHCI xhci_check_bandwidth called for root hub
[    5.110173] hub 4-0:1.0: USB hub found
[    5.110181] hub 4-0:1.0: 4 ports detected
[    5.404633] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    5.429967] isapnp: No Plug & Play device found
[    5.432701] i8042: PNP: PS/2 Controller [PNP0303:PS2E,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.435127] i8042: Detected active multiplexing controller, rev 1.1
[    5.436786] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.436796] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    5.436811] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    5.436815] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    5.436819] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    5.436989] mousedev: PS/2 mouse device common for all mice
[    5.437140] rtc_cmos 00:05: RTC can wake from S4
[    5.437268] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    5.437301] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    5.437403] device-mapper: uevent: version 1.0.3
[    5.437466] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    5.437483] EISA: Probing bus 0 at eisa.0
[    5.437485] EISA: Cannot allocate resource for mainboard
[    5.437487] Cannot allocate resource for EISA slot 1
[    5.437489] Cannot allocate resource for EISA slot 2
[    5.437490] Cannot allocate resource for EISA slot 3
[    5.437492] Cannot allocate resource for EISA slot 4
[    5.437494] Cannot allocate resource for EISA slot 5
[    5.437495] Cannot allocate resource for EISA slot 6
[    5.437497] Cannot allocate resource for EISA slot 7
[    5.437498] Cannot allocate resource for EISA slot 8
[    5.437500] EISA: Detected 0 cards.
[    5.437508] cpufreq-nforce2: No nForce2 chipset.
[    5.437595] cpuidle: using governor ladder
[    5.437717] cpuidle: using governor menu
[    5.437722] ledtrig-cpu: registered to indicate activity on CPUs
[    5.437724] EFI Variables Facility v0.08 2004-May-17
[    5.437921] ashmem: initialized
[    5.438067] TCP: cubic registered
[    5.438183] NET: Registered protocol family 10
[    5.438390] NET: Registered protocol family 17
[    5.438401] Key type dns_resolver registered
[    5.438605] Using IPI No-Shortcut mode
[    5.438704] Loading module verification certificates
[    5.443829] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: fceb9fd088cf158e29d83343e1c98bf8ab23d94a'
[    5.443840] registered taskstats version 1
[    5.447083] Key type trusted registered
[    5.449821] Key type encrypted registered
[    5.451443] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.453183] rtc_cmos 00:05: setting system clock to 2013-05-03 02:19:28 UTC (1367547568)
[    5.453998] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.453999] EDD information not available.
[    5.454122] Freeing unused kernel memory: 784k freed
[    5.454248] Write protecting the kernel text: 6252k
[    5.454293] Write protecting the kernel read-only data: 2432k
[    5.454294] NX-protecting the kernel data: 3988k
[    5.466082] udevd[108]: starting version 175
[    5.491011] Disabling lock debugging due to kernel taint
[    5.494920] ahci 0000:00:1f.2: version 3.0
[    5.494979] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    5.495009] ahci: SSS flag set, parallel bus scan disabled
[    5.508534] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x2f impl RAID mode
[    5.508540] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    5.508547] ahci 0000:00:1f.2: setting latency timer to 64
[    5.522324] atl1c 0000:03:00.0: version 1.0.1.1-NAPI
[    5.536916] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    5.536927] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.537223] hub 1-1:1.0: USB hub found
[    5.537273] hub 1-1:1.0: 6 ports detected
[    5.540875] scsi0 : ahci
[    5.540962] scsi1 : ahci
[    5.541025] scsi2 : ahci
[    5.541107] scsi3 : ahci
[    5.541188] scsi4 : ahci
[    5.541265] scsi5 : ahci
[    5.541297] ata1: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617100 irq 41
[    5.541300] ata2: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617180 irq 41
[    5.541302] ata3: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617200 irq 41
[    5.541305] ata4: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617280 irq 41
[    5.541307] ata5: DUMMY
[    5.541310] ata6: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617380 irq 41
[    5.648429] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    5.780942] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    5.780959] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.781318] hub 2-1:1.0: USB hub found
[    5.781508] hub 2-1:1.0: 8 ports detected
[    5.860169] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.861303] ata1.00: ATA-8: Hitachi HTS545050A7E380, GG2OA7A0, max UDMA/133
[    5.861323] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.862587] ata1.00: configured for UDMA/133
[    5.862833] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 GG2O PQ: 0 ANSI: 5
[    5.863030] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.863035] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    5.863067] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.863131] sd 0:0:0:0: [sda] Write Protect is off
[    5.863137] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.863188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.948076] usb 3-2: new full-speed USB device number 2 using xhci_hcd
[    5.965007] usb 3-2: New USB device found, idVendor=03eb, idProduct=0902
[    5.965011] usb 3-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    5.965013] usb 3-2: Product: USB 2.0 Hub
[    5.965236] usb 3-2: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    5.965415] hub 3-2:1.0: USB hub found
[    5.965521] hub 3-2:1.0: 4 ports detected
[    6.027577]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 sda10 > sda4
[    6.028286] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.031958] tsc: Refined TSC clocksource calibration: 1696.146 MHz
[    6.031965] Switching to clocksource tsc
[    6.036126] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    6.179796] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    6.180535] ata2.00: ATA-9: SAMSUNG MZMPC032HBCD-00000, CXM1201Q, max UDMA/133
[    6.180551] ata2.00: 62533296 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    6.181026] ata2.00: configured for UDMA/133
[    6.181253] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG MZMPC032 CXM1 PQ: 0 ANSI: 5
[    6.181455] sd 1:0:0:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    6.181467] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    6.181611] sd 1:0:0:0: [sdb] Write Protect is off
[    6.181617] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.181657] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.182937]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 > sdb4
[    6.183390] sd 1:0:0:0: [sdb] Attached SCSI disk
[    6.186782] usb 1-1.4: New USB device found, idVendor=04f2, idProduct=b2f9
[    6.186790] usb 1-1.4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    6.186796] usb 1-1.4: Product: TOSHIBA Web Camera
[    6.186801] usb 1-1.4: Manufacturer: Chicony Electronics Co.,Ltd.
[    6.186814] usb 1-1.4: SerialNumber: 0x0001
[    6.259857] usb 1-1.6: new full-speed USB device number 4 using ehci-pci
[    6.354483] usb 1-1.6: New USB device found, idVendor=0930, idProduct=021d
[    6.354495] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    6.354502] usb 1-1.6: Product: RT Bluetooth Radio
[    6.354507] usb 1-1.6: Manufacturer: Realtek
[    6.354512] usb 1-1.6: SerialNumber: 00e04c000001
[    6.427605] usb 3-2.3: new low-speed USB device number 3 using xhci_hcd
[    6.452673] usb 3-2.3: New USB device found, idVendor=0a81, idProduct=0101
[    6.452677] usb 3-2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.452679] usb 3-2.3: Product: USB Keyboard
[    6.452681] usb 3-2.3: Manufacturer: CHESEN
[    6.452889] usb 3-2.3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    6.452896] usb 3-2.3: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    6.465091] usbcore: registered new interface driver usbhid
[    6.465095] usbhid: USB HID core driver
[    6.467152] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input4
[    6.467226] hid-generic 0003:0A81:0101.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:14.0-2.3/input0
[    6.468467] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.3/3-2.3:1.1/input/input5
[    6.468554] hid-generic 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:14.0-2.3/input1
[    6.499407] ata3: SATA link down (SStatus 0 SControl 300)
[    6.523444] usb 3-2.4: new full-speed USB device number 4 using xhci_hcd
[    6.542234] usb 3-2.4: New USB device found, idVendor=046d, idProduct=c52f
[    6.542238] usb 3-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.542240] usb 3-2.4: Product: USB Receiver
[    6.542242] usb 3-2.4: Manufacturer: Logitech
[    6.544122] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.4/3-2.4:1.0/input/input6
[    6.544403] hid-generic 0003:046D:C52F.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-2.4/input0
[    6.546210] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.4/3-2.4:1.1/input/input7
[    6.546503] hid-generic 0003:046D:C52F.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-2.4/input1
[    6.819028] ata4: SATA link down (SStatus 0 SControl 300)
[    7.138626] ata6: SATA link down (SStatus 0 SControl 300)
[    8.873658] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   10.237647] Adding 12001276k swap on /dev/sda4.  Priority:-1 extents:1 across:12001276k 
[   10.835819] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.882856] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   10.911477] udevd[408]: starting version 175
[   11.618230] lp: driver loaded but no devices found
[   11.957198] mei 0000:00:16.0: setting latency timer to 64
[   11.957258] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[   11.971854] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   11.971861] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.971864] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   11.971867] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.971869] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   11.971872] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.971873] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.975510] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   11.975559] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   11.976093] wmi: Mapper loaded
[   11.995250] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[   11.995330] input: Toshiba input device as /devices/virtual/input/input8
[   12.020076] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[   12.033281] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[   12.034448] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[   12.035746] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[   12.038135] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.083757] [drm] Initialized drm 1.1.0 20060810
[   12.144064] Bluetooth: Core ver 2.16
[   12.144080] NET: Registered protocol family 31
[   12.144082] Bluetooth: HCI device and connection manager initialized
[   12.144090] Bluetooth: HCI socket layer initialized
[   12.144093] Bluetooth: L2CAP socket layer initialized
[   12.144100] Bluetooth: SCO socket layer initialized
[   12.335495] usbcore: registered new interface driver btusb
[   12.441073] [drm] Memory usable by graphics device = 2048M
[   12.441083] i915 0000:00:02.0: setting latency timer to 64
[   12.441486] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   12.441497] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.441499] [drm] Driver supports precise vblank timestamp query.
[   12.441589] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.480689] psmouse serio2: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x122c00, board id: 1744, fw id: 1122530
[   12.480697] psmouse serio2: synaptics: Toshiba Satellite U840W detected, limiting rate to 40pps.
[   12.513701] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   12.552126] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   12.604519] fbcon: inteldrmfb (fb0) is primary device
[   12.655261] type=1400 audit(1367547575.708:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=696 comm="apparmor_parser"
[   12.655270] type=1400 audit(1367547575.708:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=656 comm="apparmor_parser"
[   12.655690] type=1400 audit(1367547575.708:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=696 comm="apparmor_parser"
[   12.655696] type=1400 audit(1367547575.708:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=656 comm="apparmor_parser"
[   12.655916] type=1400 audit(1367547575.708:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=696 comm="apparmor_parser"
[   12.655923] type=1400 audit(1367547575.708:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=656 comm="apparmor_parser"
[   12.791504] init: avahi-cups-reload main process (733) terminated with status 1
[   12.796728] Linux video capture interface: v2.00
[   12.833771] type=1400 audit(1367547575.884:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=721 comm="apparmor_parser"
[   12.833781] type=1400 audit(1367547575.884:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=722 comm="apparmor_parser"
[   12.877731] cfg80211: Calling CRDA to update world regulatory domain
[   12.880128] Bluetooth: RFCOMM TTY layer initialized
[   12.880137] Bluetooth: RFCOMM socket layer initialized
[   12.880138] Bluetooth: RFCOMM ver 1.11
[   12.903927] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera (04f2:b2f9)
[   12.910377] input: TOSHIBA Web Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input10
[   12.910459] usbcore: registered new interface driver uvcvideo
[   12.910459] USB Video Class driver (1.1.1)
[   12.915596] ppdev: user-space parallel port driver
[   13.034092] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.034093] Bluetooth: BNEP filters: protocol multicast
[   13.034098] Bluetooth: BNEP socket layer initialized
[   13.070068] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   13.117953] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.118179] rtlwifi: wireless switch is on
[   13.382835] cfg80211: World regulatory domain updated:
[   13.382835] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.382837] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.382838] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.382839] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.382840] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.382840] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.382849] cfg80211: Calling CRDA for country: EC
[   13.386162] cfg80211: Regulatory domain changed to country: EC
[   13.386163] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.386164] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.386165] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   13.386166] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   13.386166] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   14.162508] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   14.409726] Console: switching to colour frame buffer device 224x48
[   14.413621] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   14.413623] i915 0000:00:02.0: registered panic notifier
[   14.434646] acpi device:41: registered as cooling_device4
[   14.434835] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.435504] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input11
[   14.435655] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.435769] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   14.462151] init: failsafe main process (754) killed by TERM signal
[   14.475489] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.475594] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   14.475671] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   14.524214] sed[830]: segfault at b77c0002 ip b77c0002 sp 00000008 error 14
[   14.524623] init: mountall-net main process (753) terminated with status 139
[   14.687244] type=1400 audit(1367547577.740:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=853 comm="apparmor_parser"
[   17.458896] init: alsa-restore main process (1037) terminated with status 99
[   17.475610] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.478527] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.493113] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[   17.508168] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.514255] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.550977] init: gdm main process (1080) killed by TERM signal
[  776.194244] usb 3-4: new high-speed USB device number 5 using xhci_hcd
[  776.210720] usb 3-4: config 1 interface 0 altsetting 0 bulk endpoint 0x81 has invalid maxpacket 64
[  776.210731] usb 3-4: config 1 interface 0 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64
[  776.211080] usb 3-4: New USB device found, idVendor=12d1, idProduct=380b
[  776.211090] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  776.211097] usb 3-4: Product: HUAWEI WiMAX USB Stick
[  776.211102] usb 3-4: Manufacturer: HUAWEI Communications
[  776.211107] usb 3-4: SerialNumber: 08FF0004
[  776.259942] Initializing USB Mass Storage driver...
[  776.260100] scsi6 : usb-storage 3-4:1.0
[  776.260177] usbcore: registered new interface driver usb-storage
[  776.260179] USB Mass Storage support registered.
[  777.257799] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     1.00 PQ: 0 ANSI: 2
[  777.259723] sr0: scsi3-mmc drive: 0x/0x caddy
[  777.259738] cdrom: Uniform CD-ROM driver Revision: 3.20
[  777.259917] sr 6:0:0:0: Attached scsi CD-ROM sr0
[  777.260004] sr 6:0:0:0: Attached scsi generic sg2 type 5
tos@tos:~$

```

**DPKG -L:**
```

tos@tos:~$ dpkg -l
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  accountsservic 0.6.29-1ubun i386         query and manipulate user account
ii  acl            2.2.51-8ubun i386         Access control list utilities
ii  adduser        3.113+nmu3ub all          add and remove users and groups
ii  alacarte       3.6.1-0ubunt all          easy GNOME menu editing tool
ii  alsa-base      1.0.25+dfsg- all          ALSA driver configuration files
ii  alsa-utils     1.0.25-4ubun i386         Utilities for configuring and usi
ii  anacron        2.3-19ubuntu i386         cron-like program that doesn't go
ii  apg            2.2.3.dfsg.1 i386         Automated Password Generator - St
ii  app-install-da 13.04.3      all          Ubuntu applications (data files)
ii  apparmor       2.8.0-0ubunt i386         User-space parser utility for App
ii  appmenu-gtk:i3 12.10.3daily i386         Export GTK menus over DBus
ii  appmenu-gtk3:i 12.10.3daily i386         Export GTK menus over DBus
ii  appmenu-qt     0.2.7daily13 i386         application menu for Qt
ii  appmenu-qt5    0.2.7daily13 i386         application menu for Qt5
ii  apport         2.9.2-0ubunt all          automatically generate crash repo
ii  apport-gtk     2.9.2-0ubunt all          GTK+ frontend for the apport cras
ii  apt            0.9.7.7ubunt i386         commandline package manager
ii  apt-transport- 0.9.7.7ubunt i386         https download transport for APT
ii  apt-utils      0.9.7.7ubunt i386         package managment related utility
ii  apt-xapian-ind 0.45ubuntu2  all          maintenance and search tools for 
ii  aptdaemon      1.0-0ubuntu9 all          transaction based package managem
ii  aptdaemon-data 1.0-0ubuntu9 all          data files for clients
ii  apturl         0.5.2ubuntu1 i386         install packages using the apt pr
ii  apturl-common  0.5.2ubuntu1 i386         install packages using the apt pr
rc  argyll         1.4.0-8ubunt i386         Color Management System, calibrat
ii  aspell         0.60.7~20110 i386         GNU Aspell spell-checker
ii  aspell-en      7.1-0-1      all          English dictionary for GNU Aspell
ii  at-spi2-core   2.8.0-1      i386         Assistive Technology Service Prov
ii  avahi-daemon   0.6.31-1ubun i386         Avahi mDNS/DNS-SD daemon
ii  bamfdaemon     0.4.0daily13 i386         Window matching library - daemon
rc  baobab         3.6.4-0ubunt i386         GNOME disk usage analyzer
ii  base-files     6.12ubuntu2  i386         Debian base system miscellaneous 
ii  base-passwd    3.5.26       i386         Debian base system master passwor
ii  bash           4.2-5ubuntu3 i386         GNU Bourne Again SHell
ii  bash-completio 1:2.0-1ubunt all          programmable completion for the b
ii  bc             1.06.95-4ubu i386         GNU bc arbitrary precision calcul
ii  bind9-host     1:9.9.2.dfsg i386         Version of 'host' bundled with BI
ii  binfmt-support 2.0.13       i386         Support for extra binary formats
ii  binutils       2.23.2-2ubun i386         GNU assembler, linker and binary 
ii  bison          2:2.5.dfsg-3 i386         YACC-compatible parser generator
ii  blueman        1.23-0ubuntu i386         A Graphical bluetooth manager
ii  bluez          4.101-0ubunt i386         Bluetooth tools and daemons
ii  bsdmainutils   9.0.4ubuntu3 i386         collection of more utilities from
ii  bsdutils       1:2.20.1-5.1 i386         Basic utilities from 4.4BSD-Lite
ii  build-essentia 11.6ubuntu4  i386         Informational list of build-essen
ii  busybox-initra 1:1.20.0-8ub i386         Standalone shell setup for initra
ii  busybox-static 1:1.20.0-8ub i386         Standalone rescue shell with tons
ii  bzip2          1.0.6-4      i386         high-quality block-sorting file c
ii  ca-certificate 20130119     all          Common CA certificates
rc  ca-certificate 20121112+nmu all          Common CA certificates (JKS keyst
ii  colord         0.1.30-0ubun i386         system service to manage device c
ii  command-not-fo 0.3ubuntu7   all          Suggest installation of packages 
ii  command-not-fo 0.3ubuntu7   i386         Set of data files for command-not
ii  compiz         1:0.9.9~dail all          OpenGL window and compositing man
ii  compiz-core    1:0.9.9~dail i386         OpenGL window and compositing man
ii  compiz-gnome   1:0.9.9~dail i386         OpenGL window and compositing man
ii  compiz-plugins 1:0.9.9~dail i386         OpenGL window and compositing man
ii  console-setup  1.70ubuntu7  all          console font and keymap setup pro
ii  consolekit     0.4.5-3.1ubu i386         framework for defining and tracki
ii  coreutils      8.20-3ubuntu i386         GNU core utilities
ii  cpio           2.11+dfsg-0. i386         GNU cpio -- a program to manage a
ii  cpp            4:4.7.3-1ubu i386         GNU C preprocessor (cpp)
ii  cpp-4.7        4.7.3-1ubunt i386         GNU C preprocessor
ii  crda           1.1.2-1ubunt i386         wireless Central Regulatory Domai
ii  cron           3.0pl1-124ub i386         process scheduling daemon
ii  cups           1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  cups-client    1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  cups-common    1.6.2-1ubunt all          Common UNIX Printing System(tm) -
ii  cups-daemon    1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  cups-driver-gu 5.2.9-1ubunt all          transitional dummy package for gu
ii  cups-filters   1.0.34-0ubun i386         OpenPrinting CUPS Filters
ii  cups-pk-helper 0.2.4-0ubunt i386         PolicyKit helper to configure cup
ii  cups-ppdc      1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  dash           0.5.7-3ubunt i386         POSIX-compliant shell
ii  dbus           1.6.8-1ubunt i386         simple interprocess messaging sys
ii  dbus-x11       1.6.8-1ubunt i386         simple interprocess messaging sys
ii  dconf-gsetting 0.16.0-0ubun i386         simple configuration storage syst
ii  dconf-service  0.16.0-0ubun i386         simple configuration storage syst
ii  dconf-tools    0.16.0-0ubun i386         simple configuration storage syst
ii  debconf        1.5.49ubuntu all          Debian configuration management s
ii  debconf-i18n   1.5.49ubuntu all          full internationalization support
ii  debianutils    4.3.4        i386         Miscellaneous utilities specific 
ii  desktop-base   7.0.3ubuntu1 all          common files for the Debian Deskt
ii  desktop-file-u 0.21-0ubuntu i386         Utilities for .desktop files
ii  dictionaries-c 1.12.11      all          Common utilities for spelling dic
ii  diffutils      1:3.2-8      i386         File comparison utilities
ii  dmidecode      2.11+2012032 i386         SMBIOS/DMI table decoder
ii  dmsetup        2:1.02.74-6u i386         Linux Kernel Device Mapper usersp
ii  dmz-cursor-the 0.4.3        all          Style neutral, scalable cursor th
ii  dnsmasq-base   2.65-1ubuntu i386         Small caching DNS proxy and DHCP/
ii  dnsutils       1:9.9.2.dfsg i386         Clients provided with BIND
ii  dosfstools     3.0.14-1ubun i386         utilities for making and checking
ii  dpkg           1.16.10ubunt i386         Debian package management system
ii  dpkg-dev       1.16.10ubunt all          Debian package development tools
ii  e2fslibs:i386  1.42.5-1ubun i386         ext2/ext3/ext4 file system librar
ii  e2fsprogs      1.42.5-1ubun i386         ext2/ext3/ext4 file system utilit
ii  ed             1.6-2ubuntu1 i386         classic UNIX line editor
ii  eject          2.1.5+deb1+c i386         ejects CDs and operates CD-Change
ii  elementary-ico 2.7.1-0ubunt all          simple and appealing Tango-styled
ii  evolution-data 3.6.4-0ubunt i386         evolution database backend server
ii  evolution-data 3.6.4-0ubunt all          architecture independent files fo
ii  fakeroot       1.18.4-2ubun i386         tool for simulating superuser pri
ii  ffmpegthumbnai 2.0.8-0ubunt i386         fast and lightweight video thumbn
ii  file           5.11-2ubuntu i386         Determines file type using "magic
ii  file-roller    3.6.3-1ubunt i386         archive manager for GNOME
ii  findutils      4.4.2-5ubunt i386         utilities for finding files--find
ii  firefox        20.0+build1- i386         Safe and easy web browser from Mo
ii  firefox-global 20.0+build1- i386         Safe and easy web browser from Mo
ii  firefox-locale 20.0+build1- i386         English language pack for Firefox
ii  fontconfig     2.10.2-0ubun i386         generic font configuration librar
ii  fontconfig-con 2.10.2-0ubun all          generic font configuration librar
rc  fonts-cantarel 0.0.11-0ubun all          sans serif font family designed f
ii  fonts-freefont 20120503-1   all          Freefont Serif, Sans and Mono Tru
ii  fonts-liberati 1.07.2-6ubun all          Fonts with the same metrics as Ti
ii  fonts-nanum    3.020-2      all          Nanum Korean fonts
ii  foomatic-db-co 20130308-0ub all          OpenPrinting printer support - Co
ii  foomatic-filte 4.0.17-1ubun i386         OpenPrinting printer support - fi
rc  four-in-a-row  1:3.8.0-0ubu i386         four-in-a-row game for GNOME
rc  freepats       20060219-1   all          Free patch set for MIDI audio syn
ii  friendly-recov 0.2.25       all          Make recovery more user-friendly
ii  ftp            0.17-28      i386         classical file transfer client
ii  fuse           2.9.0-1ubunt i386         Filesystem in Userspace
ii  g++            4:4.7.3-1ubu i386         GNU C++ compiler
ii  g++-4.7        4.7.3-1ubunt i386         GNU C++ compiler
ii  galculator     2.1-2        i386         scientific calculator
ii  gawk           1:4.0.1+dfsg i386         GNU awk, a pattern scanning and p
ii  gcc            4:4.7.3-1ubu i386         GNU C compiler
ii  gcc-4.7        4.7.3-1ubunt i386         GNU C compiler
ii  gcc-4.7-base:i 4.7.3-1ubunt i386         GCC, the GNU Compiler Collection 
ii  gconf-service  3.2.6-0ubunt i386         GNOME configuration database syst
ii  gconf-service- 3.2.6-0ubunt i386         GNOME configuration database syst
ii  gconf2         3.2.6-0ubunt i386         GNOME configuration database syst
ii  gconf2-common  3.2.6-0ubunt all          GNOME configuration database syst
ii  gcr            3.6.2-0ubunt i386         GNOME crypto services (daemon and
ii  gdebi          0.9~exp2     all          simple tool to install deb files 
ii  gdebi-core     0.9~exp2     all          simple tool to install deb files
rc  gdm            3.6.1-0ubunt i386         Next generation GNOME Display Man
ii  genisoimage    9:1.1.11-2ub i386         Creates ISO-9660 CD-ROM filesyste
ii  geoclue        0.12.99-0ubu i386         Geographic information framework
ii  geoclue-ubuntu 1.0.1-0ubunt i386         Provide positioning for GeoClue v
ii  geoip-database 20130213-1   all          IP lookup command line tools that
ii  gettext-base   0.18.1.1-10u i386         GNU Internationalization utilitie
ii  ghostscript    9.07~dfsg2-0 i386         interpreter for the PostScript la
ii  ghostscript-cu 9.07~dfsg2-0 i386         interpreter for the PostScript la
ii  ghostscript-x  9.07~dfsg2-0 i386         interpreter for the PostScript la
ii  giblib1:i386   1.2.4-8      i386         wrapper library for imlib2, and o
ii  gir1.2-atk-1.0 2.8.0-1      i386         ATK accessibility toolkit (GObjec
ii  gir1.2-freedes 1.36.0-1     i386         Introspection data for some FreeD
ii  gir1.2-gconf-2 3.2.6-0ubunt i386         GNOME configuration database syst
ii  gir1.2-gdkpixb 2.28.0-0ubun i386         GDK Pixbuf library - GObject-Intr
ii  gir1.2-glib-2. 1.36.0-1     i386         Introspection data for GLib, GObj
ii  gir1.2-gmenu-3 3.6.2-0ubunt i386         GObject introspection data for th
ii  gir1.2-gnomebl 3.6.1-0ubunt i386         Introspection data for GnomeBluet
ii  gir1.2-gtk-3.0 3.6.4-0ubunt i386         GTK+ graphical user interface lib
ii  gir1.2-javascr 1.10.2-0ubun i386         GObject introspection data for th
ii  gir1.2-notify- 0.7.5-2      i386         sends desktop notifications to a 
ii  gir1.2-package 0.7.6-3ubunt i386         GObject introspection data for th
ii  gir1.2-panelap 1:3.6.2-0ubu i386         GObject introspection for the GNO
ii  gir1.2-pango-1 1.32.5-0ubun i386         Layout and rendering of internati
ii  gir1.2-soup-2. 2.40.3-0ubun i386         GObject introspection data for th
ii  gir1.2-vte-2.9 1:0.34.2-0ub i386         GObject introspection data for th
ii  gir1.2-webkit- 1.10.2-0ubun i386         GObject introspection data for th
ii  gir1.2-wnck-3. 3.4.5-0ubunt i386         GObject introspection data for th
ii  gkbd-capplet   3.6.0-0ubunt i386         GNOME Panel applet for libgnomekb
ii  gksu           2.0.2-6ubunt i386         graphical frontend to su
ii  glib-networkin 2.36.1-0ubun i386         network-related giomodules for GL
ii  glib-networkin 2.36.1-0ubun all          network-related giomodules for GL
ii  glib-networkin 2.36.1-0ubun i386         network-related giomodules for GL
ii  gnome-accessib 3.6.5-0ubunt all          Accessibility themes for the GNOM
ii  gnome-applets  3.5.92-0ubun i386         Various applets for the GNOME pan
ii  gnome-applets- 3.5.92-0ubun all          Various applets for the GNOME pan
ii  gnome-bluetoot 3.6.1-0ubunt i386         GNOME Bluetooth tools
ii  gnome-control- 1:3.6.3-0ubu i386         utilities to configure the GNOME 
ii  gnome-control- 1:3.6.3-0ubu all          configuration applets for GNOME -
ii  gnome-control- 1.2daily13.0 i386         change the settings of the Unity 
ii  gnome-desktop3 3.6.3-0ubunt all          Common files for GNOME desktop ap
ii  gnome-disk-uti 3.6.1-1ubunt i386         manage and configure disk drives 
ii  gnome-icon-the 3.6.2-0ubunt all          GNOME Desktop icon theme (small s
ii  gnome-icon-the 3.6.2-0ubunt all          GNOME Desktop icon theme
ii  gnome-icon-the 3.6.2-0ubunt all          GNOME desktop icon theme (symboli
ii  gnome-keyring  3.6.3-0ubunt i386         GNOME keyring services (daemon an
ii  gnome-menus    3.6.2-0ubunt i386         GNOME implementation of the freed
rc  gnome-nettool  3.2.0-1      i386         network information tool for GNOM
pc  gnome-nibbles  1:3.8.0-0ubu i386         snake game, up to four players
ii  gnome-panel    1:3.6.2-0ubu i386         launcher and docking facility for
ii  gnome-panel-da 1:3.6.2-0ubu all          common files for the GNOME Panel
ii  gnome-power-ma 3.6.0-1ubunt i386         power management tool for the GNO
pc  gnome-robots   1:3.8.0-0ubu i386         improved old BSD robots game
ii  gnome-screensa 3.6.1-0ubunt i386         GNOME screen saver and locker
ii  gnome-session  3.6.2-0ubunt all          GNOME Session Manager - GNOME 3 s
ii  gnome-session- 3.6.2-0ubunt i386         GNOME Session Manager - Minimal r
ii  gnome-session- 3.6.2-0ubunt all          GNOME Session Manager - common fi
ii  gnome-session- 3.6.2-0ubunt all          GNOME Session Manager - GNOME fal
ii  gnome-settings 3.6.4-0ubunt i386         daemon handling the GNOME session
rc  gnome-sudoku   1:3.8.1-0ubu all          Sudoku puzzle game for GNOME
ii  gnome-system-m 3.8.0-0ubunt i386         Process viewer and system resourc
ii  gnome-system-t 3.0.0-2ubunt i386         Cross-platform configuration util
ii  gnome-themes-s 3.6.5-0ubunt i386         Standard GNOME themes
ii  gnome-themes-s 3.6.5-0ubunt all          Data files for GNOME standard the
ii  gnome-time-adm 3.0.0-2ubunt i386         GNOME Time Administration Tool
ii  gnome-user-sha 3.0.4-0ubunt i386         User level public file sharing vi
ii  gnupg          1.4.12-7ubun i386         GNU privacy guard - a free PGP re
ii  gpgv           1.4.12-7ubun i386         GNU privacy guard - signature ver
ii  grep           2.14-1       i386         GNU grep, egrep and fgrep
ii  groff-base     1.22.1-3     i386         GNU troff text-formatting system 
ii  grub-common    2.00-13ubunt i386         GRand Unified Bootloader (common 
ii  grub-gfxpayloa 0.6          i386         GRUB gfxpayload blacklist
ii  grub-pc        2.00-13ubunt i386         GRand Unified Bootloader, version
ii  grub-pc-bin    2.00-13ubunt i386         GRand Unified Bootloader, version
ii  grub2-common   2.00-13ubunt i386         GRand Unified Bootloader (common 
ii  gsettings-desk 3.6.1-0ubunt all          GSettings deskop-wide schemas
ii  gsfonts        1:8.11+urwcy all          Fonts for the Ghostscript interpr
ii  gstreamer0.10- 0.1.3-1      i386         ICE library (GStreamer plugin)
ii  gstreamer0.10- 0.10.36-1.1u i386         GStreamer plugins from the "base"
ii  gstreamer0.10- 0.10.31-3+nm i386         GStreamer plugins from the "good"
ii  gstreamer0.10- 0.10.31-3+nm i386         GStreamer plugin for PulseAudio
ii  gstreamer1.0-p 1.0.6-1ubunt i386         GStreamer plugins from the "bad" 
ii  gstreamer1.0-p 1.0.6-1      i386         GStreamer plugins from the "base"
ii  gstreamer1.0-p 1.0.6-1ubunt i386         GStreamer plugins from the "good"
ii  gstreamer1.0-x 1.0.6-1      i386         GStreamer plugins for X11 and Pan
ii  gtk2-engines:i 1:2.20.2-2ub i386         theme engines for GTK+ 2.x
ii  gtk2-engines-p 2.24.17-0ubu i386         pixbuf-based theme for GTK+ 2.x
ii  gtk3-engines-u 1.0.3daily12 i386         Unico Gtk+ 3 theme engine
ii  gucharmap      1:3.6.1-0ubu i386         Unicode character picker and font
rc  guile-2.0-libs 2.0.7-0ubunt i386         Core Guile libraries
ii  gvfs:i386      1.16.1-0ubun i386         userspace virtual filesystem - GI
ii  gvfs-backends  1.16.1-0ubun i386         userspace virtual filesystem - ba
ii  gvfs-bin       1.16.1-0ubun i386         userspace virtual filesystem - bi
ii  gvfs-common    1.16.1-0ubun all          userspace virtual filesystem - co
ii  gvfs-daemons   1.16.1-0ubun i386         userspace virtual filesystem - se
ii  gvfs-fuse      1.16.1-0ubun i386         userspace virtual filesystem - fu
ii  gvfs-libs:i386 1.16.1-0ubun i386         userspace virtual filesystem - pr
ii  gzip           1.5-1.1ubunt i386         GNU compression utilities
rc  hamster-indica 0.1+037dd2e- all          Hamster Appindicator
ii  hardinfo       0.5.1-1.2ubu i386         Displays system information
ii  hdparm         9.43-1ubuntu i386         tune hard disk parameters for hig
ii  hicolor-icon-t 0.12-1ubuntu all          default fallback theme for FreeDe
ii  hostname       3.12ubuntu1  i386         utility to set/show the host name
ii  hud            13.04.0daily i386         Backend for the Unity HUD
ii  humanity-icon- 0.6.2        all          Humanity Icon theme
ii  hwdata         0.234-1      all          hardware identification / configu
ii  ibus           1.4.2-0ubunt i386         Intelligent Input Bus - core
ii  ifupdown       0.7.5ubuntu2 i386         high level tools to configure net
ii  im-config      0.21ubuntu3  all          Input method configuration framew
rc  imagemagick-co 8:6.7.7.10-5 all          image manipulation programs -- in
ii  indicator-appl 12.10.2daily i386         Clone of the GNOME panel indicato
ii  indicator-appl 12.10.1daily i386         Application Indicators
ii  indicator-appl 12.10.0.1-0u i386         Application Indicators
ii  indicator-appm 13.01.0daily i386         Indicator for application menus.
ii  indicator-blue 0.0.6daily13 i386         System bluetooth indicator.
ii  indicator-date 12.10.3daily i386         Simple clock
ii  indicator-mess 12.10.6daily i386         indicator that collects messages 
ii  indicator-powe 12.10.6daily i386         Indicator showing power state.
ii  indicator-prin 0.1.7daily13 i386         indicator showing active print jo
ii  indicator-sess 12.10.5daily i386         indicator showing session managem
ii  indicator-soun 12.10.2daily i386         System sound indicator.
ii  indicator-sync 12.10.5daily i386         indicator for synchronisation pro
ii  info           4.13a.dfsg.1 i386         Standalone GNU Info documentation
ii  initramfs-tool 0.103ubuntu0 all          tools for generating an initramfs
ii  initramfs-tool 0.103ubuntu0 i386         binaries used by initramfs-tools
ii  initscripts    2.88dsf-13.1 i386         scripts for initializing and shut
rc  inkscape       0.48.4-0.1ub i386         vector-based drawing program
ii  inputattach    1:1.4.3-1    i386         utility to connect serial-attache
ii  insserv        1.14.0-5ubun i386         boot sequence organizer using LSB
ii  install-info   4.13a.dfsg.1 i386         Manage installed documentation in
ii  iproute        20121211-2   i386         networking and traffic control to
ii  iptables       1.4.12-2ubun i386         administration tools for packet f
ii  iputils-arping 3:20101006-3 i386         Tool to send ICMP echo requests t
ii  iputils-ping   3:20101006-3 i386         Tools to test the reachability of
ii  iputils-tracep 3:20101006-3 i386         Tools to trace the network path t
ii  irqbalance     1.0.5-2      i386         Daemon to balance interrupts for 
ii  isc-dhcp-clien 4.2.4-5ubunt i386         ISC DHCP client
ii  isc-dhcp-commo 4.2.4-5ubunt i386         common files used by all the isc-
ii  iso-codes      3.41-1       all          ISO language, territory, currency
ii  kbd            1.15.5-1ubun i386         Linux console font and keytable u
ii  keyboard-confi 1.70ubuntu7  all          system-wide keyboard preferences
ii  klibc-utils    2.0.1-3.1ubu i386         small utilities built with klibc 
ii  kmod           9-3ubuntu1   i386         tools for managing Linux kernel m
ii  krb5-locales   1.10.1+dfsg- all          Internationalization support for 
ii  language-pack- 1:13.04+2013 all          translation updates for language 
ii  language-pack- 1:13.04+2013 all          translations for language English
ii  language-pack- 1:13.04+2013 all          GNOME translation updates for lan
ii  language-pack- 1:13.04+2013 all          GNOME translations for language E
ii  language-selec 0.110        all          Language selector for Ubuntu
ii  language-selec 0.110        all          Language selector for Ubuntu
ii  leafpad        0.8.18.1-3   i386         GTK+ based simple text editor
ii  less           456-1ubuntu1 i386         pager program similar to more
rc  liba52-0.7.4   0.7.4-16buil i386         library for decoding ATSC A/52 st
ii  libaa1:i386    1.4p5-40     i386         ASCII art library
ii  libabiword-2.9 2.9.2+svn201 i386         efficient, featureful word proces
rc  libaccounts-gl 1.8-0ubuntu1 i386         library for single signon
rc  libaccounts-qt 1.6bzr13.02. i386         QT library for single sign on
ii  libaccountsser 0.6.29-1ubun i386         query and manipulate user account
ii  libacl1:i386   2.2.51-8ubun i386         Access control list shared librar
ii  libalgorithm-d 1.19.02-3    all          module to find differences betwee
ii  libalgorithm-d 0.04-2build3 i386         module to find differences betwee
ii  libalgorithm-m 0.08-2       all          Perl module for three-way merge o
rc  libamd2.2.0    1:3.4.0-3ubu i386         approximate minimum degree orderi
ii  libappindicato 12.10.1daily i386         Application Indicators
ii  libappindicato 12.10.1daily i386         Application Indicators
ii  libapt-inst1.5 0.9.7.7ubunt i386         deb package format runtime librar
ii  libapt-pkg4.12 0.9.7.7ubunt i386         package managment runtime library
ii  libarchive13:i 3.1.2-5ubunt i386         Multi-format archive and compress
rc  libart-2.0-2:i 2.3.21-2     i386         Library of functions for 2D graph
ii  libasn1-8-heim 1.6~git20120 i386         Heimdal Kerberos - ASN.1 library
ii  libasound2:i38 1.0.25-4ubun i386         shared library for ALSA applicati
ii  libasound2-plu 1.0.25-2ubun i386         ALSA library additional plugins
ii  libaspell15    0.60.7~20110 i386         GNU Aspell spell-checker runtime 
ii  libasprintf0c2 0.18.1.1-10u i386         GNU library to use fprintf and fr
ii  libass4:i386   0.10.1-1     i386         library for SSA/ASS subtitles ren
ii  libasyncns0:i3 0.8-4build1  i386         Asynchronous name service query l
ii  libatasmart4:i 0.19-2       i386         ATA S.M.A.R.T. reading and parsin
ii  libatk-bridge2 2.8.1-1      i386         AT-SPI 2 toolkit bridge - shared 
rc  libatk-wrapper 0.30.4-0ubun i386         An ATK implementation for Java us
ii  libatk1.0-0:i3 2.8.0-1      i386         ATK accessibility toolkit
ii  libatk1.0-data 2.8.0-1      all          Common files for the ATK accessib
ii  libatkmm-1.6-1 2.22.6-1ubun i386         C++ wrappers for ATK accessibilit
ii  libatm1:i386   1:2.5.1-1.5  i386         shared library for ATM (Asynchron
ii  libatspi2.0-0: 2.8.0-1      i386         Assistive Technology Service Prov
ii  libattr1:i386  1:2.4.46-8ub i386         Extended attribute shared library
ii  libaudclient2: 3.3.4-1      i386         audacious dbus remote control lib
ii  libaudcore1:i3 3.3.4-1      i386         audacious core engine library
ii  libaudio2:i386 1.9.3-5      i386         Network Audio System - shared lib
ii  libaudit-commo 1:2.2.2-1ubu all          Dynamic library for security audi
ii  libaudit1:i386 1:2.2.2-1ubu i386         Dynamic library for security audi
ii  libavahi-clien 0.6.31-1ubun i386         Avahi client library
ii  libavahi-commo 0.6.31-1ubun i386         Avahi common data files
ii  libavahi-commo 0.6.31-1ubun i386         Avahi common library
ii  libavahi-core7 0.6.31-1ubun i386         Avahi's embeddable mDNS/DNS-SD li
ii  libavahi-glib1 0.6.31-1ubun i386         Avahi GLib integration library
rc  libavahi-gobje 0.6.31-1ubun i386         Avahi GObject library
rc  libavahi-ui-gt 0.6.31-1ubun i386         Avahi GTK+ User interface library
ii  libavc1394-0:i 0.5.4-2      i386         control IEEE 1394 audio/video dev
ii  libavcodec53:i 6:0.8.6-1ubu i386         Libav codec library
ii  libavformat53: 6:0.8.6-1ubu i386         Libav file format library
ii  libavutil51:i3 6:0.8.6-1ubu i386         Libav utility library
rc  libbabl-0.1-0: 0.1.10-1ubun i386         Dynamic, any to any, pixel format
ii  libbamf3-1:i38 0.4.0daily13 i386         Window matching library - shared 
ii  libbind9-90    1:9.9.2.dfsg i386         BIND9 Shared Library used by BIND
ii  libbinio1ldbl  1.4+dfsg1-1  i386         Binary I/O stream class library
ii  libbison-dev:i 2:2.5.dfsg-3 i386         YACC-compatible parser generator 
ii  libblkid1:i386 2.20.1-5.1ub i386         block device id library
ii  libbluetooth3: 4.101-0ubunt i386         Library to use the BlueZ Linux Bl
ii  libbluray1:i38 1:0.2.3-1    i386         Blu-ray disc playback support lib
rc  libbonobo2-0:i 2.32.1-0ubun i386         Bonobo CORBA interfaces library
rc  libbonobo2-com 2.32.1-0ubun all          Bonobo CORBA interfaces library -
rc  libbonoboui2-0 2.24.5-0ubun i386         The Bonobo UI library
rc  libboost-date- 1.49.0-3.2ub i386         set of date-time libraries based 
rc  libboost-iostr 1.49.0-3.2ub i386         Boost.Iostreams Library
rc  libboost-progr 1.49.0-3.2ub i386         program options library for C++
rc  libboost-threa 1.49.0-3.2ub i386         portable C++ multi-threading
rc  libbrlapi0.5:i 4.4-8ubuntu4 i386         braille display access via BRLTTY
ii  libbs2b0       3.1.0+dfsg-2 i386         Bauer stereophonic-to-binaural DS
ii  libbsd0:i386   0.4.2-1ubunt i386         utility functions from BSD system
ii  libburn4       1.2.4-0ubunt i386         library to provide CD/DVD writing
ii  libbz2-1.0:i38 1.0.6-4      i386         high-quality block-sorting file c
ii  libc-bin       2.17-0ubuntu i386         Embedded GNU C Library: Binaries
ii  libc-dev-bin   2.17-0ubuntu i386         Embedded GNU C Library: Developme
ii  libc6:i386     2.17-0ubuntu i386         Embedded GNU C Library: Shared li
ii  libc6-dev:i386 2.17-0ubuntu i386         Embedded GNU C Library: Developme
ii  libcaca0:i386  0.99.beta18- i386         colour ASCII art library
ii  libcairo-gobje 1.12.14-0ubu i386         The Cairo 2D vector graphics libr
ii  libcairo-perl  1.103-1      i386         Perl interface to the Cairo graph
ii  libcairo2:i386 1.12.14-0ubu i386         The Cairo 2D vector graphics libr
ii  libcairomm-1.0 1.10.0-1ubun i386         C++ wrappers for Cairo (shared li
ii  libcamel-1.2-4 3.6.4-0ubunt i386         Evolution MIME message handling l
ii  libcanberra-gt 0.30-0ubuntu i386         translates GTK+ widgets signals t
ii  libcanberra-gt 0.30-0ubuntu i386         GTK+ helper for playing widget ev
ii  libcanberra-gt 0.30-0ubuntu i386         GTK+ 3.0 helper for playing widge
ii  libcanberra-gt 0.30-0ubuntu i386         translates GTK3 widgets signals t
ii  libcanberra-pu 0.30-0ubuntu i386         PulseAudio backend for libcanberr
ii  libcanberra0:i 0.30-0ubuntu i386         simple abstract interface for pla
ii  libcap-ng0     0.6.6-2ubunt i386         An alternate POSIX capabilities l
ii  libcap2:i386   1:2.22-1.2ub i386         support for getting/setting POSIX
ii  libcap2-bin    1:2.22-1.2ub i386         basic utility programs for using 
rc  libcdaudio1    0.99.12p2-12 i386         library for controlling a CD-ROM 
ii  libcddb2       1.3.2-3fakes i386         library to access CDDB data - run
ii  libcdio-cdda1  0.83-4       i386         library to read and control digit
ii  libcdio-parano 0.83-4       i386         library to read digital audio CDs
ii  libcdio13      0.83-4       i386         library to read and control CD-RO
ii  libcdparanoia0 3.10.2+debia i386         audio extraction tool for samplin
rc  libcdr-0.0-0   0.0.11-2     i386         library for reading and convertin
ii  libck-connecto 0.4.5-3.1ubu i386         ConsoleKit libraries
ii  libclass-isa-p 0.36-5       all          report the search path for a clas
ii  libcloog-ppl1: 0.16.1-1     i386         Chunky Loop Generator (runtime li
rc  libclucene-con 2.3.3.4-2    i386         language specific text analyzers 
rc  libclucene-cor 2.3.3.4-2    i386         core library for full-featured te
rc  libclutter-1.0 1.12.2-0ubun i386         Open GL based interactive canvas 
rc  libclutter-gst 2.0.2-0ubunt i386         Open GL based interactive canvas 
rc  libclutter-gtk 1.4.2-0ubunt i386         Open GL based interactive canvas 
rc  libcmis-0.3-3  0.3.1-1ubunt i386         CMIS protocol client library
rc  libcogl-pango1 1.14.0-0ubun i386         Object oriented GL/GLES Abstracti
rc  libcogl12:i386 1.14.0-0ubun i386         Object oriented GL/GLES Abstracti
rc  libcolord-gtk1 0.1.24-0ubun i386         system service to manage device c
ii  libcolord1:i38 0.1.30-0ubun i386         system service to manage device c
ii  libcolorhug1:i 0.1.30-0ubun i386         library to access the ColorHug co
rc  libcolumbus0-0 0.4.0daily13 i386         error tolerant matching engine - 
ii  libcomerr2:i38 1.42.5-1ubun i386         common error description library
ii  libcompfaceg1  1:1.5.2-5    i386         Compress/decompress images for ma
ii  libcompizconfi 1:0.9.9~dail i386         Settings library for plugins - Op
ii  libcrack2      2.8.22-0ubun i386         pro-active password checker libra
ii  libcroco3:i386 0.6.8-1      i386         Cascading Style Sheet (CSS) parsi
ii  libcue1        1.4.0-1      i386         CUE Sheet Parser Library
ii  libcups2:i386  1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  libcupscgi1:i3 1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  libcupsfilters 1.0.34-0ubun i386         OpenPrinting CUPS Filters - Share
ii  libcupsimage2: 1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  libcupsmime1:i 1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  libcupsppdc1:i 1.6.2-1ubunt i386         Common UNIX Printing System(tm) -
ii  libcurl3:i386  7.29.0-1ubun i386         easy-to-use client-side URL trans
ii  libcurl3-gnutl 7.29.0-1ubun i386         easy-to-use client-side URL trans
ii  libdaemon0     0.14-2build1 i386         lightweight C library for daemons
ii  libdatrie1:i38 0.2.6-1      i386         Double-array trie library
ii  libdb5.1:i386  5.1.29-5ubun i386         Berkeley v5.1 Database Libraries 
ii  libdbus-1-3:i3 1.6.8-1ubunt i386         simple interprocess messaging sys
ii  libdbus-glib-1 0.100.2-1    i386         simple interprocess messaging sys
ii  libdbusmenu-gl 12.10.3daily i386         library for passing menus over DB
ii  libdbusmenu-gt 12.10.3daily i386         library for passing menus over DB
ii  libdbusmenu-gt 12.10.3daily i386         library for passing menus over DB
ii  libdbusmenu-qt 0.9.2daily13 i386         Qt implementation of the DBusMenu
ii  libdbusmenu-qt 0.9.2daily13 i386         Qt5 implementation of the DBusMen
rc  libdc1394-22:i 2.2.0-2build i386         high level programming interface 
ii  libdca0        0.0.5-5      i386         decoding library for DTS Coherent
ii  libdconf1:i386 0.16.0-0ubun i386         simple configuration storage syst
ii  libdecoration0 1:0.9.9~dail i386         Compiz window decoration library
ii  libdee-1.0-4   1.2.3~daily1 i386         model to synchronize mutiple inst
ii  libdevmapper-e 2:1.02.74-6u i386         Linux Kernel Device Mapper event 
ii  libdevmapper1. 2:1.02.74-6u i386         Linux Kernel Device Mapper usersp
rc  libdirac-encod 1.0.2-6      i386         open and royalty free high qualit
ii  libdirectfb-1. 1.2.10.0-5   i386         direct frame buffer graphics - sh
ii  libdiscid0:i38 0.2.2-3build i386         Library for creating MusicBrainz 
ii  libdjvulibre-t 3.5.25.3-3   all          Linguistic support files for libd
ii  libdjvulibre21 3.5.25.3-3   i386         Runtime support for the DjVu imag
rc  libdmapsharing 2.9.15-1ubun i386         DMAP client and server library - 
ii  libdns95       1:9.9.2.dfsg i386         DNS Shared Library used by BIND
ii  libdpkg-perl   1.16.10ubunt all          Dpkg perl modules
ii  libdrm-intel1: 2.4.43-0ubun i386         Userspace interface to intel-spec
ii  libdrm-nouveau 2.4.43-0ubun i386         Userspace interface to nouveau-sp
ii  libdrm-radeon1 2.4.43-0ubun i386         Userspace interface to radeon-spe
ii  libdrm2:i386   2.4.43-0ubun i386         Userspace interface to kernel DRM
ii  libdv4:i386    1.0.0-6      i386         software library for DV format di
ii  libdvdnav4:i38 4.2.0+201302 i386         DVD navigation library
ii  libdvdread4    4.2.0+201210 i386         library for reading DVDs
ii  libebackend-1. 3.6.4-0ubunt i386         Utility library for evolution dat
ii  libebook-1.2-1 3.6.4-0ubunt i386         Client library for evolution addr
ii  libecal-1.2-15 3.6.4-0ubunt i386         Client library for evolution cale
ii  libedata-book- 3.6.4-0ubunt i386         Backend library for evolution add
ii  libedata-cal-1 3.6.4-0ubunt i386         Backend library for evolution cal
ii  libedataserver 3.6.4-0ubunt i386         Utility library for evolution dat
rc  libedataserver 3.6.4-0ubunt i386         GUI utility library for evolution
ii  libedit2:i386  2.11-2008061 i386         BSD editline and history librarie
ii  libegl1-mesa:i 9.1.1-0ubunt i386         free implementation of the EGL AP
ii  libegl1-mesa-d 9.1.1-0ubunt i386         free implementation of the EGL AP
ii  libelf1:i386   0.153-2ubunt i386         library to read and write ELF fil
ii  libelfg0:i386  0.8.13-4~1   i386         an ELF object file access library
ii  libenca0       1.14-2       i386         Extremely Naive Charset Analyser 
ii  libenchant1c2a 1.6.0-7build i386         Wrapper library for various spell
ii  libencode-loca 1.03-1       all          utility to determine the locale e
ii  libept1.4.12   1.0.9        i386         High-level library for managing D
ii  libevdocument3 3.6.1-1ubunt i386         Document (PostScript, PDF) render
ii  libevent-2.0-5 2.0.19-stabl i386         Asynchronous event notification l
ii  libevview3-3   3.6.1-1ubunt i386         Document (PostScript, PDF) render
rc  libexempi3:i38 2.2.0-1build i386         library to parse XMP metadata (Li
ii  libexif12:i386 0.6.21-1     i386         library to parse EXIF files
rc  libexiv2-12    0.23-1       i386         EXIF/IPTC metadata manipulation l
ii  libexo-1-0:i38 0.10.2-1     i386         Library with extensions for Xfce
ii  libexo-common  0.10.2-1     all          libexo common files
ii  libexo-helpers 0.10.2-1     i386         libexo helpers
ii  libexpat1:i386 2.1.0-2      i386         XML parsing C library - runtime l
rc  libexttextcat- 3.4.0-2      i386         Language detection library
ii  libfaad2:i386  2.7-8        i386         freeware Advanced Audio Decoder -
ii  libfarstream-0 0.1.2-1ubunt i386         Audio/Video communications framew
rc  libfarstream-0 0.2.2-1ubunt i386         Audio/Video communications framew
ii  libffi6:i386   3.0.13-2ubun i386         Foreign Function Interface librar
ii  libffmpegthumb 2.0.8-0ubunt i386         shared library for ffmpegthumbnai
rc  libfftw3-doubl 3.3.3-2ubunt i386         Library for computing Fast Fourie
ii  libfftw3-singl 3.3.3-2ubunt i386         Library for computing Fast Fourie
ii  libfile-fcntll 0.14-2       i386         Perl module for file locking with
ii  libfile-listin 6.04-1       all          module to parse directory listing
ii  libflac8:i386  1.2.1-6build i386         Free Lossless Audio Codec - runti
ii  libflite1:i386 1.4-release- i386         Small run-time speech synthesis e
ii  libfluidsynth1 1.1.6-2      i386         Real-time MIDI software synthesiz
ii  libfm-data     1.1.0-0ubunt all          file management support (common d
ii  libfm-gtk-bin  1.1.0-0ubunt i386         file management support (utilitie
ii  libfm-gtk-data 1.1.0-0ubunt i386         file management support (common f
ii  libfm-gtk3     1.1.0-0ubunt i386         file management support (GTK+ GUI
ii  libfm3         1.1.0-0ubunt i386         file management support (core lib
rc  libfolks-eds25 0.8.0-1      i386         Evolution-data-server backend for
rc  libfolks-telep 0.8.0-1      i386         Telepathy backend for libfolks
rc  libfolks25     0.8.0-1      i386         library to aggregates people into
ii  libfontconfig1 2.10.2-0ubun i386         generic font configuration librar
ii  libfontembed1: 1.0.34-0ubun i386         OpenPrinting CUPS Filters - Font 
ii  libfontenc1:i3 1:1.1.1-1    i386         X11 font encoding library
ii  libframe6:i386 2.5.0daily13 i386         Touch Frame Library
ii  libfreetype6:i 2.4.11-0ubun i386         FreeType 2 font engine, shared li
ii  libfribidi0:i3 0.19.5-1     i386         Free Implementation of the Unicod
rc  libfs6:i386    2:1.0.4-1    i386         X11 Font Services library
ii  libfuse2:i386  2.9.0-1ubunt i386         Filesystem in Userspace (library)
ii  libgail-3-0:i3 3.6.4-0ubunt i386         GNOME Accessibility Implementatio
rc  libgail18:i386 2.24.17-0ubu i386         GNOME Accessibility Implementatio
ii  libgbm1:i386   9.1.1-0ubunt i386         generic buffer management API -- 
rc  libgc1c3:i386  1:7.2d-0ubun i386         conservative garbage collector fo
ii  libgcc-4.7-dev 4.7.3-1ubunt i386         GCC support library (development 
ii  libgcc1:i386   1:4.7.3-1ubu i386         GCC support library
ii  libgck-1-0     3.6.2-0ubunt i386         Glib wrapper library for PKCS#11 
ii  libgconf-2-4:i 3.2.6-0ubunt i386         GNOME configuration database syst
ii  libgcr-3-1     3.6.2-0ubunt i386         Library for Crypto UI related tas
ii  libgcr-3-commo 3.6.2-0ubunt all          Library for Crypto UI related tas
ii  libgcrypt11:i3 1.5.0-3ubunt i386         LGPL Crypto library - runtime lib
ii  libgd2-xpm:i38 2.0.36~rc1~d i386         GD Graphics Library version 2
ii  libgda-5.0-4   5.0.3-2ubunt i386         data abstraction library based on
ii  libgda-5.0-com 5.0.3-2ubunt all          data abstraction library based on
ii  libgdata-commo 0.13.2-2svn1 all          Library for accessing GData webse
ii  libgdata13     0.13.2-2svn1 i386         Library for accessing GData webse
ii  libgdbm3:i386  1.8.3-11ubun i386         GNU dbm database routines (runtim
rc  libgdict-1.0-6 3.6.0-0ubunt i386         GNOME Dictionary base library - r
rc  libgdiplus     2.10-3ubuntu i386         interface library for System.Draw
ii  libgdk-pixbuf2 2.28.0-0ubun i386         GDK Pixbuf library
ii  libgdk-pixbuf2 2.28.0-0ubun all          GDK Pixbuf library - data files
rc  libgee-0.8-2:i 0.8.6-0ubunt i386         GObject based collection library
ii  libgee2:i386   0.6.8-0ubunt i386         GObject based collection library
rc  libgegl-0.2-0: 0.2.0-2+nmu1 i386         Generic Graphics Library
ii  libgeis1:i386  2.2.15daily1 i386         Gesture engine interface support
ii  libgeoclue0    0.12.99-0ubu i386         C API for GeoClue
ii  libgeoip1:i386 1.4.8+dfsg-4 i386         non-DNS IP-to-country resolver li
rc  libgexiv2-2    0.6.1-0ubunt i386         GObject-based wrapper around the 
rc  libgfortran3:i 4.7.3-1ubunt i386         Runtime library for GNU Fortran a
ii  libgif4:i386   4.1.6-10ubun i386         library for GIF images (library)
rc  libgimp2.0     2.8.4-1ubunt i386         Libraries for the GNU Image Manip
ii  libgirepositor 1.36.0-1     i386         Library for handling GObject intr
rc  libgjs0c       1.34.0-0ubun i386         Mozilla-based javascript bindings
ii  libgksu2-0     2.0.13~pre1- i386         library providing su and sudo fun
ii  libgl1-mesa-dr 9.1.1-0ubunt i386         free implementation of the OpenGL
ii  libgl1-mesa-gl 9.1.1-0ubunt i386         free implementation of the OpenGL
ii  libglade2-0:i3 1:2.6.4-1ubu i386         library to load .glade files at r
ii  libglapi-mesa: 9.1.1-0ubunt i386         free implementation of the GL API
ii  libgles2-mesa: 9.1.1-0ubunt i386         free implementation of the OpenGL
ii  libglew1.8:i38 1.9.0.is.1.8 i386         OpenGL Extension Wrangler - runti
ii  libglewmx1.8:i 1.9.0.is.1.8 i386         OpenGL Extension Wrangler (Multip
ii  libglib-perl   3:1.261-1    i386         interface to the GLib and GObject
ii  libglib2.0-0:i 2.36.0-1ubun i386         GLib library of C routines
ii  libglib2.0-bin 2.36.0-1ubun i386         Programs for the GLib library
rc  libglib2.0-cil 2.12.10-5    i386         CLI binding for the GLib utility 
ii  libglib2.0-dat 2.36.0-1ubun all          Common files for GLib library
ii  libglibmm-2.4- 2.35.9-0ubun i386         C++ wrapper for the GLib toolkit 
ii  libglu1-mesa:i 9.0.0-0ubunt i386         Mesa OpenGL utility library (GLU)
ii  libgme0        0.5.5-2      i386         Playback library for video game m
rc  libgmime-2.6-0 2.6.13-0ubun i386         MIME message parser and creator l
ii  libgmlib1:i386 1.0.8-1      i386         gnome-mplayer library (shared lib
ii  libgmp10:i386  2:5.0.5+dfsg i386         Multiprecision arithmetic library
ii  libgmpxx4ldbl: 2:5.0.5+dfsg i386         Multiprecision arithmetic library
ii  libgmtk1:i386  1.0.8-1      i386         gnome-mplayer toolkit (shared lib
ii  libgmtk1-data  1.0.8-1      all          gnome-mplayer toolkit (common fil
ii  libgnome-bluet 3.6.1-0ubunt i386         GNOME Bluetooth tools - support l
ii  libgnome-contr 1:3.6.3-0ubu i386         utilities to configure the GNOME 
ii  libgnome-deskt 3.6.3-0ubunt i386         Utility library for loading .desk
ii  libgnome-keyri 3.6.0-1      all          GNOME keyring services library - 
ii  libgnome-keyri 3.6.0-1      i386         GNOME keyring services library
rc  libgnome-media 3.0.0-1ubunt i386         GNOME Media Profiles library
ii  libgnome-menu- 3.6.2-0ubunt i386         GNOME implementation of the freed
rc  libgnome2-0:i3 2.32.1-2ubun i386         The GNOME library - runtime files
rc  libgnome2-comm 2.32.1-2ubun all          The GNOME library - common files
rc  libgnomecanvas 2.30.3-1ubun i386         powerful object-oriented display 
ii  libgnomekbd-co 3.6.0-0ubunt all          GNOME library to manage keyboard 
ii  libgnomekbd8   3.6.0-0ubunt i386         GNOME library to manage keyboard 
rc  libgnomeui-0:i 2.24.5-2ubun i386         GNOME user interface library - ru
rc  libgnomevfs2-0 1:2.24.4-1ub i386         GNOME Virtual File System (runtim
rc  libgnomevfs2-c 1:2.24.4-1ub i386         GNOME Virtual File System (common
rc  libgnomevfs2-e 1:2.24.4-1ub i386         GNOME Virtual File System (extra 
ii  libgnutls26:i3 2.12.23-1ubu i386         GNU TLS library - runtime library
ii  libgoa-1.0-0:i 3.6.2-1ubunt i386         library for GNOME Online Accounts
ii  libgoa-1.0-com 3.6.2-1ubunt all          library for GNOME Online Accounts
ii  libgoffice-0.1 0.10.1-1ubun i386         Document centric objects library 
ii  libgoffice-0.1 0.10.1-1ubun all          Document centric objects library 
ii  libgomp1:i386  4.7.3-1ubunt i386         GCC OpenMP (GOMP) support library
ii  libgpg-error0: 1.10-3.1ubun i386         library for common error values a
ii  libgpgme11     1.2.0-1.4ubu i386         GPGME - GnuPG Made Easy
ii  libgphoto2-2:i 2.4.14-2     i386         gphoto2 digital camera library
ii  libgphoto2-por 2.4.14-2     i386         gphoto2 digital camera port libra
ii  libgpm2:i386   1.20.4-6ubun i386         General Purpose Mouse - shared li
ii  libgpod4:i386  0.8.2-7ubunt i386         library to read and write songs a
ii  libgrail6      3.1.0daily13 i386         Gesture Recognition And Instantia
ii  libgrip0       0.3.6daily13 i386         provides multitouch gestures to G
ii  libgs9         9.07~dfsg2-0 i386         interpreter for the PostScript la
ii  libgs9-common  9.07~dfsg2-0 all          interpreter for the PostScript la
ii  libgsf-1-114   1.14.26-1ubu i386         Structured File Library - runtime
ii  libgsf-1-commo 1.14.26-1ubu all          Structured File Library - common 
rc  libgsl0ldbl    1.15+dfsg.2- i386         GNU Scientific Library (GSL) -- l
ii  libgsm1:i386   1.0.13-4     i386         Shared libraries for GSM speech c
ii  libgssapi-krb5 1.10.1+dfsg- i386         MIT Kerberos runtime libraries - 
ii  libgssapi3-hei 1.6~git20120 i386         Heimdal Kerberos - GSSAPI support
ii  libgssdp-1.0-3 0.14.2-0ubun i386         GObject-based library for SSDP
rc  libgstreamer-p 0.10.23-7ubu i386         GStreamer shared libraries from t
ii  libgstreamer-p 1.0.6-1ubunt i386         GStreamer development files for l
ii  libgstreamer-p 0.10.36-1.1u i386         GStreamer libraries from the "bas
ii  libgstreamer-p 1.0.6-1      i386         GStreamer libraries from the "bas
ii  libgstreamer-p 1.0.6-1ubunt i386         GStreamer development files for l
ii  libgstreamer0. 0.10.36-1ubu i386         Core GStreamer libraries and elem
ii  libgstreamer1. 1.0.6-1      i386         Core GStreamer libraries and elem
ii  libgtk-3-0:i38 3.6.4-0ubunt i386         GTK+ graphical user interface lib
ii  libgtk-3-bin   3.6.4-0ubunt i386         programs for the GTK+ graphical u
ii  libgtk-3-commo 3.6.4-0ubunt all          common files for the GTK+ graphic
rc  libgtk-vnc-2.0 0.5.1-1ubunt i386         VNC viewer widget for GTK+3 (runt
ii  libgtk2-perl   2:1.244-1ubu i386         Perl interface to the 2.x series 
ii  libgtk2.0-0:i3 2.24.17-0ubu i386         GTK+ graphical user interface lib
rc  libgtk2.0-cil  2.12.10-5    i386         CLI binding for the GTK+ toolkit 
ii  libgtk2.0-comm 2.24.17-0ubu all          common files for the GTK+ graphic
rc  libgtkhtml-4.0 4.6.4-0ubunt i386         HTML rendering/editing library - 
rc  libgtkhtml-edi 4.6.4-0ubunt i386         HTML rendering/editing library - 
ii  libgtkmm-2.4-1 1:2.24.2-1ub i386         C++ wrappers for GTK+ (shared lib
ii  libgtkmm-3.0-1 3.6.0-0ubunt i386         C++ wrappers for GTK+ (shared lib
rc  libgtksourcevi 3.6.3-0ubunt i386         shared libraries for the GTK+ syn
ii  libgtkspell0   2.0.16-1ubun i386         a spell-checking addon for GTK's 
ii  libgtop2-7     2.28.4-3     i386         gtop system monitoring library (s
ii  libgtop2-commo 2.28.4-3     all          gtop system monitoring library (c
ii  libgucharmap-2 1:3.6.1-0ubu i386         Unicode browser widget library (s
ii  libgudev-1.0-0 1:198-0ubunt i386         GObject-based wrapper library for
ii  libguess1:i386 1.1-1        i386         high-speed character set detectio
ii  libgupnp-1.0-4 0.20.0-1ubun i386         GObject-based library for UPnP
rc  libgupnp-av-1. 0.11.6-1     i386         Audio/Visual utility library for 
rc  libgupnp-dlna- 0.9.4-2      i386         DLNA utility library for GUPnP
ii  libgupnp-igd-1 0.2.1-2ubunt i386         library to handle UPnP IGD port m
ii  libgusb2:i386  0.1.5-0ubunt i386         GLib wrapper around libusb1
ii  libgutenprint2 5.2.9-1ubunt i386         runtime for the Gutenprint printe
rc  libgvnc-1.0-0  0.5.1-1ubunt i386         VNC gobject wrapper (runtime libr
ii  libgweather-3- 3.6.2-0ubunt i386         GWeather shared library
ii  libgweather-co 3.6.2-0ubunt all          GWeather common files
ii  libgxps2:i386  0.2.2-2ubunt i386         handling and rendering XPS docume
ii  libharfbuzz0:i 0.9.13-1     i386         OpenType text shaping engine
ii  libhcrypto4-he 1.6~git20120 i386         Heimdal Kerberos - crypto library
ii  libheimbase1-h 1.6~git20120 i386         Heimdal Kerberos - Base library
ii  libheimntlm0-h 1.6~git20120 i386         Heimdal Kerberos - NTLM support l
ii  libhtml-parser 3.69-2       i386         collection of modules that parse 
ii  libhtml-tagset 3.20-2       all          Data tables pertaining to HTML
ii  libhtml-tree-p 5.02-1       all          Perl module to represent and crea
ii  libhttp-cookie 6.00-2       all          HTTP cookie jars
ii  libhttp-date-p 6.02-1       all          module of date conversion routine
ii  libhttp-messag 6.03-1       all          perl interface to HTTP style mess
ii  libhttp-negoti 6.00-2       all          implementation of content negotia
ii  libhunspell-1. 1.3.2-4ubunt i386         spell checker and morphological a
ii  libhx509-5-hei 1.6~git20120 i386         Heimdal Kerberos - X509 support l
rc  libhyphen0     2.8.3-2      i386         ALTLinux hyphenation library - sh
ii  libibus-1.0-0: 1.4.2-0ubunt i386         Intelligent Input Bus - shared li
ii  libical0       0.48-2       i386         iCalendar library implementation 
rc  libicc2:i386   2.12+argyll1 i386         ICC profile I/O library
ii  libice6:i386   2:1.0.8-2    i386         X11 Inter-Client Exchange library
ii  libicu48:i386  4.8.1.1-12   i386         International Components for Unic
ii  libid3tag0     0.15.1b-10bu i386         ID3 tag reading library from the 
rc  libidl0:i386   0.8.14-0.2ub i386         library for parsing CORBA IDL fil
ii  libidn11:i386  1.25-2       i386         GNU Libidn library, implementatio
ii  libido3-0.1-0: 12.10.3daily i386         Shared library providing extra gt
ii  libiec61883-0: 1.2.0-0.1ubu i386         an partial implementation of IEC 
ii  libieee1284-3: 0.2.11-10bui i386         cross-platform library for parall
ii  libijs-0.35    0.35-8build1 i386         IJS raster image transport protoc
rc  libilmbase6:i3 1.0.1-6      i386         several utility libraries from IL
rc  libimdi0:i386  1.4.0-8ubunt i386         Integer Multi-Dimensional Interpo
ii  libimlib2      1.4.5-1ubunt i386         powerful image loading and render
ii  libimobiledevi 1.1.4-1ubunt i386         Library for communicating with th
ii  libindicator3- 12.10.2daily i386         panel indicator applet - shared l
ii  libindicator7  12.10.2daily i386         panel indicator applet - shared l
ii  libio-socket-i 2.69-2       all          object interface for AF_INET6 dom
ii  libio-socket-s 1.76-2ubuntu all          Perl module implementing object o
rc  libiptcdata0   1.0.4-3ubunt i386         Library to parse IPTC metadata
ii  libisc92       1:9.9.2.dfsg i386         ISC Shared Library used by BIND
ii  libisccc90     1:9.9.2.dfsg i386         Command Channel Library used by B
ii  libisccfg90    1:9.9.2.dfsg i386         Config File Handling Library used
ii  libisofs6      1.2.6-0ubunt i386         library to create ISO9660 images
ii  libitm1:i386   4.7.3-1ubunt i386         GNU Transactional Memory Library
ii  libiw30:i386   30~pre9-8ubu i386         Wireless tools - library
ii  libjack-jackd2 1.9.9.5+2013 i386         JACK Audio Connection Kit (librar
ii  libjasper1:i38 1.900.1-14   i386         JasPer JPEG-2000 runtime library
rc  libjavascriptc 1.10.2-0ubun i386         Javascript engine library for GTK
ii  libjavascriptc 1.10.2-0ubun i386         Javascript engine library for GTK
ii  libjbig0:i386  2.0-2ubuntu1 i386         JBIGkit libraries
ii  libjbig2dec0   0.11+2012012 i386         JBIG2 decoder library - shared li
ii  libjpeg-turbo8 1.2.1-0ubunt i386         IJG JPEG compliant runtime librar
ii  libjpeg8:i386  8c-2ubuntu7  i386         Independent JPEG Group's JPEG run
ii  libjs-jquery   1.7.2+debian all          JavaScript library for dynamic we
ii  libjson-glib-1 0.15.2-0ubun i386         GLib JSON manipulation library
ii  libjson0:i386  0.10-1.2ubun i386         JSON manipulation library - share
ii  libjte1        1.19-1build1 i386         Jigdo Template Export - runtime l
ii  libk5crypto3:i 1.10.1+dfsg- i386         MIT Kerberos runtime libraries - 
rc  libkate1       0.4.1-1      i386         Kate is a codec for karaoke and t
ii  libkeyutils1:i 1.5.5-4      i386         Linux Key Management Utilities (l
ii  libklibc       2.0.1-3.1ubu i386         minimal libc subset for use with 
ii  libkmod2:i386  9-3ubuntu1   i386         libkmod shared library
ii  libkpathsea6   2012.2012062 i386         TeX Live: path search library for
ii  libkrb5-26-hei 1.6~git20120 i386         Heimdal Kerberos - libraries
ii  libkrb5-3:i386 1.10.1+dfsg- i386         MIT Kerberos runtime libraries
ii  libkrb5support 1.10.1+dfsg- i386         MIT Kerberos runtime libraries - 
rc  liblangtag1    0.4.0-6      i386         library to access tags for identi
ii  liblcms1:i386  1.19.dfsg-1. i386         Little CMS color management libra
ii  liblcms2-2:i38 2.4-0ubuntu3 i386         Little CMS 2 color management lib
ii  libldap-2.4-2: 2.4.31-1ubun i386         OpenLDAP libraries
ii  liblightdm-gob 1.6.0-0ubunt i386         LightDM GObject client library
rc  liblinear1     1.8+dfsg-1ub i386         Library for Large Linear Classifi
ii  liblircclient0 0.9.0-0ubunt i386         infra-red remote control support 
ii  libllvm3.2:i38 3.2-2ubuntu5 i386         Low-Level Virtual Machine (LLVM),
ii  liblocale-gett 1.05-7build2 i386         module using libc functions for i
ii  liblockfile-bi 1.09-5ubuntu i386         support binaries for and cli util
ii  liblockfile1:i 1.09-5ubuntu i386         NFS-safe locking library
ii  libloudmouth1- 1.4.3-9      i386         Lightweight C Jabber library
rc  liblouis2:i386 2.4.1-1ubunt i386         Braille translation library - sha
rc  liblqr-1-0:i38 0.4.1-2      i386         converts plain array images into 
ii  libltdl7:i386  2.4.2-1.2ubu i386         A system independent dlopen wrapp
rc  liblua5.1-0:i3 5.1.5-4      i386         Shared library for the Lua interp
ii  liblwp-mediaty 6.02-1       all          module to guess media type for a 
ii  liblwp-protoco 6.03-1       all          HTTPS driver for LWP::UserAgent
ii  liblwres90     1:9.9.2.dfsg i386         Lightweight Resolver Library used
ii  liblzma5:i386  5.1.1alpha+2 i386         XZ-format compression library
ii  liblzo2-2:i386 2.06-1build1 i386         data compression library
rc  libmad0:i386   0.15.1b-7ubu i386         MPEG audio decoder library
ii  libmagic1:i386 5.11-2ubuntu i386         File type determination library u
rc  libmagick++5:i 8:6.7.7.10-5 i386         object-oriented C++ interface to 
rc  libmagickcore5 8:6.7.7.10-5 i386         low-level image manipulation libr
rc  libmagickwand5 8:6.7.7.10-5 i386         image manipulation library
ii  libmeanwhile1  1.0.2-4ubunt i386         open implementation of the Lotus 
ii  libmenu-cache2 0.4.1-0ubunt i386         LXDE implementation of the freede
ii  libmessaging-m 12.10.6daily i386         Messaging Menu - shared library
ii  libmetacity-pr 1:2.34.13-0u i386         library for the Metacity window m
ii  libmhash2      0.9.9.9-1.1  i386         Library for cryptographic hashing
ii  libmimic0      1.0.4-2.1bui i386         A video codec for Mimic V2.x cont
ii  libminiupnpc8  1.6-3ubuntu2 i386         UPnP IGD client lightweight libra
rc  libmission-con 1:5.14.0-0ub i386         management daemon for Telepathy (
ii  libmms0:i386   0.6.2-3      i386         MMS stream protocol library - sha
ii  libmng1:i386   1.0.10-3buil i386         Multiple-image Network Graphics l
ii  libmodplug1    1:0.8.8.4-3  i386         shared libraries for mod music ba
ii  libmount1:i386 2.20.1-5.1ub i386         block device id library
ii  libmowgli2:i38 1.0.0-1      i386         high performance development fram
rc  libmozjs185-1. 1.8.5-1.0.0+ i386         Spidermonkey javascript engine
ii  libmp3lame0:i3 3.99.5+repac i386         MP3 encoding library
ii  libmpc2:i386   0.9-4build1  i386         multiple precision complex floati
rc  libmpcdec6     2:0.1~r459-1 i386         MusePack decoder - library
rc  libmpeg2-4:i38 0.5.1-5      i386         MPEG1 and MPEG2 video decoder lib
ii  libmpfr4:i386  3.1.1-1      i386         multiple precision floating-point
ii  libmpg123-0:i3 1.14.4-1     i386         MPEG layer 1/2/3 audio decoder (s
rc  libmspub-0.0-0 0.0.5-2      i386         library for parsing the mspub fil
ii  libmtdev1:i386 1.1.2-1ubunt i386         Multitouch Protocol Translation L
ii  libmtp-common  1.1.5-42-g6e all          Media Transfer Protocol (MTP) com
ii  libmtp-runtime 1.1.5-42-g6e i386         Media Transfer Protocol (MTP) run
ii  libmtp9:i386   1.1.5-42-g6e i386         Media Transfer Protocol (MTP) lib
ii  libmusicbrainz 3.0.2-2.1    i386         library to access the MusicBrainz
rc  libmusicbrainz 5.0.1-2      i386         Library to access the MusicBrainz
rc  libmutter0a    3.6.3-0ubunt i386         window manager library from the M
ii  libmysqlclient 5.5.31-0ubun i386         MySQL database client library
rc  libmythes-1.2- 2:1.2.2-1bui i386         simple thesaurus library
ii  libnatpmp1     20110808-3ub i386         portable and fully compliant impl
ii  libnautilus-ex 1:3.6.3-0ubu i386         libraries for nautilus components
ii  libncurses5:i3 5.9-10ubuntu i386         shared libraries for terminal han
ii  libncursesw5:i 5.9-10ubuntu i386         shared libraries for terminal han
ii  libneon27-gnut 0.29.6-3     i386         HTTP and WebDAV client library (G
ii  libnet-dbus-pe 1.0.0-2      i386         Perl extension for the DBus bindi
ii  libnet-http-pe 6.03-2       all          module providing low-level HTTP c
ii  libnet-ssleay- 1.48-1       i386         Perl module for Secure Sockets La
ii  libnetfilter-c 1.0.1-1      i386         Netfilter netlink-conntrack libra
rc  libnetpbm10    2:10.0-15ubu i386         Graphics conversion tools shared 
ii  libnettle4:i38 2.4-3        i386         low level cryptographic library (
ii  libnewt0.52    0.52.14-11ub i386         Not Erik's Windowing Toolkit - te
ii  libnfnetlink0  1.0.0-1.1ubu i386         Netfilter netlink library
ii  libnice10:i386 0.1.3-1      i386         ICE library (shared library)
ii  libnih-dbus1:i 1.0.3-4ubunt i386         NIH D-Bus Bindings Library
ii  libnih1:i386   1.0.3-4ubunt i386         NIH Utility Library
ii  libnl-3-200:i3 3.2.16-0ubun i386         library for dealing with netlink 
ii  libnl-genl-3-2 3.2.16-0ubun i386         library for dealing with netlink 
ii  libnl-route-3- 3.2.16-0ubun i386         library for dealing with netlink 
ii  libnm-glib-vpn 0.9.8.0-0ubu i386         network management framework (GLi
ii  libnm-glib4    0.9.8.0-0ubu i386         network management framework (GLi
ii  libnm-gtk-comm 0.9.8.0-1ubu all          network management framework (com
ii  libnm-gtk0     0.9.8.0-1ubu i386         network management framework (GNO
ii  libnm-util2    0.9.8.0-0ubu i386         network management framework (sha
ii  libnotify4:i38 0.7.5-2      i386         sends desktop notifications to a 
ii  libnspr4:i386  2:4.9.5-1ubu i386         NetScape Portable Runtime Library
ii  libnss-mdns    0.10-3.2buil i386         NSS module for Multicast DNS name
ii  libnss3:i386   2:3.14.3-0ub i386         Network Security Service librarie
ii  libnss3-1d:i38 2:3.14.3-0ub i386         Network Security Service librarie
ii  libnuma1       2.0.8-1      i386         Libraries for controlling NUMA po
ii  libnux-4.0-0   4.0.1daily13 i386         Visual rendering toolkit for real
ii  libnux-4.0-com 4.0.1daily13 i386         Visual rendering toolkit for real
ii  liboauth0:i386 1.0.1-0ubunt i386         C library for implementing OAuth 
ii  libobrender27  3.5.0-7      i386         rendering library for openbox the
ii  libobt0        3.5.0-7      i386         parsing library for openbox
rc  libofa0        0.9.3-5      i386         Library for acoustic fingerprinti
ii  libogg0:i386   1.3.0-4      i386         Ogg bitstream library
ii  libonig2       5.9.1-1      i386         Oniguruma regular expressions lib
ii  liboobs-1-5    3.0.0-1      i386         GObject based interface to system
rc  libopenal-data 1:1.14-4ubun all          Software implementation of the Op
rc  libopenal1:i38 1:1.14-4ubun i386         Software implementation of the Op
rc  libopencore-am 0.1.3-2      i386         Adaptive Multi Rate speech codec 
rc  libopencore-am 0.1.3-2      i386         Adaptive Multi-Rate - Wideband sp
rc  libopenexr6:i3 1.6.1-7      i386         runtime files for the OpenEXR ima
ii  libopenobex1   1.5-2build2  i386         OBEX protocol library
ii  libopenvg1-mes 9.1.1-0ubunt i386         free implementation of the OpenVG
ii  libopts25      1:5.17.1-1ub i386         automated option processing libra
ii  libopus0       1.0.1-0ubunt i386         Opus codec runtime library
rc  liborbit2:i386 1:2.14.19-0. i386         libraries for ORBit2 - a CORBA OR
ii  liborc-0.4-0:i 1:0.4.17-1   i386         Library of Optimized Inner Loops 
ii  libots0        0.5.0-2.1    i386         Open Text Summarizer (library)
ii  libp11-kit-gno 3.6.3-0ubunt i386         GNOME keyring module for the PKCS
ii  libp11-kit0:i3 0.14-1       i386         Library for loading and coordinat
ii  libpackagekit- 0.7.6-3ubunt i386         Library for accessing PackageKit 
ii  libpam-ck-conn 0.4.5-3.1ubu i386         ConsoleKit PAM module
ii  libpam-gnome-k 3.6.3-0ubunt i386         PAM module to unlock the GNOME ke
ii  libpam-modules 1.1.3-8ubunt i386         Pluggable Authentication Modules 
ii  libpam-modules 1.1.3-8ubunt i386         Pluggable Authentication Modules 
ii  libpam-runtime 1.1.3-8ubunt all          Runtime support for the PAM libra
ii  libpam-xdg-sup 0.2-0ubuntu2 i386         PAM module for XDG_RUNTIME_DIR su
ii  libpam0g:i386  1.1.3-8ubunt i386         Pluggable Authentication Modules 
ii  libpanel-apple 1:3.6.2-0ubu i386         library for GNOME Panel applets
ii  libpango-perl  1.224-1      i386         Perl module to layout and render 
ii  libpango1.0-0: 1.32.5-0ubun i386         Layout and rendering of internati
ii  libpangomm-1.4 2.28.4-1ubun i386         C++ Wrapper for pango (shared lib
ii  libpaper-utils 1.1.24+nmu2u i386         library for handling paper charac
ii  libpaper1:i386 1.1.24+nmu2u i386         library for handling paper charac
ii  libparted0debi 2.3-11ubuntu i386         disk partition manipulator - shar
ii  libpcap0.8:i38 1.3.0-1      i386         system interface for user-level p
ii  libpci3:i386   1:3.1.9-6ubu i386         Linux PCI Utilities (shared libra
ii  libpciaccess0: 0.13.1-2     i386         Generic PCI access library for X
ii  libpcre3:i386  1:8.31-2     i386         Perl 5 Compatible Regular Express
ii  libpcsclite1:i 1.8.6-3ubunt i386         Middleware to access a smart card
rc  libpeas-1.0-0  1.6.2-0ubunt i386         Application plugin library
ii  libperl5.14    5.14.2-21    i386         shared Perl library
ii  libpipeline1:i 1.2.2-2      i386         pipeline manipulation library
ii  libpisock9     0.12.5-5ubun i386         library for communicating with a 
ii  libpixman-1-0: 0.28.2-0ubun i386         pixel-manipulation library for X 
ii  libplist1      1.8-2        i386         Library for handling Apple binary
ii  libplymouth2:i 0.8.8-0ubunt i386         graphical boot animation and logg
ii  libpng12-0:i38 1.2.49-1ubun i386         PNG library - runtime
ii  libpolkit-agen 0.105-1ubunt i386         PolicyKit Authentication Agent AP
ii  libpolkit-back 0.105-1ubunt i386         PolicyKit backend API
ii  libpolkit-gobj 0.105-1ubunt i386         PolicyKit Authorization API
ii  libpoppler-gli 0.20.5-1ubun i386         PDF rendering library (GLib-based
ii  libpoppler28:i 0.20.5-1ubun i386         PDF rendering library
ii  libpopt0:i386  1.16-7ubuntu i386         lib for parsing cmdline parameter
ii  libportaudio2: 19+svn201111 i386         Portable audio I/O - shared libra
ii  libpostproc52: 6:0.8.6-1ubu i386         Libav video postprocessing librar
ii  libppl-c4:i386 1.0-1ubuntu2 i386         Parma Polyhedra Library (C interf
ii  libppl12:i386  1.0-1ubuntu2 i386         Parma Polyhedra Library (runtime 
ii  libprocps0:i38 1:3.3.3-2ubu i386         library for accessing process inf
ii  libprotobuf7   2.4.1-3ubunt i386         protocol buffers C++ library
ii  libproxy1:i386 0.4.11-0ubun i386         automatic proxy configuration man
rc  libpst4:i386   0.6.54-4.1   i386         library for reading Microsoft Out
ii  libpth20       2.0.7-16ubun i386         The GNU Portable Threads
ii  libpulse-mainl 1:3.0-0ubunt i386         PulseAudio client libraries (glib
ii  libpulse0:i386 1:3.0-0ubunt i386         PulseAudio client libraries
ii  libpulsedsp:i3 1:3.0-0ubunt i386         PulseAudio OSS pre-load library
ii  libpurple0     1:2.10.7-0ub i386         multi-protocol instant messaging 
ii  libpwquality1  1.1.1-1      i386         library for password quality chec
ii  libpython-stdl 2.7.4-0ubunt i386         interactive high-level object-ori
ii  libpython2.7:i 2.7.4-2ubunt i386         Shared Python runtime library (ve
ii  libpython2.7-m 2.7.4-2ubunt i386         Minimal subset of the Python lang
ii  libpython2.7-s 2.7.4-2ubunt i386         Interactive high-level object-ori
ii  libpython3-std 3.3.1-0ubunt i386         interactive high-level object-ori
ii  libpython3.3:i 3.3.1-1ubunt i386         Shared Python runtime library (ve
ii  libpython3.3-m 3.3.1-1ubunt i386         Minimal subset of the Python lang
ii  libpython3.3-s 3.3.1-1ubunt i386         Interactive high-level object-ori
rc  libqjson0:i386 0.8.1-1      i386         Qt-based library that maps JSON d
ii  libqpdf10:i386 4.0.1-2      i386         runtime library for PDF transform
ii  libqt4-dbus:i3 4:4.8.4+dfsg i386         Qt 4 D-Bus module
ii  libqt4-declara 4:4.8.4+dfsg i386         Qt 4 Declarative module
ii  libqt4-network 4:4.8.4+dfsg i386         Qt 4 network module
rc  libqt4-opengl: 4:4.8.4+dfsg i386         Qt 4 OpenGL module
ii  libqt4-script: 4:4.8.4+dfsg i386         Qt 4 script module
ii  libqt4-sql:i38 4:4.8.4+dfsg i386         Qt 4 SQL module
ii  libqt4-sql-mys 4:4.8.4+dfsg i386         Qt 4 MySQL database driver
ii  libqt4-sql-sql 4:4.8.4+dfsg i386         Qt 4 SQLite 3 database driver
rc  libqt4-test:i3 4:4.8.4+dfsg i386         Qt 4 test module
ii  libqt4-xml:i38 4:4.8.4+dfsg i386         Qt 4 XML module
ii  libqt4-xmlpatt 4:4.8.4+dfsg i386         Qt 4 XML patterns module
ii  libqtcore4:i38 4:4.8.4+dfsg i386         Qt 4 core module
ii  libqtgui4:i386 4:4.8.4+dfsg i386         Qt 4 GUI module
rc  libqtwebkit4:i 2.3.0-0ubunt i386         Web content engine library for Qt
ii  libquadmath0:i 4.7.3-1ubunt i386         GCC Quad-Precision Math Library
rc  libquvi7:i386  0.4.1-1      i386         library for parsing video downloa
ii  libraptor2-0   2.0.8-2      i386         Raptor 2 RDF syntax library
ii  librasqal3     0.9.29-1     i386         Rasqal RDF query library
ii  libraw1394-11: 2.0.9-1      i386         library for direct access to IEEE
rc  libraw5:i386   0.14.7-0ubun i386         raw image decoder library
ii  librdf0        1.0.16-1     i386         Redland Resource Description Fram
ii  libreadline5:i 5.2+dfsg-1   i386         GNU readline and history librarie
ii  libreadline6:i 6.2-9ubuntu1 i386         GNU readline and history librarie
ii  libresid-build 2.1.1-14     i386         SID chip emulation class based on
ii  librest-0.7-0: 0.7.90-0ubun i386         REST service access library
rc  librhythmbox-c 2.98-0ubuntu i386         support library for the rhythmbox
ii  libroken18-hei 1.6~git20120 i386         Heimdal Kerberos - roken support 
ii  librsvg2-2:i38 2.36.4-1     i386         SAX-based renderer library for SV
ii  librsvg2-commo 2.36.4-1     i386         SAX-based renderer library for SV
ii  librtmp0:i386  2.4+20111222 i386         toolkit for RTMP streams (shared 
rc  librygel-core- 0.18.0-1     i386         GNOME UPnP/DLNA services - core l
rc  librygel-rende 0.18.0-1     i386         GNOME UPnP/DLNA services - render
rc  librygel-rende 0.18.0-1     i386         GNOME UPnP/DLNA services - render
rc  librygel-serve 0.18.0-1     i386         GNOME UPnP/DLNA services - server
ii  libsamplerate0 0.1.8-5      i386         Audio sample rate conversion libr
ii  libsane:i386   1.0.23-0ubun i386         API library for scanners
ii  libsane-common 1.0.23-0ubun i386         API library for scanners -- docum
ii  libsasl2-2:i38 2.1.25.dfsg1 i386         Cyrus SASL - authentication abstr
ii  libsasl2-modul 2.1.25.dfsg1 i386         Cyrus SASL - pluggable authentica
ii  libschroedinge 1.0.11-2     i386         library for encoding/decoding of 
ii  libsdl1.2debia 1.2.15-5ubun i386         Simple DirectMedia Layer
ii  libsecret-1-0: 0.15-0ubuntu i386         Secret store
ii  libsecret-comm 0.15-0ubuntu all          Secret store (common files)
ii  libselinux1:i3 2.1.9-5ubunt i386         SELinux runtime shared libraries
ii  libsemanage-co 2.1.6-6ubunt all          Common files for SELinux policy m
ii  libsemanage1:i 2.1.6-6ubunt i386         SELinux policy management library
ii  libsepol1:i386 2.1.4-3ubunt i386         SELinux library for manipulating 
ii  libshout3:i386 2.3.1-1ubunt i386         MP3/Ogg Vorbis broadcast streamin
rc  libsidplay1    1.36.59-5    i386         SID (MOS 6581) emulation library
ii  libsidplay2    2.1.1-14     i386         SID (MOS 6581) emulation library
ii  libsigc++-2.0- 2.2.10-0.2   i386         type-safe Signal Framework for C+
rc  libsignon-exte 8.49-0ubuntu i386         Single Sign On framework
rc  libsignon-glib 1.9-0ubuntu1 i386         library for signond
rc  libsignon-plug 8.49-0ubuntu i386         Single Sign On framework
rc  libsignon-qt1  8.49-0ubuntu i386         Single Sign On framework
ii  libsigsegv2    2.9-4ubuntu3 i386         Library for handling page faults 
ii  libslang2:i386 2.2.4-15ubun i386         S-Lang programming library - runt
rc  libslv2-9      0.6.6+dfsg1- i386         library for simple use of LV2 plu
ii  libsm6:i386    2:1.2.1-2    i386         X11 Session Management library
ii  libsmbclient:i 2:3.6.9-1ubu i386         shared library for communication 
ii  libsndfile1:i3 1.0.25-5     i386         Library for reading/writing audio
ii  libsocket6-per 0.23-1build3 i386         Perl extensions for IPv6
rc  libsofia-sip-u 1.12.11+2011 i386         Sofia-SIP library glib/gobject in
rc  libsofia-sip-u 1.12.11+2011 i386         Sofia-SIP library runtime
ii  libsoundtouch0 1.7.1-1      i386         Sound stretching library
ii  libsoup-gnome2 2.40.3-0ubun i386         HTTP library implementation in C 
ii  libsoup2.4-1:i 2.40.3-0ubun i386         HTTP library implementation in C 
ii  libspandsp2    0.0.6~pre20- i386         Telephony signal processing libra
ii  libspectre1:i3 0.2.7-2      i386         Library for rendering PostScript 
ii  libspeex1:i386 1.2~rc1-7ubu i386         The Speex codec runtime library
ii  libspeexdsp1:i 1.2~rc1-7ubu i386         The Speex extended runtime librar
ii  libsqlite3-0:i 3.7.15.2-1ub i386         SQLite 3 shared library
ii  libss2:i386    1.42.5-1ubun i386         command-line interface parsing li
ii  libssl1.0.0:i3 1.0.1c-4ubun i386         SSL shared libraries
ii  libstartup-not 0.12-2       i386         library for program launch feedba
ii  libstdc++6:i38 4.7.3-1ubunt i386         GNU Standard C++ Library v3
ii  libstdc++6-4.7 4.7.3-1ubunt i386         GNU Standard C++ Library v3 (deve
ii  libswitch-perl 2.16-2       all          switch statement for Perl
ii  libswscale2:i3 6:0.8.6-1ubu i386         Libav video scaling library
ii  libsysfs2:i386 2.1.0+repack i386         interface library to sysfs
ii  libsystemd-dae 198-0ubuntu1 i386         systemd utility library
ii  libt1-5        5.1.2-3.6    i386         Type 1 font rasterizer library - 
ii  libtag1-vanill 1.8-1        i386         audio meta-data library - vanilla
ii  libtag1c2a:i38 1.8-1        i386         audio meta-data library
ii  libtalloc2:i38 2.0.7+git201 i386         hierarchical pool based memory al
ii  libtasn1-3:i38 2.14-2       i386         Manage ASN.1 structures (runtime)
ii  libtdb1:i386   1.2.10-2ubun i386         Trivial Database - shared library
rc  libtelepathy-f 0.6.0-1      i386         Glue library between telepathy an
ii  libtelepathy-g 0.20.2-0ubun i386         Telepathy framework - GLib librar
rc  libtelepathy-l 0.8.0-0ubunt i386         Telepathy logger service - utilit
ii  libtext-charwi 0.04-7build2 i386         get display widths of characters 
ii  libtext-iconv- 1.7-5build1  i386         converts between character sets i
ii  libtext-wrapi1 0.06-7       all          internationalized substitute of T
ii  libthai-data   0.1.19-1     all          Data files for Thai language supp
ii  libthai0:i386  0.1.19-1     i386         Thai language support library
ii  libtheora0:i38 1.1.1+dfsg.1 i386         The Theora Video Compression Code
ii  libtidy-0.99-0 20091223cvs- i386         HTML syntax checker and reformatt
ii  libtiff5:i386  4.0.2-4ubunt i386         Tag Image File Format (TIFF) libr
ii  libtimedate-pe 1.2000-1     all          collection of modules to manipula
ii  libtimezonemap 0.4.0        i386         GTK+3 timezone map widget
ii  libtinfo5:i386 5.9-10ubuntu i386         shared low-level terminfo library
rc  libtotem-plpar 3.4.4-1      i386         Totem Playlist Parser library - r
rc  libtotem0      3.6.3-0ubunt i386         Main library for the Totem media 
rc  libtracker-ext 0.14.5-1ubun i386         tracker extractor library
rc  libtracker-min 0.14.5-1ubun i386         tracker data miner library
rc  libtracker-spa 0.14.5-1ubun i386         metadata database, indexer and se
ii  libts-0.0-0:i3 1.0-11       i386         touch screen library
rc  libtwolame0    0.3.13-1buil i386         MPEG Audio Layer 2 encoding libra
ii  libudev1:i386  198-0ubuntu1 i386         libudev shared library
ii  libudisks2-0:i 2.1.0-2      i386         GObject based library to access u
rc  libumfpack5.4. 1:3.4.0-3ubu i386         sparse LU factorization library
ii  libuniconf4.6  4.6.1-6      i386         C++ network libraries for rapid a
rc  libunistring0: 0.9.3-5build i386         Unicode string library for C
ii  libunity-commo 6.90.2daily1 all          binding to get places into the la
ii  libunity-core- 7.0.0daily13 i386         Core library for the Unity interf
ii  libunity-misc4 4.0.5daily13 i386         Miscellaneous functions for Unity
ii  libunity-proto 6.90.2daily1 i386         binding to get places into the la
ii  libunity-webap 2.5.0~daily1 i386         Web Apps integration with the Uni
ii  libunity9:i386 6.90.2daily1 i386         binding to get places into the la
ii  libupower-glib 0.9.20-1     i386         abstraction for power management 
ii  liburi-perl    1.60-1       all          module to manipulate and access U
ii  libusb-0.1-4:i 2:0.1.12-23+ i386         userspace USB programming library
ii  libusb-1.0-0:i 2:1.0.12-2ub i386         userspace USB programming library
ii  libusbmuxd2    1.0.8-1ubunt i386         USB multiplexor daemon for iPhone
ii  libustr-1.0-1: 1.0.4-3ubunt i386         Micro string library: shared libr
ii  libutempter0   1.1.5-4build i386         A privileged helper for utmp/wtmp
ii  libuuid1:i386  2.20.1-5.1ub i386         Universally Unique ID library
ii  libv4l-0:i386  0.8.9-1      i386         Collection of video4linux support
ii  libv4lconvert0 0.8.9-1      i386         Video4linux frame format conversi
ii  libva1:i386    1.0.15-4buil i386         Video Acceleration (VA) API for L
ii  libvdpau1:i386 0.4.1-8      i386         Video Decode and Presentation API
rc  libvisio-0.0-0 0.0.25-1     i386         library for parsing the visio fil
ii  libvisual-0.4- 0.4.0-5      i386         Audio visualization framework
ii  libvo-aacenc0: 0.1.2-1      i386         VisualOn AAC encoder library
ii  libvo-amrwbenc 0.1.2-1      i386         VisualOn AMR-WB encoder library
ii  libvorbis0a:i3 1.3.2-1.3    i386         The Vorbis General Audio Compress
ii  libvorbisenc2: 1.3.2-1.3    i386         The Vorbis General Audio Compress
ii  libvorbisfile3 1.3.2-1.3    i386         The Vorbis General Audio Compress
ii  libvpx1:i386   1.1.0-1      i386         VP8 video codec (shared library)
ii  libvte-2.90-9  1:0.34.2-0ub i386         Terminal emulator widget for GTK+
ii  libvte-2.90-co 1:0.34.2-0ub all          Terminal emulator widget for GTK+
ii  libvte-common  1:0.28.2-5ub all          Terminal emulator widget for GTK+
ii  libvte9        1:0.28.2-5ub i386         Terminal emulator widget for GTK+
ii  libwacom-commo 0.7-1        all          Wacom model feature query library
ii  libwacom2:i386 0.7-1        i386         Wacom model feature query library
ii  libwavpack1:i3 4.60.1-3     i386         audio codec (lossy and lossless) 
ii  libwayland0:i3 1.0.5-0ubunt i386         wayland compositor infrastructure
ii  libwbclient0:i 2:3.6.9-1ubu i386         Samba winbind client library
rc  libwebkitgtk-1 1.10.2-0ubun i386         Web content engine library for GT
ii  libwebkitgtk-3 1.10.2-0ubun i386         Web content engine library for GT
ii  libwebkitgtk-3 1.10.2-0ubun all          Web content engine library for GT
ii  libwhoopsie0   0.2.15       i386         Ubuntu error tracker submission -
rc  libwildmidi-co 0.2.3.4-2.1u all          software MIDI player configuratio
rc  libwildmidi1:i 0.2.3.4-2.1u i386         software MIDI player library
ii  libwind0-heimd 1.6~git20120 i386         Heimdal Kerberos - stringprep imp
ii  libwmf0.2-7:i3 0.2.8.4-10.3 i386         Windows metafile conversion libra
ii  libwnck-3-0:i3 3.4.5-0ubunt i386         Window Navigator Construction Kit
ii  libwnck-3-comm 3.4.5-0ubunt all          Window Navigator Construction Kit
ii  libwnck-common 1:2.30.7-0ub all          Window Navigator Construction Kit
ii  libwnck22      1:2.30.7-0ub i386         Window Navigator Construction Kit
ii  libwpd-0.9-9   0.9.6-2      i386         Library for handling WordPerfect 
ii  libwpg-0.2-2   0.2.1-1build i386         WordPerfect graphics import/conve
ii  libwps-0.2-2   0.2.7-1      i386         Works text file format import fil
ii  libwrap0:i386  7.6.q-24     i386         Wietse Venema's TCP wrappers libr
ii  libwv-1.2-4:i3 1.2.9-3      i386         Library for accessing Microsoft W
ii  libwvstreams4. 4.6.1-6      i386         C++ network libraries for rapid a
ii  libwvstreams4. 4.6.1-6      i386         C++ network libraries for rapid a
ii  libwww-perl    6.04-1       all          simple and consistent interface t
ii  libwww-robotru 6.01-1       all          database of robots.txt-derived pe
ii  libx11-6:i386  2:1.5.0-1ubu i386         X11 client-side library
ii  libx11-data    2:1.5.0-1ubu all          X11 client-side library
ii  libx11-xcb1:i3 2:1.5.0-1ubu i386         Xlib/XCB interface library
rc  libx264-123:i3 2:0.123.2189 i386         x264 video coding library
ii  libxapian22    1.2.12-2     i386         Search engine library
ii  libxatracker1: 9.1.1-0ubunt i386         X acceleration library -- runtime
ii  libxau6:i386   1:1.0.7-1    i386         X11 authorisation library
ii  libxaw7:i386   2:1.0.10-2   i386         X11 Athena Widget library
ii  libxcb-dri2-0: 1.8.1-2ubunt i386         X C Binding, dri2 extension
ii  libxcb-glx0:i3 1.8.1-2ubunt i386         X C Binding, glx extension
ii  libxcb-render0 1.8.1-2ubunt i386         X C Binding, render extension
ii  libxcb-shape0: 1.8.1-2ubunt i386         X C Binding, shape extension
ii  libxcb-shm0:i3 1.8.1-2ubunt i386         X C Binding, shm extension
ii  libxcb-util0:i 0.3.8-2build i386         utility libraries for X C Binding
ii  libxcb-xfixes0 1.8.1-2ubunt i386         X C Binding, xfixes extension
ii  libxcb1:i386   1.8.1-2ubunt i386         X C Binding
ii  libxcomposite1 1:0.4.3-2bui i386         X11 Composite extension library
ii  libxcursor1:i3 1:1.1.13-1   i386         X cursor management library
ii  libxdamage1:i3 1:1.1.3-2bui i386         X11 damaged region extension libr
ii  libxdmcp6:i386 1:1.1.1-1    i386         X11 Display Manager Control Proto
ii  libxext6:i386  2:1.3.1-2    i386         X11 miscellaneous extension libra
ii  libxfce4ui-1-0 4.10.0-1     i386         widget library for Xfce
ii  libxfce4util-c 4.10.0-1     all          common files for libxfce4util
ii  libxfce4util6  4.10.0-1     i386         Utility functions library for Xfc
ii  libxfconf-0-2  4.10.0-1     i386         Client library for Xfce4 configur
ii  libxfixes3:i38 1:5.0-4ubunt i386         X11 miscellaneous 'fixes' extensi
ii  libxfont1      1:1.4.5-2    i386         X11 font rasterisation library
ii  libxft2:i386   2.3.1-1      i386         FreeType-based font drawing libra
ii  libxi6:i386    2:1.6.99.1-0 i386         X11 Input extension library
ii  libxinerama1:i 2:1.1.2-1    i386         X11 Xinerama extension library
ii  libxkbcommon0: 0.2.0-0ubunt i386         library interface to the XKB comp
ii  libxkbfile1:i3 1:1.0.8-1    i386         X11 keyboard file manipulation li
ii  libxklavier16  5.2.1-1ubunt i386         X Keyboard Extension high-level A
ii  libxml-parser- 2.41-1build2 i386         Perl module for parsing XML files
ii  libxml-twig-pe 1:3.39-1ubun all          Perl module for processing huge X
ii  libxml2:i386   2.9.0+dfsg1- i386         GNOME XML library
ii  libxmu6:i386   2:1.1.1-1    i386         X11 miscellaneous utility library
ii  libxmuu1:i386  2:1.1.1-1    i386         X11 miscellaneous micro-utility l
ii  libxp6:i386    1:1.0.1-2bui i386         X Printing Extension (Xprint) cli
ii  libxpm4:i386   1:3.5.10-1   i386         X11 pixmap library
ii  libxrandr2:i38 2:1.4.0-1ubu i386         X11 RandR extension library
ii  libxrender1:i3 1:0.9.7-1    i386         X Rendering Extension client libr
ii  libxres1:i386  2:1.0.6-1    i386         X11 Resource extension library
ii  libxslt1.1:i38 1.1.27-1ubun i386         XSLT 1.0 processing library - run
ii  libxss1:i386   1:1.2.2-1    i386         X11 Screen Saver extension librar
ii  libxt6:i386    1:1.1.3-1    i386         X11 toolkit intrinsics library
ii  libxtst6:i386  2:1.2.1-1    i386         X11 Testing -- Record extension l
ii  libxv1:i386    2:1.0.7-1    i386         X11 Video extension library
ii  libxvidcore4:i 2:1.3.2-9    i386         Open source MPEG-4 video codec (l
ii  libxvmc1       2:1.0.7-1ubu i386         X11 Video extension library
ii  libxxf86dga1:i 2:1.1.3-2    i386         X11 Direct Graphics Access extens
ii  libxxf86vm1:i3 1:1.1.2-1    i386         X11 XFree86 video mode extension 
ii  libyajl2       2.0.4-2      i386         Yet Another JSON Library
ii  libyelp0       3.6.2-0ubunt i386         Library for the GNOME help browse
rc  libytnef0      1.5-4build1  i386         improved decoder for application/
rc  libzapojit-0.0 0.0.2-2      i386         Library for accessing SkyDrive an
ii  libzbar0       0.10+doc-8   i386         bar code scanner and decoder (lib
ii  libzeitgeist-1 0.3.18-1ubun i386         library to access Zeitgeist - sha
ii  libzephyr4     3.0.2-2      i386         Project Athena's notification ser
rc  libzvbi0:i386  0.2.33-6     i386         Vertical Blanking Interval decode
ii  lightdm        1.6.0-0ubunt i386         Display Manager
ii  lightdm-gtk-gr 1.5.1-0ubunt i386         LightDM GTK+ Greeter
ii  linux-firmware 1.106        all          Firmware for Linux kernel drivers
ii  linux-generic  3.8.0.19.35  i386         Complete Generic Linux kernel and
ii  linux-headers- 3.8.0-19.29  all          Header files related to Linux ker
ii  linux-headers- 3.8.0-19.29  i386         Linux kernel headers for version 
ii  linux-headers- 3.8.0.19.35  i386         Generic Linux kernel headers
ii  linux-image-3. 3.8.0-19.29  i386         Linux kernel image for version 3.
ii  linux-image-ex 3.8.0-19.29  i386         Linux kernel image for version 3.
ii  linux-image-ge 3.8.0.19.35  i386         Generic Linux kernel image
ii  linux-libc-dev 3.8.0-19.30  i386         Linux Kernel Headers for developm
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
ii  locales        2.13+git2012 all          common files for locale support
ii  lockfile-progs 0.1.17       i386         Programs for locking and unlockin
ii  login          1:4.1.5.1-1u i386         system login tools
ii  logrotate      3.8.3-3ubunt i386         Log rotation utility
ii  lsb-base       4.0-0ubuntu2 all          Linux Standard Base 4.0 init scri
ii  lsb-release    4.0-0ubuntu2 all          Linux Standard Base version repor
ii  lshw           02.16-1      i386         information about hardware config
ii  lsof           4.86+dfsg-1u i386         Utility to list open files
ii  ltrace         0.5.3-2.1ubu i386         Tracks runtime library calls in d
ii  lubuntu-artwor 0.38.1       all          artwork for Lubuntu
ii  lubuntu-artwor 0.38.1       all          artwork for Lubuntu - 13.04 versi
ii  lubuntu-defaul 0.31         all          Set default session to Lubuntu
ii  lubuntu-defaul 0.31         all          default settings for Lubuntu
ii  lubuntu-icon-t 0.38.1       all          icon theme for Lubuntu
ii  lubuntu-lxpane 0.38.1       all          panel specific icons for Lubuntu 
ii  lxappearance   0.5.2-1ubunt i386         LXDE GTK+ theme switcher
ii  lxappearance-o 0.2.0-4ubunt i386         LXDE GTK+ theme switcher (plugin)
ii  lxinput        0.3.2-1      i386         LXDE keyboard and mouse configura
ii  lxkeymap       0.8.0~bzr25+ all          Application that allows to easily
ii  lxlauncher     0.2.2-3ubunt i386         LXDE launcher for netbooks
ii  lxmenu-data    0.1.2-2      all          LXDE freedesktop.org menu specifi
ii  lxpanel        0.5.12-0ubun i386         LXDE panel
ii  lxpanel-indica 0.5.12-0ubun i386         lxpanel indicator applet
ii  lxrandr        0.1.2-3      i386         LXDE monitor configuration tool
ii  lxsession      0.4.9.2~git2 i386         default session manager for LXDE
ii  lxsession-data 0.4.9.2~git2 all          Common files for lxsession
ii  lxsession-edit 0.4.9.2~git2 i386         configure what application start 
ii  lxshortcut     0.1.2-3      i386         LXDE application shortcut editor
ii  lxtask         0.1.4-3ubunt i386         LXDE task manager
ii  lxterminal     0.1.11-4ubun i386         LXDE terminal emulator
ii  m4             1.4.16-5     i386         a macro processing language
ii  make           3.81-8.2ubun i386         An utility for Directing compilat
ii  makedev        2.3.1-92ubun all          creates device files in /dev
ii  man-db         2.6.3-3      i386         on-line manual pager
ii  mawk           1.3.3-17ubun i386         a pattern scanning and text proce
ii  memtest86+     4.20-1.1ubun i386         thorough real-mode memory tester
ii  metacity       1:2.34.13-0u i386         lightweight GTK+ window manager
ii  metacity-commo 1:2.34.13-0u all          shared files for the Metacity win
ii  mime-support   3.52-2ubuntu all          MIME files 'mime.types' & 'mailca
ii  mlocate        0.25-0ubuntu i386         quickly find files on the filesys
ii  mobile-broadba 20130312-1   all          database of mobile broadband serv
ii  modemmanager   0.6.0.0.real i386         D-Bus service for managing modems
ii  module-init-to 9-3ubuntu1   all          transitional dummy package (modul
rc  mono-runtime   2.10.8.1-5ub i386         Mono runtime
ii  mount          2.20.1-5.1ub i386         Tools for mounting and manipulati
ii  mountall       2.48build1   i386         filesystem mounting tool
ii  mousetweaks    3.6.0-0ubunt i386         mouse accessibility enhancements 
ii  mplayer2       2.0-554-gf63 i386         next generation movie player for 
ii  mtr-tiny       0.82-3ubuntu i386         Full screen ncurses traceroute to
ii  multiarch-supp 2.17-0ubuntu i386         Transitional package to ensure mu
ii  mysql-common   5.5.31-0ubun all          MySQL database common files, e.g.
ii  nano           2.2.6-1ubunt i386         small, friendly text editor inspi
ii  nautilus-data  1:3.6.3-0ubu all          data files for nautilus
ii  ncurses-base   5.9-10ubuntu all          basic terminal type definitions
ii  ncurses-bin    5.9-10ubuntu i386         terminal-related programs and man
ii  net-tools      1.60-24.2ubu i386         The NET-3 networking toolkit
ii  netbase        5.0ubuntu1   all          Basic TCP/IP networking system
ii  netcat-openbsd 1.105-7ubunt i386         TCP/IP swiss army knife
ii  network-manage 0.9.8.0-0ubu i386         network management framework (dae
ii  network-manage 0.9.8.0-1ubu i386         network management framework (GNO
ii  notification-d 0.7.6-1      i386         daemon for displaying passive pop
ii  ntfs-3g        1:2013.1.13- i386         read/write NTFS driver for FUSE
ii  ntp            1:4.2.6.p5+d i386         Network Time Protocol daemon and 
ii  ntpdate        1:4.2.6.p5+d i386         client for setting system time fr
ii  nux-tools      4.0.1daily13 i386         Visual rendering toolkit for real
ii  obconf         1:2.0.3+2011 i386         preferences manager for Openbox w
ii  obex-data-serv 0.4.6-0ubunt i386         D-Bus service for OBEX client and
ii  obexd-client   0.46-1ubuntu i386         D-Bus OBEX client
ii  openbox        3.5.0-7      i386         standards compliant, fast, light-
rc  openjdk-7-jre- 7u21-2.3.9-1 i386         OpenJDK Java runtime, using Hotsp
ii  openprinting-p 20130308-0ub all          OpenPrinting printer support - Po
ii  openssh-client 1:6.1p1-4    i386         secure shell (SSH) client, for se
ii  openssl        1.0.1c-4ubun i386         Secure Socket Layer (SSL) binary 
ii  os-prober      1.57ubuntu1  i386         utility to detect other OSes on a
ii  packagekit     0.7.6-3ubunt i386         Provides a package management ser
ii  packagekit-bac 0.7.6-3ubunt i386         APT backend for PackageKit
ii  packagekit-too 0.7.6-3ubunt i386         Provides PackageKit command-line 
ii  parted         2.3-11ubuntu i386         disk partition manipulator
ii  passwd         1:4.1.5.1-1u i386         change and administer password an
ii  patch          2.6.1-3ubunt i386         Apply a diff file to an original
ii  pciutils       1:3.1.9-6ubu i386         Linux PCI Utilities
ii  pcmanfm        1.1.0-0ubunt i386         extremely fast and lightweight fi
ii  perl           5.14.2-21    i386         Larry Wall's Practical Extraction
ii  perl-base      5.14.2-21    i386         minimal Perl system
ii  perl-modules   5.14.2-21    all          Core Perl modules
ii  pidgin-data    1:2.10.7-0ub all          multi-protocol instant messaging 
ii  pidgin-microbl 0.3.0-3      i386         Microblogging plugins for Pidgin
ii  plymouth       0.8.8-0ubunt i386         graphical boot animation and logg
ii  plymouth-label 0.8.8-0ubunt i386         graphical boot animation and logg
ii  plymouth-theme 0.38.1       all          plymouth theme for Lubuntu
ii  plymouth-theme 0.38.1       all          plymouth text theme for Lubuntu
ii  plymouth-theme 0.8.8-0ubunt i386         graphical boot animation and logg
ii  pm-utils       1.4.1-9git1  all          utilities and scripts for power m
ii  policykit-1    0.105-1ubunt i386         framework for managing administra
ii  policykit-1-gn 0.105-1ubunt i386         GNOME authentication agent for Po
ii  poppler-data   0.4.6-2      all          encoding data for the poppler PDF
ii  poppler-utils  0.20.5-1ubun i386         PDF utilities (based on Poppler)
ii  popularity-con 1.56ubuntu1  all          Vote for your favourite packages 
ii  powermgmt-base 1.31build1   i386         Common utils and configs for powe
ii  ppp            2.4.5-5.1ubu i386         Point-to-Point Protocol (PPP) - d
ii  pppconfig      2.3.19ubuntu all          A text menu based utility for con
ii  pppoeconf      1.20ubuntu1  all          configures PPPoE/ADSL connections
ii  printer-driver 5.2.9-1ubunt i386         printer drivers for CUPS
ii  printer-driver 1.13+nondbs- i386         printer driver for HP-GDI printer
ii  procps         1:3.3.3-2ubu i386         /proc file system utilities
ii  psmisc         22.20-1ubunt i386         utilities that use the proc file 
ii  pulseaudio     1:3.0-0ubunt i386         PulseAudio sound server
ii  pulseaudio-mod 1:3.0-0ubunt i386         X11 module for PulseAudio sound s
ii  pulseaudio-uti 1:3.0-0ubunt i386         Command line tools for the PulseA
ii  python         2.7.4-0ubunt i386         interactive high-level object-ori
ii  python-appindi 12.10.1daily i386         Python bindings for libappindicat
ii  python-apt     0.8.8ubuntu6 i386         Python interface to libapt-pkg
ii  python-apt-com 0.8.8ubuntu6 all          Python interface to libapt-pkg (l
ii  python-aptdaem 1.0-0ubuntu9 all          Python 2 module for the server an
ii  python-aptdaem 1.0-0ubuntu9 all          Python 2 GTK+ 3 widgets to run an
ii  python-cairo   1.8.8-1ubunt i386         Python bindings for the Cairo vec
ii  python-chardet 2.0.1-2build all          universal character encoding dete
ii  python-cups    1.9.62-0ubun i386         Python bindings for CUPS
ii  python-cupshel 1.3.12+20130 all          Python modules for printer config
ii  python-dbus    1.1.1-1ubunt i386         simple interprocess messaging sys
ii  python-dbus-de 1.1.1-1ubunt all          main loop integration development
ii  python-debian  0.1.21+nmu2u all          Python modules to work with Debia
ii  python-defer   1.0.6-2      all          Small framework for asynchronous 
ii  python-gconf   2.28.1+dfsg- i386         Python bindings for the GConf con
ii  python-gi      3.8.0-2      i386         Python 2.x bindings for gobject-i
ii  python-gi-cair 3.8.0-2      i386         Python Cairo bindings for the GOb
ii  python-gnomeke 2.32.0+dfsg- i386         Python bindings for the GNOME key
ii  python-gobject 3.8.0-2      all          Python 2.x bindings for GObject -
ii  python-gobject 2.28.6-11    i386         deprecated static Python bindings
ii  python-gtk2    2.24.0-3ubun i386         Python bindings for the GTK+ widg
ii  python-ibus    1.4.2-0ubunt all          Intelligent Input Bus - Python su
ii  python-libxml2 2.9.0+dfsg1- i386         Python bindings for the GNOME XML
ii  python-minimal 2.7.4-0ubunt i386         minimal subset of the Python lang
ii  python-notify  0.1.1-3ubunt i386         Python bindings for libnotify
ii  python-package 0.7.6-3ubunt all          PackageKit backend Python binding
ii  python-pkg-res 0.6.34-0ubun all          Package Discovery and Resource Ac
ii  python-pycurl  7.19.0-5ubun i386         Python bindings to libcurl
ii  python-pysqlit 2.6.3-3      i386         Python interface to SQLite 3
ii  python-six     1.2.0-1      all          Python 2 and 3 compatibility libr
ii  python-smbc    1.0.13-0ubun i386         Python bindings for Samba clients
ii  python-support 1.0.15       all          automated rebuilding support for 
ii  python-xapian  1.2.12-2     i386         Xapian search engine interface fo
ii  python-xdg     0.25-2       all          Python 2 library to access freede
ii  python-xklavie 0.4-4        i386         Python binding for libxklavier, a
ii  python-zeitgei 0.9.5-0ubunt all          event logging framework - Python 
ii  python2.7      2.7.4-2ubunt i386         Interactive high-level object-ori
ii  python2.7-mini 2.7.4-2ubunt i386         Minimal subset of the Python lang
ii  python3        3.3.1-0ubunt i386         interactive high-level object-ori
ii  python3-apport 2.9.2-0ubunt all          Python 3 library for Apport crash
ii  python3-apt    0.8.8ubuntu6 i386         Python 3 interface to libapt-pkg
ii  python3-aptdae 1.0-0ubuntu9 all          Python 3 module for the server an
ii  python3-aptdae 1.0-0ubuntu9 all          Python 3 GTK+ 3 widgets to run an
rc  python3-aptdae 1.0-0ubuntu9 all          PackageKit compatibilty for AptDa
ii  python3-comman 0.3ubuntu7   all          Python 3 bindings for command-not
ii  python3-dbus   1.1.1-1ubunt i386         simple interprocess messaging sys
ii  python3-defer  1.0.6-2      all          Small framework for asynchronous 
ii  python3-distup 1:0.192.10   all          manage release upgrades
ii  python3-gdbm:i 3.3.1-0ubunt i386         GNU dbm database support for Pyth
ii  python3-gi     3.8.0-2      i386         Python 3 bindings for gobject-int
ii  python3-minima 3.3.1-0ubunt i386         minimal subset of the Python lang
ii  python3-pkg-re 0.6.34-0ubun all          Package Discovery and Resource Ac
ii  python3-proble 2.9.2-0ubunt all          Python 3 library to handle proble
ii  python3-softwa 0.92.17      all          manage the repositories that you 
ii  python3-update 1:0.186      all          python 3.x module for update-mana
ii  python3-xkit   0.5.0ubuntu1 all          library for the manipulation of x
ii  python3.3      3.3.1-1ubunt i386         Interactive high-level object-ori
ii  python3.3-mini 3.3.1-1ubunt i386         Minimal subset of the Python lang
ii  qdbus          4:4.8.4+dfsg i386         Qt 4 D-Bus tool
ii  qtchooser      0.0.1~git201 i386         Wrapper to select between Qt deve
ii  readline-commo 6.2-9ubuntu1 all          GNU readline and history librarie
ii  resolvconf     1.69ubuntu1  all          name server information handler
ii  rfkill         0.4-2ubuntu1 i386         tool for enabling and disabling w
ii  rsync          3.0.9-4      i386         fast, versatile, remote (and loca
ii  rsyslog        5.8.11-2ubun i386         reliable system and kernel loggin
ii  rtkit          0.10-2build1 i386         Realtime Policy and Watchdog Daem
rc  rygel          0.18.0-1     i386         GNOME UPnP/DLNA services
ii  scrot          0.8-13       i386         command line screen capture utili
rc  seahorse       3.6.3-0ubunt i386         GNOME front end for GnuPG
ii  sed            4.2.1-10ubun i386         The GNU sed stream editor
ii  sensible-utils 0.0.7ubuntu1 all          Utilities for sensible alternativ
ii  session-migrat 0.2          i386         Tool to migrate in user session s
ii  sgml-base      1.26+nmu4ubu all          SGML infrastructure and SGML cata
ii  shared-mime-in 1.1-0ubuntu2 i386         FreeDesktop.org shared MIME datab
rc  signond        8.49-0ubuntu i386         Single Sign On framework
ii  software-prope 0.92.17      all          manage the repositories that you 
ii  software-prope 0.92.17      all          manage the repositories that you 
ii  sound-theme-fr 0.7.pristine all          freedesktop.org sound theme
rc  spamassassin   3.3.2-6ubunt all          Perl-based spam filter using text
ii  ssl-cert       1.0.32       all          simple debconf wrapper for OpenSS
ii  strace         4.5.20-2.3ub i386         A system call tracer
ii  sudo           1.8.6p3-0ubu i386         Provide limited super user privil
ii  system-config- 1.3.12+20130 all          Printer configuration GUI
ii  system-config- 1.3.12+20130 all          Printer configuration GUI
ii  system-tools-b 2.10.2-1ubun i386         System Tools to manage computer c
ii  systemd-servic 198-0ubuntu1 i386         systemd runtime services
ii  systemd-shim   2-0ubuntu1   i386         shim for systemd
ii  sysv-rc        2.88dsf-13.1 all          System-V-like runlevel change mec
ii  sysvinit-utils 2.88dsf-13.1 i386         System-V-like utilities
ii  tar            1.26+dfsg-5  i386         GNU version of the tar archiving 
ii  tcpdump        4.3.0-1ubunt i386         command-line network traffic anal
rc  telepathy-indi 0.3.1daily13 i386         Desktop service to integrate Tele
rc  telepathy-miss 1:5.14.0-0ub i386         management daemon for Telepathy r
ii  telnet         0.17-36build i386         The telnet client
ii  texinfo        4.13a.dfsg.1 i386         Documentation system for on-line 
ii  time           1.7-24       i386         GNU time program for measuring CP
rc  tracker        0.14.5-1ubun i386         metadata database, indexer and se
rc  tracker-gui    0.14.5-1ubun i386         metadata database, indexer and se
rc  tracker-miner- 0.14.5-1ubun i386         metadata database, indexer and se
ii  tsconf         1.0-11       all          touch screen library common files
ii  ttf-dejavu     2.33-3ubuntu all          Metapackage to pull in ttf-dejavu
ii  ttf-dejavu-cor 2.33-3ubuntu all          Vera font family derivate with ad
ii  ttf-dejavu-ext 2.33-3ubuntu all          Vera font family derivate with ad
ii  ttf-ubuntu-fon 0.80-0ubuntu all          Ubuntu Font Family, sans-serif ty
ii  ttf-wqy-microh 0.2.0-beta-1 all          A droid derived Sans-Seri style C
ii  tzdata         2013b-1ubunt all          time zone and daylight-saving tim
ii  ubuntu-drivers 1:0.2.76     i386         Detect and install additional Ubu
ii  ubuntu-extras- 2010.09.27   all          GnuPG keys of the Ubuntu extras a
ii  ubuntu-keyring 2012.05.19   all          GnuPG keys of the Ubuntu archive
ii  ubuntu-release 1:0.192.10   all          manage release upgrades
ii  ubuntu-standar 1.299        i386         The Ubuntu standard system
ii  ubuntu-system- 0.2.4        all          Dbus service to set various syste
ii  ucf            3.0025+nmu3  all          Update Configuration File: preser
ii  udev           175-0ubuntu2 i386         rule-based device node and kernel
ii  udisks2        2.1.0-2      i386         D-BUS service to access and manip
ii  ufw            0.33-0ubuntu all          program for managing a Netfilter 
ii  unattended-upg 0.79.3ubuntu all          automatic installation of securit
ii  unionfs-fuse   0.24-2.2ubun i386         Fuse implementation of unionfs
ii  unity          7.0.0daily13 i386         Interface designed for efficiency
ii  unity-asset-po 0.8.24daily1 all          Unity Assets Pool
ii  unity-common   7.0.0daily13 all          Common files for the Unity interf
ii  unity-services 7.0.0daily13 i386         Services for the Unity interface
ii  unity-webapps- 2.5.0~daily1 i386         Service for Web Apps integration 
rc  uno-libs3      4.0.2-0ubunt i386         LibreOffice UNO runtime environme
ii  unzip          6.0-8ubuntu1 i386         De-archiver for .zip files
ii  upower         0.9.20-1     i386         abstraction for power management
ii  upstart        1.8-0ubuntu1 i386         event-based init daemon
ii  ureadahead     0.100.0-16   i386         Read required files in advance
ii  usb-modeswitch 1.2.3+repack i386         mode switching tool for controlli
ii  usb-modeswitch 20120815-2   all          mode switching data for usb-modes
ii  usbmuxd        1.0.8-1ubunt i386         USB multiplexor daemon for iPhone
ii  usbutils       1:005-3ubunt i386         Linux USB utilities
ii  util-linux     2.20.1-5.1ub i386         Miscellaneous system utilities
ii  uuid-runtime   2.20.1-5.1ub i386         runtime components for the Univer
ii  wget           1.14-1ubuntu i386         retrieves files from the web
ii  whiptail       0.52.14-11ub i386         Displays user-friendly dialog box
ii  whois          5.0.20ubuntu i386         intelligent WHOIS client
ii  whoopsie       0.2.15       i386         Ubuntu error tracker submission
ii  wireless-regdb 2011.04.28-1 all          wireless regulatory database
ii  wireless-tools 30~pre9-8ubu i386         Tools for manipulating Linux Wire
ii  wodim          9:1.1.11-2ub i386         command line CD/DVD writing tool
ii  wpasupplicant  1.0-3ubuntu1 i386         client support for WPA and WPA2 (
ii  wvdial         1.61-4.1     i386         intelligent Point-to-Point Protoc
rc  x11-apps       7.7~3ubuntu1 i386         X applications
ii  x11-common     1:7.7+1ubunt all          X Window System (X.Org) infrastru
rc  x11-session-ut 7.6+2build1  i386         X session utilities
ii  x11-utils      7.7~1ubuntu1 i386         X11 utilities
ii  x11-xkb-utils  7.7~1        i386         X11 XKB utilities
ii  x11-xserver-ut 7.7~3ubuntu2 i386         X server utilities
ii  xauth          1:1.0.7-1ubu i386         X authentication utility
ii  xbitmaps       1.1.1-2      all          Base X bitmaps
ii  xdg-user-dirs  0.14-0ubuntu i386         tool to manage well known user di
ii  xdg-user-dirs- 0.10-0ubuntu i386         tool to manage well known user di
ii  xdg-utils      1.1.0~rc1-2u all          desktop integration utilities fro
ii  xfce-keyboard- 4.10.0-1     all          xfce keyboard shortcuts configura
ii  xfce4-notifyd  0.2.2-3      i386         simple, visually-appealing notifi
ii  xfce4-power-ma 1.2.0-1ubunt i386         power manager for Xfce desktop
ii  xfce4-power-ma 1.2.0-1ubunt all          power manager for Xfce desktop, a
ii  xfconf         4.10.0-1     i386         utilities for managing settings i
ii  xfonts-base    1:1.0.3      all          standard fonts for X
ii  xfonts-encodin 1:1.0.4-1ubu all          Encodings for X.Org fonts
rc  xfonts-mathml  6ubuntu1     all          Type1 Symbol font for MathML
ii  xfonts-utils   1:7.7~1      i386         X Window System font utility prog
rc  xinit          1.3.2-1      i386         X server initialisation tool
ii  xinput         1.6.0-1      i386         Runtime configuration and test of
ii  xkb-data       2.5.1-3ubunt all          X Keyboard Extension (XKB) config
ii  xml-core       0.13+nmu2    all          XML infrastructure and XML catalo
ii  xscreensaver   5.15-2ubuntu i386         Automatic screensaver for X
ii  xscreensaver-d 5.15-2ubuntu i386         data files to be shared among scr
ii  xserver-common 2:1.13.3-0ub all          common files used by various X se
ii  xserver-xephyr 2:1.13.3-0ub i386         nested X server
ii  xserver-xorg   1:7.7+1ubunt i386         X.Org X server
ii  xserver-xorg-c 2:1.13.3-0ub i386         Xorg X server - core server
ii  xserver-xorg-i 1:7.7+1ubunt i386         X.Org X server -- input driver me
ii  xserver-xorg-i 1:2.7.3-0ubu i386         X.Org X server -- evdev input dri
ii  xserver-xorg-i 1:1.7.2-3    i386         X.Org X server -- mouse input dri
ii  xserver-xorg-i 1.6.2-1ubunt i386         Synaptics TouchPad driver for X.O
ii  xserver-xorg-i 1:12.9.0-0ub i386         X.Org X server -- VMMouse input d
ii  xserver-xorg-i 1:0.19.0-0ub i386         X.Org X server -- Wacom input dri
ii  xserver-xorg-v 1:7.7+1ubunt i386         X.Org X server -- output driver m
ii  xserver-xorg-v 1:7.1.0-0ubu i386         X.Org X server -- AMD/ATI display
ii  xserver-xorg-v 1:1.5.2-0ubu i386         X.Org X server -- Cirrus display 
ii  xserver-xorg-v 1:0.4.3-0ubu i386         X.Org X server -- fbdev display d
ii  xserver-xorg-v 2:2.21.6-0ub i386         X.Org X server -- Intel i8xx, i9x
ii  xserver-xorg-v 6.9.3-0ubunt i386         X.Org X server -- ATI Mach64 disp
ii  xserver-xorg-v 1:1.6.2-0ubu i386         X.Org X server -- MGA display dri
ii  xserver-xorg-v 0.7.0-0ubunt i386         X.Org X server -- Generic modeset
ii  xserver-xorg-v 1:1.2.7-0ubu i386         X.Org X server -- Neomagic displa
ii  xserver-xorg-v 1:1.0.7-0ubu i386         X.Org X server -- Nouveau display
ii  xserver-xorg-v 1:0.3.1-0ubu i386         X.Org X server -- VIA display dri
ii  xserver-xorg-v 0.1.0-0ubunt i386         X.Org X server -- QXL display dri
ii  xserver-xorg-v 6.9.1-0ubunt i386         X.Org X server -- ATI r128 displa
ii  xserver-xorg-v 1:7.1.0-0ubu i386         X.Org X server -- AMD/ATI Radeon 
ii  xserver-xorg-v 1:0.6.5-0ubu i386         X.Org X server -- legacy S3 displ
ii  xserver-xorg-v 1:2.3.6-0ubu i386         X.Org X server -- Savage display 
ii  xserver-xorg-v 1:1.7.7-0ubu i386         X.Org X server -- SiliconMotion d
ii  xserver-xorg-v 1:0.10.7-0ub i386         X.Org X server -- SiS display dri
ii  xserver-xorg-v 1:0.9.6-0ubu i386         X.Org X server -- SiS USB display
ii  xserver-xorg-v 1:1.4.5-0ubu i386         X.Org X server -- tdfx display dr
ii  xserver-xorg-v 1:1.3.6-0ubu i386         X.Org X server -- Trident display
ii  xserver-xorg-v 1:2.3.2-0ubu i386         X.Org X server -- VESA display dr
ii  xserver-xorg-v 1:12.0.2+git i386         X.Org X server -- VMware display 
ii  xterm          278-1ubuntu2 i386         X terminal emulator
ii  xul-ext-ubufox 2.6-0ubuntu1 all          Ubuntu-specific configuration def
ii  xz-utils       5.1.1alpha+2 i386         XZ-format compression utilities
ii  yelp           3.6.2-0ubunt i386         Help browser for GNOME
ii  yelp-xsl       3.6.1-1      all          XSL stylesheets for the yelp help
ii  zeitgeist      0.9.5-0ubunt all          event logging framework
ii  zeitgeist-core 0.9.5-0ubunt i386         event logging framework - engine
ii  zeitgeist-data 0.9.5-1ubunt i386         event logging framework - passive
ii  zenity         3.6.0-0ubunt i386         Display graphical dialog boxes fr
ii  zenity-common  3.6.0-0ubunt all          Display graphical dialog boxes fr
ii  zip            3.0-6ubuntu1 i386         Archiver for .zip files
ii  zlib1g:i386    1:1.2.7.dfsg i386         compression library - runtime
tos@tos:~$

```

**USB_MODESWITCH:**
```

tos@tos:~$ usb_modeswitch -H -v 12d1 -p 380b -u 3 -b 3 -d 6

Looking for default devices ...
   found matching product ID
Getting the current device configuration ...
Error getting the current configuration (error -9). Assuming configuration 1.
 No configuration setting possible for this device.
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 003 ...
Getting the current device configuration ...
Error getting the current configuration (error -9). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -9). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Invalid mode combination. Check your configuration. Aborting.

tos@tos:~$ 

```

--- END OF POST ---

---

### Post by Sean Moran on 2013-05-05
Just a bump as a last resort before this other 3G broadband stick runs out of its last 100Mb.

---

### Post by bmork on 2013-05-09
> **Sean Moran said:**
> ```

[  776.194244] usb 3-4: new high-speed USB device number 5 using xhci_hcd
[  776.210720] usb 3-4: config 1 interface 0 altsetting 0 bulk endpoint 0x81 has invalid maxpacket 64
[  776.210731] usb 3-4: config 1 interface 0 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64

```


This looks fishy, but apparently it's working despite those warnings....

> 
```

[  776.211080] usb 3-4: New USB device found, idVendor=12d1, idProduct=380b
[  776.211090] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  776.211097] usb 3-4: Product: HUAWEI WiMAX USB Stick
[  776.211102] usb 3-4: Manufacturer: HUAWEI Communications
[  776.211107] usb 3-4: SerialNumber: 08FF0004
[  776.259942] Initializing USB Mass Storage driver...
[  776.260100] scsi6 : usb-storage 3-4:1.0
[  776.260177] usbcore: registered new interface driver usb-storage
[  776.260179] USB Mass Storage support registered.
[  777.257799] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     1.00 PQ: 0 ANSI: 2
[  777.259723] sr0: scsi3-mmc drive: 0x/0x caddy
[  777.259738] cdrom: Uniform CD-ROM driver Revision: 3.20
[  777.259917] sr 6:0:0:0: Attached scsi CD-ROM sr0
[  777.260004] sr 6:0:0:0: Attached scsi generic sg2 type 5
tos@tos:~$

```


OK, so you got one mass storage interface.  That's typical for mode switching devices. Good start. Looking at the latest usb-modeswitch-data, there is already a matching entry for this device (and it was added as early as the 20110227 release):

```

bjorn@nemi:~$ tar zxOvf /usr/share/usb_modeswitch/configPack.tar.gz 12d1:380b
12d1:380b
# Huawei BM358 WiMAX

TargetClass=0x02

MessageContent="5553424312345678000000000000061e000000000000000000000000000000" 
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000" 
NeedResponse=1 

```


> 
**USB_MODESWITCH:**
```

tos@tos:~$ usb_modeswitch -H -v 12d1 -p 380b -u 3 -b 3 -d 6

Looking for default devices ...
   found matching product ID
Getting the current device configuration ...
Error getting the current configuration (error -9). Assuming configuration 1.
 No configuration setting possible for this device.
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 003 ...
Getting the current device configuration ...
Error getting the current configuration (error -9). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -9). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Invalid mode combination. Check your configuration. Aborting.

tos@tos:~$ 

```


I believe the "No driver found. Either detached before or never attached" is a sign that usb_modeswitch has already run, and failed.  udev will start it automatically when you plug the device.  Try setting
```

EnableLogging=1

```

in /etc/usb_modeswitch.conf and look for interesting log files in  /var/log/usb_modeswitch_*.  You can also try setting DisableSwitching=1 in the same file to prevent the automatic switching and have a chance to look at the device before the first switching command is sent to it.

Note that the second message in the config I quoted above is a standard "eject" command. You could also try switching it manually, using the eject utility.  But you naturally have to do this before usb_modeswitch unbind the storage driver.

---

### Post by fat yak on 2013-05-20
For info, I bought a 3G USB modem last week - Huawei E398 for my asus netbook running Ubuntu 12.04LTS.
Initially nothing recognised but lsusb showed it was there.
Disconnected home wifi and it all connected automatically without installing any more drivers or anything ??
Yak.

---

