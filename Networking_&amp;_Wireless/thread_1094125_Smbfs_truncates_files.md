---
title: "Smbfs truncates files"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by raulherbster on 2009-03-12
Hi,

I'm using ubuntu as a VM on a Windows environment for building and testing. I need to share some paths using samba. Everything worked really fine with Gutsy. However, samba filesharing has now some serious problems in Intrepid, since smbfs was rewritten and it introduced bugs with truncating files.

We discovered such problems with autotools-based projects -- the "autoconf" step produces a "configure" which is truncated at the end.

Does anybody have any idea which is the problem?

Thanks a lot in advance, Raul.

---

