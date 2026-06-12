---
title: "Banshee Creative Zen V Plus MTP"
date: 2011-11-05
forum: Multimedia Software
---

### Post by Sami Lehtinen on 2011-11-05
Kind of solved, I decided that Banshee simply isn't working and started using Gnomad2 instead. Everything is now working as expected. (But Banshee is still broken!)

--

Hi,

For some strange reason we can't connect Banshee with Creative Zen Plus device. It seems that there is some kind of issue with connecting the device. I have tried many things and I got extensive logs.

First version information:
```

[Info  14:07:56.192] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC]

```Crash error message:
```

** (Banshee:4351): WARNING **: Error rescanning Purchased Music: No such file or directory
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
Stacktrace:

Segmentation fault

```Output of mtp-detect:

```

libmtp version: 1.1.0

Listing raw device(s)
Device 0 (VID=041e and PID=4152) is a Creative ZEN V Plus.
   Found 1 device(s):
   Creative: ZEN V Plus (041e:4152) @ bus 1, dev 6
Attempting to connect device(s)
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4152
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 1
      Device number: 6
      Device entry info:
         Vendor: Creative
         Vendor id: 0x041e
         Product: ZEN V Plus
         Vendor id: 0x4152
         Device flags: 0x00000001
Configuration 0, interface 0, altsetting 0:
   Interface description contains the string "MTP"
   Device recognized as MTP, no further probing.
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative Zen V Plus
   Device version: 1.11.01_0.05.09
   Serial number: C7C2470A0002FA9DC7C493380002FA9D
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
   Detected object size: 64 bits
   Extensions:
        microsoft.com: 1.0
        microsoft.com/WMPPD: 10.0
        microsoft.com/WMDRMPD: 10.1
        audible.com: 1.0
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1016: Set device property value
   1017: Reset device property value
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      de99: Audio WAVE Codec UINT32 data type enumeration: 85,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b901: WMA
      de99: Audio WAVE Codec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   300c: ASF
      de99: Audio WAVE Codec UINT32 data type enumeration: 353,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b904: Audible.com Codec
      da01: Unknown property UINT32 data type enumeration: 2, 3, 4,  GET/SET
      da02: Unknown property array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: Unknown property UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba03: Abstract Audio Album
      dc86: Representative Sample Data array of UINT8 data type byte array:  GET/SET
      dc81: Representative Sample Format UINT16 data type enumeration: 14337,  READ ONLY
      dc83: Representative Sample Height UINT32 data type range: MIN 0, MAX 112, STEP 1 READ ONLY
      dc82: Representative Sample Sise UINT32 data type range: MIN 0, MAX 20480, STEP 1 READ ONLY
      dc84: Representative Sample Width UINT32 data type range: MIN 0, MAX 128, STEP 1 READ ONLY
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 2304, STEP 1 GET/SET
      dc86: Representative Sample Data array of UINT8 data type byte array:  GET/SET
      dc81: Representative Sample Format UINT16 data type enumeration: 14337,  READ ONLY
      dc83: Representative Sample Height UINT32 data type range: MIN 0, MAX 170, STEP 1 READ ONLY
      dc82: Representative Sample Sise UINT32 data type range: MIN 0, MAX 20480, STEP 1 READ ONLY
      dc84: Representative Sample Width UINT32 data type range: MIN 0, MAX 170, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 3072, STEP 1 GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   300a: MS AVI
      de99: Audio WAVE Codec UINT32 data type enumeration: 17,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 16000, MAX 384000, STEP 1 READ ONLY
      de9d: Frames Per Thousand Seconds UINT32 data type range: MIN 6000, MAX 15000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 128, STEP 1 GET/SET
      de91: Total Bit Rate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      de9b: Video Four CC Codec UINT32 data type enumeration: 3,  READ ONLY
      de9c: Video Bit Rate UINT32 data type range: MIN 0, MAX 4000000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 128, STEP 1 GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   bb83: vCard3
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   be03: vCalendar2
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3000: Undefined Type
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3001: Association/Directory
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b802: Firmware
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 2018082816
      FreeSpaceInBytes: 613253120
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: C7C2470A0002FA9DC7C493380002FA9D
Special directories:
   Default music folder: 0x00000056
   Default playlist folder: 0x00004b53
   Default picture folder: 0x00000066
   Default video folder: 0x0000006a
   Default organizer folder: 0x00000062
   Default zencast folder: 0xffffffff
   Default album folder: 0x0000addc
   Default text folder: 0xffffffff
MTP-specific device properties:
   Friendly name: My Zen
   Synchronization partner: (NULL)
   Battery level 249 of 255 (97%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Microsoft Advanced Systems Format
   Audible.com Audio Codec
   Abstract Playlist file
   Abstract Album file
   JPEG file
   Audio Video Interleave
   VCard version 3
   VCalendar version 2
   Folder
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20111105 11:15:40Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>

WMPInfo.xml file contents:
<DeviceInfo>
    <WMP DeviceID="{0CE06679-B6EA-4637-AC1E-E18FB9846E53}" RelationshipID="{00ACA2FB-DDB1-4B59-9051-6234B4C78CD8}"/>
</DeviceInfo>

OK.

```When Banshee won't crash, it remains in this loop for ever and user UI hangs.

```

LIBMTP PANIC: failed to open session on second attempt
[Warn  14:24:57.049] Failed to load media-player-info file for 1
[Warn  14:25:32.288] Failed to load media-player-info file for 1
Device 0 (VID=041e and PID=4152) is a Creative ZEN V Plus.
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
[Warn  14:25:33.869] Failed to load media-player-info file for 1
LIBMTP PANIC: failed to open session on second attempt
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device

```And pro-tips fo help me with this situation? I have done fair share of Googling, and in some forums they claim that libmtp would be currently broken and wouldn't work with Zen V Plus.

 - Thanks!

---

