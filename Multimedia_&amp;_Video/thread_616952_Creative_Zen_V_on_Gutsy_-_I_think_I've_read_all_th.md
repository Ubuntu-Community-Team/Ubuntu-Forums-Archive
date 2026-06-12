---
title: "Creative Zen V on Gutsy - I think I've read all the threads....."
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by aspiteri on 2007-11-18
Dear Helpful Others,

I've been reading through masses of threads on this matter (great 60 odd page thread on getting these Creatives up on Dapper), but cannot get this Gutsy based system to work with my girlfriends Xmas pressy, a nano replacing Creative Zen V on her first Linux PC.
:)

I feel I've tried all the advice and I have got to the point where I think the device wont play ball with libmtp, it does not mater which player I try (gnomad2, Amarok, Rhythmbox) and from this mtp-detect (libmtp6 & mtp-tools) output I wonder what to do next.

The Zen has the latest firmware from Creative - I'm starting to wonder if these new Zens are still MTP compatible.... oh the doubt :confused:

Any Ideas?


#########one for the developers????############
felicity@HomePC:~$ sudo mtp-detect
[sudo] password for felicity:
libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4158) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4158
   IN endpoint maxpacket: 64 bytes
   OUT endpoint maxpacket: 64 bytes
   Device flags: 0x00000000
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
   Model: Creative ZEN V (Video)
   Device version: 1.32.01_1.01.10
   Serial number: D5CBCD0A4003001CD5CDE9C74003001C
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
Supported operations:

  <<<<Full output cut down since libmtp developer comment received - see post 23rdNov07>>>>>

WMPInfo.xml Does not exist on this device
PTP: Closing session
OK.
felicity@HomePC:~$ 
##########################################

---

### Post by aspiteri on 2007-11-19
UPDATE:
Have mailed the libmtp mail list with the following progress and the mtp-detect output.  It looks like my Zen has a new VID ( 4158 ), not listed in the libmtp.rules file.

[I]Hi,

I have just bought a new Creative Zen V to work with Ubuntu 7.10 (Gutsy Gibbon).  Having followed many a thread on how to get Gnomad2, Amarok and Rhythmbox working with libmtp and this new Zen, now strongly suspect libmtp is not happy with this Zen, as the mtp-detect (before and after)shows below.

After doing the following I can now dock the Zen, but gnomad2 does no more than display the device's information and add empty playlists.
To:
/etc/udev/rules.d/libmtp.rules
Added:
# Creative Zen V (Video)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4158", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
Then:
sudo /etc/init.d/udev restart

Do you have any advice for me?

Regards
Alan[/I]

---

### Post by aspiteri on 2007-11-22
I got a simple reply from the libmtp guys:

libmtp-discuss
Reply
	
2007/11/20, **@googlemail.com>:

> Do you have any advice for me?

This device is supported by the CVS version of libmtp. Either compile
from source or talk to Ubuntu about upgrading the distribution.

Linus

---

### Post by brucehelp on 2008-02-01
Found this from Gnomad2 site
[http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)
News


2008-01-28: Gnomad 2.9.1 adds support for device detection using D-Bus and HAL, you can plug in/out devices and gnomad2 will react. We will not erroneously delete "." or ".." dirs. We can cancel up/download on MTP devices. You can use taglib only if you want to. (No more libid3tag, but this is NOT RECOMMENDED). And finally we have folder support for the MTP device


Working Devices:
Creative NOMAD Jukebox 1 (aka D.A.P.)
Creative NOMAD Jukebox 2
Creative NOMAD Jukebox 3
Creative NOMAD Jukebox Zen
Creative NOMAD Jukebox Zen USB 2.0
Creative NOMAD Jukebox Zen NX
Creative NOMAD Jukebox Zen Xtra
Creative Zen Touch
Creative Zen Micro
Creative Zen Sleek
Creative Zen
Dell Digital Jukebox ("Dell DJ")
Second Generation Dell DJ
Dell Pocket DJ

MTP devices:
Creative Zen Portable Media Center
Creative Zen MicroPhoto
Creative Zen Vision
Creative Zen Vision:M
Creative Zen Sleek Photo
Creative Zen Xtra (MTP mode)
Creative Zen Micro (MTP mode)
Creative Zen Touch (MTP mode)
Creative Zen Sleek (MTP mode)
Creative Zen V
Creative Zen V Plus
Second Generation Dell DJ (MTP mode)
Dell Pocket DJ (MTP mode)

Perhaps:
Any other MTP device which can play audio. I haven't tested them much, but they reportedly work with libmtp so should be OK. This includes:
Samsung YH- and YP- MTP players
Intel PMC
JVC Alneo
Philips HDD/GoGear series
Sandisk MTP devices
iRiver MTP devices
Toshiba Gigabeat devices
Archos MTP devices
Dunlop MP3 player
Sirius Stiletto


You are invited to read the Gnomad README file and Change Log

---

