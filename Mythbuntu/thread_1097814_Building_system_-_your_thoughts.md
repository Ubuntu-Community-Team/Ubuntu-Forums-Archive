---
title: "Building system - your thoughts"
date: 2009-03-16
forum: Mythbuntu
---

### Post by Billsputters on 2009-03-16
I've been following the development of MythTV for a good while now and have been lurking on the forum trying to learn what I can. So I am a complete newbie regarding installing a MythTV system.

It's all to be built around an MSI Media Live box, with a 5600 AM2 CPU and 1TB WD green hard drive. As the finished system will live in Uganda, I only be able to record composite from the Sat Receiver (DSTV) so a simple Hauppauge WinTV PVR150 should suffice.

I was toying with the idea of having a separate SSD drive for the boot partition, and using the larger drive for the video/music data. From what I have read, I can have the large partition named /Video (or something) and have subfolders below that and then configure MythTV to use them. Am I correct in this assumption, or is it more complicated? And is it worth investing in an SSD for such purposes. I may well in the future separate Front end and Back end into two machines at a later date.

What is the preferred way of installing. Mythbuntu direct or Ubunto desktop, remove unwanted apps (Openoffice etc.) and then add in MythTV.

Using 2Meg Ram - do I need a swap disc? If I go the SSD route for / and /swap I have read that swap partitions are not that effective on SSD's due to cyclelife - mind you this was with another OS of the XP variety!

Sorry for all the questions in one post.

---

### Post by 4dognight on 2009-03-16
Your CPU and memory is more than plenty for what you want to record.
As for SSD, I have just recently tried installing onto a 4gb CF , with success. A fresh install uses about 1.3 GB. I would also advise setting vm.swappiness=0 to avoid using a swap file. I would reccomend using the mythbuntu distro. It works very well.

---

### Post by Billsputters on 2009-03-28
Finally got all the bits. About to try an install. I read somewhere that /cache is used for the buffer for LiveTV. Is that right?

---

### Post by fenian on 2009-03-28
> **Billsputters said:**
> Finally got all the bits. About to try an install. I read somewhere that /cache is used for the buffer for LiveTV. Is that right?

No,live tv is recorded temporarily to /var/lib/mythtv/recordings .

---

