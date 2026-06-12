---
title: "Zen recognized by mtp-detect, but not in amarok/gnomad"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by st00ner on 2007-12-17
EDIT: Its working, and here is how i did it.

You need to install the latest version of libmtp from cvs.

```

sudo apt-get install libtool cvs build-essential
cvs -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp login
no password
cvs -z3 -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp co -P libmtp
cd libmtp
./autogen.sh
./configure
make
sudo make install

```

Copy the udev rules and restart udev
```

sudo cp libmtp.rules /etc/udev/rules.d
sudo /etc/init.d/udev restart

```


Use the correct links:
```

sudo rm /usr/lib/libmtp.so.6
sudo ln -s /usr/local/lib/libmtp.so.7 /usr/lib/libmtp.so.6

```

and all should be ok :]

----------------------------------------------------------------------

Hi, i just got a Creative Zen 8gb (the black one), it is detected in mtp-detect:

```

st00ner@st00ner-desktop:~$ sudo mtp-detect
libmtp version: 0.2.4

Attempting to connect device(s)
PTP: Opening session
ptp2/ptp_usb_getdata: detected a broken PTP header, code field insane, expect problems! (But continuing)
ptp_usb_getresp: detected a broken PTP header, transaction ID insane, expect problems! (But continuing)
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4157
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000080
Microsoft device descriptor 0xee:
        0000: 1203 4d00 5300 4600 5400 3100 3000 3000   ..M.S.F.T.1.0.0.
        0010: fe00                                      ..
Microsoft device response to control message 1, CMD 0xfe:
        0000: 2800 0000 0001 0400 0100 0000 0000 0000   (...............
        0010: 0001 4d54 5000 0000 0000 0000 0000 0000   ..MTP...........
        0020: 0000 0000 0000 0000                       ........
Microsoft device response to control message 2, CMD 0xfe:
        0000: 2800 0000 0001 0400 0100 0000 0000 0000   (...............
        0010: 0001 4d54 5000 0000 0000 0000 0000 0000   ..MTP...........
        0020: 0000 0000 0000 0000                       ........
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative ZEN
   Device version: 1.13.01_0.06.01
   Serial number: 0A000000D0C59CAE0002D298BD209CAE
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
   Detected object size: 64 bits
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
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b901: WMA
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b904: Audible.com Codec
      da01: unknown(da01) UINT32 data type enumeration: 2, 3, 4,  GET/SET
      da02: unknown(da02) array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: unknown(da03) UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b982: MP4
      de99: AudioWAVECodec UINT32 data type enumeration: 41222,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba03: Abstract Audio Album
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 24576, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   ba01: Abstract Multimedia Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 3328, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 4992, STEP 1 GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   300a: MS AVI
      de99: AudioWAVECodec UINT32 data type enumeration: 85, 17, 1,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 1536000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 4000000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 844515635, 878070084, 1482049860, 808802372, 1196444237, 1145656920,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 3000000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   300c: ASF
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b981: WMV
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   bb83: vCard3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   be03: vCalendar2
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   b802: Firmware
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 8195899392
      FreeSpaceInBytes: 2277048320
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 0A000000D0C59CAE0002D298BD209CAE
Special directories:
   Default music folder: 0x00000057
   Default playlist folder: 0x0000005b
   Default picture folder: 0x00000067
   Default video folder: 0x0000006b
   Default organizer folder: 0x00000063
   Default zencast folder: 0x00000073
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: My Zen
   Synchronization partner: (NULL)
   Battery level 252 of 255 (98%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20070810 14:11:43Z#</VALUE><FLAG>DRM_CLK_NOT_SET</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AAAACq6cxdCY0gIArpwgvQAAAAA=</UNIQUEID><PUBLICKEY private="1">Rqdfxugbzxsqz+G5amxsoT29OlSH0/DFhLaIuX3OHYR88afByeV2TA==</PUBLICKEY><KEYDATA>FoTXyFZ4OuJodOotokEjtJ3u6Z4=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>CbpVKSTlWKlN1QBWQClV5FH/aUK7CS2xca2ksJdDsE1MK1J0LnT6Rw==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>xhFuwYWBg+cTv0FiPSkABFzclR0=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.108.193</SECURITYVERSION><CERTIFICATE private="1">Rqdfxugbzxsqz+G5amxsoT29OlSH0/DFhLaIuX3OHYR88afByeV2TAIEbMHZogEpPL2PgM2LBLIlDw4y/Wm6Dm96LZDym5a2UmUI8vgt2NmIm4Mi</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative ZEN</NAME>
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
WMPInfo.xml Does not exist on this device
PTP: Closing session
OK.


```

