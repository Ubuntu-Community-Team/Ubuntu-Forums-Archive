---
title: "libmtp and Samsung yp-t9j"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by Alex&amp;Linux on 2007-07-19
Just got this new Samsung mult-media reproducing device, and it seems that libmtp isnt detecting the hardware.
Running mtp-detect as root allowed me to view data on the device, but I have since not been able to reproduce the event.
What I get is the following: 

```
ajn@ajn-desktop:~$ mtp-detect
No MTP devices.
No devices.
```

There was one chap that mentioned upgrading libmtp5 to version 1.5 (instead of 1.3, which Ive freshly installed from the repos)

Anyone recall a solution?
My HP did have Vista on it, and it would be really annoying to stick it back on there.

Saludos!

---

### Post by Alex&amp;Linux on 2007-07-19
Heres an update.
After rebooting, running mtp-detect as root shows the following output:

```
ajn@ajn-desktop:~$ sudo mtp-detect
Password:
Autodetected device "Samsung Yepp T9" (VID=04e8,PID=507f) is known.
PTP: Opening session
Connected to MTP device.
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 507f
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Device info:
   Manufacturer: Samsung Electronics Co.,Ltd.
   Model: Samsung YP-T9
   Device version: V1.67
   Serial number: C53FDC12000000FB
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMPPD: 10.0; microsoft.com/WMDRMPD: 10.1microsoft.com/WMPPD: 11.,; 
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
   1011: Self test device
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9805: Get object property list
   9806: Set object property list
   9810: Get object references
   9811: Set object references
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
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd402: Device Friendly Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0x5011: Date Time
Playable File (Object) Types and Object Properties Supported:
   3000: Undefined Type
      dc01: StorageID
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc0b: ParentObject
      dc4f: NonConsumable
      dc44: Name
   3001: Association/Directory
      dc01: StorageID
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc0b: ParentObject
      dc4f: NonConsumable
      dc44: Name
   3009: MP3
      dc01: StorageID
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc0b: ParentObject
      dc4f: NonConsumable
      dc44: Name
      dc46: Artist
      dc8b: Track
      dc8c: Genre
      dc9a: AlbumName
      de9a: AudioBitRate
      dc03: ProtectionStatus
      de99: AudioWAVECodec
      de93: SampleRate
      de94: NumberOfChannels
      dc8a: Rating
      dc89: Duration
   b901: WMA
      dc01: StorageID
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc0b: ParentObject
      dc4f: NonConsumable
      dc44: Name
      dc46: Artist
      dc8b: Track
      dc8c: Genre
      dc9a: AlbumName
      de9a: AudioBitRate
      dc03: ProtectionStatus
      de99: AudioWAVECodec
      de93: SampleRate
      de94: NumberOfChannels
      dc8a: Rating
      dc89: Duration
   ba05: Abstract Audio Video Playlist
      dc01: StorageID
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc0b: ParentObject
      dc4f: NonConsumable
      dc44: Name
   3801: JPEG
      dc01: StorageID
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc0b: ParentObject
      dc4f: NonConsumable
      dc44: Name
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 2009456640
      FreeSpaceInBytes: 1990463488
      FreeSpaceInObjects: 4294967295
      StorageDescription: Samsung YP-T9 Storage
      VolumeIdentifier: c53fdc12000000fb
Special directories:
   Default music folder: 0x00008001
   Default playlist folder: 0x00008002
   Default picture folder: 0x00008004
   Default video folder: 0x00008005
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00000000
   Default album folder: 0x00000000
   Default text folder: 0x00008003
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: (NULL)
   Battery level 60 of 100 (60%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   JPEG file

```

So the device is there, and I should be able to do something with it!
Anyone know how to use terminal to throw some data into this device?

---

### Post by Alex&amp;Linux on 2007-07-20
Ok, so I really want this music on my portable multimedia reproducing device, and so Ive taken another crack at it.

I was able to download some mtp support packages for Amarok, and mount the device, and transfer the files, however, though they successfully transfer, and the device shows at least the file names in the file browser, the full data is not there. 

Ive tried transferring a few file types, one at a time, to no avail.

With confidence, I am now going to sleep!

---

### Post by Alex&amp;Linux on 2007-07-23
So, fixed it by downgrading the firmware to 1.60, which allows the device to support UMS, which is PnP with Linux!
If youre looking for the firmware download, you can get it here: [http://samsung.t9.googlepages.com/#upgrading-firmware]("http://samsung.t9.googlepages.com/#upgrading-firmware")

---

### Post by !nkubus on 2007-07-23
I had the same issues with the player and I have to use UMS also

---

