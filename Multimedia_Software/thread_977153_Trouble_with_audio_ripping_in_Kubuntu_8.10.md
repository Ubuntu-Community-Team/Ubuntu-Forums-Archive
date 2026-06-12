---
title: "Trouble with audio ripping in Kubuntu 8.10"
date: 2008-11-09
forum: Multimedia Software
---

### Post by swaq on 2008-11-09
I am running Kubuntu 8.10 64-bit and can not rip a CD.  When I put an audio CD in the computer no windows or boxes come up.  I tried going to audiocd:/ and at first it displayed some files and directories but then it stopped working without me changing anything, giving access errors or something.  After unchecking the System Settings -> Advanced -> Audio CDs -> Specify CD Device box I could see it again and I went to the FLAC folder and started copying the files to my hard drive.  It got about 200 bytes in and then it just stopped copying.  After that nothing would copy at all and I keep getting the following error:

```
Unknown error. If you have a cd in the drive try running
cdparanoia -vsQ as yourself (not root). Do you see a track list? If
not, make sure you have permission to access the CD device. If
you are using SCSI emulation (possible if you have an IDE CD
writer) then make sure you check that you have read and write
permissions on the generic SCSI device, which is probably
/dev/sg0, /dev/sg1, etc.. If it still does not work, try typing
audiocd:/?device=/dev/sg0 (or similar) to tell kio_audiocd which
device your CD-ROM is.
```

I tried the cdparanoia command and it said: "004: Unable to read table of contents header".  If I try the ?device=/dev/xxx then I either get the same error as before, a "could not read /dev/xxx", or "Device does not have read permissions for this account. Check the read permissions on the device."

I tried ripping with soundKonverter, and it can see the contents of the CD and properly look up the CDDB tags, but when I go to rip to my hard drive it fails no matter what codec I was trying to rip to.  The log just gives the error: "Removing file from conversion list. Exit code 1"

VLC will play CDs.  Amarok also seems to work, except that it takes 8 minutes to load the songs into the playlist.  Please help!

---

### Post by swaq on 2008-11-10
Forgot to mention, I have two optical drives.  One is a Blu-ray drive and the other is a DVD burner.  VLC will play an audio CD from either, but neither works for ripping.

---

### Post by mc4man on 2008-11-10
First I have to thank you for the audiocd:/. I've only used kde4 for a couple of days and couldn't find the audio cd anywhere.(would have been nice if there was a link visible somewhere

It seems to be working fine here with the built-in ripper/encoder (I'm assuming that's what the Flac, mp3, ect. folders are all about.
The only thing that comes to mind is right after the install I added myself to the disc group, other than that nothing special. (noticed cdrom and plugdev groups were already enabled by default while doing so
Sorry couldn't be more helpful - kde4 is still totally foreign to me coming from gnome

edit: just noticed you can create your own link and   finished an album in Ogg/Vorbis so it does work as expected.

---

### Post by swaq on 2008-11-10
Thanks for the reply.  I'm not sure if I'm in the 'disk' group.  I'll have to check that when I get off work.

---

### Post by swaq on 2008-11-10
I added myself to the 'disk' group and at first I could see the contents of audiocd:/.  I started copying from the FLAC folder again and it only got 188 kB in before it said "Stalled" and wouldn't copy anymore.  Then going to audiocd:/ gave the same error as above again.  soundKonverter is still not working.

---

### Post by swaq on 2008-11-10
Just tried the cdparanoia command again and it displayed a track listing.  So I tried using cdparanoia to rip to wav and it was successful...  So, why aren't audiocd:/ and soundKonverter working?

---

### Post by swaq on 2008-11-11
Still having this problem.  Is there any other diagnostics or such that I can do to help pinpoint the problem?

---

### Post by swaq on 2008-11-13
Anyone?  Sorry that I keep bumping this thread.

---

### Post by AlterEgo on 2008-11-15
All I can add is a 'me too'.

Soundkonvertor works nicely, excdept for Flac.

---

### Post by swaq on 2009-04-04
So today I decided to give this a shot again.  I was able to rip a full CD, but it wasn't what I expected.  It ripped the CD out of my second drive using the tags from the CD in the first drive...  What the heck?

---

### Post by swaq on 2009-04-04
Hmm, I just unchecked "Specify CD Device" under the Audiocd IO Slave Configuration and I can now copy files using audiocd:/ from my second drive.  Haven't tried the first drive again yet.

---

### Post by swaq on 2009-04-04
Well I know I'm talking to a wall, but oh well.

The first drive still doesn't work, but that's not a big issue as long as I can get at least one to work.  However, after ripping one CD I put in another one and tried to refresh audiocd:/.  Unfortunately it is still displaying the file names from the last CD I ripped...  This is so annoying.

---

