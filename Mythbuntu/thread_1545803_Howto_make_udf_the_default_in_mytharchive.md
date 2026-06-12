---
title: "Howto make udf the default in mytharchive"
date: 2010-08-04
forum: Mythbuntu
---

### Post by bcg30506 on 2010-08-04
I am making native archives onto DVD/DL discs with mytharchive so I can free up space but still watch old shows either through mythvideo or by importing the archives back as recordings.  This is working fine for me thus far.

However, some of the shows are over 3GB in size, which my mythbuntu 10.04 system handles great.  But one of my frontends is a Mac running OS/X and it requires the discs to be burned with the UDF option.  Otherwise, the large files show a negative filesize and they cannot be used or even copied from the mounted disc in Leopard.

I ran a test by manually burning a disc on my Linux system using genisoimage with the -udf parameter added, and this disc worked perfectly on the Mac now too.

So my question is, how do I make the udf option always be on by default when using mytharchive's interface so I don't have to use the command line to make these discs in the future?  Under settings, I do not see an option for genisoimage at all - only mkisofs which appears to no longer be used in 0.23-fixes for native archives.

Thanks.

---

