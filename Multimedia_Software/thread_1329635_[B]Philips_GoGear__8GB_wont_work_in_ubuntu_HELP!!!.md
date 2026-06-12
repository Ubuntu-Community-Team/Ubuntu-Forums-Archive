---
title: "[B]Philips GoGear  8GB wont work in ubuntu HELP!!![B/]"
date: 2009-11-17
forum: Multimedia Software
---

### Post by xenosaga456 on 2009-11-17
ya i got a 8GB Philips gogear and it wont work in ubuntu 9.10  it shows up and it reconizes it but the device will NOT show up on the desktop,computer or any media player



```
sudo lsusb
```


```
me@my-laptop:~$ sudo lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0471:084e Philips 
Bus 001 Device 003: ID 03f0:7b04 Hewlett-Packard 
Bus 001 Device 002: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 064e:a110 Suyin Corp. HP Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```



```
sudo mtp-detect
```



```
Listing raw device(s)
avoid probing device using kernel interface "uvcvideo"
   Found 1 device(s):
   Philips: GoGear SA6014/SA6015/SA6024/SA6025/SA6044/SA6045 (0471:084e) @ bus 0, dev 4
Attempting to connect device(s)
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 0471
   idProduct: 084e
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 4
      Device entry info:
         Vendor: Philips
         Vendor id: 0x0471
         Product: GoGear SA6014/SA6015/SA6024/SA6025/SA6044/SA6045
         Vendor id: 0x084e
         Device flags: 0x00000002
Microsoft device descriptor 0xee:
	0000: 1203 4d00 5300 4600 5400 3100 3000 3000	..M.S.F.T.1.0.0.
	0010: 0100                                   	..
Device info:
   Manufacturer: Philips 
   Model: Philips GoGear SA60XX
   Device version: PH05020F00
   Serial number: 0000000B6AF623F807110111510428A0
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
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
   100b: Delete object
   100c: Send object info
   100d: Send object
   100f: Format storage
   1010: Reset device
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   9810: Get object references
   9811: Set object references
   9802: Get object property description
   9801: Get object properties supported
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   101b: Get partial object
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
   0x4004
   0x4005
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd103: Revocation Info
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX 268435456, STEP 1 GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de92: BitRateType UINT16 data type enumeration: 0, 1, 2, 3,  GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
   b901: WMA
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX 268435456, STEP 1 GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de92: BitRateType UINT16 data type enumeration: 0, 1, 2, 3,  GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
   3008: MS Wave
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX 268435456, STEP 1 GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 1, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de92: BitRateType UINT16 data type enumeration: 0, 1, 2, 3,  GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
   3801: JPEG
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 320, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 240, STEP 1 GET/SET
   300a: MS AVI
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 320, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 240, STEP 1 GET/SET
      de97: ScanDepth UINT16 data type enumeration: 1,  READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 15000, MAX 30000, STEP 1 GET/SET
      de9b: VideoFourCCCodec UINT32 data type enumeration: 0, 1195724877, 861293911,  GET/SET
      de9e: KeyFrameDistance UINT32 data type range: MIN 1000, MAX 10000, STEP 1 GET/SET
      de9c: VideoBitRate UINT32 data type range: MIN 32768, MAX 2048000, STEP 1 GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc8c: Genre STRING data type GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 1, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dea1: EncodingProfile STRING data type GET/SET
   b981: WMV
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 320, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 240, STEP 1 GET/SET
      de97: ScanDepth UINT16 data type enumeration: 1,  READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 15000, MAX 30000, STEP 1 GET/SET
      de9b: VideoFourCCCodec UINT32 data type enumeration: 0, 1195724877, 861293911,  GET/SET
      de9e: KeyFrameDistance UINT32 data type range: MIN 1000, MAX 10000, STEP 1 GET/SET
      de9c: VideoBitRate UINT32 data type range: MIN 32768, MAX 2048000, STEP 1 GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc8c: Genre STRING data type GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 1, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dea1: EncodingProfile STRING data type GET/SET
   300c: ASF
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 320, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 240, STEP 1 GET/SET
      de97: ScanDepth UINT16 data type enumeration: 1,  READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 15000, MAX 30000, STEP 1 GET/SET
      de9b: VideoFourCCCodec UINT32 data type enumeration: 0, 1195724877, 861293911,  GET/SET
      de9e: KeyFrameDistance UINT32 data type range: MIN 1000, MAX 10000, STEP 1 GET/SET
      de9c: VideoBitRate UINT32 data type range: MIN 32768, MAX 2048000, STEP 1 GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc8c: Genre STRING data type GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 1, MAX 320000, STEP 1 READ ONLY
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dea1: EncodingProfile STRING data type GET/SET
   3001: Association/Directory
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc9a: AlbumName STRING data type GET/SET
   ba05: Abstract Audio Video Playlist
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   3000: Undefined Type
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   b802: Firmware
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   ba03: Abstract Audio Album
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc09: DateModified STRING data type DATETIME FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 1000000, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 1000000, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 10000000, STEP 1 READ ONLY
      dc9b: AlbumArtist STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 8065646592
      FreeSpaceInBytes: 7710429021
      FreeSpaceInObjects: 19259
      StorageDescription: Internal Storage
      VolumeIdentifier: 0000000B6AF623F807110111510428A0
Special directories:
   Default music folder: 0x00000000
   Default playlist folder: 0x00000000
   Default picture folder: 0x00000000
   Default video folder: 0x00000000
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00000000
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: Philips GoGear SA60XX
   Synchronization partner: Longhorn Sync Engine
   Battery level 100 of 100 (100%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   JPEG file
   Audio Video Interleave
   Microsoft Windows Media Video
   Microsoft Advanced Systems Format
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20091109 01:07:31Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>AG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AAAAC2r2I/gHEQERUQQooAAAAAA=</UNIQUEID><PUBLICKEY private="1">tIiEJXVLPLvEyxUiIDetv+YQIFWZyjkLwvkDygWbxG5BXaddiOayfA==</PUBLICKEY><KEYDATA>cmnq3kBBHdoljghbXLOt0vX62zc=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>QA7nG4xUEBEOWrAFPfSE6JyaCkkNrM+anvBmmeN5IFX2FP4SCbJjOA==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>fQMkBXgarIWJFIxYbpS0ojQopMc=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.107.107</SECURITYVERSION><CERTIFICATE private="1">tIiEJXVLPLvEyxUiIDetv+YQIFWZyjkLwvkDygWbxG5BXaddiOayfAIEa2svtpdjO7cUJE3zUTcXm8p7XNOgBkKB/VEJCfrUZWqeJI1/ZTzqoex8</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>SA60xx</NAME>
    <MANUFACTURER>Perception Digital Ltd</MANUFACTURER>
    <MAKE>Philips Audio & Multi Media Applications</MAKE>
    <DISTRIBUTOR>Koninklijke Philips Electronics N.V.</DISTRIBUTOR>
    <MODEL>00</MODEL>
    <SECURITYLEVEL>2000</SECURITYLEVEL>
    <HARDWARE_VER_MAJOR>02</HARDWARE_VER_MAJOR>
    <HARDWARE_VER_MINOR>00</HARDWARE_VER_MINOR>
    <FIRMWARE_VER_MAJOR>08</FIRMWARE_VER_MAJOR>
    <FIRMWARE_VER_MINOR>00</FIRMWARE_VER_MINOR>
    <FEATURES>
        <CLOCK>2</CLOCK>
        <SECURECLOCK>
            <URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL>
            <PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY>
        </SECURECLOCK>
        <METERING>1</METERING>
        <LICENSE_ACQ>0</LICENSE_ACQ>
        <LICENSE_SYNC>1</LICENSE_SYNC>
        <ENCRYPTION>1</ENCRYPTION>
        <SYMMETRIC_OPT>1</SYMMETRIC_OPT>
    </FEATURES>
    <LIMITS>
        <MAXCHAINDEPTH>5</MAXCHAINDEPTH>
        <MAXLICENSESIZE>10240</MAXLICENSESIZE>
        <MAXHEADERSIZE>5120</MAXHEADERSIZE>
    </LIMITS><PUBLICKEY>O/xY2BVO97/4QEvlk+ETiHxn13rWyg5HsWO/Uy3DHCQg7rowMRF0gw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>vgUBFIcCPVuNuYhGWODMqCH8XiNw83pAwS9S8KWZckb7T99BX4i+OQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>1743</AUTH_ID><PUBLICKEY>Q5qnbSHxftMJXBVdgoi0Ds8CrUgXgToCUcmJIz4LSDcycDSj2n5FfQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>cdq3bQ3V+qGBJXT52FXvDw4jVzret3LRWnpa6q7bMHiSeyZWfRuQMg==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>s9lZMSUkYRzjmE8Ju5CtPS6lclfC1BG7Np/QWoLoOXDlt4gYBywCdw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
OK.
```


