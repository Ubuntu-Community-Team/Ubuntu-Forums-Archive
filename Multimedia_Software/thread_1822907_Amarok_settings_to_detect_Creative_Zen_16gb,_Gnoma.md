---
title: "Amarok settings to detect Creative Zen 16gb, Gnomad2 crashes"
date: 2011-08-11
forum: Multimedia Software
---

### Post by choclo on 2011-08-11
Hello there, am running 9.10 and can't get my Zen to work with it. 
Have done a lot of goggling to no avail, here's the output from mtp-detect.
Is there some sort of DRM restriction thing goin on here? I can't see whats on it, managed to get it to kinda work in banshee but then it didn't. 

```
100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1012: Set object protection
   1016: Set device property value
   1017: Reset device property value
   1019: Move object
   101b: Get partial object
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
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
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
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b901: WMA
      de99: Audio WAVE Codec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b904: Audible.com Codec
      da01: Unknown property UINT32 data type enumeration: 2, 3, 4,  GET/SET
      da02: Unknown property array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: Unknown property UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b982: MP4
      de99: Audio WAVE Codec UINT32 data type enumeration: 41222,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: Original Release Date STRING data type DATETIME FORM GET/SET
      dc9a: Album Name STRING data type GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: Use Count UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: Buy flag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba03: Abstract Audio Album
      dc86: Representative Sample Data array of UINT8 data type byte array:  GET/SET
      dc81: Representative Sample Format UINT16 data type enumeration: 14337,  READ ONLY
      dc83: Representative Sample Height UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc82: Representative Sample Sise UINT32 data type range: MIN 0, MAX 24576, STEP 1 READ ONLY
      dc84: Representative Sample Width UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba05: Abstract Audio Video Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba01: Abstract Multimedia Album
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 3328, STEP 1 GET/SET
      dc86: Representative Sample Data array of UINT8 data type byte array:  GET/SET
      dc81: Representative Sample Format UINT16 data type enumeration: 14337,  READ ONLY
      dc83: Representative Sample Height UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: Representative Sample Sise UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: Representative Sample Width UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 4992, STEP 1 GET/SET
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   300a: MS AVI
      de99: Audio WAVE Codec UINT32 data type enumeration: 85, 17, 1,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 8000, MAX 1536000, STEP 1 READ ONLY
      de9d: Frames Per Thousand Seconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: Total Bit Rate UINT32 data type range: MIN 0, MAX 4000000, STEP 1 READ ONLY
      de9b: Video Four CC Codec UINT32 data type enumeration: 844515635, 878070084, 1482049860, 808802372, 1196444237, 1145656920,  READ ONLY
      de9c: Video Bit Rate UINT32 data type range: MIN 0, MAX 3000000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: Representative Sample Data array of UINT8 data type byte array:  GET/SET
      dc81: Representative Sample Format UINT16 data type enumeration: 14337,  READ ONLY
      dc83: Representative Sample Height UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: Representative Sample Sise UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: Representative Sample Width UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   300c: ASF
      de99: Audio WAVE Codec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: Frames Per Thousand Seconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: Total Bit Rate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: Video Four CC Codec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: Video Bit Rate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: Representative Sample Data array of UINT8 data type byte array:  GET/SET
      dc81: Representative Sample Format UINT16 data type enumeration: 14337,  READ ONLY
      dc83: Representative Sample Height UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: Representative Sample Sise UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: Representative Sample Width UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b981: WMV
      de99: Audio WAVE Codec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: Audio Bit Rate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: Frames Per Thousand Seconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: Total Bit Rate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: Video Four CC Codec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: Video Bit Rate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: Representative Sample Data array of UINT8 data type byte array:  GET/SET
      dc81: Representative Sample Format UINT16 data type enumeration: 14337,  READ ONLY
      dc83: Representative Sample Height UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: Representative Sample Sise UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: Representative Sample Width UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: Sample Rate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: Number Of Channels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: Audio Bit Depth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   bb83: vCard3
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   be03: vCalendar2
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b802: Firmware
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3000: Undefined Type
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3001: Association/Directory
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: Object File Name STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: Non Consumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: Protection Status UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 16140402688
      FreeSpaceInBytes: 312705024
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 301100017192C2270002D9B162A10227
Special directories:
   Default music folder: 0x00000058
   Default playlist folder: 0x00043715
   Default picture folder: 0x00000068
   Default video folder: 0x0000006c
   Default organizer folder: 0x00000064
   Default zencast folder: 0x00000074
   Default album folder: 0x0003e9ae
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: My Zen
   Synchronization partner: {00000000-0000-0000-0000-000000000000}
   Battery level 255 of 255 (100%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   MPEG-4 Part 14 Container Format (Audio+Video Emphasis)
   Abstract Album file
   Abstract Playlist file
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20110811 11:20:09Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AQARMCfCknGx2QIAJwKhYgAAAAA=</UNIQUEID><PUBLICKEY private="1">n8JTFKudTvEjVWR9qexzjTy0ywCr/odvQ8/Yhx1W96v6KmWVI3B1fA==</PUBLICKEY><KEYDATA>IRcCMlg5wR2t54L1wULsx5cLDOc=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>jakVE7ADVpgevbATcnwkiYjMUWdM9A/uaK/4mUO0ihpPvlutK3r2Ag==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>Ky8NGdKVyI9iEpAmonRo6FBacV0=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.108.193</SECURITYVERSION><CERTIFICATE private="1">n8JTFKudTvEjVWR9qexzjTy0ywCr/odvQ8/Yhx1W96v6KmWVI3B1fAIEbMHV+PKVnRLZNxGya48blz9N69nQF2qXRuFnYa/V5e2HOn4QKo+Eth4Q</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative ZEN</NAME>
  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>
  <MODEL>DVP-FL0001</MODEL>
  <SECURITYLEVEL>2000</SECURITYLEVEL>
  <HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR>
  <HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR>
  <FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR>
  <FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR>
  <FEATURES>
    <CLOCK>2</CLOCK>
    <SECURECLOCK>
      <URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL>
      <PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY>
    </SECURECLOCK>
    <METERING>1</METERING>
    <LICENSE_ACQ>0</LICENSE_ACQ>
    <LICENSE_SYNC>1</LICENSE_SYNC>
    <ENCRYPTION>0</ENCRYPTION>
    <SYMMETRIC_OPT>1</SYMMETRIC_OPT>
  </FEATURES>
  <LIMITS>
    <MAXCHAINDEPTH>2</MAXCHAINDEPTH>
    <MAXLICENSESIZE>10240</MAXLICENSESIZE>
    <MAXHEADERSIZE>5120</MAXHEADERSIZE>
  </LIMITS><PUBLICKEY>01jSNo4LLYCkLWpnsvVOxk1wvxbm2krcn20LgpXL9Zf91opCNsMyAQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>DrK/bNN2aO5ImZHdepevdhlT6UePVcdaxTWOMvw/8RYKeQFjSPwWUw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>2085</AUTH_ID><PUBLICKEY>U3xlv/ZHjD1bOwjB+VKpZuAf3UI+x+5XtTYc7TvHKdQeGpyFrOmOEw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>iBzmFZxhy/VC9d2REO5iicO+dguqv8zhB7QPZe0JOj7BNKAwmrQoew==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>Ko25GwcWTT0R8xP4rS9+h4Z/EHX03y7Gb/281mD8U0nQGG3Rk9O+TA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>

WMPInfo.xml file contents:
<DeviceInfo>
    <WMP DeviceID="{6CFCC93D-D3CE-4710-9C8E-513D65E1DFFC}" RelationshipID="{00000000-0000-0000-0000-000000000000}"/>
</DeviceInfo>

OK.

```

Added this -> 
# Creative Zen
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4157", SYMLINK+="libmtp-%k", MODE="666" 
to etc/udev/rule.d/libmtp.rules in accordance with instructions here -> [http://ubuntuforums.org/showthread.php?t=643512](http://ubuntuforums.org/showthread.php?t=643512)
Amarok seems to have no add mtp devices capabilities with my version, what's going on here people? Could someone lend a hand please and thanks in advance!?!?!

---

### Post by choclo on 2011-08-13
I believe a bump after more than 24 hours is considered ok? :D

---

### Post by choclo on 2011-08-16
Anyone?

---

### Post by cottfcfan on 2011-08-18
What Zen are you using.
I have a Creative Zen xi-fi 16gb, anf it works perfectly with Banshee and Amarok, from 10.04 onward.
It could be that 9.10 is too old, and its not supported anymore.
Maybe time to upgrade.

---

