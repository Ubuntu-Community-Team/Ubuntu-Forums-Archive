---
title: "mp3 player undetected"
date: 2010-05-07
forum: Multimedia Software
---

### Post by a z on 2010-05-07
hi everyone,
i love 10.4 so far, but my Sansa Clip+ 4gb mp3 player isn't detected at all in nautilus. my usb memory stick shows up nicely though. i should also mention, this same mp3 player is detected just fine on my work computer (pclinuxos - lxde) - rrrr....

any thoughts?

---

### Post by unmole on 2010-05-07
Can you plug in your Clip and post the output of ```
dmesg |tail
```

Also, do you have any idea about the firmware version you are using?

---

### Post by a z on 2010-05-07
i will try that tonight.
thank you

---

### Post by a z on 2010-05-07
here's what i got:

dmesg |tail
[149833.264060] wlan0: no IPv6 routers present
[150035.596153] hub 2-0:1.0: unable to enumerate USB device on port 1
[150037.232131] usb 2-1: new full speed USB device using uhci_hcd and address 14
[150037.405511] usb 2-1: configuration #1 chosen from 1 choice
[150037.428331] scsi6 : SCSI emulation for USB Mass Storage devices
[150037.432720] usb-storage: device found at 14
[150037.432727] usb-storage: waiting for device to settle before scanning
[150042.433293] usb-storage: device scan complete
[150063.112104] usb 2-1: reset full speed USB device using uhci_hcd and address 14
[150064.060192] usb 2-1: reset full speed USB device using uhci_hcd and address 14

any clues?

---

### Post by unmole on 2010-05-08
Are you able to mount the player on other systems? I got messages like that when my USB drive got corrupted and I had to format it. DON'T format your Clip though. I dunno if if it can be restored.

---

### Post by a z on 2010-05-10
yep, 
as i stated initially, it's detected/mounted just fine on other computers - just ignored on my 10.4 box.
thanks again for any ideas, i'd hate to throw the baby out with the usb-bathwater.
a z

---

### Post by a z on 2010-05-16
PLEASE,
once again, my sansa clip+ mp3 player is completely undetected in my fresh 10.4 install.
other facts:
* same player IS detected in windows and another (non-ubuntu) linux computer
* yes, i've updated my firmware, and also tried setting its USB-mode to MSC - no dice

man, i know this forum moves so fast that this post will be buried in no time, but i really love ubuntu, and streaming/ripping internet radio is one of my favorite things to do. that makes this sort of a deal-breaker for me.

please help

ps, one more fun-fact:
* i also set up Lubuntu (10.4 w/lxde) on 2 other boxes an encountered the EXACT same issue - a kernel-thing maybe?

---

### Post by MartyBuntu on 2010-05-16
This is a peculiar thing with Sansas, same with my Sansa E250...try this:

With the clip turned off, plug it into your computer
Wait 20 seconds
Unplug the USB cable from your computer, but leave the other end plugged into the Clip
Quickly plug the USB back into the computer

Does it show up now?

---

### Post by a z on 2010-05-16
whew!

no, the unplug-trick didn't work, but it gave me another idea:
if i'm logged in, then plug it in i get nothing, 
but if i log out -plug it in- THEN log back in with it already connected, viola!

thanks for the suggestions.

hope this is also helpful for other folk's usb detection/mounting issues

a z

---

