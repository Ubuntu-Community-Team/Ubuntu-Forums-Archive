---
title: "Android Banshee MTP internal vs. external microSD distinction limitation"
date: 2013-12-24
forum: Multimedia Software
---

### Post by alanwalterthomas on 2013-12-24
I have an LG-P716 cellphone.
It runs stock Android 4.2.1.
It also has 2 GB internal storage & I added a 32 GB microSD card.

I'd like to connect it to banshee. Banshee has an extension under "Devices Support" called "MTP Media Player Support" which allows me to sync my Android media with banshee's media.

Banshee recognizes the cellphone, but does not distinguish between the internal storage & the microSD card. Instead, there is a single entry for the device called "Music" that reports a size equal to the internal & microSD together.
Windows Media Player correctly distinguishes between "Internal Storage" & "SD Card". However, it seems that linux (after I installed mtp-tools) is capable of telling the difference. I ran "mtp-detect" and it returned this (entire output is at the end of this post)

```

Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 1914658816
      FreeSpaceInBytes: 539676672
      FreeSpaceInObjects: 1073741824
      StorageDescription: Internal storage
      VolumeIdentifier: (null)
   StorageID: 0x00020001
      StorageType: 0x0004 removable RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 31434539008
      FreeSpaceInBytes: 31417761792
      FreeSpaceInObjects: 1073741824
      StorageDescription: SD card
      VolumeIdentifier: (null)
Special directories:
   Default music folder: 0x00000001
   Default playlist folder: 0xffffffff
   Default picture folder: 0x00000006
   Default video folder: 0xffffffff
   Default organizer folder: 0xffffffff
   Default zencast folder: 0xffffffff
   Default album folder: 0xffffffff
   Default text folder: 0xffffffff
MTP-specific device properties:
   Friendly name: LG-P716
   Synchronization partner: LG-P716

```

Can anyone help me work around this, so that banshee sees both storage spaces as it ought to?

```

alan@DESKTOP:~$ mtp-detect
Unable to open ~/.mtpz-data for reading, MTPZ disabled.libmtp version: 1.1.6

Listing raw device(s)
Device 0 (VID=1004 and PID=631c) is a LG Electronics Inc. LG-E610/E612/E617G/E970/P700.
   Found 1 device(s):
   LG Electronics Inc.: LG-E610/E612/E617G/E970/P700 (1004:631c) @ bus 2, dev 39
Attempting to connect device(s)
Android device detected, assigning default bug flags
USB low-level info:
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 1004
   idProduct: 631c
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 2
      Device number: 39
      Device entry info:
         Vendor: LG Electronics Inc.
         Vendor id: 0x1004
         Product: LG-E610/E612/E617G/E970/P700
         Vendor id: 0x631c
         Device flags: 0x08008106
Configuration 0, interface 0, altsetting 0:
   Interface description contains the string "MTP"
   Device recognized as MTP, no further probing.
Device info:
   Manufacturer: LGE
   Model: LG-P716
   Device version: 1.0
   Serial number: 33dfb747
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; android.com: 1.0;
   Detected object size: 64 bits
   Extensions:
        microsoft.com: 1.0
        android.com: 1.0
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
   100a: Get thumbnail
   100b: Delete object
   100c: Send object info
   100d: Send object
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   1017: Reset device property value
   101b: Get partial object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9810: Get object references
   9811: Set object references
   95c1: Get Partial Object (64bit Offset)
   95c2: Send Partial Object
   95c3: Truncate Object
   95c4: Begin Edit Object
   95c5: End Edit Object
Events supported:
   0x4002
   0x4003
   0x4004
   0x4005
   0x400c
Device Properties Supported:
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0x5003: Image Size
Playable File (Object) Types and Object Properties Supported:
   3000: Undefined Type
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   3001: Association/Directory
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   3004: Text
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   3005: HTML
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   3008: MS Wave
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   3009: MP3
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   300b: MPEG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   3801: JPEG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   3807: GIF
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   380b: PNG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   b901: WMA
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   b902: OGG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   b903: AAC
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   b982: MP4
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   b984: 3GP
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   ba05: Abstract Audio Video Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   ba10: WPL Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   ba11: M3U Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   ba14: PLS Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   ba82: XMLDocument
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   b906: FLAC
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   300a: MS AVI
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   300c: ASF
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   3804: BMP
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
      dc48: Description STRING data type READ ONLY
      dc87: Width UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc88: Height UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc47: Date Authored STRING data type DATETIME FORM READ ONLY
   ba83: Microsoft Word Document
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   ba85: Microsoft Excel Spreadsheet (.xls)
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
   ba86: Microsoft Powerpoint (.ppt)
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc08: Date Created STRING data type DATETIME FORM READ ONLY
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 1914658816
      FreeSpaceInBytes: 539676672
      FreeSpaceInObjects: 1073741824
      StorageDescription: Internal storage
      VolumeIdentifier: (null)
   StorageID: 0x00020001
      StorageType: 0x0004 removable RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 31434539008
      FreeSpaceInBytes: 31417761792
      FreeSpaceInObjects: 1073741824
      StorageDescription: SD card
      VolumeIdentifier: (null)
Special directories:
   Default music folder: 0x00000001
   Default playlist folder: 0xffffffff
   Default picture folder: 0x00000006
   Default video folder: 0xffffffff
   Default organizer folder: 0xffffffff
   Default zencast folder: 0xffffffff
   Default album folder: 0xffffffff
   Default text folder: 0xffffffff
MTP-specific device properties:
   Friendly name: LG-P716
   Synchronization partner: LG-P716
libmtp supported (playable) filetypes:
   Folder
   Text file
   HTML file
   RIFF WAVE file
   ISO MPEG-1 Audio Layer 3
   MPEG video stream
   JPEG file
   GIF bitmap file
   Portable Network Graphics
   Microsoft Windows Media Audio
   Ogg container format
   Advanced Audio Coding (AAC)/MPEG-2 Part 7/MPEG-4 Part 3
   MPEG-4 Part 14 Container Format (Audio+Video Emphasis)
   Abstract Playlist file
   XML file
   Free Lossless Audio Codec (FLAC)
   Audio Video Interleave
   Microsoft Advanced Systems Format
   BMP bitmap file
   DOC file
   XLS file
   PPT file

WMPInfo.xml file contents:
<DeviceInfo>
    <WMP DeviceID="{3B876769-FCF2-4204-9F3D-67B78EF66EF4}" RelationshipID="{00000000-0000-0000-0000-000000000000}"/>
</DeviceInfo>

OK.
alan@DESKTOP:~$

```

