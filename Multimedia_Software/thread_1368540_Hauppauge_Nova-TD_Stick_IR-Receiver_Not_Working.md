---
title: "Hauppauge Nova-TD Stick IR-Receiver Not Working"
date: 2009-12-30
forum: Multimedia Software
---

### Post by chromerium on 2009-12-30
Hi all,

So I've been bashing my head against this for about 10 hours now and I'm really stuck. I've got the Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity USB DVB-T device working well with MythTV except for the IR-receiver.

It is detected and a device created:

```
[   24.586140] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/input/input11
[   24.586204] dvb-usb: schedule remote query interval to 50 msecs.
[   24.586209] dvb-usb: Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity successfully initialized and connected.
[   24.587981] usbcore: registered new interface driver dvb_usb_dib0700

```

output from /proc/bus/input/devices:

```
I: Bus=0003 Vendor=2040 Product=9580 Version=0001
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:1d.7-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-1/input/input11
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffd

```

the /dev/input/event4 device exists (after messing with the hal config) but I see nothing when pressing keys on the remote and either cat'ing the device or using one of the other tools like evtest.

I think something else is nabbing the keypresses before it gets to the dev/input device. Can anyone shed some light on this? I'm literally tearing my hair out here. :(

---

### Post by chromerium on 2009-12-30
I've checked with lsof and confirmed no other daemon has snatched the device from under me. Nothing else is using it.

It definitely works, as booting OSX lets me use it.

Does anyone have any idea at all?

---

