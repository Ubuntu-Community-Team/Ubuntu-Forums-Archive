---
title: "huawei e585 connection"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by M@xil on 2011-11-06
Hi there 

I have ubuntu 11.10 and am trying to connect to the internet via a huawei e585 modem but no joy. 

If somebody could help me with the usb_modeswitch installation would be grateful as i am a absolute beginner.

regards
M

---

### Post by praseodym on 2011-11-06
Hi,

please show the terminal outputs of

```
uname -a
lsusb
lsmod
usb-devices
```
Do you have any connection? If yes, install it via:

```
sudo apt-get install usb-modeswitch
```

---

### Post by M@xil on 2011-11-06
will post the results, but have no connection to the internet.

regards
M

---

### Post by praseodym on 2011-11-06
copy the outputs into a text file and upload it

---

### Post by M@xil on 2011-11-07
Here is the ouput as requested without the modem and with it.

Without connection
uname -a  
 

 Linux User1-PC 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux  
 

 lsusb  
 

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse  
 Bus 001 Device 004: ID 0b38:0010 Gear Head 107-Key Keyboard  
 

 lsmod  
 

 Module                  Size  Used by  
 rfcomm                 47946  0  
 bnep                   18436  2  
 bluetooth             166112  10 rfcomm,bnep  
 pci_stub               12622  1  
 vboxpci                23200  0  
 vboxnetadp             13382  0  
 vboxnetflt             23441  0  
 vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt  
 parport_pc             36962  0  
 ppdev                  17113  0  
 snd_hda_codec_hdmi     32040  1  
 binfmt_misc            17540  1  
 joydev                 17693  0  
 snd_hda_codec_realtek   330769  1  
 snd_hda_intel          33390  3  
 snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13668  1 snd_hda_codec  
 snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec  
 radeon               1015995  3  
 snd_seq_midi           13324  0  
 snd_rawmidi            30547  1 snd_seq_midi  
 psmouse                73882  0  
 serio_raw              13166  0  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event  
 ttm                    76805  1 radeon  
 drm_kms_helper         42558  1 radeon  
 drm                   236330  5 radeon,ttm,drm_kms_helper  
 snd_timer              29991  2 snd_pcm,snd_seq  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq  
 shpchp                 37345  0  
 i2c_algo_bit           13423  1 radeon  
 snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 mei                    41480  0  
 soundcore              12680  1 snd  
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp  
 usbhid                 47198  0  
 hid                    95463  1 usbhid  
 ahci                   26002  2  
 libahci                26861  1 ahci  
 xhci_hcd               78641  0  
 e1000e                160535  0  
 

 usb-devices  
 

 T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0002 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd  
 S:  Product=EHCI Host Controller  
 S:  SerialNumber=0000:00:1a.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1  
 P:  Vendor=8087 ProdID=0024 Rev=00.00  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0  
 D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1  
 P:  Vendor=093a ProdID=2510 Rev=01.00  
 S:  Manufacturer=PixArt  
 S:  Product=USB Optical Mouse  
 C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid  
 

 T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0  
 D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1  
 P:  Vendor=0b38 ProdID=0010 Rev=01.02  
 C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid  
 I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid  
 

 T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0002 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd  
 S:  Product=EHCI Host Controller  
 S:  SerialNumber=0000:00:1d.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1  
 P:  Vendor=8087 ProdID=0024 Rev=00.00  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0002 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic xhci_hcd  
 S:  Product=xHCI Host Controller  
 S:  SerialNumber=0000:04:00.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2  
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0003 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic xhci_hcd  
 S:  Product=xHCI Host Controller  
 S:  SerialNumber=0000:04:00.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 

With connection

 lsusb 

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse  
 Bus 001 Device 004: ID 0b38:0010 Gear Head 107-Key Keyboard  
 Bus 001 Device 006: ID 12d1:1432 Huawei Technologies Co., Ltd.  
 

 lsmod  
 Module                  Size  Used by  
 option                 25477  0  
 usb_wwan               20491  1 option  
 cdc_ether              13536  0  
 usbnet                 26212  1 cdc_ether  
 usbserial              47107  2 option,usb_wwan  
 usb_storage            57901  0  
 uas                    18027  0  
 rfcomm                 47946  0  
 bnep                   18436  2  
 bluetooth             166112  10 rfcomm,bnep  
 pci_stub               12622  1  
 vboxpci                23200  0  
 vboxnetadp             13382  0  
 vboxnetflt             23441  0  
 vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt  
 parport_pc             36962  0  
 ppdev                  17113  0  
 snd_hda_codec_hdmi     32040  1  
 binfmt_misc            17540  1  
 joydev                 17693  0  
 snd_hda_codec_realtek   330769  1  
 snd_hda_intel          33390  3  
 snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13668  1 snd_hda_codec  
 snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec  
 radeon               1015995  3  
 snd_seq_midi           13324  0  
 snd_rawmidi            30547  1 snd_seq_midi  
 psmouse                73882  0  
 serio_raw              13166  0  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event  
 ttm                    76805  1 radeon  
 drm_kms_helper         42558  1 radeon  
 drm                   236330  5 radeon,ttm,drm_kms_helper  
 snd_timer              29991  2 snd_pcm,snd_seq  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq  
 shpchp                 37345  0  
 i2c_algo_bit           13423  1 radeon  
 snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 mei                    41480  0  
 soundcore              12680  1 snd  
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp  
 usbhid                 47198  0  
 hid                    95463  1 usbhid  
 ahci                   26002  2  
 libahci                26861  1 ahci  
 xhci_hcd               78641  0  
 e1000e                160535  0  
 

 

 usb-devices  
 

 T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0002 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd  
 S:  Product=EHCI Host Controller  
 S:  SerialNumber=0000:00:1a.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1  
 P:  Vendor=8087 ProdID=0024 Rev=00.00  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  6 Spd=480 MxCh= 0  
 D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1  
 P:  Vendor=12d1 ProdID=1432 Rev=01.00  
 S:  Manufacturer=Huawei Incorporated  
 S:  Product=HUAWEI Mobile Connect  
 S:  SerialNumber=1234567890ABCDEF  
 C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA  
 I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option  
 I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage  
 I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=(none)  
 I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)  
 

 T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0  
 D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1  
 P:  Vendor=093a ProdID=2510 Rev=01.00  
 S:  Manufacturer=PixArt  
 S:  Product=USB Optical Mouse  
 C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid  
 

 T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=03 Dev#=  4 Spd=1.5 MxCh= 0  
 D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1  
 P:  Vendor=0b38 ProdID=0010 Rev=01.02  
 C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid  
 I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid  
 

 T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0002 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd  
 S:  Product=EHCI Host Controller  
 S:  SerialNumber=0000:00:1d.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1  
 P:  Vendor=8087 ProdID=0024 Rev=00.00  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2  
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0002 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic xhci_hcd  
 S:  Product=xHCI Host Controller  
 S:  SerialNumber=0000:04:00.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub  
 

 T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2  
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1  
 P:  Vendor=1d6b ProdID=0003 Rev=03.00  
 S:  Manufacturer=Linux 3.0.0-12-generic xhci_hcd  
 S:  Product=xHCI Host Controller  
 S:  SerialNumber=0000:04:00.0  
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA  
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by M@xil on 2011-11-09
Hi there 

I went out and bought a netgear wireless g usb adapter product code WG111v3 plugged it in and within 5 seconds was on the net through ubuntu.  No problems had more drama going through windows7. 

To all who replied to my post, thanks for the time spent replying, will mark this as solved if i can find out how
Regards
M

---

