---
title: "sansa connect mp3 player will not mount"
date: 2009-06-01
forum: Multimedia Software
---

### Post by andrea000 on 2009-06-01
Hello all i have a sansa [connect]("http://forums.sandisk.com/sansa/board?board.id=connect") mp3 player i found
that it is a mtp type player but ubuntu will not 
mount it sansa says it does not support linux but
all players say that there is no way to change
settings from mtp to msc how could i get this to
mount so i can put songs on it.I use ubuntu 8.10
please help i have been working on this off and
on for weeks with no luck

[IMG]http://www.ubergizmo.com/photos/2007/11/sansa-connect-upgraded.jpg[/IMG]

---

### Post by CanadianLinux on 2009-06-28
Bump,

I also have a connect, got it for 40 bucks. I installed lib-mtp but I am still unable to have the PC load up the device properly. 

Using mtp-detect Gives me

```

ry@ry-desktop:~$ mtp-detect 
libmtp version: 0.3.7


Listing raw device(s)
   Found 1 device(s):
   SanDisk: Sansa Connect (0781:7480) @ bus 0, dev 3
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.
ry@ry-desktop:~$ mtp-detect 
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   SanDisk: Sansa Connect (0781:7480) @ bus 0, dev 3
Attempting to connect device(s)
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
PTP: Sequence number mismatch 2 vs expected 5.LIBMTP PANIC: could not inspect object property descriptions!
PTP: Sequence number mismatch 3 vs expected 6.LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
Error 7: Unable to read Maximum Battery Level for this device even though the device supposedly supports this functionality
Error 1: Get Storage information failed.
Error 2: PTP Layer error 02ff: get_all_metadata_fast(): could not get proplist of all objects.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: get_handles_recursively(): could not get object handles.
Error 2: (Look this up in ptp.h for an explanation.)
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 0781
   idProduct: 7480
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 3
      Device entry info:
         Vendor: SanDisk
         Vendor id: 0x0781
         Product: Sansa Connect
         Vendor id: 0x7480
         Device flags: 0x00000000
Configuration 0, interface 0, altsetting 0:
   Interface description contains the string "MTP"
   Device recognized as MTP, no further probing.
Device info:
   Manufacturer: SanDisk
   Model: Sansa Connect
   Device version: 1.1
   Serial number: 00350000106c8075ac25bcb80300b7b8
   Vendor extension ID: 0x00000006
   Vendor extension description:  microsoft.com/WMDRMPD: 10.1;
   Detected object size: 32 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1010: Reset device
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   1017: Reset device property value
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   100b: Delete object
   100c: Send object info
   100d: Send object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9805: Get object property list
   9804: Set object property value
   9807: Get interdependent property description
   4001: Unknown (4001)
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
   910b: Send WMDRM-PD Request
   100f: Format storage
   9806: Set object property list
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
Playable File (Object) Types and Object Properties Supported:
   b104: Unknown(b104)
   b901: WMA
   b982: MP4
   ba03: Abstract Audio Album
   ba05: Abstract Audio Video Playlist
   3000: Undefined Type
   3001: Association/Directory
   3008: MS Wave
   3009: MP3
   3801: JPEG
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
   Friendly name: (NULL)
   Synchronization partner: (NULL)
libmtp supported (playable) filetypes:
   Microsoft Windows Media Audio
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   RIFF WAVE file
   ISO MPEG-1 Audio Layer 3
   JPEG file
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)

```

---

### Post by andrea000 on 2009-07-18
I'm not trying to drag up a old post but i found a way to make it 
work so i'm posting to tell how i did it maybe it will help someone
else as this will work on some other players also.sandisk blocks
this on newer firmware version.soooo

first reset to the default firmware and stop all wifi as this is
the way sandisk updates there firmware.

now you need to install **libnjb**, **libmtp 3.6** and **gnomad2** and **usbmount**
and then it then reboot both ubuntu and the player now it should work it only
mount's as a usb drive but now you can drag mp3's on to it.

---

### Post by Kopasakis on 2009-11-05
thank you:KS

---

### Post by Doc on 2009-11-07
I have one of these and have been using it for a while on 9.04. This link shows the the easiest way I've found to get it to work without needing to install any new packages:

[http://www.howtoforge.com/sandisk_mp3_player_linux](http://www.howtoforge.com/sandisk_mp3_player_linux)

Good luck

---

### Post by roystreet on 2009-11-19
Hi Doc,
   I looked at the link you have placed here & it looks wonderful...One problem though.  Right in the beginning it directs you to the settings >> USB Mode.  There is no "USB Mode" listed in my settings.  

I forget what model I use, but it is a 1gb model.  I can go into settings >> System info & it states it is version 01.01.05P.  I don't know if that means anything to anyone.  I took out the battery to see if there was a model number listed anywhere & there isn't.

Thanks for any help!
~roystreet

---

