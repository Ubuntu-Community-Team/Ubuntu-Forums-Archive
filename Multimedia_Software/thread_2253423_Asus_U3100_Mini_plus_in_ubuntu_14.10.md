---
title: "Asus U3100 Mini plus in ubuntu 14.10"
date: 2014-11-19
forum: Multimedia Software
---

### Post by gkaran89 on 2014-11-19
Hey there,

I'm running ubuntu 14.10 with kernel 3.16.0 and having some trouble making my asus U3100 mini plus to work.

[From what I understand]("http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T") it should work out of the box since kernel 3.7 (?) but somehow it doesn't.

When I first plugged in the tv tuner it couldn't work since it couldn't find the correct driver. I tried downloading the driver provided in the "19.07.2013" update from [here]("http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T") and also add the following in **/etc/modprobe.d/usbhid.conf** but still not way through.

> [COLOR=#000000][FONT=monospace]options usbhid quirks=0x0b05:0x1779:0x0004[/FONT][/COLOR]

dmesg gives the following when I connect the device:

> [ 7168.419999] usb 3-2: new high-speed USB device number 11 using xhci_hcd[ 7168.554060] usb 3-2: New USB device found, idVendor=0b05, idProduct=1779
[ 7168.554062] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7168.554064] usb 3-2: Product: AF9035A USB Device
[ 7168.554065] usb 3-2: Manufacturer: Afa Technologies Inc.
[ 7168.554065] usb 3-2: SerialNumber: CT7009002900351
[ 7168.556416] usb 3-2: dvb_usb_af9035: prechip_version=00 chip_version=03 chip_type=3802
[ 7168.556751] usb 3-2: dvb_usb_v2: found a 'Asus U3100Mini Plus' in cold state
[ 7168.556793] usb 3-2: dvb_usb_v2: downloading firmware from file 'dvb-usb-af9035-02.fw'
[ 7168.870252] usb 3-2: dvb_usb_af9035: firmware version=11.5.9.0
[ 7168.870258] usb 3-2: dvb_usb_v2: found a 'Asus U3100Mini Plus' in warm state
[ 7168.872133] usb 3-2: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[ 7168.872144] DVB: registering new adapter (Asus U3100Mini Plus)
[ 7168.873847] af9033 6-0038: firmware version: LINK 11.5.9.0 - OFDM 5.17.9.1
[ 7168.877598] af9033 6-0038: Afatech AF9033 successfully attached
[ 7168.877604] usb 3-2: DVB: registering adapter 0 frontend 0 (Afatech AF9033 (DVB-T))...
[ 7168.928213] systemd-udevd[4573]: Failed to apply ACL on /dev/dvb/adapter0/dvr0: No such file or directory
[ 7168.928218] systemd-udevd[4573]: Failed to apply ACL on /dev/dvb/adapter0/dvr0: No such file or directory
[ 7168.928897] systemd-udevd[4575]: Failed to apply ACL on /dev/dvb/adapter0/frontend0: No such file or directory
[ 7168.928901] systemd-udevd[4575]: Failed to apply ACL on /dev/dvb/adapter0/frontend0: No such file or directory
[ 7168.930487] systemd-udevd[4572]: Failed to apply ACL on /dev/dvb/adapter0/demux0: No such file or directory
[ 7168.930492] systemd-udevd[4572]: Failed to apply ACL on /dev/dvb/adapter0/demux0: No such file or directory
[ 7168.930534] systemd-udevd[4574]: Failed to apply ACL on /dev/dvb/adapter0/net0: No such file or directory
[ 7168.930537] systemd-udevd[4574]: Failed to apply ACL on /dev/dvb/adapter0/net0: No such file or directory


Has anyone managed to make this work in 14.10? If yes, please share. Otherwise if anyone has any ideas on how to make it work I would appreciate it very much if they could share.

---

