---
title: "cannot get sansa express working as MTP device with amarok"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by mercer77 on 2008-02-28
Hello, 
There are some other threads on this, and I've tried all the advice with no joy. When I plug the Sansa Express in, it mounts ok. When I run a mtp-detect, it gives me an "unsafe removal" dialogue box. If I try to connect to it in Amarok, the program sometimes freezes up and the only way I can recover it is to reboot. It's as if Ubuntu is fighting with itself over whether the Sansa is an MTP device or a simple USB disk. The Sansa works fine in Windows, where I managed to upgrade the firmware to the latest US version (which unlocked the FM radio which this model isn't supposed to have!!)

Many thanks for any help.

Neil

Here's the result of running mtp-detect. As a relative newbie this doesn't mean too much to me!

> libmtp version: 0.2.5

Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 0781
   idProduct: 7460
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000046
Microsoft device descriptor 0xee:
        0000: 1203 4d00 5300 4600 5400 3100 3000 3000   ..M.S.F.T.1.0.0.
        0010: 0100                                      ..
Device info:
   Manufacturer: Sandisk
   Model: Sansa Express
   Device version: 01.01.05A
   Serial number: 0002FA821A7B839D0002FA821A7AC785
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMDRMPD: 10.1; microsoft.com/WMPPD: 10.0; microsoft.com/WMPPD: 11.0; audible.com: 1.0
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   101b: Get partial object
   100b: Delete object
   100c: Send object info
   100d: Send object
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   9802: Get object property description
   9801: Get object properties supported
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
   100f: Format storage
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9202: Report Acquired Items
   9203: Get transferable playlist types
   97f1: Unknown (97f1)
   97f2: Unknown (97f2)
   97f3: Unknown (97f3)
   97f4: Unknown (97f4)
   1010: Reset device
Events supported:
   0x4004
   0x4005
Device Properties Supported:
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd402: Friendly Device Name
   0xd401: Synchronization Partner
   0x5001: Battery Level
   0xd405: Device Icon
   0xd100: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
   3008: MS Wave
   b901: WMA
   300c: ASF
   3001: Association/Directory
   ba05: Abstract Audio Video Playlist
   3801: JPEG
   3807: GIF
   3804: BMP
   ba03: Abstract Audio Album
   3000: Undefined Type
   b904: Audible.com Codec
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 1022623744
      FreeSpaceInBytes: 223657984
      FreeSpaceInObjects: 4294967295
      StorageDescription: Internal Memory
      VolumeIdentifier: 0002FA821A7B839D0002FA821A7AC785
   StorageID: 0x00020001
      StorageType: 0x0004
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 2032664576
      FreeSpaceInBytes: 2024275968
      FreeSpaceInObjects: 4294967295
      StorageDescription: Expansion Card
      VolumeIdentifier: 8050069E
Special directories:
   Default music folder: 0x00000075
   Default playlist folder: 0x00000320
   Default picture folder: 0x00000000
   Default video folder: 0x00000000
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00000000
   Default album folder: 0x0000007d
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: (NULL)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   RIFF WAVE file
   Microsoft Windows Media Audio
   Microsoft Advanced Systems Format
   JPEG file
   GIF bitmap file
   BMP bitmap file
   Audible.com Audio Codec
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)

It repeats this many times, so I've edited it to the end...
> Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_File_To_File_Descriptor(): Could not get file from device.
Error 2: (Look this up in ptp.h for an explanation.)
PTP: Closing session
ERROR: Could not close session!
OK.

---

### Post by mercer77 on 2008-02-29
hello, sorry if I sound impatient, but can anyone help with this? I've got a three GBs worth or  mp3 to fill, and unless I can sort it out I'm going to have to fire up my collection in Windoze to do it!

Many thanks...
Neil

---

### Post by mercer77 on 2008-03-02
For now I've managed to get the sansa express working in Amarok as a standard USB media device (I think this means it's working as an MSC device). It's not ideal because I really want to be able to put playlists on, but at least I can get music on there for the time being.

having done a little bit of further reading around, it appears that for some reason the MTP drivers cannot cover this problem which is a shame. I've been gradually trying to switch to ubuntu from windows over the last few months. It's generally been great, but sometimes the simplest things can drive you insane!

---

### Post by locketine on 2008-03-06
I have the same problem with my Sansa e260. Well mine buggers out alot faster.
> PTP: request code 0x1015 sending req wrote only 140736812617648 bytes instead of 16
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)
WMPInfo.xml Does not exist on this device
PTP: Closing session
usb_clear_halt() on INTERRUPT endpoint: Connection timed out


MSC mode works pretty well but I'd really like to use the nice extra features provided by MTP mode.

I'm pretty sure you can just copy over playlists from amarok to the Sansa and use them directly. If you can't with the default firmware throw rockbox on it.

---

### Post by mercer77 on 2008-03-10
> **locketine said:**
> I have the same problem with my Sansa e260. Well mine buggers out alot faster.


MSC mode works pretty well but I'd really like to use the nice extra features provided by MTP mode.

I'm pretty sure you can just copy over playlists from amarok to the Sansa and use them directly. If you can't with the default firmware throw rockbox on it.


I've looked into rockbox but it's not available on the sansa express, and it doesn't look likely to happen anytime soon. Interesting what you said about copying playlists across, I will give that a go!

---

