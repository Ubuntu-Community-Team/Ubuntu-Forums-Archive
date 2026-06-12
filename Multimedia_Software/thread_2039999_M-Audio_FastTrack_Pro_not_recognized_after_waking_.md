---
title: "M-Audio FastTrack Pro not recognized after waking from sleep"
date: 2012-08-10
forum: Multimedia Software
---

### Post by dewdrop_world on 2012-08-10
Lately, every time -- *every* time -- I wake my Ubuntu 12.04 machine from sleep, I can't use my M-Audio FastTrack Pro until I issue the following incantation:

```
sudo modprobe -r snd-usb-audio
sudo modprobe snd-usb-audio
```

The sequence is:

- Wake from sleep.
- Power up the M-Audio.
- ```
lsusb
``` and the M-Audio is shown.
- ```
aplay -l
``` and the M-Audio is **not** shown.

I would like to avoid the need to restart the usb-audio module.

Any tricks?

Thanks!
James

---

### Post by Arightwizard on 2012-08-10
I'm no expert, but I assume this should help,
Open the terminal, and type the following:

sudo su
echo snd-usb-audio >> /etc/modules
exit

and reboot/sleep/whatever, let me know if it's working.

BTW:
about the m-audio fast track pro, if you don't mind me asking, do you know of any place I could get it -new- for under $100? I recently bought a mic, but I'm still trying to get the fast track to use it.

---

### Post by dewdrop_world on 2012-08-10
> **Arightwizard said:**
> I'm no expert, but I assume this should help,
Open the terminal, and type the following:

sudo su
echo snd-usb-audio >> /etc/modules
exit

and reboot/sleep/whatever, let me know if it's working.

Okay, I think I see what that's doing. I'll see if it works next time.

At least, according to [1], /etc/modules should be used when resuming, not only booting.

> BTW:
about the m-audio fast track pro, if you don't mind me asking, do you know of any place I could get it -new- for under $100? I recently bought a mic, but I'm still trying to get the fast track to use it.

New for under $100? That's a stretch. Maybe ebay.

Well, I was talking about the fast track pro, which has two line/mic inputs and four outputs, plus S/PDIF. If you're looking for the regular FastTrack (one mic in, one line in, and two outputs IIRC), under $100 might be possible. Maybe try [http://www.pricegrabber.com](http://www.pricegrabber.com).

hjh

[1] [http://askubuntu.com/questions/161984/suspend-hibernate-not-working-on-a-toshiba-satellite-l300/167269#167269](http://askubuntu.com/questions/161984/suspend-hibernate-not-working-on-a-toshiba-satellite-l300/167269#167269)

---

