---
title: "Problem with USB ethernet on boot (after upgrade to Ubuntu 11.10)"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by antonism on 2011-10-16
Hi!

I have an old pc as server here, with a usb ethernet.
After the 11.10 upgrade, the USB seems that is not started at boot.
If I unplug it and plug it again, after boot, everything works fine.

But the problem is that is a monitorless and unattended pc, so I need it to work on boot.

My card is:

```
# lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 9710:7830 MosChip Semiconductor MCS7830 10/100 Mbps Ethernet adapter
``````
# lsmod
Module                  Size  Used by
nls_utf8               12493  0 
cifs                  247650  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_cs46xx             83783  0 
gameport               15027  2 snd_cs46xx
snd_ac97_codec        105614  1 snd_cs46xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_cs46xx,snd_ac97_codec
ir_lirc_codec          12770  0 
snd_seq_midi           13132  0 
lirc_dev               18720  1 ir_lirc_codec
snd_rawmidi            25269  2 snd_cs46xx,snd_seq_midi
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ir_rc6_decoder         12490  0 
bttv                  112771  1 
i2c_algo_bit           13184  1 bttv
dahdi                 205492  0 
snd_timer              28659  2 snd_pcm,snd_seq
v4l2_common            16757  1 bttv
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_rc5_decoder         12490  0 
hisax                 505571  0 
ir_nec_decoder         12490  0 
snd                    55295  7 snd_cs46xx,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt              12595  2 dahdi,hisax
videodev               75143  3 bttv,v4l2_common
videobuf_dma_sg        18747  1 bttv
i2c_piix4              13095  0 
videobuf_core          25193  2 bttv,videobuf_dma_sg
btcx_risc              13400  1 bttv
rc_core                25760  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,bttv,ir_rc5_decoder,ir_nec_decoder
mcs7830                13414  0 
tveeprom               17009  1 bttv
usbnet                 25175  1 mcs7830
soundcore              12600  1 snd
isdn                  133735  1 hisax
snd_page_alloc         14073  2 snd_cs46xx,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
serio_raw              12990  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
pata_pdc2027x          13288  2 
```Any ideas?

---

### Post by antonism on 2011-10-16
dmesg:

before removal:

```
[    0.100595] usbcore: registered new interface driver usbfs
[    0.100668] usbcore: registered new interface driver hub
[    0.100875] usbcore: registered new device driver usb
[    0.956446] usb 1-1: new low speed USB device number 2 using uhci_hcd
[    1.340484] usb 1-2: new full speed USB device number 3 using uhci_hcd
[    3.430099] generic-usb 0003:1941:8021.0001: hiddev0,hidraw0: USB HID v1.00 Device [HID 1941:8021] on usb-0000:00:07.2-1/input0
[    3.430205] usbcore: registered new interface driver usbhid
[    3.430217] usbhid: USB HID core driver
[   11.200609] usb 1-2: applying rev.C fixup
[   11.206593] usb 1-2: applying rev.C fixup
[   11.220830] MOSCHIP usb-ethernet driver 1-2:1.0: eth0: register 'MOSCHIP usb-ethernet driver' at usb-0000:00:07.2-2, MOSCHIP 7830/7832/7730 usb-NET adapter, 00:13:3b:60:00:16
[   11.220966] usbcore: registered new interface driver MOSCHIP usb-ethernet driver
```

after removal/insert again the usb ethernet:

```
[  912.671576] usb 1-2: USB disconnect, device number 3
[  912.671835] MOSCHIP usb-ethernet driver 1-2:1.0: eth2: unregister 'MOSCHIP usb-ethernet driver' usb-0000:00:07.2-2, MOSCHIP 7830/7832/7730 usb-NET adapter
[  917.128069] usb 1-2: new full speed USB device number 4 using uhci_hcd
[  917.380728] usb 1-2: applying rev.C fixup
[  917.388713] usb 1-2: applying rev.C fixup
[  917.403770] MOSCHIP usb-ethernet driver 1-2:1.0: eth0: register 'MOSCHIP usb-ethernet driver' at usb-0000:00:07.2-2, MOSCHIP 7830/7832/7730 usb-NET adapter, 00:13:3b:60:00:16
```

---

### Post by antonism on 2011-10-17
If it helps, usb-devices shows the following:

```
# usb-devices 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:07.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=9710 ProdID=7830 Rev=01.00
S:  Manufacturer=Moschip Semiconductor
S:  Product=USB-MAC Controller   
S:  SerialNumber=3b600016
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
basename: extra operand `driver'
Try `basename --help' for more information.
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=ff Driver=

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1941 ProdID=8021 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
```

Also, restarting networking shows the following error:

```
/etc/init.d/networking restart
 * /etc/network/options still exists and it will be IGNORED! Read README.Debian of netbase.
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          

ssh stop/waiting
ssh start/running, process 19732
/etc/network/if-up.d/upstart: 38: cannot create /run/network/ifup.eth2: Directory nonexistent
run-parts: /etc/network/if-up.d/upstart exited with return code 2
                                                                         [ OK ]
```

---

### Post by Hafswerk on 2012-01-21
Hi,

did you find a solution to this problem? I'm having a very similiar issue with a usb attached bluetooth dongle, and was hoping you had found a way to reset usb devices on boot.

---

### Post by antonism on 2012-01-21
> **Hafswerk said:**
> Hi,

did you find a solution to this problem? I'm having a very similiar issue with a usb attached bluetooth dongle, and was hoping you had found a way to reset usb devices on boot.

Dirty solution:

I added the ifconfig blah blah blah up to the /etc/rc.local....

---

