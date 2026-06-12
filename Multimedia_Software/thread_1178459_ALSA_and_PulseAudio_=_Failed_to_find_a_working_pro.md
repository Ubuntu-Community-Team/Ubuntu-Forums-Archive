---
title: "ALSA and PulseAudio = Failed to find a working profile"
date: 2009-06-04
forum: Multimedia Software
---

### Post by teel on 2009-06-04
Hi,
When upgraded to new Ubuntu (sometimes I feel it is a downgrade in
terms of functionality) I can't make my Line6 PODxt working. When I
turn the device on this is what my syslog says:

Jun  4 20:20:26 tomek-desktop kernel: [ 1931.020026] usb 3-2: new full speed USB device using ohci_hcd and address 2
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.282807] usb 3-2:
configuration #1 chosen from 1 choice
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.379611] line6usb driver
version 0.8.1
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.380981] line6usb 3-2:1.0:
Line6 PODxt found
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403072] line6usb 3-2:1.0:
Line6 PODxt now attached
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403077] Line6 device 0: PODxt:0
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403080] Line6 device 1: (not used)
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403082] Line6 device 2: (not used)
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403083] Line6 device 3: (not used)
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403085] Line6 device 4: (not used)
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403086] Line6 device 5: (not used)
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403088] Line6 device 6: (not used)
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403090] Line6 device 7: (not used)
Jun  4 20:20:27 tomek-desktop kernel: [ 1931.403123] usbcore:
registered new interface driver line6usb
Jun  4 20:20:27 tomek-desktop pulseaudio[3801]: module-alsa-card.c:
Failed to find a working profile.
Jun  4 20:20:27 tomek-desktop pulseaudio[3801]: module.c: Failed to
load  module "module-alsa-card" (argument: "device_id=1
name=usb_device_e41_5044_noserial_if0_sound_card_0
card_name=alsa_card.usb_device_e41_5044_noserial_if0_sound_card_0
tsched=0"): initialization failed.

In 8.10 it worked out of the box.

I have no bloody idea where to start debuggin from, could you please
give a hint?
ALSA 1.0.18, PulseAudio 0.9.15, kernel 2.6.28-11

Best regards,
Tomek

---

