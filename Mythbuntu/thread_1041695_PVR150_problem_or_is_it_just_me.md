---
title: "PVR150 problem or is it just me?"
date: 2009-01-16
forum: Mythbuntu
---

### Post by beachdaze on 2009-01-16
New install of Mythbuntu 8.10 AMD64.  Finally got it all setup and can see the cable tv signal, but it looks like crap.  There seems to be green artifacts (looks like the old Matrix screen saver) running throughout the picture.  I do not get this issue when booted into the Windows partition and using the WinTV app that I downloaded from Hauppauge.  Anyone got an idea why?  I have installed the Gnome desktop as this machine will also be a workstation.

Here is the setup:

Asus A8N-SLI Deluxe (NForce 4 chipset) Motherboard
AMD X2 64 3800+ CPU
4GB DDR400 RAM
Nvidia 6600GT 256MB Video (using the 177 driver)
Creative X-Fi Sound Card
sda = 1TB SATA NTFS drive for storage
sdb = 300GB SATA NTFS Windows (boot drive)
sdc = 300GB SATA Mythbuntu
sdd = 1TB NTFS for backups (USB external)

Thanks for any help - 
Bruce

---

### Post by ian dobson on 2009-01-17
Hi,

Have you setup MythTV to use the correct resolution. If I don't use the native PAL resolution for my PVR-500 (2 PVR-150's on a card) I get lines running across the screen.

Regards
Ian Dobson

---

### Post by xinix on 2009-01-18
Try setting the recording resolution to 720x480.  I had to set my PVR150 to this inorder to get a stable picture.  Do it by going to:
Utilities/Setup > Setup > TV Settings > Recording Profiles > MPEG-2 Encoders
And set if for all the recording profiles you use.

---

### Post by beachdaze on 2009-01-18
> **xinix said:**
> Try setting the recording resolution to 720x480.  I had to set my PVR150 to this inorder to get a stable picture.  Do it by going to:
Utilities/Setup > Setup > TV Settings > Recording Profiles > MPEG-2 Encoders
And set if for all the recording profiles you use.

That was the resolution it was set for.  I will play around with the setings some more see if I can get it any better.

---

