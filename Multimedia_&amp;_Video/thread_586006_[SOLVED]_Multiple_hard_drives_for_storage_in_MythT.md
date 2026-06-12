---
title: "[SOLVED] Multiple hard drives for storage in MythTV?"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Blue Sassley on 2007-10-21
Hi I wanted to know if I can use multiple hard drives in my MythTV backend server for storage or can you only have one big drive or a RAID 0 or 5 array?

Thanks for the help,
Blue

---

### Post by rusty0101 on 2007-10-21
As I understand it, at the moment you can only use a 'single filesystem' solution. That does not mean single drive, just that you have to use something that presents multiple drives (if used) as a single drive.

The reason for this is that the branch that is working on multiple drive solutions for MythTV is not in the main branch yet, or is not in the release editions yet, which are what Ubuntu and Mythbuntu are using at the moment.

If you are willing to wait a few months, I would expect that the 8.04 development editions will support support storage groups. If you can afford a 500 Gig or 750 Gig drive to dedicate to that storage in the interim, it could be the foundation for additional storage later on as well.

---

