---
title: "VLC with DVB-T USB TV card"
date: 2011-11-02
forum: Multimedia Software
---

### Post by marin123 on 2011-11-02
Hi guys!

I have a problem with my TV USB card. I plugged it in USB and opened VLC and opened stream, everything like it should be and I got error message that input cannot be opened.
So I took a look at /dev/dvb/adapter0 and realized that directory dvb doesn't exist.
I checked with lsmod is driver loaded and it is.
Now, I remember that I did this with Ubuntu 10.10 without any problem, but this new one refuses to work.
Am I missing something? This did work before by just plugging it in and opening the right frequency in VLC. Yes, I put in right freq. And even tried running vlc as sudo, but no luck.

---

### Post by BicyclerBoy on 2011-11-02
Check for any messages/errors in the output from 
dmesg

look for terms like:
firmware upload sucess
registering tuner input with ..


dmesg | grep dvb
dmesg | grep firmware

Do you have the non-free firmware package installed ?

---

### Post by marin123 on 2011-11-03
Dmesg mentions my tuner just here:

```
[ 4171.294875] usb 2-1.3: new high speed USB device number 5 using ehci_hcd
[ 4171.397909] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input13
[ 4171.398099] generic-usb 0003:15A4:1001.0003: input,hidraw1: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:1d.0-1.3/input1
```

These:

dmesg | grep dvb
dmesg | grep firmware

don't return anything. 

If I run lsusb, I get this for the tuner:

```
Bus 002 Device 005: ID 15a4:1001 Afatech Technologies, Inc. AF9015/AF9035 DVB-T stick
```

---

### Post by BicyclerBoy on 2011-11-03
Your USB tuner is being grabbed by the USB HID driver..

/etc/modprobe.d/usbhid.conf needs to have the line (for module version): 
options usbhid quirks=0x15a4:0x1001:0x0004

You then may need to run:
sudo update-initramfs -u
reboot.
Check dmesg again..

see LinuxTV.org
[http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick)

You likely had this in your previous install or the HID driver has changed..

---

