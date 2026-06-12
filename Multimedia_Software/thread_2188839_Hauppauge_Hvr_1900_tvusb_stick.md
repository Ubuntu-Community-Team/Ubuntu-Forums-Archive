---
title: "Hauppauge Hvr 1900 tvusb stick"
date: 2013-11-19
forum: Multimedia Software
---

### Post by matosch83 on 2013-11-19
Hi I got a problem first I brought the hauppauge 930c-hd tried to  install it until I saw only the 930c works, now I bought the 1900 and I  think because I tried to install looks like a old firmware from the 930  older now from the 1900 I cant get it working

lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 2040:7300 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:644a Microdia 
Bus 002 Device 003: ID 8087:07da Intel Corp. 

dmesg
[  141.650136] usb 3-4: new high-speed USB device number 3 using xhci_hcd
[  141.670239] usb 3-4: New USB device found, idVendor=2040, idProduct=7300
[  141.670247] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  141.670252] usb 3-4: Product: WinTV
[  141.670255] usb 3-4: Manufacturer: Hauppauge
[  141.670259] usb 3-4: SerialNumber: 7300-00-F0814018
[  141.687251] WARNING: You are using an experimental version of the media stack.
[  141.687251]  As the driver is backported to an older kernel, it doesn't offer
[  141.687251]  enough quality for its usage in production.
[  141.687251]  Use it with care.
[  141.687251] Latest git patches (needed if you report a bug to [email]linux-media@vger.kernel.org[/email]):
[  141.687251]  80f93c7b0f4599ffbdac8d964ecd1162b8b618b9 [media] media: st-rc: Add ST remote control driver
[  141.687251]  8ab1aa87f3f7381be195efcabf08dbc74626f25d [media] gpio-ir-recv: Include linux/of.h header
[  141.687251]  b91670a0e924078521a838b9e707e42012c5e76a [media] tvp7002: Include linux/of.h header
[  141.687486] cx2341x: disagrees about version of symbol v4l2_ctrl_grab
[  141.687491] cx2341x: Unknown symbol v4l2_ctrl_grab (err -22)
[  141.687504] cx2341x: disagrees about version of symbol v4l2_ctrl_handler_setup
[  141.687507] cx2341x: Unknown symbol v4l2_ctrl_handler_setup (err -22)
[  141.687518] cx2341x: disagrees about version of symbol v4l2_ctrl_new_custom
[  141.687520] cx2341x: Unknown symbol v4l2_ctrl_new_custom (err -22)
[  141.687536] cx2341x: disagrees about version of symbol v4l2_ctrl_new_std_menu
[  141.687540] cx2341x: Unknown symbol v4l2_ctrl_new_std_menu (err -22)
[  141.687564] cx2341x: disagrees about version of symbol v4l2_ctrl_activate
[  141.687569] cx2341x: Unknown symbol v4l2_ctrl_activate (err -22)
[  141.687606] cx2341x: Unknown symbol v4l2_ctrl_handler_init (err 0)
[  141.687619] cx2341x: disagrees about version of symbol v4l2_ctrl_new_std
[  141.687623] cx2341x: Unknown symbol v4l2_ctrl_new_std (err -22)
[  141.687636] cx2341x: disagrees about version of symbol v4l2_ctrl_g_ctrl
[  141.687640] cx2341x: Unknown symbol v4l2_ctrl_g_ctrl (err -22)
[  141.687652] cx2341x: disagrees about version of symbol v4l2_ctrl_handler_free
[  141.687657] cx2341x: Unknown symbol v4l2_ctrl_handler_free (err -22)
[  141.687671] cx2341x: disagrees about version of symbol v4l2_ctrl_cluster
[  141.687675] cx2341x: Unknown symbol v4l2_ctrl_cluster (err -22)

would be happy for help and oh yeah i tried to install it as well on my xubuntu mashine but isnt working either

i did it like this site told me to:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1900](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1900)

greetings 
MATOSCH83

p.s. i deleted the cx2341x.fw files but still the same and now i dont know what to do and i didnt find anything
in the web and i dont want to use windows to watch european tvprograms (PAL) on my american tv (NTSC)

---

