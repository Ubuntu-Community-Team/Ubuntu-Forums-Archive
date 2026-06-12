---
title: "MSI Mega Sky 580 (DVB-T)"
date: 2013-12-25
forum: Multimedia Software
---

### Post by epek on 2013-12-25
Hello!

I've had issues with this adapter before, it worked around 8.10 afair - I gave it away - now that there aren't even Windows drivers for it anymore, I got it back.
This is the actual state:

[ 1847.776652] usb 3-4: new high-speed USB device number 5 using xhci_hcd
[ 1847.857630] usb 3-4: New USB device found, idVendor=0db0, idProduct=5581
[ 1847.857638] usb 3-4: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1847.857642] usb 3-4: Product: PC-DTV Receiver
[ 1847.857645] usb 3-4: Manufacturer: PC-DTV Receiver
[ 1847.857648] usb 3-4: SerialNumber: 00000001
[ 1847.859935] usb 3-4: dvb_usb_v2: found a 'MSI Mega Sky 55801 DVB-T USB2.0' in warm state
[ 1847.859981] usb 3-4: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[ 1847.859989] DVB: registering new adapter (MSI Mega Sky 55801 DVB-T USB2.0)
_***[ 1849.868173] zl10353_read_register: readreg error (reg=127, ret==0)***_
[ 1849.868238] usb 3-4: dvb_usb_v2: 'MSI Mega Sky 55801 DVB-T USB2.0' error while loading driver (-5)
[ 1849.869115] usb 3-4: dvb_usb_v2: 'MSI Mega Sky 55801 DVB-T USB2.0' successfully deinitialized and disconnected
[ 1849.874870] input: PC-DTV Receiver PC-DTV Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/input/input15
[ 1849.875212] hid-generic 0003:0DB0:5581.0005: input,hidraw0: USB HID v1.01 Keyboard [PC-DTV Receiver PC-DTV Receiver] on usb-0000:00:14.0-4/input1
[ 1850.396360] systemd-udevd[9363]: Failed to apply ACL on /dev/dvb/adapter0/net0: No such file or directory
[ 1850.396384] systemd-udevd[9363]: Failed to apply ACL on /dev/dvb/adapter0/net0: No such file or directory
[ 1850.404798] systemd-udevd[9362]: Failed to apply ACL on /dev/dvb/adapter0/dvr0: No such file or directory
[ 1850.404820] systemd-udevd[9362]: Failed to apply ACL on /dev/dvb/adapter0/dvr0: No such file or directory
[ 1850.405536] systemd-udevd[9361]: Failed to apply ACL on /dev/dvb/adapter0/demux0: No such file or directory
[ 1850.405545] systemd-udevd[9361]: Failed to apply ACL on /dev/dvb/adapter0/demux0: No such file or directory

I found the following:
[https://linuxtv.org/patch/2719/](https://linuxtv.org/patch/2719/)
ML archive thread, which contains a discussion on GPIOs on a Leadtek WinFast DVR3100 H.

I guess the solution would be similar. Should I rather report this issue to the guys at linuxtv.org?
I also activated debug and debug_regs on the zl10353 module, but I don't see any log message from it.

---

