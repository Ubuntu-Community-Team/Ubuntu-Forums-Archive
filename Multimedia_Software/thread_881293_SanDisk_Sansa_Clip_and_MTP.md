---
title: "SanDisk Sansa Clip and MTP"
date: 2008-08-05
forum: Multimedia Software
---

### Post by Unevolved on 2008-08-05
I can get my Sansa Clip to work fine in MSC mode, which would be enough to sate me, you'd think.  But no.  I can't make playlists.  Not even by making a Go List, because those don't show up in the "Playlists" folder like other Sansas.  So really, my only option is to get MTP working somehow.

All I'm really doing now is trying random things hoping it'll work.  I have libmtp7 installed, and I checked in /etc/udev/rules.d/45-libmtp7.rules to make sure the player is listed, and the device IDs and everything match up fine.  So it should be working, to the extent of my limited knowledge.  

For what its worth, Banshee appeared to load the player *once* in MTP, but then locked up, and hasn't recognized the player since.  Any help in this matter would be greatly appreciated, as always.  Mods, if this is in the wrong section, please move.  I seem to have trouble with this.

Edit:  Here's the output of mtp-detect:

```
jake@jake-laptop:~$ mtp-detect
libmtp version: 0.2.6.1

Attempting to connect device(s)
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after re-initializing USB interface
Clearing stall on OUT endpoint
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1599
Detect: There has been an error connecting. Exiting
```

---

### Post by Unevolved on 2008-08-06
Bump for morning traffic.  Think it's the player?  I can still return it if that's the issue.

---

### Post by Unevolved on 2008-08-06
Bump one last time.  I really need some help on this.

---

### Post by Unevolved on 2008-08-06
I hate to keep bumping, but I'm at a loss.  I promise, I only bump if the thread has worked its way to the second page.  I'm just really hoping someone can help me out with this.

---

### Post by Unevolved on 2008-08-06
Guess I'll make this my own personal update thread.

I've figured out it's an issue with libmtp7.  I've reinstalled to no avail, but at least I've got something to go off of.  lsusb shows the device, but mtp-detect throws an error message.  Seems to me that's where I need to be focusing my energy right now.

---

### Post by Unevolved on 2008-08-07
Thursday bump.

I found out it may be even beyond libmtp7, perhaps something to do with the USB drivers?

In that regard, what would happen if I got a wire, and plugged the player into an IEEE1394 port?   Or would libmtp not even recognize it?

---

### Post by Unevolved on 2008-08-09
Bump for the weekend.  I'm considering buying a B-plug USB to i394 Firewire cord, just to see what happens.

---

### Post by Unevolved on 2008-08-09
If no one here can help me, can someone at least tell me where else I could ask?  Another forum, perhaps?  This is clearly beyond me, and I need help.

---

### Post by bofh42 on 2008-09-02
Had the same problem with my new clip.  Updating libmtp to 0.3.1 solved the problem.  I don't know if there is an ubuntu package for it yet.  The sourcecode can be downloaded from [http://libmtp.sourceforge.net/index.php](http://libmtp.sourceforge.net/index.php)

---

### Post by gentlewolf on 2008-09-13
This worked for me too. Thanks!

---

