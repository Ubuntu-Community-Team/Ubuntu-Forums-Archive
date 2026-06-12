---
title: "Can not find WIFI Network"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by DarkCore on 2006-07-06
Ubuntu can't find my wifi network. I know the device/driver work becuase the lights are on my device. (Can any one tell me how I can access my drive from Windows?) Then I can post the log.

---

### Post by Derek Djons on 2006-07-06
Windows cannot read the Linux file system as far as I know. So it isn't possible to read the content of your Linux partition from Windows. The best thing to do is to use an FAT32 formatted USB Stick.

---

### Post by DarkCore on 2006-07-06
Okay, then  what can I do to fix my wireless network?

---

### Post by diepruis on 2006-07-06
[QUOTE=Derek Djons]Windows cannot read the Linux file system as far as I know. So it isn't possible to read the content of your Linux partition from Windows. The best thing to do is to use an FAT32 formatted USB Stick.[/QUOTE]

There are programs and drivers that can, however they are unstable and I wouldn't recommend them (I lost data using the ext2 drivers). I'd post the URL but I can't remember it.

[QUOTE=DarkCore]Okay, then what can I do to fix my wireless network?[/QUOTE]

We need some more information to help with that, for example the card you're using (and its chipset if you know what it is), the output of "lspci -v", "iwconfig", "ifconfig" and what you've done so far to configure the network.

---

