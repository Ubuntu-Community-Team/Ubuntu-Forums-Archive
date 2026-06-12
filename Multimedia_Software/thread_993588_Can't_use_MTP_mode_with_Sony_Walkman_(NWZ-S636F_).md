---
title: "Can't use MTP mode with Sony Walkman (NWZ-S636F )"
date: 2008-11-25
forum: Multimedia Software
---

### Post by element_G on 2008-11-25
I just got a Sony S Series Walkman (NWZ-S636) and I can't connect to it through MTP with Amarok or gnomad2. What I want to do is set up playlists for the device.

What I CAN do is connect the device with UMS (generic audio device) with Amarok
Thanks to [http://ubuntuforums.org/showthread.php?t=866297](http://ubuntuforums.org/showthread.php?t=866297)

I have seen this: [http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)
but I'm not sure if this will work for me as it references the NWZ-A828 specifically.

---

### Post by element_G on 2008-11-28
anyone?

---

### Post by robz0rz on 2008-11-30
Hey

I just bought a Sony Walkman NWZ-S639F, and I'm experiencing the same problem!

I'm using Ubuntu 8.04 LTS, but I can confirm that this also happens on Ubuntu 8.10 and on Fedora 10.

**mtp-detect** detects my player and gives me a lot of information about it, but applications like Banshee, Amarok, Rhythmbox don't recognize the Walkman. Banshee even gives a fwe error messages (about not being able to cnnect to more than one player at a time) and throws an exception in certain cases.


The guide on the kubuntuforums link that you posted was handy for me, because on Ubuntu 8.04 LTS, I had to recompile hal in order to mount my Walkman at all. However, recompiling libmtp7 (from source or from cvs) did not fix my problems.


I already filed a bug about this at [http://bugzilla.gnome.org/show_bug.cgi?id=562664](http://bugzilla.gnome.org/show_bug.cgi?id=562664) , please consider posting a comment, maybe with your **mtp-detect** output. At least post the output of **mtp-detect** here please.

For now, it seems this bug is specific to the NWZ-S6xx series of Walkmans. If anyone knows a way to get these Walkmans running with media applications, please post. Thank you

---

### Post by element_G on 2008-12-01
Thanks for your response, after running mtp-detect I get the following
```
libmtp version: 0.3.3

Listing raw device(s)
Device 0 (VID=054c and PID=038e) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
   Found 1 device(s):
   054c:038e @ bus 0, dev 2
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.
```Which doesn't seem to give me as much to work with as what was posted on the bugzilla thread. I am currently updating libmtp and hal with the fixes found in the kubuntu forums thread (see OP) and will update once that has finished.

UPDATE: it seems that my attempts to update hal, libmtp and fix them according to the kubuntu thread have left me with a screwed up hal (my mouse and keyboard are a little messed up). I ended up having to reinstall hardy, for now, I will try just fixing my libmtp and hal, and not updating to the intrepid versions of these libs.

---

### Post by robz0rz on 2008-12-03
I've noticed that in Ubuntu 8.10 and Fedora 10, HAL seems to have been fixed already. If you have no further reason to stay with 8.04.1 LTS, I suggest you upgrade to the newest version. MTP is still troublesome, but HAL is able to mount the Walkman.


Also, when fixing MTP through the tutorial in the Kubuntuforums thread, don't forget to adapt the solution to your player!

```
$ lsusb
Bus *xxx* Device *yyy*: ID 054c:*_zzzz_* Sony Corp.
```

Type in *lsusb* in terminal, and look for the line that ends on Sony Corp. Whatever code stands instead of *_zzzz_* is important. Then, add the following to music-players.h instead of what is said in the thread:

```
{ "Sony", 0x054c, "Walkman NWZ-S636", 0x*_zzzz_*, DEVICE_FLAG_UNLOAD_DRIVER },
``` replacing *_zzzz_* with the appropriate code obviously.


Maybe this was the reason for *mtp-detect* to fail.

---

### Post by element_G on 2008-12-03
I've been sticking with ubuntu 8.04 because it 'just worked', and as far as I know kubuntu 8.10 doesn't have KDE 3.5 anymore so upgrading would ruin my KDE install (correct me if I'm wrong) I will give the fixes from the forum thread another shot tonight.

---

### Post by element_G on 2008-12-04
I have applied the fixes to libmtp7 (0.2.6) as described in the kubuntu thread above, I used 038e in place of 035b while editing libmtp's files.

Now it would seem that my PC attempts to connect to my Walkman, however I get this message with mtp-detect
```
sudo mtp-detect
libmtp version: 0.2.6.1

Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
PTP: Opening session
Floating point exception

```
Amarok and Gnomad2 both seem to attempt to connect as well, but they error out. Rhythmbox wont even start when my Walkman is connected. 

What am I missing?

---

### Post by robz0rz on 2009-01-02
Could you maybe see if you have the latest firmware version on your walkman, and if not, update it using a Windows machine? I tried on my walkman from version 1.10 to 1.11, but it hasn't changed anything... Please see if it changes anything for you.

I'm slowly getting the idea that the problem lies with faulty mtp in our walkman. I might go back to the store with my warranty and trade it in for a new one, to see whether the problem is model-specific. Who knows

---

### Post by Mangus on 2009-05-19
Hi!
I have the same problem with the same player (except that mine is the 16Gb model).

Even with ubuntu 9.40 the problem remains the same.
No mtp connection with amarok, and always the same errors with mtp-detect.

---

### Post by dj_bridges on 2009-06-29
Mangus - I have the same model as you (S639F) and am struggling to find anyway of transfering / syncing with my music library.

Have installed just about every music player, but none of them work. Annoyingly it seems like amarok2 has regressed in its compatibility options (amarok 1.4 was able to transfer seamlessly with this player). None of the other players seem to be able to see the device. Strangely though the system recognises it and mounts it correctly, but nothing is recognised with mtp-detect.

Anyone made any breakthroughs with this player??? At the minute it is next to useless - too many songs to transfer to do it manually......

---

