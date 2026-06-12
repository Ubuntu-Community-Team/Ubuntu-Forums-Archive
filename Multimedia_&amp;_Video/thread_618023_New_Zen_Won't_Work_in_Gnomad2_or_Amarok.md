---
title: "New Zen Won't Work in Gnomad2 or Amarok"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by finding_my_zen on 2007-11-19
I'm using Ubuntu Gutsy Gibbon and Amarok 1.4.7
-------------------------
when I do sudo mtp-detect it gives me this----

libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting

I'm very new at this so bare with me, PLEASE HELP!!! :confused:

---

### Post by the_real_bubba on 2007-11-26
Exact same thing here.  Apparently the version of libmtp in CVS works.  Either install from source or do like me, which is to put the Zen in a drawer and leave it there until the Ubuntu libmtp gets updated to the supported version.

---

### Post by the_real_bubba on 2007-11-26
Why lbmtp requires recompiling to recognize a new device is beyond me.  Could there not just be a plaintext file with the required catalog of devices?

---

### Post by finding_my_zen on 2007-11-26
Thanks for the info, =D I thought it was something like that. I'll probably just wait for the update too.

---

### Post by the_real_bubba on 2007-11-27
As far as I can tell, even loading up the SD card with mp3s doesn't make them playable, the device really is intended to be completely useless without Windoze.  Glad I kept my MuVo!

---

### Post by finding_my_zen on 2007-11-27
To bad... oh well, I'll just have to use my sisters competer

---

### Post by hyde200j on 2007-12-17
libmtp v0.2.4 is available at 
[http://libmtp.sourceforge.net/index.php?page=download]("http://libmtp.sourceforge.net/index.php?page=download")
Even easier go get the hardy .debs 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=libmtp]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=libmtp")

mtp-detect warned of some bad header, but gnomad2 at least provided some primitive add/remove functionality for my 8GB Zen.  Haven't played around with it too much yet, but that much is certain for me.

---

### Post by st00ner on 2007-12-18
[http://ubuntuforums.org/showthread.php?t=643512](http://ubuntuforums.org/showthread.php?t=643512)

Instructions on building from cvs. the cvs version fixed my poblem

---

### Post by Lord DarkPat on 2007-12-18
Try Banshee, you may be lucky

---

