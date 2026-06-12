---
title: "Brasero cannot see DVD, and /media/cdrom0 appears empty"
date: 2011-08-24
forum: Multimedia Software
---

### Post by peruvianllama on 2011-08-24
On 10.04, opening Brasero and selecting the 1:1 disc copy option, the dropdown list for "Select disc to copy" is greyed out, with the message "No disc available. There is a (non-commercial) DVD in the drive which does not have any apparent problems. If I open VLC Player and select "Media->Open Disc", then VLC allows me to open /dev/sr0 and correctly plays the DVD video from the disc.

Under the Disk Utility, it shows that media is mounted from the DVD drive, and specifically mounted at /media/cdrom0. Yet browsing to that directory with Nautilus shows me just an empty folder. Running, as root:
*ls -lh /media/cdrom0*
gives me 
*dr--r--r-- 2 4294967295 4294967295 508 1999-12-31 20:00 VIDEO_TS*
which is roughly what I'd expect. Further, the CD/DVD drive does not show as an icon next to File System, Desktop, Network, etc., from within Nautilus, nor under the 'Places' menu, nor on the desktop after the disc has been inserted. DVDs containing regular data do not encounter any of these issues; things are mounted and recognized exactly as I would expect.

Ultimately, I have been able to use k9copy to create an ISO of the DVD, but the 1:1 copy in Brasero was initially what I was hoping for (I'm not certain whether k9 does a straight byte-for-byte copy, or whether there's encoding/decoding going on in between).

Any thoughts on what could be causing any or all of this? Brasero having some problems is one thing; but why is /media/cdrom0 apparently empty, despite the drive being mounted?

---