### Post by chili555 on 2013-11-19
I know nothing about your device and little about v4l. I have been told, however, that I know just a bit about drivers, firmware, etc. Also, I love a mystery! First, in the link you gave, it says:> usb 7-2: new high speed USB device using ehci_hcd and address 4
usb 7-2: New USB device found, idVendor=2040, idProduct=7300
usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 7-2: Product: WinTV
usb 7-2: Manufacturer: Hauppauge
usb 7-2: SerialNumber: 7300-00-F06BBD71
usb 7-2: configuration #1 chosen from 1 choice
usbcore: registered new interface driver pvrusb2
[COLOR="#FF0000"]pvrusb2[/COLOR]: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
pvrusb2: Debug mask is 31 (0x1f)And, further:> If dmesg output does not look like this your kernel may be to old.So how old is your kernel?```
uname -r
```In my 13.10 system, the driver pvrusb2 exists and evidently claims your device:```
chili@Think410:~$ modinfo pvrusb2
filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/media/usb/pvrusb2/pvrusb2.ko
version:        0.9.1
license:        GPL
description:    Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
author:         Mike Isely <isely@pobox.com>
firmware:       v4l-pvrusb2-73xxx-01.fw
firmware:       v4l-pvrusb2-73xxx-01.fw
firmware:       v4l-pvrusb2-24xxx-01.fw
firmware:       v4l-pvrusb2-29xxx-01.fw
srcversion:     421D4D440E1E18D974C2C04
alias:          usb:v0CCDp0039d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p7501d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p7500d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v[COLOR="#FF0000"]2040[/COLOR]p[COLOR="#FF0000"]7300[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
<snip>
```My system does not have the xx-73 firmware, and I suspect you'd need it, too.

Does your system have the driver pvrusb2?```
modinfo pvrusb2
```Perhaps I have given you something to move forward with.

---

### Post by matosch83 on 2013-11-23
So ok this is the mechine i wanna use the hauppauge 1900 this is the acer revo with xubuntu on it, here the hauppauge is somewhat registereted i think but i dont get it to work with the other programs

hier the dmesg

