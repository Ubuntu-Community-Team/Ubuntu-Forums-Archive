---
title: "samba file server crc errors"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by joshlaf on 2006-02-27
Hi.

I'm having trouble with my file server.  My laptop running Windows XP Profressional connects through my wireless router which is connected to my Linux file server running Breezy Badger 5.10.  Samba is configured and works great for small files of a few megabytes but when i try to copy larger files of 500MB+ by dragging the files to the mapped network drive, they stop about 1/4 way through and windows gives me a CRC error message and the transfer halts.  This problem has repeated itself dozens of times.

I checked log.smbd and it states:

lib/util_sock.c:get_peer_addr(1150)
getpeername failed.  Error was transport endpoint is not connected.

I've been researching this all day and haven't gotten anywhere.

The computer I am using as a file server is a 7 year old Dell Dimension XPS with 128MB ram and 600MHz Pentium III processor.  Is it likely something is not configured properly with Samba or is it possible with the transfer of large 1 Gig+ files there is some kind of buffer being over run?

I am some what new to Linux and any help on this is appreciated.

Thanks

Josh

---

