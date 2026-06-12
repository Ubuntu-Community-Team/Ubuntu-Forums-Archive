---
title: "Connecting 2 MTP music players."
date: 2008-12-27
forum: Multimedia Software
---

### Post by Almothegreat on 2008-12-27
After finally getting my Sony walkman to connect, and happily using rhythmbox to transfer MP3s to and from the device, ive run into a little problem.

When connecting two Sony walkmans (as I have one and my partner has one), hey both show up in 'computer' fine and will open with the file browser, however when connecting them both to rhythmbox only one will connect fine, the other will connect, though differently to the first one.

The first one connects via MTP, and shows the artist/album panels,ect, and also allows me to rename the device.

The second one connects via ??? (USB perhaps?) and does not show the panels, it only shows a list of media on the device, it also does not have an option to rename.

Running mtp-detect give me an error on one, and a usual printout for the other. Im fairly new to linux so maybe a keen eye can help me.

Any help would be great, I would prefer to be able to have them both connected at the same time, and with ability to rename so I can tell them apart, however if ultimately its not possible I guess ill just have to plug in one at a time.

```
al@al-desktop:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 2 device(s):
   Sony: Walkman NWZ-A728B (054c:035c) @ bus 0, dev 48
   Sony: Walkman NWZ-A728B (054c:035c) @ bus 0, dev 47
Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
usb_claim_interface(): Bad file descriptor
LIBMTP PANIC: Could not open session on device
Unable to open raw device 0
PTP: Opening session
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 054c
   idProduct: 035c
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 47
      Device entry info:
         Vendor: Sony
         Vendor id: 0x054c
         Product: Walkman NWZ-A728B
         Vendor id: 0x035c
         Device flags: 0x00000002
Microsoft device descriptor 0xee:
	0000: 1203 4d00 5300 4600 5400 3100 3000 3000	..M.S.F.T.1.0.0.
	0010: 3000                                   	0.
Microsoft device response to control message 1, CMD 0x30:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000                    	........
Microsoft device response to control message 2, CMD 0x30:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000                    	........
Device info:
   Manufacturer: Sony Corporation
   Model: WALKMAN NWZ-A726
   Device version: 1.01
   Serial number: 00000000000000000000000005120300
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMDRMPD: 10.1; sony.net/WMFU: 1.0; 
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
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   101b: Get partial object
   9810: Get object references
   9811: Set object references
   9802: Get object property description
   9801: Get object properties supported
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9201: Report Added/Deleted Items
   9807: Get interdependent property description
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
   9401: Unknown (9401)
   9402: Unknown (9402)
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
Playable File (Object) Types and Object Properties Supported:
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc05: AssociationType UINT16 data type enumeration: 0, 1,  GET/SET
   3008: MS Wave
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 1, MAX 2147483647, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 1,  GET/SET
      de9a: AudioBitRate UINT32 data type enumeration: 128000, 176400, 192000, 256000, 352800, 384000, 512000, 705600, 768000, 1024000, 1411200, 1536000,  GET/SET
      de91: TotalBitRate UINT32 data type enumeration: 128000, 176400, 192000, 256000, 352800, 384000, 512000, 705600, 768000, 1024000, 1411200, 1536000,  GET/SET
   3009: MP3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
      dc42: SyncID STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 1, MAX 2147483647, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 16000, 22050, 24000, 32000, 44100, 48000,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 32000, MAX 320000, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 32000, MAX 320000, STEP 1 GET/SET
   300c: ASF
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
   3801: JPEG
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  GET/SET
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 65536, STEP 1 GET/SET
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 200, STEP 1 GET/SET
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 200, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc87: Width UINT32 data type range: MIN 1, MAX 4000, STEP 1 GET/SET
      dc88: Height UINT32 data type range: MIN 1, MAX 4000, STEP 1 GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
   b802: Firmware
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
   b901: WMA
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
      dc42: SyncID STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 1, MAX 2147483647, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 16000, 22050, 32000, 44100, 48000,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 512000, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 5000, MAX 512000, STEP 1 GET/SET
   b982: MP4
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
      dc42: SyncID STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc87: Width UINT32 data type range: MIN 2, MAX 320, STEP 2 GET/SET
      dc88: Height UINT32 data type range: MIN 2, MAX 240, STEP 2 GET/SET
      dc89: Duration UINT32 data type range: MIN 1, MAX 2147483647, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 41222,  GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 16000, MAX 288000, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 2788000, STEP 1 GET/SET
      de9b: VideoFourCCCodec UINT32 data type enumeration: 844313677, 875967048,  GET/SET
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 2500000, STEP 1 GET/SET
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 1000, MAX 30000, STEP 1 GET/SET
      dea1: EncodingProfile STRING data type GET/SET
   b984: 3GP
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 1, MAX 2147483647, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 41222,  GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 16000, MAX 288000, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 2788000, STEP 1 GET/SET
   ba03: Abstract Audio Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  GET/SET
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 65536, STEP 1 GET/SET
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 200, STEP 1 GET/SET
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 200, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc08: DateCreated STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 3840933888
      FreeSpaceInBytes: 15630336
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 00000000000000000000000005120300
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
   Friendly name: WALKMAN
   Synchronization partner: (NULL)
   Battery level 100 of 100 (100%)
libmtp supported (playable) filetypes:
   RIFF WAVE file
   ISO MPEG-1 Audio Layer 3
   Microsoft Advanced Systems Format
   JPEG file
   Firmware file
   Microsoft Windows Media Audio
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)

Secure Time:
<DRMCLOCK type="status"><VALUE>#20081228 00:50:36Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AAABBwgAAAUBBQUBAgADAAA=</UNIQUEID><PUBLICKEY private="1">Uy/Ml4j5yN/PADCm8Q/OmSELOVCu/ct0Fnna97wxieKj12tKQLcnHw==</PUBLICKEY><KEYDATA>Rlb2E9WCxwApsCBD1EFYHOp5hAs=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>cmOJFJTEI5gh7Gt/Y+bmOhq4uQAg6qzK2VgMK/V1D7hd9PMjKVSjeA==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>oENpITnnpBU1LbjRzck2KhjTzSo=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.109.133</SECURITYVERSION><CERTIFICATE private="1">Uy/Ml4j5yN/PADCm8Q/OmSELOVCu/ct0Fnna97wxieKj12tKQLcnHwIEbYWnx8T/09vis2XTQNXgKuYoXDc9CPeJg1jrCjQ3xSmA0NhMM21lq1lb</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Walkman</NAME><MANUFACTURER>Sony</MANUFACTURER><MAKE>Sony</MAKE><DISTRIBUTOR>Sony</DISTRIBUTOR><MODEL>Walkman</MODEL><SECURITYLEVEL>2000</SECURITYLEVEL><FEATURES><CLOCK>2</CLOCK><SECURECLOCK><URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL><PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY></SECURECLOCK><METERING>1</METERING><LICENSE_ACQ>1</LICENSE_ACQ><LICENSE_SYNC>1</LICENSE_SYNC><ENCRYPTION>1</ENCRYPTION><SYMMETRIC_OPT>1</SYMMETRIC_OPT></FEATURES><LIMITS><MAXCHAINDEPTH>2</MAXCHAINDEPTH><MAXLICENSESIZE>10240</MAXLICENSESIZE><MAXHEADERSIZE>5120</MAXHEADERSIZE></LIMITS><PUBLICKEY>vm04OpfYNJGbKI7lA8XRU7xsblw4FvoHSpcAkJNRNUp09y0PwU+JEw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>nE64aBhQi/NrJvbvITqm2rDcFHOYz3XBivxfDq4WrJsXwfTlxedTHQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>2281</AUTH_ID><PUBLICKEY>2P/m6ASJN++3mYEVB6ZurQE4aUWH8eYbqpZ7IIVsLE8OLLetpxhASg==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>vbOMFgVCw5NkJRDv1qNrgypcrAJY1GJwjwc0aA4uh7SGFgjrJgzZKQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>YzVoCTMJRDHjvl5JOI2anu/+J1pOKCDnoidlvh1/Yk/PnnMQEdRPdw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
WMPInfo.xml Does not exist on this device
PTP: Closing session
OK.
al@al-desktop:~$ 

```

---

