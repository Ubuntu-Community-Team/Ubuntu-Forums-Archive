---
title: "Joining Windows Server 2008 R2 Domain"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by Macrotus on 2011-09-10
Hi all

I have multiple computers Windows computers joined this Windows Server 2008 R2 domain. Now I'm trying to join my Ubuntu computers to the domain. 

I've downloaded and installed Active Directory membership named program from software center, and when I'm joining the domain, I got this

> 9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS server. Potentially the requested address does not exist.

Details

Error code: CENTERROR_DOMAINJOIN_LSASS_ERROR (0x00080047)

Backtrace:
    main.c:335
    djmodule.c:323
    djauthinfo.c:843
    djauthinfo.c:1187

What's wrong?

---

