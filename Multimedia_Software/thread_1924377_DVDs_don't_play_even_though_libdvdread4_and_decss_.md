---
title: "DVDs don't play even though libdvdread4 and decss are installed"
date: 2012-02-12
forum: Multimedia Software
---

### Post by mhellwig on 2012-02-12
Hello everyone. I have a vexing problem.

New Laptop, fresh Ubuntu install, Laptop doesn't come with an internal DVD drive. So USB drive hooked up that works fine on another Linux laptop (not running ubuntu).

So, like it says in the title, libdvdread4 is installed and I ran the script that installs the libdecss or whatever it's called.

When inserting a DVD (any DVD) and attempting to play it with mplayer, I get something like the following:

```

$ mplayer dvd://2
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://2.
libdvdread: Using libdvdcss version 1.2.11 for DVD access
There are 8 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00033426
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00033426)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0003832f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000383d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000f2455
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0010a81f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0010a853
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 2
audio stream: 0 format: ac3 (5.1) language: de aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
number of audio channels on disk: 2.
number of subtitles on disk: 0



Exiting... (End of file)

```so CSS does seem to work but it returns to the prompt immediately and doesn't play anything. playing that same title on that same DVD in that same USB Drive on my other laptop (running ARCH, guess that doesn't matter) will play the movie. Note that the drive (a liteon) has been firmware-flashed to be region code free.

dmesg upon trying to play reads like so:

```

[ 1421.253816] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1421.253836] sr 2:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 1421.253851] sr 2:0:0:0: [sr0]  Add. Sense: Read of scrambled sector without authentication
[ 1421.253870] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 03 83 d6 00 00 02 00 00 00
[ 1421.253901] end_request: I/O error, dev sr0, sector 921432

```all the posts I could find that had the same dmesg error were resolved by correctly installing libdvdread and/or decss. But that does not seem to be my problem.

Any help?

---

### Post by inobe on 2012-02-12
not much help here but a shot in the dark.

try restarting without the device plugged in, when started up plug it in.

if you've done that already, try the opposite, remove any other usb devices.

curious about it being /dev/sr0, what other devices doe's this laptop have?

---

