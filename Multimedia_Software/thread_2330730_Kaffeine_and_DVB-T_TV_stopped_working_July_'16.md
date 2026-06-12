---
title: "Kaffeine and DVB-T TV stopped working July '16"
date: 2016-07-14
forum: Multimedia Software
---

### Post by madsmaddad2 on 2016-07-14
I am running Kubuntu 16.04 and Kaffeine 1.22 and a couple of weeks ago the TV stopped working with the following message: "No Device Found".  Dmesg shows the device as usual:

```
[ 6896.941019] usb 3-6: new high-speed USB device number 3 using xhci_hcd
[ 6897.069080] usb 3-6: New USB device found, idVendor=14aa, idProduct=0225
[ 6897.069085] usb 3-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 6899.014472] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a fi
rmware
[ 6899.030064] dvb-usb: downloading firmware from file 'dvb-usb-wt220u-fc03.fw'
[ 6899.055771] usbcore: registered new interface driver dvb_usb_dtt200u
[ 6900.415809] usb 3-6: USB disconnect, device number 3
[ 6900.415846] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[ 6901.536781] usb 3-6: new high-speed USB device number 4 using xhci_hcd
[ 6901.665377] usb 3-6: New USB device found, idVendor=14aa, idProduct=0226
[ 6901.665381] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6901.665383] usb 3-6: Product: Digital TV Receiver
[ 6901.665384] usb 3-6: Manufacturer: Digital TV Receiver
[ 6901.665385] usb 3-6: SerialNumber: 20060503
[ 6901.666088] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[ 6901.666135] dvb-usb: will use the device's hardware PID filter (table count: 15).
[ 6901.666238] DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom))
[ 6901.667127] usb 3-6: DVB: registering adapter 0 frontend 0 (WideView USB DVB-T)...
[ 6901.667391] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-6/input/input12
[ 6901.667503] dvb-usb: schedule remote query interval to 300 msecs.
[ 6901.667506] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[ 6911.664249] hid-generic 0003:14AA:0226.0002: timeout initializing reports
[ 6911.664369] input: Digital TV Receiver Digital TV Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.1/0003:14
AA:0226.0002/input/input13
[ 6911.720481] hid-generic 0003:14AA:0226.0002: input,hidraw1: USB HID v1.10 Keyboard [Digital TV Receiver Digital TV Rece
iver] on usb-0000:00:14.0-6/input1
peterm@peterm-MBB-34204H:~$ 
```

I am not sure where to look now for a solution. The firmware is in the usual folder - /lib/firmware. 

Can anyone offer any suggestions? My thoughts are that something that has updated in the last two weeks has somehow clobbered it.

---

### Post by ma7eu on 2016-07-17
Perhaps the failure of the device? or 
bug in the driver code

---

