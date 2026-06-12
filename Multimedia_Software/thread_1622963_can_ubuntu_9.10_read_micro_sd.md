---
title: "can ubuntu 9.10 read micro sd?"
date: 2010-11-16
forum: Multimedia Software
---

### Post by lohren michael on 2010-11-16
ubuntu 9.10 can't read micro sd? tried to read it using a card reader usb or sort of but it doesn't seem to be recognize... if ubuntu 9.10 can read micro sd using a usb card reader or something, how?

---

### Post by barbedsaber on 2010-11-16
When it's in a converter or card reader, a micro SD should show up the same as a normal SD card.
and 9.10 can read normal SD cards, so in answer to your question. yes.

what are you using to read the card (ie, what sort of card reader)

---

### Post by lohren michael on 2010-11-16
plugged the micro sd into ubuntu 9.10 via usb card reader or sort of but it doesn't recognized. it is recognized when i plugged it into ubuntu 10.4 or windows server 2003 with the same stuff. that ubuntu 9.10 computer that i used can read micro sd when the micro sd is plugged in into a certain type of samsung phone

---

### Post by wojox on 2010-11-16
Run 

```
lsusb
```

See if it notices it.

---

### Post by drs305 on 2010-11-16
Threads merged. Please do not post multiple threads on the same topic.

---

### Post by efflandt on 2010-11-16
Is it microSD (up to 2 GB) or microSDHC (larger than 2 GB)?  Some older computers or card readers may have trouble reading SDHC or microSDHC.

In the past I booted 9.10 live/install iso from 2 GB microSD in an SD adapter in an old Lexar USB SD card reader.  And it would also boot my early Athlon64 desktop from a built-in card reader (internally connected through USB).

It would not boot from the memory card slot on my laptop because that is a different type of unbootable block device (not USB mass-storage), but it could boot microSD in a USB adapter.  The built-in slot would mount SD or microSD in SD adapter, but could not cope with higher speed SD or SDHC.

---

