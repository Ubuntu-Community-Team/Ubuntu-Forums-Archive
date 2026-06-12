---
title: "Amarok, Gnomad not detecting (MTP) Creative Zen"
date: 2009-03-10
forum: Multimedia Software
---

### Post by dubhousing on 2009-03-10
Hi All,

Until recently Amarok and Gnomad had been playing nicely with my creative zen.  With a little jiggering and config I was able to get them both to find and read the contents of the player, transfer podcasts, etc.

I don't know what the intervening event or action was, but now nothing works.  Trying to connect in Amarok often causes a frozen session requiring a force quit; gnomad reports on startu pthat "no jukeboxes are connected."  After trying to connect with either of these, or trying to detect with mtp-detect, I am then unable to use the player and have to do a forced reset (stick a pencil in a slot to power-down/power-up).

After I reset the last time, I tried mtp-detect again, and got a mix of good and problematic output.  Here are the error parts, from the beginning and later the end of the output:

> PTP: Opening session
Error 2: PTP Layer error 02ff: get_all_metadata_fast(): could not get proplist of all objects.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: get_handles_recursively(): could not get object handles.
Error 2: (Look this up in ptp.h for an explanation.)

> Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)
WMPInfo.xml Does not exist on this device
PTP: Closing session
ERROR: Could not close session!
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
OK.


[the OK at the end is hilarious]

Incidentally, when I try to autodetect the device in amarok, it asks me if the dcop and hal daemons are running.

Any ideas?

TIA

---

### Post by jimmyhacker on 2009-03-10
try to put that XML file in Webcam :lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by dubhousing on 2009-03-10
Hm.  I think it's gonna take me several more weeks of Ubuntu to grasp the forum sense of humor. :-)

---

### Post by dubhousing on 2009-03-11
Solution found, in case anyone is interested.  Simply sudo apt-get remove libmtp and then compile the latest version (not yet ubuntu packaged) from source.

---

### Post by psablo on 2009-03-12
Same problem:
On my LapTop running Hardy 8.04, Gnomad2 works fine, but I just installed Ibex64 8.10 on my desktop and Gnomad2 doesn't see my Creative Zen MP3 player.  I opened gnomad2.desktop and edited the line exec=gksudo gnomad2 so permission is not the issue.

When I run Gnomad2 I get the message:
"no jukeboxes found on USB bus"

I have libmtp8 and libnjb5 installed from the package manager so do you really think sudo apt-get remove libmtp and then recompile from source will help?

---

### Post by dubhousing on 2009-03-12
I don't have enough ubuntu under my belt to know for sure (it's been about 3 weeks), but it worked for me.  Considering that it had been working for me on the libmtp released in package manager, my solution seems a little suspect.  

Note, however, that the ver released in ubuntu repositories is 3.0, and the latest version from the libmtp developer is 3.6.  Try it and maybe post the results?  It's still working for me.

---

### Post by erwinsoo on 2010-04-27
Using 10.04. When i start gnomad2 to scan my zen jukebox, it force quits. tried reinstalling libnjp5 and libmtp8 still the same. Never had this prob before with 9.10

---

### Post by NoBugs! on 2010-05-01
Looks like 10.04 breaks libmtp for creative players. You can download the previous version from [here]("http://packages.ubuntu.com/karmic/libmtp8")

then,
```
sudo dpkg -i ~/libmtp8_0.3.7-3ubuntu2_i386.deb

``` it should work :)

---

### Post by saking on 2010-06-06
I am having the same problem.  I tried the solution suggested by NoBugs! and now, Gnomad2 doesn't crash, but it still says "No jukeboxes found on USB bus"

Also, I am wondering if taking this downgrading approach will affect how I receive bug fixes and upgrades in the future.

---

### Post by Barbalras on 2010-06-30
I'm having a similar problem. When I open gnomad2 it recognizes the zen micro but the program hangs while "scanning datafiles..." 
I can see my music inside the device but the scanning datafiles dialog doesn't let me transfer any songs

installing the package mentioned above didn't do any help, I already had that same version.

Any thoughts?

---

### Post by NoBugs! on 2010-08-04
> **saking said:**
> now, Gnomad2 doesn't crash, but it still says "No jukeboxes found on USB bus"

That means the system already auto-detected it. Go to Places - mp3-player, then click the eject/unmount button.

It seems the latest update in 10.04 fixed libmtp, Rhythmbox can transfer files fine, but [gnomad crashes]("https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967").

---

### Post by Avoozl on 2010-08-12
Confirming that gnomad2 works on Ubuntu 10.04 for my Samsung YP-S3 only after installing the old version of libmtp8 provided in this thread and unmounting the player (which was automounted when plugged in) before launching gnomad2.  

I also wanted to mention that I have had various problems with gnomad in the past, and while I don't have to do this currently, at one point gnomad would work for me if I ran it with gksudo but it would not work as a normal user.

---

### Post by SleepCat on 2010-08-22
Got the same problem with my Zen X-fi style :( I tried the suggestions above, but it just can't detect it in gnomad and rhytmbox.

I'm on ubuntu 10.04

---

### Post by Capt_Zaphod on 2010-08-25
Same trouble for me.

---

### Post by mrv on 2010-11-11
Has anyone tried Zen Style 100/300 or X-Fi Style in Ubuntu 10.10? It at least has newer libmtp.

---

### Post by johnlm on 2010-11-13
I am currently having problems with my old Creative Zen, although Samsung P3 seems to be recognised straight away, when using 10.10

---

### Post by normanp on 2011-08-05
I notice that the Zen X-Fi Style is mantioned in the latest version of media-player-info.
What is this file for? If I just replace my current version (12-1) with this newer version (14-1) will my player be recognised? Alternatively will I need to update libmtp or libmtp8 or whatever?
Thanks

---

### Post by normanp on 2011-08-05
> **normanp said:**
> I notice that the Zen X-Fi Style is mantioned in the latest version of media-player-info.
What is this file for? If I just replace my current version (12-1) with this newer version (14-1) will my player be recognised? Alternatively will I need to update libmtp or libmtp8 or whatever?
Thanks

dubhousing - please could you explain how you did your suggestion in post #4?

---

