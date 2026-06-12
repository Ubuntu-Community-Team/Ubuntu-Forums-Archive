---
title: "Video card needed for TV??"
date: 2018-10-15
forum: Multimedia Software
---

### Post by linuxhippy on 2018-10-15
I've been running Mythbuntu software for many years now on different old computers.  My most recent box is an old Power Spec 6640 AMD Athlon 64 from around 15 years ago that has integrated video, 4 PCI slots (2 are populated with tuner cards), and a now blown PCIe slot.  I had a Radeon PCIe Video card in this computer for many years but unfortunately a couple weeks ago the card fan stopped working and blew out that PCIe slot.  It took me a while to figure out what was going on since it effected my BIOS and the video seemed to work.  So I got around to taking that PCIe card out and replacing with an ATI card and I had the same BIOS problems again (it won't boot and asks for a password).  I found that if I leave the PCIe slot empty it boots but in the process of figuring things out I wiped my drive of mythbuntu.

I reinstalled mythbuntu 16.04.5 with a fresh install and it boots fine.  I am just using the integrated video now which seems to work for setting up everything including my Pinnacle PCI tuner cards which scan OK and find plenty of channels.  The problem happens when I go into the frontend and try to watch TV.  It gives no error but almost immediately closes the TV and returns to the top menu in mythbuntu.  I am able to watch the videos it downloads for testing just fine in fullscreen but LiveTV is a problem.   Does this mean that I need a video card?  Perhaps an old PCI video card would work?

Oh the RAM.  I have 128 MB dedicated in the BIOS for the integrated video and about 1.4 GB for everything else.

Marty

---

### Post by deadflowr on 2018-10-16
Check the livetv storage settings and owner/group permissions.
Even with a well worn and super old gpu you would get playback.
[https://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions]("https://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions")

---

### Post by linuxhippy on 2018-10-16
Nice-I thought this should work without a video card. I'm not sure if I could even find a PCI video card anymore since everything PCIe.

I'll check permissions and post back!

Marty

---

### Post by deadflowr on 2018-10-16
> **linuxhippy said:**
> Nice-I thought this should work without a video card. I'm not sure if I could even find a PCI video card anymore since everything PCIe.

I'll check permissions and post back!

Marty

Perhaps misunderstood (or I worded it off-key), I meant any gpu (integrated or dedicated) would run something. So it should run with or without a dedicated video card.

The issue you have is something I have seen myself, and it usually ends up being I mucked the permissions.
(Usually when I replace the disk the storage is on. And then I forget it has unique group and permission settings)
From memory the directory needs to be writable by the mythtv group as well as the owner.

But that's me and what I've seen with regards to the issue at hand.

---

### Post by linuxhippy on 2018-10-16
U didn't word it wrong but jogged my memory.  I've been using mythbuntu for over 10 years and permissions problems are something I dealt with years ago and forgot.  I think what u said is probable.  What integrated video does that I don't like is that some windows won't maximize so I found a new PCI video card still in the box on eBay and bought it so I'm guaranteed to be happy with free TV again!  
I've been using Mint Linux, Fedora, Slackware, and Ubuntu all that time and didn't totally forget about permissions so use home directory for each user and usually good but not in mythbuntu.  Here's good article:

[https://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions]("https://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions")

My PVR computer is named FreeVo-anybody remember TiVo?? :lolflag:


Marty

---

### Post by linuxhippy on 2018-10-16
Got it working and it was a permissions thing.  I set the 2 recording directories in the backend to a place where mythtv (that's the mythbuntu user/group) can write.  Anything in /var/lib/mythtv would work.  I used these 2:

/var/lib/mythtv/recordings
/var/lib/mythtv/livetv

Then started the backend and TV was fine though some shows were choppy and I think that's due to integrated video but my video card is on the way.

Thanks for all the help!

Marty

---

