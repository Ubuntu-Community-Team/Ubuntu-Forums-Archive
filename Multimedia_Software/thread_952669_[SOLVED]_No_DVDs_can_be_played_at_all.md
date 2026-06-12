---
title: "[SOLVED] No DVDs can be played at all"
date: 2008-10-19
forum: Multimedia Software
---

### Post by adm1968 on 2008-10-19
I have Totem, Kaffeine, MPlayer, SMPlayer, VLC all installed, with all codecs I know of under Ubuntu 8.04

None of my commercial DVDs can be played using any of them ...

Is there anything absolutely essential that I may have overlooked?

Many thanks in advance

---

### Post by mc4man on 2008-10-19
You should ck and see if you've installed libdvdcss2. If so then ck. and see if a region has been set on the drive.

If libdvdcss2 hasn't been installed then either add medibuntu as a software source or go here and direct install latest ver.

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)  
( libdvdcss2_1.2.10-0.2medibuntu1   '10-Sep-2008 21:30 	 36K' is the latest for i386

to add medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To ck. if region has been set (only needs to have been set once
install regionset
run from terminal with a dvd in the drive
regionset

Should say 'set' around line 4 (type: SET

---

### Post by xnostradamusx on 2008-10-19
are you sure you are using a dvd rom not a cd rom only?

---

### Post by adm1968 on 2008-10-20
> **mc4man said:**
> You should ck and see if you've installed libdvdcss2. If so then ck. and see if a region has been set on the drive.

If libdvdcss2 hasn't been installed then either add medibuntu as a software source or go here and direct install latest ver.

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)  
( libdvdcss2_1.2.10-0.2medibuntu1   '10-Sep-2008 21:30 	 36K' is the latest for i386

to add medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To ck. if region has been set (only needs to have been set once
install regionset
run from terminal with a dvd in the drive
regionset

Should say 'set' around line 4 (type: SET

Many thanks!
I updated my sources with Medibuntu, and things seem now OK

Cheers!

---

