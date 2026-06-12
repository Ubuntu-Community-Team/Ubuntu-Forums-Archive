---
title: "Problems with BUFFALO WLI-U2-KG54-AI Wireless USB card"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by lunix- on 2010-04-29
Hi guys!
I'm trying to get an wireless usb adapter to work, and I'm having some problems. Ubuntu doesn't autodetect it, and finding drivers that work is difficult. I did try to make it work on a win7 computer too, without luck.
[This is how the little bugger looks like]("http://www.trustedreviews.com/inline_image/3038")

I have got a d-link card too, this one ubuntu autodetects, and "ifconfig wlan0 up" and its up and running. But things are not that easy with the Buffalo one.

I'll paste the last dmesg in hope that there is someone out there that can see what the problem is. 

Im afraid I'll have to use ndiswrapper, but if it doesnt work on win7 then it will not work on ubuntu+ndiswrapper either I guess?

Maybe the card is even broken?

```
[ 2757.660021] usb 2-2: new high speed USB device using ehci_hcd and address 9
[ 2757.846875] usb 2-2: configuration #1 chosen from 1 choice
[ 2757.879325] input: BUFFALO WLI-U2-KG54-AI as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input8
[ 2757.879440] generic-usb 0003:0411:006C.0004: input,hidraw1: USB HID v1.00 Keyboard [BUFFALO WLI-U2-KG54-AI] on usb-0000:00:1d.7-2/input0
[ 2767.049583] usb 2-2: USB disconnect, address 9
[ 2767.380023] usb 2-2: new high speed USB device using ehci_hcd and address 10
[ 2767.565565] usb 2-2: configuration #1 chosen from 1 choice
[ 2767.565930] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2767.566048] usb-storage: device found at 10
[ 2767.566051] usb-storage: waiting for device to settle before scanning
```

Anyone able to help?:confused:

---

### Post by MiroDz on 2010-06-04
There is a small switch on the side of the device, use needle or  something similar to switch it to another position. Be carefull as it's  quite easy to break the switch. That switch chooses between wifi and  flash-memory function of the device. Mine work's well under Ubuntu  (since 9.04, maybe even 8.04).

---

### Post by lunix- on 2010-06-15
Thanks lol, that could definitely be the solution
If that doesnt work, Ill consider it dead, and let my trainees dissect it muahahaaa:twisted:

---

### Post by derver on 2011-02-10
> **MiroDz said:**
> There is a small switch on the side of the device, use needle or  something similar to switch it to another position. Be carefull as it's  quite easy to break the switch. That switch chooses between wifi and  flash-memory function of the device. Mine work's well under Ubuntu  (since 9.04, maybe even 8.04).

Thank you. I'm new and I had the same problem, but your simple answer helped me. A thousand thanks.

---

