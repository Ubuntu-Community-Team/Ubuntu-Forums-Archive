---
title: "dvdbackup: Error reading MENU VOB"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by yang on 2007-02-12
I installed dvdbackup and tried using it on my DVD (not a copy-protected or encrypted DVD - it's just my dance troupe's recording). I get the below output. My hardware is a Dell D600 Latitude laptop. If this is too out-of-scope for this forum, suggestion of another more targeted forum would be appreciated. Thanks in advance for any help.

```

$ dvdbackup -M -v 2 -i /dev/dvd -o dt-fa07-dvdrip

libdvdread: Using libdvdcss version 1.2.5 for DVD access







File sizes for Title set 0 VIDEO_TS.XXX

IFO = 20480, MENU_VOB = 867991552, BUP = 20480

At top of loop

After opening files

After Menu VOB check

After Menu Title VOB check

After Menu Title BUP check







File sizes for Title set 1 i.e.VTS_01_X.XXX

IFO: 57344, MENU: 0

VOB 1 is 1073565696

VOB 2 is 1073565696

VOB 3 is 1073565696

VOB 4 is 265795584

BUP: 57344

Bottom of loop



libdvdread: Attempting to retrieve all CSS keys

libdvdread: This can take a _long_ time, please be patient



libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000123

libdvdread: Elapsed time 0

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000678d9

libdvdread: Elapsed time 0

libdvdread: Found 1 VTS's

libdvdread: Elapsed time 0

Error reading MENU VOB

Mirror of VMG failed

Mirror of DVD failed

```

---

