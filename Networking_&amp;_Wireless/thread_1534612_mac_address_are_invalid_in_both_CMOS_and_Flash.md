---
title: "mac address are invalid in both CMOS and Flash"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by z987k on 2010-07-19
I just spent a considerable amount of time fixing a bad bios flash and I wanted to post this up in case anyone else out there comes across it so they will know what to do.  Motherboard is an ASROCK 4CORE DUAL VSTA

After flashing the most current bios to a new plcc chip, I got the error "mac address are invalid in both CMOS and Flash press F1 to continue" on startup.  This prevents your onboard nic from working as it can't be talked to without a mac.

So I download the mac address changer tool from ASROCK and used as they said to, but got a "write mac function call fail" error when writing the correct mac address.  Apparently something is either wrong with their tool, or that tool does not work for the 4CORE DUAL VSTA.

A correct and working tool is found here: [http://wiki.nothing.sh/download/ASRock/4CoreDual-SATA2/4Core_MACtool.ZIP](http://wiki.nothing.sh/download/ASRock/4CoreDual-SATA2/4Core_MACtool.ZIP)
and here: [http://www.megaupload.com/?d=LYCJ3XZN](http://www.megaupload.com/?d=LYCJ3XZN)
and the attachment to this post here: [ATTACH]163965[/ATTACH]
Documentation is provided in a readme within the ZIP.  If for some reason those links quit working, PM me, I'm sure I'll keep a copy of it somewhere as important as it is.

Hope this helps someone in the future.

---

### Post by Ben Cole on 2011-07-19
Thanks you very much for posting this. Helped me solve a most irritating problem.

---

### Post by ingo on 2012-03-08
I've put it on a FreeDOS bootable CD stick and get an error message:

```
Illegal Instruction occured
...
Opcades @CS: IP 0F 01 56 FA 0F 20 C0 0C
Aborting program
```

---

