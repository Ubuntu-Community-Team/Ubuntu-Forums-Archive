---
title: "MP3 player can't be mounted"
date: 2019-04-13
forum: Multimedia Software
---

### Post by claus on 2019-04-13
Hello,

today, I bought a new MP3 player ('Video Scooter' by Intenso), but Ubuntu doesn't mount the player. When I look under 'drives', the player has the address **/dev/sdb**, but I cannot mount it to **/media/claus/mp3-player**. I get an error message, saying 'No medium'.

```
lsusb
``` gives the output ```
Bus 002 Device 015: ID 071b:3203 Domain Technologies, Inc. Rockchip Media Player
```

```
dmesg:
[133930.016845] usb 2-2: Product: INTENSO VIDEO SCOOTER
[133930.016847] usb 2-2: Manufacturer: RockChip
[133930.016849] usb 2-2: SerialNumber: USBV1.00
[133930.017127] usb-storage 2-2:1.0: USB Mass Storage device detected
[133930.018423] usb-storage 2-2:1.0: Quirks match for vid 071b pid 3203: 400
[133930.018456] scsi host6: usb-storage 2-2:1.0
[133931.044640] scsi 6:0:0:0: Direct-Access     INTENSO  VIDEO  SCOOTER        PQ: 0 ANSI: 0 CCS
[133931.045022] sd 6:0:0:0: Attached scsi generic sg2 type 0
[133931.048248] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

The mount point is [B]/mnt/usb-INTENSO_VIDEO_SCOOTER_USBV1.00-0:0
[/B], but the directory /mnt/ is empty. :(

What can I do to solve this problem?

TIA,

Claus

---

### Post by yancek on 2019-04-13
Does the directory /media/clause/mp3-player exist?
What command did you use to try to mount it?  Did you try to access it in a file manager?
Do you have data (music files) on the player?
You also indicate a mount point directory in the /mnt directory, did you create that?

---

### Post by Holger_Gehrke on 2019-04-13
if [this]("https://www.intenso.de/produkte/mp3-player/videoscooter") is the player you've got, it doesn't have any built-in memory. There should have been a micro SD card in the package which should go in a slot on the left side of the device. Check the card in some other device just in case the problem is with the card ...

Holger

---

### Post by claus on 2019-04-14
> **yancek said:**
> Does the directory /media/clause/mp3-player exist?

Yep, I created it.

> **yancek said:**
> What command did you use to try to mount it?  Did you try to access it in a file manager?

I used 'sudo mount /dev/sdb /media/claus/mp3-player'. And yes, I did try to access it via file manager.

> **yancek said:**
> Do you have data (music files) on the player?

No, not yet.

> **yancek said:**
> You also indicate a mount point directory in the /mnt directory, did you create that?

No.

Claus

---

### Post by claus on 2019-04-14
> **Holger_Gehrke said:**
> if [this]("https://www.intenso.de/produkte/mp3-player/videoscooter") is the player you've got, it doesn't have any built-in memory. There should have been a micro SD card in the package which should go in a slot on the left side of the device. Check the card in some other device just in case the problem is with the card ...

Holger

Hello Holger,

thanks for your advice. I inserted the micro SD card, but unfortunately I don't have a card reader to check if the card is ok. On Monday, I will go to the store where I bought it (Saturn in Stuttgart) and see if they can help me. I once performed a reset of the player to its default state, because the player wasn't mounted, but this didn't help. :( Before I bought this player, I had another player from Intenso without a micro SD card, and this player was mounted without any problems.

Claus

---

### Post by claus on 2019-04-15
The MP3 player can now be mounted. The problem was that the micro SD card was not fully inserted in the slot; therefore the error message 'No medium'.

Thanks to all who responded.

Claus

---

