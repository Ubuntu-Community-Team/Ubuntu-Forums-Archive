---
title: "problems with usb headset"
date: 2010-06-12
forum: Multimedia Software
---

### Post by wal3 on 2010-06-12
Hello,
since using 10.04 I have a big problem with my usb headset (freetalk everyman)

1. Problem:
I cannot regulate the volume of the phones (output) anymore with gnome-volume-control. By default the volume is set to 100% which is way too loud. When I set it under 100% there is no sound at all. Values over 100% work.

2. Problem:
The X server is freezing iregulary when I connect the headset and disconnect it, Magic SysRq works.
I checked Xorg.0.log and found out that it recognizes the usb headset as keyboard:


(II) config/udev: Adding input device Generic FREETALK Everyman (/dev/input/event7)
(**) Generic FREETALK Everyman: Applying InputClass "evdev keyboard catchall"
(**) Generic FREETALK Everyman: always reports core events
(**) Generic FREETALK Everyman: Device: "/dev/input/event7"
(II) Generic FREETALK Everyman: Found keys
(II) Generic FREETALK Everyman: Configuring as keyboard
(II) XINPUT: Adding extended input device "Generic FREETALK Everyman" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "compaqeak8"
(**) Option "xkb_layout" "de,de"
(**) Option "xkb_variant" ",nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"



Jun  9 19:19:44 localhost kernel: [  371.116066] usb 2-6: new full speed USB device using ohci_hcd and address 4
Jun  9 19:19:44 localhost kernel: [  371.341244] usb 2-6: configuration #1 chosen from 1 choice
Jun  9 19:19:44 localhost kernel: [  371.358076] input: Generic FREETALK Everyman as /devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.3/input/input7
Jun  9 19:19:44 localhost kernel: [  371.358146] generic-usb 0003:1460:3286.0004: input,hidraw3: USB HID v1.00 Device [Generic FREETALK Everyman] on usb-0000:00:02.0-6/input3
Jun  9 19:19:45 localhost kernel: [  371.536865] usbcore: registered new interface driver snd-usb-audio

It works all fine under ubuntu 9.10.

I hope that someone can help me.
Thanks in advance.

kind regards
Mark.

---

### Post by wal3 on 2010-06-13
anyone? Do I have to mail Xorg mailing list?

---

### Post by lidex on 2010-06-13
Is this an upgrade?
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by wal3 on 2010-06-19
Thanks for your reply.

Only ~/.pulse existed.
I have removed it.  Did not help.

Isn't it problematic already that the headset is recognized at keyboard?

---

### Post by ahnise on 2010-09-16
I am having the same problem on 10.04. No mic working, and volume is off unless I set output level at or above 100%. Problem is occuring on new ubuntu 10.04 install on asus K42f laptop.

I have ubuntu 10.04 running on a dell mini 1012 and the same headset works perfectly.

---

### Post by ahnise on 2010-09-16
I rebooted my computer and the mic started working. However the volume is off except for a very small range at the top of the slider. 

Going into the Sound Preferences you can see the unamplifed setting is very close to the 100% setting defining this narrow range. Normally I would expect unamplified to be at the bottom of the slider. See included file.

---

### Post by lidex on 2010-09-24
> **ahnise said:**
> I rebooted my computer and the mic started working. However the volume is off except for a very small range at the top of the slider. 

Going into the Sound Preferences you can see the unamplifed setting is very close to the 100% setting defining this narrow range. Normally I would expect unamplified to be at the bottom of the slider. See included file.

Somewhat strange, yes. Have a look at this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)
Scroll to the section labelled "Volume range anomalies"

---

