---
title: "DVD read errors on Ubuntu, but works on Vista :O"
date: 2009-10-29
forum: Multimedia Software
---

### Post by piovisqui on 2009-10-29
Hi.

I have many DVDs with videos and I've just bought a 1TB HD. I'm trying to transfer the DVDs to the HD, however Ubuntu does not read them. On Windows Vista ALL DVDs are readable and the videos play fine. dmesg show messages like that: 

[ 4571.909149] sr0: rw=0, want=6292700, limit=2097151
[ 4571.909152] attempt to access beyond end of device
[ 4571.909154] sr0: rw=0, want=6292704, limit=2097151
[ 4571.909157] attempt to access beyond end of device
[ 4571.909160] sr0: rw=0, want=6292708, limit=2097151
[ 4571.909163] attempt to access beyond end of device
[ 4571.909166] sr0: rw=0, want=6292712, limit=2097151
[ 4571.909169] attempt to access beyond end of device
[ 4571.909171] sr0: rw=0, want=6292716, limit=2097151
[ 3853.611092] Buffer I/O error on device sr0, logical block 969753
[ 3853.611096] attempt to access beyond end of device
[ 3853.611098] sr0: rw=0, want=3879020, limit=2097151
[ 3853.611099] Buffer I/O error on device sr0, logical block 969754
[ 4571.909182] sr0: rw=0, want=6292692, limit=2097151
[ 7066.735453] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 7066.735462] ISOFS: changing to secondary root
[ 7107.932669] attempt to access beyond end of device
[ 7107.932675] sr0: rw=0, want=8606952, limit=2097151
[ 7107.932677] __ratelimit: 200 callbacks suppressed
[ 7107.932679] Buffer I/O error on device sr0, logical block 2151737
[ 7107.932682] attempt to access beyond end of device


I mount the DVDs with "mount -t auto" or "-t iso9660"

May someone help me?

---

### Post by piovisqui on 2009-10-30
Anyone? :(

---

### Post by jochen-02 on 2010-09-20
> **piovisqui said:**
> Anyone? :(

Did you manage to solve the problem meanwhile? I have no solution, only the same problem.

---

### Post by kaajd on 2010-09-21
Are you trying to copy a DVD-Video directly by copy-pasting the files and folders? This will fail every time due to the copy-protection built into commercial DVD-Video's.
I'm assuming you can watch the video on linux? In VLC or Totem Movie player? Meaning you have the necessary dvd decoding libs installed, libdvdread and/or libdvdcss. After that you can use K9Copy or DVDRip to create a backup of your DVD on your HDD.

I accept no responsibility for illegal use of this advice, this is intended for backup of self-owned DVD's only!

I may be missing some steps in the backup process but thats the main idea. You cannot just backup the files directly, they are protected with read errors, have to use a program that understands the video stream in the files.

---

### Post by andreaplanet on 2010-10-31
Same problem. Ubuntu Lucid 10.04 amd64 with ext4. Limit is 1 GByte.

[24168.595681] attempt to access beyond end of device
[24168.595683] sr0: rw=0, want=7875984, limit=2097151

I can read the DVD using GnomeBaker (create an ISO) or through a Virtual Machine running Windows XP or a fresh install of Ubuntu Maverick 10.10.

---

