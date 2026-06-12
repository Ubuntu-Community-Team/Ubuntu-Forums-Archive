---
title: "Which version of Ubuntu should I use ??"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by walkerx on 2006-06-26
My appologies if this is in the wrong area, but I have the following query

I am new to Ubuntu and installed the 64bit version of Ubuntu 6 (Latest one on download), everything is working ok, except for my freecom dvb-t stick.

I've followed the instructions in a previous post but this was for 5.10 and not  version 6.

Does any one know how to get this working, or should I download version 5.10 for amd 64bit and install that instead.

The following is what is shown by running the various commands

**lsmod**

dvb_usb_dtt200u 15236 0
dvb_usb 21960 1 dvb_usb_dtt200u
dvb_core 95788 1 dvb_usb
dvb_pll 16772 1 dvb_usb
i2c_core 26048 5 dvb_usb,dvb_pll,i2c_acpi_ec,nvidia,i2c_nforce2
usbcore 146428 8 dvb_usb_dtt200u,dvb_usb,rt2570,usb_storage,usbhi

not sure why listed as nforce2 as using nforce3 mobo

**lsusb**
Bus 003 Device 005: ID 14aa:0222 AVerMedia (again) or C&E

**dmesg**
[ 130.510043] usb 3-5: new high speed USB device using ehci_hcd and address 5
[ 130.692917] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
[ 130.717380] dvb-usb: downloading firmware from file 'dvb-usb-wt220u-02.fw'
[ 130.746647] usbcore: registered new driver dvb_usb_dtt200u

but when scan get an error saying device not found

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-EmleyMoor > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-EmleyMoor
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1884: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

thanks in advance

---

### Post by walkerx on 2006-06-26
managed to sort - needed older firmware file

[SIZE="1"][   58.008844] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free com)' in warm state.
[   58.008853] dvb-usb: will use the device's hardware PID filter (table count: 15).
[   58.010277] DVB: registering new adapter (WideView WT-220U PenType Receiver ( Typhoon/Freecom)).
[   58.010373] DVB: registering frontend 0 (WideView USB DVB-T)...
[   58.010433] input: IR-receiver inside an USB DVB receiver as /class/input/inp ut4
[   58.010456] dvb-usb: schedule remote query interval to 300 msecs.
[   58.010459] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ essfully initialized and connected.
[   58.010469] usbcore: registered new driver dvb_usb_dtt200u
[   58.061973] idVendor = 0x2001, idProduct = 0x3c00
[   58.062088] INIT bRadio=1[/SIZE]

now just need to get sound working

---