When i added an MTP device in amarok, when i try to connect it says "Could not connect to mtp device"

I looked on the libmtp website and my device is supported. What could be wrong?
I could connect just fine in windows, but it is inconvenient to boot into windows.
My libmtp version is 0.2.4

EDIT:

Amarok is spitting out this error:
```

Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
LIBMTP_Get_First_Device: Error Connecting
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
LIBMTP_Get_First_Device: Error Connecting
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
LIBMTP_Get_First_Device: Error Connecting


```

---

### Post by eth on 2007-12-18
This part may be annoying:
```

cd /etc/udev

```
and take a tour into "rules.d" file and search for your device. If not present, take another shell and type
```

lsusb

```
you should find your MP3 there. you see a line like
```

Bus 005 Device 001: ID 0000:0000 *(NAME)*

```
where  I placed 0000:0000 you find two exadecimal numbers separated by ":"
The first is the Vendor String, the second is Model, with these information you can fill a new line in the rules.d file.

---

### Post by st00ner on 2007-12-18
I made sure my device was in /etc/udev/rules.d/libmtp.rules. then I did a sudo /etc/init.d/udev restart to make sure that it was loaded. For some reason i still get the same error. Im going to try the cvs version. In the updated on the libmtp page, they talk about the broken headers sent by the new zens. Maybe this is the cause of the problems... I will keep on eye on it.

---

### Post by anthonie on 2007-12-21
Hi, trying to get my Zen Touch (MTP) installed.
Gives back the following error at the end of the procedure

> anthonie@ubuntu:~/libmtp$ sudo mtp-detect
mtp-detect: error while loading shared libraries: libmtp.so.7: cannot open shared object file: No such file or directory


Anyone has a clue?

EDIT: Never mind, had to CD back to ~ in order to get correct output from the terminal. However, it's not working in Amarok. That is, it seems to try and detect the device, but the actual content never shows up, no error message either...

---

### Post by srg84 on 2007-12-25
--------------------------------------------------------------------------------------------------------------------------------------------
mtp-detect: error while loading shared libraries: libmtp.so.7: cannot open
shared object file: No such file or directory

Ensure that /usr/local/lib is listed in /etc/ld.so.conf and run ldconfig
----
Poner esto
(include /usr/local/lib)
----


si te dice que faltan cosas instalalas con Synaptic (libusb, etc)

una vez que lo detecte mtp-detect

--------------------------------------------------------------------------------------------------------------------------------------------
sudo aptitude install fuse-utils checkinstall build-essential

wget [http://www.adebenham.com/mtpfs/mtpfs-0.4.tar.gz](http://www.adebenham.com/mtpfs/mtpfs-0.4.tar.gz)

tar -xvjf mtpfs-0.4.tar.gz

cd mtpfs-0.4
./configure --prefix=/usr
make && sudo checkinstall

mkdir ~/MTP-player
mtpfs ~/MTP-player
--------------------------------------------------------------------------------------------------------------------------------------------

ya deberia estar montado-> mejor usar la ultima version
[http://www.adebenham.com/mtpfs/](http://www.adebenham.com/mtpfs/)


para desmontarlo
------------------------------------------------------------------------------------------------------------------------------------
fusermount -u ~/MTP-device
------------------------------------------------------------------------------------------------------------------------------------

---

### Post by nickaj on 2007-12-26
Thanks! these instructions worked great

---

