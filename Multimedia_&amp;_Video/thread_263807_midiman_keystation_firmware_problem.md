---
title: "midiman keystation firmware problem"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by mikezackles on 2006-09-23
I'm trying to get my midiman keystation 61 (the old one, not the 61es) to work using the midisport-firmware-1.2 firmware loader on dapper.  I'm using a soundblaster live for which I have compiled the emu10k1 driver alongside the snd-usb-audio module.  After installing the firmware loader, tail -f /var/log/messages just gives me
Sep 23 17:36:01 elton kernel: [ 1153.478335] usb 2-2: new full speed USB device using uhci_hcd and address 4
Sep 23 17:36:01 elton kernel: [ 1153.615557] usb 2-2: configuration #1 chosen from 1 choice
when I connect the keyboard.

Running
sudo fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSportKS.ihx -D /proc/bus/usb/002/004
gives me
can't modify CPUCS: Protocol error

I'm stumped!

---

### Post by mikezackles on 2006-09-24
In case anyone else has this problem, I dug out the original driver CD for the keystation and noticed that the driver is named USBKS1x1.SYS.  There isn't a 1x1 anywhere else on the keyboard or packaging.  I haven't tried using the keyboard yet, but loading the firmware via
sudo fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport1x1.ihx -D /proc/bus/usb/002/003
gives me no errors.  (I was originally trying to load MidiSportKS.ihx which is the firmware listed under Keystation and my hardware ids.)  I'll post again once I test the keyboard.

---

