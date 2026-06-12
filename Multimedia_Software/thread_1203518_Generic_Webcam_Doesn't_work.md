---
title: "Generic Webcam Doesn't work"
date: 2009-07-03
forum: Multimedia Software
---

### Post by marianowo on 2009-07-03
Hi.
I try to use my generic and economic webcam :) and i can't do that.
I am a begginer with linux and ubuntu, but i'd drop my Windows Vista and i'm happy with this change. But... I need realy quickly to solve this problem because I have a work video conference soon.
I'd try with Camorama but when I run this program i receive this error:
```
Error (camorama)
Could not connect to video device (/dev/video0)
Please check connection
```

When I connect my cam in the USB port i write dmesg and I receive this message:
```
[41711.688845] usb 4-2: new full speed USB device using uhci_hcd and address 3
[41711.861217] usb 4-2: configuration #1 chosen from 1 choice
```


Can I run a generic bad quality webcam in my ubuntu?
This problem is about drivers?
Do I need to buy a especific webcam with Linux drivers? (For example Logitech).

Sory for my english. :)
Thank You Very Much.

---

### Post by sir_cheats_a_lot on 2009-07-06
please open a terminal, and issue the lsusb command, and then post the output.  This way we know what chip set we're dealing with, it might not be as generic as you think ;)  or it could be more generic then previously feared :lolflag:

but if you want a quick-fix solution without having to potentially jump through any hoops, the logitech quickcam chat supposedly works out of the box as of ubuntu hardy(8.04), and it's like $20 at wal-mart.

---

