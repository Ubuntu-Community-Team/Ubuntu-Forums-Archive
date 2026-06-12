---
title: "USB disconnect problem"
date: 2009-03-08
forum: Mythbuntu
---

### Post by raptorjr on 2009-03-08
I have a problem with a usb connected card reader. I'm using mythbuntu 8.10. This is what i get in the logs:

[55154.187594] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[55154.187602] usb 1-1: USB disconnect, address 14
[55154.190214] ftdi_sio 1-1:1.0: device disconnected
[55154.228245] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[55154.492014] usb 1-1: new full speed USB device using ohci_hcd and address 15
[55154.704649] usb 1-1: configuration #1 chosen from 1 choice
[55154.708648] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
[55154.708815] ftdi_sio: Detected FT232BM
[55154.708980] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB0

It is random when this occurs. It could take a few minutes to a hour. But it does occur several times every day. And it is a big problem for me. I found some old posts saying it was a kernel problem but it should be fixed now. Obviously not, or there is something else messing with my system.
This is the only thing that is connected with USB on my system, so it shouldn't be a power problem.

---

