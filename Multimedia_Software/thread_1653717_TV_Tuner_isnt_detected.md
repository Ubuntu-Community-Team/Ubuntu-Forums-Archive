---
title: "TV Tuner isnt detected"
date: 2010-12-27
forum: Multimedia Software
---

### Post by VonSpyder on 2010-12-27
I just got a Diamond ATI TV Wonder HD 750 USB, but it appears as though my 10.04 wont detect it. Myth cant find it. I tried to install it on my other comp running 10.10 but no dice. Anyone know of a way to get this Tv tuner card working in Ubuntu?

---

### Post by sanderj on 2010-12-27
Start by looking at the output of

lsusb

tail -f /var/log/messages
(at the moment you plug in the USB device)

It would help if you post the output here

---

### Post by VonSpyder on 2010-12-27
> **sanderj said:**
> Start by looking at the output of

lsusb

tail -f /var/log/messages
(at the moment you plug in the USB device)

It would help if you post the output here


Your probably looking for this:

>  Dec 27 11:13:30 machine-name kernel: [   146.312170] usb 1-1: new high speed USB device using ehci_hcd and address 4 

lsusb results:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0438:ac14 Advanced Micro Devices, Inc.
Bus 001 Device 003: ID 04f2:b175 Chicony Electyronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by sanderj on 2010-12-27
> **VonSpyder said:**
> Your probably looking for this:

Nope. More something like:


/var/log/messages :
```

Mar  9 23:15:43 quirinius kernel: [31274.040120] usb 1-6: new high speed USB device using ehci_hcd and address 6
Mar  9 23:15:43 quirinius kernel: [31274.177240] usb 1-6: configuration #1 chosen from 1 choice
Mar  9 23:15:43 quirinius kernel: [31274.183078] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 10 -> 7
Mar  9 23:15:43 quirinius kernel: [31274.183762] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.1/input/input12
Mar  9 23:15:43 quirinius kernel: [31274.184144] generic-usb 0003:15A4:9016.0003: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1d.7-6/input1
Mar  9 23:15:44 quirinius kernel: [31274.552937] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in cold state, will try to load a firmware
Mar  9 23:15:44 quirinius kernel: [31274.552962] usb 1-6: firmware: requesting dvb-usb-af9015.fw
Mar  9 23:15:44 quirinius kernel: [31274.856329] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
Mar  9 23:15:44 quirinius kernel: [31274.930213] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
Mar  9 23:15:44 quirinius kernel: [31274.930380] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Mar  9 23:15:44 quirinius kernel: [31274.931617] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
Mar  9 23:15:45 quirinius kernel: [31275.398434] af9013: firmware version:4.95.0
Mar  9 23:15:45 quirinius kernel: [31275.405435] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
Mar  9 23:15:45 quirinius kernel: [31275.449074] NXP TDA18218 successfully identified.
Mar  9 23:15:45 quirinius kernel: [31275.449099] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
Mar  9 23:15:45 quirinius kernel: [31275.460185] usbcore: registered new interface driver dvb_usb_af9015

```

---

### Post by VonSpyder on 2010-12-27
all the rest of the items listed were Skipping EDID probe due to cached edid

---

### Post by VonSpyder on 2010-12-27
i tried directing my tv vbiewer programsto read from dev/usb/001/003 and 004 since those are the only devices it could be but the tv programs arent detecting it outright and manually specifying those devices has been fruitless.

---

### Post by sanderj on 2010-12-27
Install me-tv, and try that.

---

### Post by VonSpyder on 2010-12-27
> **sanderj said:**
> Install me-tv, and try that.

Already did. As soon as it starts"ERROR: There are no DVB devices available"

---

### Post by sanderj on 2010-12-27
Your lsusb does not show any DVB device (AFAIK). Easy check: 

First: unplug your DVB-device, run lsusb, and post the output here
Then: plug in your DVB-device, run lsusb, and post the output here

If there is no difference between the two above lsusb outputs, you should check your DVB device.

---

### Post by VonSpyder on 2010-12-27
> **sanderj said:**
> Your lsusb does not show any DVB device (AFAIK). Easy check: 

First: unplug your DVB-device, run lsusb, and post the output here
Then: plug in your DVB-device, run lsusb, and post the output here

If there is no difference between the two above lsusb outputs, you should check your DVB device.

when unplugged this listing does NOT appear, and when it IS PLUGGED this listing DOES appear:

"Bus 001 Device 006: ID 0438:ac14 Advanced Micro Devices, Inc."

also tried manually inputting thedevice into Zapping tv viewer as /dev/bus/usb/001/006 but the program states it cant open that and none of the other tv programs seem to have an option for manual specification.

---

### Post by sanderj on 2010-12-27
> **VonSpyder said:**
> when unplugged this listing does NOT appear, and when it IS PLUGGED this listing DOES appear:

"Bus 001 Device 006: ID 0438:ac14 Advanced Micro Devices, Inc."

OK. What's the output of 'tail -f /var/log/messages' when you plug in the DVB-device?

---

### Post by VonSpyder on 2010-12-27
> **sanderj said:**
> OK. What's the output of 'tail -f /var/log/messages' when you plug in the DVB-device?

"Dec 27 14:00:57 machine-name kernel: [ 2591.024155] usb 1-1: new high speed USB device using ehci_hcd and address 7"

---

### Post by sanderj on 2010-12-27
> **VonSpyder said:**
> "Dec 27 14:00:57 machine-name kernel: [ 2591.024155] usb 1-1: new high speed USB device using ehci_hcd and address 7"

Ouch. I had expected more output. Maybe this means the Linux kernel doesn't know the device. 

[https://answers.launchpad.net/ubuntu/+source/linux/+question/132209](https://answers.launchpad.net/ubuntu/+source/linux/+question/132209) isn't very helpful either.

My last advice: google for "0438:ac14" and set a google alert on it; maybe update will follow

---

### Post by VonSpyder on 2010-12-27
yeah it seems like for the first time ever i have found a device that Ubuntu has total incompatability with. I dont wanna run windows...idont i dont i dont i dont....

---

### Post by BicyclerBoy on 2010-12-28
Why did you buy it then ??

[http://linuxtv.org/wiki/index.php/ATI/AMD](http://linuxtv.org/wiki/index.php/ATI/AMD)

There are plenty of supported tuner cards.

---

