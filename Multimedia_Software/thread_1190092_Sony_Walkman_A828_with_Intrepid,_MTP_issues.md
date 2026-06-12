---
title: "Sony Walkman A828 with Intrepid, MTP issues"
date: 2009-06-17
forum: Multimedia Software
---

### Post by Rebajas on 2009-06-17
Hiya,

I just got myself a Sony Walkman A828 (8Gb) and am having some issues connecting it to my 9.04 (Jaunty) desktop. When I plug it in via USB I get an empty folder rather than the folder hierarchy I see when I plug it into either my XP box or my Ubuntu 8.10 (Intrepid) laptop.

Doing mtp-detect (as directed in other threads) outputs:

```
rebajas@rebajas-desktop:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Sony: Walkman NWZ-A828/NWZ-A829 (054c:035b) @ bus 0, dev 18
Attempting to connect device(s)
PTP: Opening session
LIBMTP PANIC: Unable to read device information on device 18 on bus 0, trying to continueUnable to open raw device 0
OK.
```

Any help appreciated on this one - if you need more info just tell me what you need :)

Thanks.

---

### Post by Rebajas on 2009-06-23
No replies? Looks like I have found another use for my Windows box then...

:\

---

### Post by heyho on 2009-06-24
Free bump for this thread - having exactly the same problem here with Jaunty - No probs in previous 'buntus or XP.

Player is Sony NZW-A818.

---

### Post by heyho on 2009-06-24
Previous post a little premature!

Before plugging in USB cable, enter the following into terminal:

```
killall gvfs-gphoto2-volume-monitor
```

And all is good.:)

---

### Post by robhem on 2009-10-11
Hi, 
 
I'm trying to get a Sony NWZ-A726B to work. The killall command posted above doesn't seem to help. Following this with mtp-detect gives the following output: 
 
rob@LOUNGEPC:~$ mtp-detect
libmtp version: 0.3.0
 
Listing raw device(s)
Found 1 device(s):
Sony: Walkman NWZ-A728B (054c:035c) @ bus 0, dev 2
Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 767)
Try to reset the device.
Unable to open raw device 0
OK.
 
I'm using Jaunty. If I try to browse the player I get the following error: 
 
Sorry, could not display all the contents of "Sony Corp. WALKMAN": Failed to get folder list: -1: Unspecified error
 
I found the following post in the kubuntu forums and I wonder if this method would be appropriate? Any ideas anyone? 
 
[http://kubuntuforums.net/forums/index.php?topic=3096598.0](http://kubuntuforums.net/forums/index.php?topic=3096598.0)
 
Regards, 
Rab
 
UPDATE: I now have this Walkman working on Jaunty. See my post: [http://ubuntuforums.org/showthread.php?t=1047272](http://ubuntuforums.org/showthread.php?t=1047272)
 
Rab

---