---

### Post by alanwalterthomas on 2014-01-03
Nobody else has this problem?

---

### Post by alanwalterthomas on 2014-01-17
still a problem...

---

### Post by efflandt on 2014-01-18
Which Ubuntu version? I could not get MTP working properly in 12.04 no matter what I tried. Nautilus only shows root directories of either internal storage or microSD, nothing below that. With phone in PTP mode, Nautilus can see contents of internal storage, but nothing at all on microSD. So I resorted to using ConnectBot, SSHServer, AndFTP apps on phone so I could ssh, scp, sftp either way.

I put 13.10 on a new laptop and in that Nautilus (if that is what file manager is) can see everything on my Samsung S3 (which was running Android 4.1.2 then, but recently updated to 4.3). Note that image and music files on the phone cannot be opened directly from Ubuntu. Such files need to be copied or transferred to Ubuntu first, then they can be opened locally.

I wonder if something like **rsync** would work. I have not really used that much and cannot find an rsync command within the $PATH when I ssh to my phone. But it is my understanding that all you need on the server end (the phone) is just shell access, not necessarily an rsync daemon. SSHServer Android app can give ssh access to the phone (it can use openssh keys but default port for connection is 2222). The only thing I have not figured out is how to elegantly disconnect ssh from the phone since there is no logout, exit, or quit command and ^D just returns with no prompt, but does not actually disconnect. So I currently have to stop the SSHServer on the phone to disconnect. Although, scp and sftp have no issues disconnecting when finished.

---

### Post by alanwalterthomas on 2014-01-23
Sorry for omitting the basics, but it's Ubuntu 13.10 & banshee 2.6.1 with the Mass Storage Media Player Support & MTP Media Player Support.

---

### Post by krik2 on 2014-04-01
For Alan:
I'm solving now our problems... i hope:)
Ubuntu 12.04 LTS and LG-P700 Android 4.0.3, kern 3.0.8-perf.
I was able to connect the phone with guides found on-line (mtp-tools) and now my LG-Android connects and mounts himself automatically, seeble in Nautilus.
But till today i was not able to see my phone's sd-card on terminal, with 'ls' or 'cd' calls.

Was an absurd premissions error. 

I made the mistake to think: If i can't see anything as root, i can't see anything as 'user' (username of root, not root)...
In Terminal i tried to call as root:
**root@machine:/#** "nautilus 'mtp://[usb00x:00z]/' " (that is "sudo nautilus 'mtp://[usb00x:00z]/' ") nothing;
**root@machine:/# **"nautilus '/home/usernameofroot/.gvfs/mtp/SD-Card/" (that is "nautilus '/home/usernameofroot/.gvfs/mtp/SD-Card/") nothing;
then i exit from sudo-root in Terminal and everything works!!!

So try (no sudo):
```
nautilus '/home/usernameofroot/.gvfs/mtp/SD-Card/'
```
or
```
ls '/home/usernameofroot/.gvfs/mtp/SD-Card/
```
:guitar:

---

### Post by gustavo_fring on 2014-05-22
Hello, friend. Security Error: In this video we teach solve the problem Security Error on LG devices. is very easy to repair. repair security error lg phones easily. With few steps you will have your smartphone lg optimus repaired. Copy and paste this link into your browser: youtu.be/r5f-9uvu4Tk

---

