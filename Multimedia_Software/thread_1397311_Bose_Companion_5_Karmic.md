---
title: "Bose Companion 5 Karmic"
date: 2010-02-03
forum: Multimedia Software
---

### Post by gtechiii on 2010-02-03
So I'm using 9.10 everything is updated, I've tried all the tricks suggested for old editions of ubuntu and my Bose Companion 5 speakers are detected but wont play a sound. Any ideas?

---

### Post by worxfr on 2010-02-03
Same behavior...

It's strange, because, with an older karmic, it works !!

---

### Post by Rob Loach on 2010-02-17
Same here. The Bose 5 USB speakers use to work perfectly, but not anymore.

---

### Post by worxfr on 2010-02-17
I think, it came from with a kernel update !!

I will make some tests to understand our problem !

Did you have a 32bit or a 64bit version of karmic ?

---

### Post by [A]madeus on 2010-02-23
i got the same problem.

---

### Post by mr_skater99 on 2010-04-07
I've just bought these speakers and got home to find they dont work....
When i plug them in i see:

```
Apr  7 17:05:02 photon kernel: [499758.851286] usb 6-2: new full speed USB device using uhci_hcd and address 3
Apr  7 17:05:03 photon kernel: [499759.104144] usb 6-2: configuration #1 chosen from 1 choice
Apr  7 17:05:03 photon kernel: [499759.120044] 3:1:1: cannot get freq at ep 0x1
Apr  7 17:05:03 photon kernel: [499759.150142] generic-usb 0003:05A7:1020.0005: hiddev96,hidraw3: USB HID v1.10 Device [Bose Corporation Bose USB Audio] on usb-0000:00:1d.0-2/input2
Apr  7 17:05:03 photon pulseaudio[3332]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/sound/card1 (alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00) more often than 5 times in 10s
```

Any suggestions?

---

### Post by mr_skater99 on 2010-04-07
Mine are now working - I've changed two things - not sure which fixed it.

I turned off my previous onboard soundcard in the bios

And the volume in the mixer needs to be almost 100%  If i turn it down more than 2 - 3 notches the speakers have no sound again.  

Very strange - but i use the bose control for the volume anyways.  So suits me fine.

Hope this helps.

---

### Post by [A]madeus on 2010-05-17
Thanks [mr_skater99]("http://www.uluga.ubuntuforums.org/member.php?u=150288")
i'll try your advise.

(Edited)
i just happened to find a workaround solution as following.

> Execute "pulseaudio -k" to restart pulseaudio, then the Bose device
appears in the System->Preferences->Sound dialog, and it may be selected
as the output device.

More detail in this [link]("http://lists.fedoraproject.org/pipermail/test/2009-October/086049.html").

---

