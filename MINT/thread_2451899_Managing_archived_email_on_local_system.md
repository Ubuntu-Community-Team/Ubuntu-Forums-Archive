---
title: "Managing archived email on local system"
date: 2020-10-12
forum: MINT
---

### Post by George Heine on 2020-10-12
I use my browser, or  Thunderbird (currently 68.10) to manage active email on my system (Linux Mint 18.3).   When an old message is worth archiving, I use Getmail (currently 4.48.0) to transfer it to an mbox file on my local system.   To access the message, I have, up until now, used Fetchmail (currently 6.3.26) to read, view attachments, etc.  Fetchmail has, up until now, required my local password (minor inconvenience, but have tolerated it) , and gives me many warnings about an "insecure server" (no problem, since I am only reading and filing old emails, not sending anything).  Recently Fetchmail seems to have changed; it now asks for a password for "<username>@<servername>@<servervname>.  I editied ~/.fetchmailrc to eliminate the second servername, but it does not recoginize my email server passoword.    

Looking on this forum, it appears that Fetchmail may be obsolete (only one post later than 2016).

Is there a tool that I can use to read and manage (merge, separate, read attachments, etc.) locally stored mbox files?  I know that Thunderbird can manage locally stored mbox files, but would prefer to keep these separate from my active email.  

Thanks for any help.

---

### Post by wildmanne39 on 2020-10-12
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by TheFu on 2020-10-12
I've been using an IMAP server since the mid-1990s.  Lots of reasons for this.
Probably not the answer you want.  Have you looked at elm, pine or alpine?

---

