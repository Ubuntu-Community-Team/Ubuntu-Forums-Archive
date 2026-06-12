---
title: "Migrating 7.10 (32-bit to 64-bit)"
date: 2008-04-03
forum: Mythbuntu
---

### Post by stevanbt on 2008-04-03
Hi,
I'm planning on migrating from Mythbuntu 7.10 (32-bit) to 7.10 (64-bit) - I don't know why I installed 32-bit version to start with I just did.  I have the following setup:-

AMD 4200+
2Gig memory
2 x 500 Gib SATA drives

The 32-bit version of Mythbuntu (everything works ok).  64-bit is installed (tv cards work ok, dvds work ok).

My question is simple, I hope.  What's the best way to get the data from 32-bit to 64-bit?  I assume I'll have to dump the database from 32-bit and restore to 64-bit (hopefully no gotchas).  Then copy over recordings, music, digital pictures etc.

Thanks in advance, Steve.

---

### Post by tgm4883 on 2008-04-03
install phpmyadmin, backup the db, then just restore it in the 64-bit os(install phpmyadmin there too)

then  just copy over your recordings, etc

---