i would really love some help please......

---

### Post by Drezliok on 2009-12-01
I tried to install the latest libmtp. I had to compile it from source, It's not working for me yet but I have an open thread on how to make my Rhythmbox use the new version instead of the old.

---

### Post by Fastjack77 on 2010-07-18
Hi xenosaga456,

My Philips mp3 player was working under Ubuntu 9 AMD64, but now that I'm using Ubuntu 10.04 AMD64 desktop, it's not detected anymore....

Retrograde sucking.

---

### Post by MattressVon on 2011-03-16
Hey everyone. If you install Clementine (the multi desktop port of Amoarok 1.4) and set your Phillips Go Gear player to MTP mode, it will load all your tracks on our player with the correct tags. You need to have the latest firmware upgrade, but Clementine works well with Phillips GoGear players. It uses the sqylite database so it plays well with GoGear players.

1.) Upgrade firmware (I did this via windows 7 on my netbook dual boot, but there are instructions around for linux)

2.) Install Clementine:
sudo add-apt-repository ppa:me-davidsansome/clementine
sudo apt-get update
sudo apt-get install clementine

3.) Install Easytag

sudo apt-get install easytag

4.) Back up your tracks to your computer and reformat your player via the reformat venue option on the player.

5.) Point Clementine at your library:

Tools>preferences>music library

