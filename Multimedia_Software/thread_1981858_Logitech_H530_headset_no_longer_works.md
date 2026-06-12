---
title: "Logitech H530 headset no longer works"
date: 2012-05-17
forum: Multimedia Software
---

### Post by enigma32 on 2012-05-17
Hello,

My Logitech H530 USB headset used to work with my desktop (running 10.04/Lucid because it actually works and is LTS), however sometime in the past six months it stopped working. It still works fine on my Ubuntu laptop. I'm guessing there was an update to 10.04 in the past six months that caused the problem.

dmesg says:
```
[  835.708890] usb 3-3: new full speed USB device using xhci_hcd and address 0
[  835.730040] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
[  835.730475] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
[  835.730805] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
[  835.734718] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  835.735268] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  835.735578] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  835.735729] usb 3-3: configuration #1 chosen from 1 choice
[  835.737178] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  835.737778] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  835.738113] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  835.742298] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
*(repeats last message about 20 times, with the timestamp changing slightly)*
[  835.762609] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:1c.1/0000:04:00.0/usb3/3-3/3-3:1.3/input/input7
[  835.762722] generic-usb 0003:046D:0A0B.0004: input,hidraw2: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:04:00.0-3/input3
[  835.776878] cannot submit datapipe for urb 0, error -22: internal error
*(repeats the internal error a couple hundred times)*
```

*sudo lsusb -v* shows: [http://pastebin.com/T7K5XVtw](http://pastebin.com/T7K5XVtw)  (this is the relevant chunk only)

*sudo pulseaudio --system -vvvv* shows: [http://pastebin.com/5yxF4UF9](http://pastebin.com/5yxF4UF9)  (I've omitted the detection of other devices previous to the one having a problem)

*alsamixer* can see both the source and the sink for the device; *pamon* sees only the source, and I can't get anything to show on the "volume meter" for the source.

*aplay* reports "Unable to install hw params" when I try to play a wav file directly to the device.


Motherboard (with onboard USB controllers) is Asus P8Z68-V Pro; should be Intel Z68 Express Chipset controller.


Anyone have any idea of how to deal with this? Upgrading to 12.04 is definitely not an option, based on what I've heard about it lately, and I'd prefer to stick to LTS.

Thanks!
-Matt

---

### Post by enigma32 on 2012-05-21
Bump.

Nobody on the pulseaudio irc chat seems to reply, and no one here seems to either?
Not sure where to go from here...

---

### Post by enigma32 on 2012-05-29
Bump.

:-(

---

