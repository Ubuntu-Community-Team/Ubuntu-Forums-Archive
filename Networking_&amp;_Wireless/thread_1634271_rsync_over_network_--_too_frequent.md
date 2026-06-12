---
title: "rsync over network -- too frequent?"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-11-30
I have a home network that includes a couple of computers {A, B, C, D}.  currently, I have a cron jon that runs every minute and updates (using  rsync) the hard drives of computers {B, C, D} with the contents of hard  drive {A}.

So far everything works great, as hard drive {A} barely has any information on it.

Now, I am about to copy a lot of information (about 8 GBs) to hard drive  {A}. Naturally, the cron job will run (as it runs every 1-min) and try  to 'sync' the contents with hard drives {B, C, D}.

given my network (100Mbit/sec), there is no way the cron job will be  able to 'copy' the contents to hard drives {B, C, D} in one minute. It  will take much more time. 

Does this situation create a problem? meaning, will cron re-run a new  rsync instance 1min later, even though an existing rsync process is  running and still copying information to hard drives {B,C,D}?

will my backups be hurt / slowed down tremendously because of this? 

Thanks for any help.

---

