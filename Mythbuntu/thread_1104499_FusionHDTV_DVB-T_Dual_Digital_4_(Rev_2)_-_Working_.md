---
title: "FusionHDTV DVB-T Dual Digital 4 (Rev 2) - Working and then not"
date: 2009-03-23
forum: Mythbuntu
---

### Post by merbert on 2009-03-23
Hi

New to all of this, but thought that I had gotten to the end of my travails...

My system is a newly built box:
Mythbuntu 8.10
AMD Phenom 9550
ASUS M3N78-EM
2GB 6400 DDR2
WD 500G
Pioneer 216 
ASUS Broadcom based wireless card
FusionHDTV DVB-T Dual Digital 4 (Rev 2)

I had installed the OS, configured the wireless (which still works), updated the OS for the Rev 2 driver, and had working TV (All stations were ok). Mapped to a couple of spots on my NAS (where I have my music and other stuff) and things were/are playing fine from there.

The updates were downloaded and installed (all 181MB of them).  

I then tried to program to record from the EPG (set up as the free to air transmitted version) and selected a program, went through the process, reviewed all the options, and set it to record. When I went out to the EPG, the indicator said "Not recording", and when I checked in the scheduled recordings, there was no recording scheduled. Tried a few more times to no avail.

Redoing the drivers did not help.

I shut the thing down, and restarted later. Now I could not even watch TV (the blue led that had been bathing the bottom of my case with light was not on either). Can anyone point me to what has happened?

A couple more things 

- I have no idea how to get the remote working. I tried to follow one of the threads here, and had little success.  I have installed the lirc conf file for this remote into the directory (I'm at work and can't remember what it was, but I had to rename the old one), and still no luck.

- When I try to play a DVD MythTV locks

The (relevent) results of lsusb:

Bus 005 Device 003: ID 0fe9:db98 DVICO 
Bus 005 Device 002: ID 0fe9:db98 DVICO 

The results of dmesg |grep DVB are no lines returned.

Not sure what to do from here

Thanks

Merbert

---

