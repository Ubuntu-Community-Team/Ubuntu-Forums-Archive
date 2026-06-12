---
title: "Hard Drive problem"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by micah1104 on 2010-09-19
I have a desktop computer with Ubuntu 10.10 Beta installed on it, I have a 200 GB hard drive that I want to use with VirtualBox, but I can't because the hard drive won't mount because it has a lot of bad sectors, I tried formatting the drive with Disk Utility and it gave me this error:

Error formatting drive

An error occurred while performing an operation on "200 GB Hard Disk" (ATA ST3200822AS): The operation failed

Details:
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sda: Input/output error;

I tried doing it with GParted but the drive does not show up in there, it just shows my drive and my backup drive, does anyone know how to fix this?

---

### Post by robsoles on 2010-09-20
Playing with a drive that has bad sectors is just asking for data loss and headaches - I'm afraid the best way to fix this is to buy a shiny new HDD with as long a warranty period as you can get without paying exorbitant fees.

Sorry.

---

### Post by Mark Phelps on 2010-09-20
Questions about using the 10.10 Beta belong in the Maverick Development forum, not here.

This forum is reserved for released versions of Ubuntu.

---

### Post by Quackers on 2010-09-20
I would agree with Robsoles absolutely. A HDD with bad sectors just should not be trusted. And unless it's in a laptop they are pretty cheap nowadays.

---

### Post by Iowan on 2010-09-20
Moved to Maverick Meerkat Testing and Discussion

---

### Post by recluce on 2010-09-20
I do not believe that it is worth anybodys time to try to diagnose installation trouble with a piece of failing hardware. I have no idea where you are located, but in North America, a cheap internal hard drive is less than $50 new.

Replace that piece of junk and come back if it still doesn't work.

---

