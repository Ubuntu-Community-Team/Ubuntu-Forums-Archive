---
title: "slightly annoying F-spot behavior"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Pence on 2008-07-15
When I plug in and turn on my camera, it's detected and F-spot starts up, but it asks me which camera:
Canon PowerShot A75 on port usb:
or
Canon PowerShot A75 on port usb:002,006.
as far as I can tell, they behave exactly the same, but it's kind of annoying.

I read about using dmesg | tail to see what's happening, and it spits out stuff like this for the camera:

```
[36407.530867] usb 2-1: new full speed USB device using uhci_hcd and address 8
[36407.691012] usb 2-1: configuration #1 chosen from 1 choice
[36408.777508] usb 2-1: USB disconnect, address 8
[36411.742004] usb 2-1: new full speed USB device using uhci_hcd and address 9
[36411.906049] usb 2-1: configuration #1 chosen from 1 choice
[36421.658637] usb 2-1: USB disconnect, address 9
[36425.118627] usb 2-1: new full speed USB device using uhci_hcd and address 10
[36425.278843] usb 2-1: configuration #1 chosen from 1 choice

```

the address always increments when I turn off and turn on the camera. I'm not sure if that means anything though.

Thanks for your time.

---