6.) Open your music in easytag and remove all comments, composer, Orig artist, copyright, url, and encoded by tags (sqylite and the gogaer firmware do not like these tag options. I'm not sure why, but this is what I had to do.)

7.) Using the Scanner in Easytag rename all tracks to this format %n - %a - %t or %n - %t. (you can do others but the dash is the important part. No dots or parenthesis. 

8.) Now go into Clemementine and update your library.

9.) Set your GoGear player to MTP mode and plug it into your computer using the USB cable. 

10.) Go to Clmentine and click on devices. You should see your player. Double click on it to load it.

11.) Let your computer scan it.

12.) Go to your library and right click on an artist or album you want to add to your player. In the pop up menu select copy to device. 

13.) Under naming options make sure the tag format matches what you set in Easytag. For example, if you did %n - %t make sure it does {%track - }%title.%extension so if you have 01 - The Grape in your folder, you get 01- The Grape in the same folder on your player.

Also at the beginning of the string you need to add the destination folder. Your string by default looks like:

%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

You want it to look like:

/music/%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

Otherwise it will just load the music onto your players root directory and not put it in the music folder.

14.) Click ok and it will load the track. Notice it only does 10 tracks at a time. I still haven't figured out how to fix this. When I do I'll post it here.

Your music should now be on your player and in the right place. Unmount your player using clementine and unplug it from the USB cable. Let it update the database and go in and check out the working tags!

---

### Post by ariane5 on 2011-08-03
I have an ARCHOS 18 Vision (mp3 player from hell), having had to send a Philips GoGear back as the button started to go flakey, although it sorted my tracks perfectly

The ARCHOS absolutely will not organise audio tracks in order. I've tried 3 different operating systems, more than 6 different tag editing apps and countless audio players and nothing worked. I can't return the thing to ARCHOS as I lost the receipt and it has been driving me insane - I use it to listen to audiobooks which, clearly, need to be in the correct order.

The steps in MattressVon's post worked! Thank you so much for this. What a lifesaver. I can stop tearing my hair out now.

:-D:-D:-D:-D:-D:-D:-D:-D

---

### Post by MonthyMartins on 2012-09-11
The thing that worked for me is changing the transfer mode from MTP to MSC on the device.

---

