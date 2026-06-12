---
title: "Trying to configure NoElec R820T DVB-T RTL2832U USB Dongle"
date: 2013-10-16
forum: Multimedia Software
---

### Post by KmCsDFL on 2013-10-16
Hi, I spent several hours trying to configure NoElec R820T  DVB-T RTL2832U USB Dongle
I am running: Ubuntu13 x86_64,  Kernel 3.8.0-19-lowlatency
I'ved  git clone git://linuxtv.org/media_build.git, ./build, installed, rebooted, mprobe modules,
load unload. The follwing outputs of w_scan, lsusb dmesg and lsmod are listed here.





$dvbscan /usr/share/dvb/dvb-t/auto-Default 
[FONT=courier new]Unable to query frontend status[/FONT]

$lsusb | grep RTL
[FONT=courier new]Bus 003 Device 004: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T[/FONT]

$dmesg  (after inserting the R8200 NooElec RTL)
[FONT=courier new][11390.597991] usb 3-1: new high-speed USB device number 5 using xhci_hcd
[11390.627456] usb 3-1: New USB device found, idVendor=0bda, idProduct=2838
[11390.627464] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11390.627470] usb 3-1: Product: RTL2838UHIDIR
[11390.627476] usb 3-1: Manufacturer: Realtek
[11390.627481] usb 3-1: SerialNumber: 00000001
[11390.634009] usb 3-1: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[11390.708987] usb 3-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[11390.709005] DVB: registering new adapter (Realtek RTL2832U reference design)
[11390.712542] usb 3-1: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[11390.712707] r820t 4-001a: creating new instance
[11390.726414] r820t 4-001a: Rafael Micro r820t successfully identified
[11390.734819] Registered IR keymap rc-empty
[11390.734948] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-1/rc/rc3/input26
[11390.735219] rc3: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-1/rc/rc3
[11390.735750] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input27
[11390.736549] rc rc3: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[11390.736559] usb 3-1: dvb_usb_v2: schedule remote query interval to 400 msecs
[11390.749704] usb 3-1: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected[/FONT]

lsmod | grep dvb 
[FONT=courier new]dvb_usb_rtl28xxu       23888  0 
rtl2830                17871  1 dvb_usb_rtl28xxu
dvb_usb_v2             23935  1 dvb_usb_rtl28xxu
dvb_core              106020  3 rtl2830,rtl2832,dvb_usb_v2
rc_core                26667  12 lirc_dev,ir_lirc_codec,dvb_usb_rtl28xxu,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ir_mce_kbd_decoder,ir_jvc_decoder,dvb_usb_v2,ir_rc6_decoder,ir_sanyo_decoder
[FONT=arial]
$w_scan -c CA -k   [/FONT][/FONT]
[FONT=courier new]scan type TERRCABLE_ATSC, channellist 1
output format initial tuning data
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> "Realtek RTL2832 (DVB-T)" doesnt support TERRCABLE_ATSC -> SEARCH NEXT ONE.
main:3220: FATAL: ***** NO USEABLE TERRCABLE_ATSC CARD FOUND. *****

[/FONT]Thank you

---

