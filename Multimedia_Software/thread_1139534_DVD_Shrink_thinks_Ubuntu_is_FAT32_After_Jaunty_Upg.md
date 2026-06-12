---
title: "DVD Shrink thinks Ubuntu is FAT32 After Jaunty Upgrade - Can I Fix? Can't Create ISOs"
date: 2009-04-27
forum: Multimedia Software
---

### Post by OzzyFrank on 2009-04-27
OK, **DVD Shrink** is indeed the Windows app running in Wine, which I have done without issue since 2006 (OK, let's not get into it crashing after each disc I rip, hehe!), until the upgrade to Jaunty today. Now, when I choose to save the output as an **ISO image**, eg: Crowley.iso, it **saves a bunch of 1 Gb files** (Crowley.IO0 through to Crowley.IO3, with the remainder going to Crowley.IO4) **and a** 4Kb Crowley.**MDS file**.

Now, I can save to the usual folders (VIDEO_TS) instead of an ISO and burn that, but forget trying to create a 4.4Gb ISO image. Looking in forums I found Windows users having this happen, and invariably people would reply that it is because people are trying to save to a **FAT32** drive instead of an NTFS one. Now, I understand FAT32 has a filesize limit of 4Gb, but am perplexed as to why after all this time DVD Shrink would think I am using a FAT32 drive/partition when it has been saving to Ubuntu's EXT3 filesystem with no problems at all until now.

Does anyone know what is happening, and how to remedy this? At the moment I am just using the workaround of creating folders instead of an image, which at least means I don't have to boot into Windows just to use this app.

While we're here, I may as well ask if you guys know of an equivalent, and by "equivalent" I mean a native app that does _EVERYTHING_ DVD Shrink does, meaning removal of copyright protection (in most cases) and the choice of saving to folders or an ISO image. Not sure if I remember correctly, but **xDVDShrink** does not remove copyright protection, just shrinks projects to a burnable size (correct me if I am wrong, or if this has changed since I last used it).

By the way, just tried saving a project as an ISO to my NTFS partition, assuming it would make a difference, and it has done exactly the same as outlined above. Would this then mean it's a Wine issue with this version of Ubuntu? All comments welcome...

[COLOR="DarkRed"](Note to the easily-offended who are asking "Why one Earth are you asking about a Windows program HERE??" - everyone I personally know who uses Ubuntu also uses DVD Shrink, and I am aware from looking around that this is perhaps one of the most-used Windows programs in Ubuntu/Wine, so feel this is a valid question).[/COLOR]

---

### Post by OzzyFrank on 2009-06-09
I joined the Wine forums and reported this; it was fixed in the next Wine update a few days later. Gotta love the open source world!

---

