---
title: "problems with mp3 player"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by Bart Ellebaut on 2008-02-26
Hey, 
I seem to have a problem with my mp3/mp4 player. (MPMAN - MP-CS155)
(K)ubuntu does not recognize it.

I have looked at many threads, but nothing has helped yet.
 some interresting thing:

```

bart@bart-laptop:~$ sudo mount -t vfat /dev/sda /media/mp3player
mount: apparaat /dev/sda bestaat niet

```
```

bart@bart-laptop:~$ dmesg | tail
[22423.148000] usb 3-3: new high speed USB device using ehci_hcd and address 9
[22424.020000] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[22424.132000] usb 3-3: new high speed USB device using ehci_hcd and address 10
[22425.004000] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[22425.116000] usb 3-3: new high speed USB device using ehci_hcd and address 11
[22425.524000] usb 3-3: device not accepting address 11, error -71
[22425.636000] usb 3-3: new high speed USB device using ehci_hcd and address 12
[22426.044000] usb 3-3: device not accepting address 12, error -71
[22511.088000] FAT: bogus number of reserved sectors
[22511.088000] VFS: Can't find a valid FAT filesystem on dev hda2.

```
```

bart@bart-laptop:~$ sudo fdisk -l

Schijf /dev/hda: 40.0 GB, 40007761920 bytes
255 koppen, 63 sectoren/spoor, 4864 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xf15d9943

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/hda1   *           1        4700    37752718+  83  Linux
/dev/hda2            4701        4864     1317330    5  Uitgebreid
/dev/hda5            4701        4864     1317298+  82  Linux wisselgeheugen

```

hope someone can help me.
thx
Bart

---