[   56.644098] usb 1-3: new high-speed USB device number 3 using ehci-pci
[   56.780336] usb 1-3: New USB device found, idVendor=2040, idProduct=7300
[   56.780345] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   56.780351] usb 1-3: Product: WinTV
[   56.780356] usb 1-3: Manufacturer: Hauppauge
[   56.780361] usb 1-3: SerialNumber: 7300-00-F0814018
[   56.820702] Linux video capture interface: v2.00
[   56.927533] pvrusb2: Hardware description: WinTV HVR-1900 Model 73xxx
[   56.928405] usbcore: registered new interface driver pvrusb2
[   56.928416] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[   56.928423] pvrusb2: Debug mask is 31 (0x1f)
[   58.069463] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[   58.101254] usb 1-3: USB disconnect, device number 3
[   58.101414] pvrusb2: Device being rendered inoperable
[   59.856061] usb 1-3: new high-speed USB device number 4 using ehci-pci
[   59.997630] usb 1-3: New USB device found, idVendor=2040, idProduct=7300
[   59.997639] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   59.997646] usb 1-3: Product: WinTV
[   59.997651] usb 1-3: Manufacturer: Hauppauge
[   59.997656] usb 1-3: SerialNumber: 7300-00-F0814018
[   59.998708] pvrusb2: Hardware description: WinTV HVR-1900 Model 73xxx
[   60.030687] pvrusb2: Binding ir_rx_z8f0811_haup to i2c address 0x71.
[   60.030775] pvrusb2: Binding ir_tx_z8f0811_haup to i2c address 0x70.
[   60.068077] cx25840 2-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   60.079517] pvrusb2: Attached sub-driver cx25840
[   60.127289] tuner 2-0042: Tuner -1 found with type(s) Radio TV.
[   60.127327] pvrusb2: Attached sub-driver tuner
[   62.327750] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   62.425905] tveeprom 2-00a2: Hauppauge model 73219, rev D2F5, serial# 8470552
[   62.425917] tveeprom 2-00a2: MAC address is 00:0d:fe:81:40:18
[   62.425924] tveeprom 2-00a2: tuner model is NXP 18271C2 (idx 155, type 54)
[   62.425933] tveeprom 2-00a2: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   62.425939] tveeprom 2-00a2: audio processor is CX25843 (idx 37)
[   62.425946] tveeprom 2-00a2: decoder processor is CX25843 (idx 30)
[   62.425952] tveeprom 2-00a2: has radio, has IR receiver, has IR transmitter
[   62.425971] pvrusb2: Supported video standard(s) reported available in hardware: PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K
[   62.425997] pvrusb2: Device initialization completed successfully.
[   62.428213] pvrusb2: registered device video0 [mpeg]
[   62.428229] DVB: registering new adapter (pvrusb2-dvb)
[   64.629625] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   64.744625] tda829x 2-0042: setting tuner address to 60
[   64.788203] tda18271 2-0060: creating new instance
[   64.824496] TDA18271HD/C2 detected @ 2-0060
[   65.468494] tda18271: performing RF tracking filter calibration
[   83.228500] tda18271: RF tracking filter calibration complete
[   83.276631] tda829x 2-0042: type set to tda8295+18271
[   88.400639] cx25840 2-0044: 0x0000 is not a valid video input!
[   88.452644] usb 1-3: DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   88.457918] tda829x 2-0042: type set to tda8295
[   88.492400] tda18271 2-0060: attaching existing instance
[  322.897796] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[  322.900260] tda10048_firmware_upload: Upload failed. (file not found?)
[  462.813580] tda10048_writereg: writereg error (ret == -5)
[  462.819956] tda10048_writereg: writereg error (ret == -5)
[  464.922076] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  840.402511] audit_printk_skb: 33 callbacks suppressed
[  840.402521] type=1400 audit(1385215038.666:23): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=4761 comm="apparmor_parser"
[  840.403531] type=1400 audit(1385215038.666:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=4761 comm="apparmor_parser"
[  840.617047] type=1400 audit(1385215038.882:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=4815 comm="apparmor_parser"
[  840.618568] type=1400 audit(1385215038.882:26): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=4815 comm="apparmor_parser"
[  865.003839] type=1400 audit(1385215063.267:27): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=5171 comm="apparmor_parser"
[  865.009176] type=1400 audit(1385215063.275:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5171 comm="apparmor_parser"
[  865.009520] type=1400 audit(1385215063.275:29): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=5171 comm="apparmor_parser"
[  865.208935] type=1400 audit(1385215063.475:30): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=5170 comm="apparmor_parser"
[  865.210197] type=1400 audit(1385215063.475:31): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=5170 comm="apparmor_parser"
[  866.046728] type=1400 audit(1385215064.311:32): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=5174 comm="apparmor_parser"
[  866.050207] type=1400 audit(1385215064.315:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=5174 comm="apparmor_parser"
[  866.393515] type=1400 audit(1385215064.659:34): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld-akonadi" pid=5175 comm="apparmor_parser"
[  866.394670] type=1400 audit(1385215064.659:35): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=5175 comm="apparmor_parser"
[  866.407885] type=1400 audit(1385215064.671:36): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=5177 comm="apparmor_parser"
[  884.596960] type=1400 audit(1385215082.863:37): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=5172 comm="apparmor_parser"
[  884.599452] type=1400 audit(1385215082.863:38): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//sanitized_helper" pid=5172 comm="apparmor_parser"
[  884.602307] type=1400 audit(1385215082.867:39): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=5172 comm="apparmor_parser"
[  884.605129] type=1400 audit(1385215082.871:40): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer//sanitized_helper" pid=5172 comm="apparmor_parser"
[  884.607593] type=1400 audit(1385215082.871:41): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=5172 comm="apparmor_parser"
[  884.609907] type=1400 audit(1385215082.875:42): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer//sanitized_helper" pid=5172 comm="apparmor_parser"
[  886.913083] type=1400 audit(1385215085.179:43): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=5244 comm="apparmor_parser"
[  886.914348] type=1400 audit(1385215085.179:44): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=5244 comm="apparmor_parser"
[  887.109810] type=1400 audit(1385215085.375:45): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=5245 comm="apparmor_parser"
[  887.110265] type=1400 audit(1385215085.375:46): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5245 comm="apparmor_parser"
[  906.900994] audit_printk_skb: 18 callbacks suppressed
[  906.901003] type=1400 audit(1385215105.167:53): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=5246 comm="apparmor_parser"
[  906.903366] type=1400 audit(1385215105.167:54): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//sanitized_helper" pid=5246 comm="apparmor_parser"
[  906.905918] type=1400 audit(1385215105.171:55): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=5246 comm="apparmor_parser"
[  906.907704] type=1400 audit(1385215105.171:56): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer//sanitized_helper" pid=5246 comm="apparmor_parser"
[  906.909583] type=1400 audit(1385215105.175:57): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=5246 comm="apparmor_parser"
[  906.911434] type=1400 audit(1385215105.175:58): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer//sanitized_helper" pid=5246 comm="apparmor_parser"

uname -r
3.8.0-32-generic

modinfo pvrusb2
vrusb2.ko
version:        0.9.1
license:        GPL
description:    Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
author:         Mike Isely <isely@pobox.com>
firmware:       v4l-pvrusb2-73xxx-01.fw
firmware:       v4l-pvrusb2-73xxx-01.fw
firmware:       v4l-pvrusb2-24xxx-01.fw
firmware:       v4l-pvrusb2-29xxx-01.fw
srcversion:     058270D589794597AA47853
alias:          usb:v0CCDp0039d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p7501d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p7500d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p7300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11BAp1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v11BAp1003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1164p0602d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1164p0622d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p2400d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p2950d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2040p2900d*dc*dsc*dp*ic*isc*ip*in*
depends:        dvb-core,v4l2-common,tveeprom,videodev,cx2341x
intree:         Y
vermagic:       3.8.0-32-generic SMP mod_unload modversions 686 
parm:           adapter_nr:DVB adapter numbers (array of short)
parm:           video_nr:Offset for device's video dev minor (array of int)
parm:           radio_nr:Offset for device's radio dev minor (array of int)
parm:           vbi_nr:Offset for device's vbi dev minor (array of int)
parm:           ctlchg:0=optimize ctl change 1=always accept new ctl value (int)
parm:           init_pause_msec:hardware initialization settling delay (int)
parm:           procreload:Attempt init failure recovery with firmware reload (int)
parm:           tuner:specify installed tuner type (array of int)
parm:           video_std:specify initial video standard (array of int)
parm:           tolerance:specify stream error tolerance (array of int)
parm:           tv_freq:specify initial television frequency (int)
parm:           radio_freq:specify initial radio frequency (int)
parm:           debug:Debug trace mask (int)
parm:           i2c_scan:scan i2c bus at insmod time (int)
parm:           ir_mode:specify: 0=disable IR reception, 1=normal IR (array of int)
parm:           disable_autoload_ir_video:1=do not try to autoload ir_video IR receiver (int)


i hope that helps or better saz someone cant help me cause with the programs saz said it would work it doesnt work the dvb-c

---

### Post by chili555 on 2013-11-23
As I said, I know nothing about your device and little about v4l, but I'd try to rectify this:> [ 322.897796] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[ 322.900260] tda10048_firmware_upload: Upload failed. (file not found?)On my system, the file exists in /lib/firmware. Is it in yours?```
chili@Think410:~$ locate dvb-fe-tda10048-1.0.fw
/lib/firmware/dvb-fe-tda10048-1.0.fw
```If not, I'd do:```
sudo apt-get install linux-firmware-nonfree
```Then remove and re-insert the device and check the logs.

---

### Post by matosch83 on 2013-11-23
ok so thx for the hint i got now the missing file and the nonfree now it looks like this but dvb-c is still not working, but now with the programm tvtime television viewer it tells me  that pvrub2 something is wrong with the ioctl (i/o-control)
also it looks like with w_scan that the dvb-t is working but the dvb-c doesnt want to ...........

    18.148340] init: failsafe main process (494) killed by TERM signal[   18.375963] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   18.471978] tveeprom 0-00a2: Hauppauge model 73219, rev D2F5, serial# 8470552
[   18.471986] tveeprom 0-00a2: MAC address is 00:0d:fe:81:40:18
[   18.471992] tveeprom 0-00a2: tuner model is NXP 18271C2 (idx 155, type 54)
[   18.471998] tveeprom 0-00a2: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   18.472055] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[   18.472074] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[   18.472085] tveeprom 0-00a2: has radio, has IR receiver, has IR transmitter
[   18.472105] pvrusb2: Supported video standard(s) reported available in hardware: PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K
[   18.472129] pvrusb2: Device initialization completed successfully.
[   18.472353] pvrusb2: registered device video0 [mpeg]
[   18.472365] DVB: registering new adapter (pvrusb2-dvb)
[   19.959357] type=1400 audit(1385219325.456:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=629 comm="apparmor_parser"
[   19.960723] type=1400 audit(1385219325.460:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=629 comm="apparmor_parser"
[   19.961313] type=1400 audit(1385219325.460:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=629 comm="apparmor_parser"
[   20.335357] type=1400 audit(1385219325.832:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=633 comm="apparmor_parser"
[   20.335996] type=1400 audit(1385219325.832:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=633 comm="apparmor_parser"
[   20.675462] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.788589] tda829x 0-0042: setting tuner address to 60
[   20.816545] type=1400 audit(1385219326.316:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=635 comm="apparmor_parser"
[   20.839617] type=1400 audit(1385219326.336:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=628 comm="apparmor_parser"
[   20.840856] type=1400 audit(1385219326.340:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=628 comm="apparmor_parser"
[   20.929446] type=1400 audit(1385219326.428:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=632 comm="apparmor_parser"
[   20.931524] type=1400 audit(1385219326.428:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=632 comm="apparmor_parser"
[   20.933849] tda18271 0-0060: creating new instance
[   20.968588] TDA18271HD/C2 detected @ 0-0060
[   21.344582] tda18271: performing RF tracking filter calibration
[   22.299972] type=1400 audit(1385219327.796:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=630 comm="apparmor_parser"
[   22.312200] type=1400 audit(1385219327.812:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=630 comm="apparmor_parser"
[   22.314661] type=1400 audit(1385219327.812:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=630 comm="apparmor_parser"
[   23.456914] Bluetooth: Core ver 2.16
[   23.456981] NET: Registered protocol family 31
[   23.456988] Bluetooth: HCI device and connection manager initialized
[   23.457016] Bluetooth: HCI socket layer initialized
[   23.457027] Bluetooth: L2CAP socket layer initialized
[   23.457049] Bluetooth: SCO socket layer initialized
[   23.605146] Bluetooth: RFCOMM TTY layer initialized
[   23.605177] Bluetooth: RFCOMM socket layer initialized
[   23.605184] Bluetooth: RFCOMM ver 1.11
[   24.016294] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.016305] Bluetooth: BNEP filters: protocol multicast
[   24.016327] Bluetooth: BNEP socket layer initialized
[   25.621903] init: avahi-cups-reload main process (828) terminated with status 1
[   25.987526] ppdev: user-space parallel port driver
[   26.064228] audit_printk_skb: 9 callbacks suppressed
[   26.064236] type=1400 audit(1385219331.564:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=872 comm="apparmor_parser"
[   26.065556] type=1400 audit(1385219331.564:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=872 comm="apparmor_parser"
[   31.488939] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.489820] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.747715] r8169 0000:03:00.0 eth0: link down
[   31.747866] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.749222] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.705330] wlan0: authenticate with 9c:c7:a6:6e:b7:1c
[   34.752717] wlan0: send auth to 9c:c7:a6:6e:b7:1c (try 1/3)
[   34.754248] wlan0: authenticated
[   34.756203] wlan0: associate with 9c:c7:a6:6e:b7:1c (try 1/3)
[   34.759608] wlan0: RX AssocResp from 9c:c7:a6:6e:b7:1c (capab=0x431 status=0 aid=3)
[   34.759684] wlan0: associated
[   34.759742] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.759924] cfg80211: Calling CRDA for country: DE
[   34.767296] cfg80211: Regulatory domain changed to country: DE
[   34.767304] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   34.767310] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   34.767314] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   34.767319] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   34.767323] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   34.767328] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   39.116583] tda18271: RF tracking filter calibration complete
[   39.164587] tda829x 0-0042: type set to tda8295+18271
[   44.312592] cx25840 0-0044: 0x0000 is not a valid video input!
[   44.543215] usb 1-3: DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   44.544850] tda829x 0-0042: type set to tda8295
[   44.566345] init: udev-fallback-graphics main process (1306) terminated with status 1
[   44.580360] tda18271 0-0060: attaching existing instance
[   44.681435] init: plymouth-splash main process (1324) terminated with status 1
[  255.667536] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  293.260583] cx25840 0-0044: 0x0000 is not a valid video input!
[  314.712552] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[  314.726558] tda10048_firmware_upload: firmware read 24878 bytes.
[  314.726564] tda10048_firmware_upload: firmware uploading
[  317.920674] tda10048_firmware_upload: firmware uploaded
[  537.873624] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  673.112615] cx25840 0-0044: 0x0000 is not a valid video input!

i hope this helps more now

---

### Post by chili555 on 2013-11-23
> pvrub2 something is wrong with the ioctl (i/o-control)Although I am way, way out of my depth, I suspect it would be helpful to see the actual error. You might get more clues starting tvtime from the terminal. Then you can copy and paste the messages here and we can booth Google them.

---

### Post by matosch83 on 2013-12-06
ok i got it working with tv viewer, everything works fine so thx for all your help

---

