---
title: "copy to samba share slow with dolphin in maverick"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by mstreibe on 2011-01-13
I have a new laptop with a 10.10 64-bit kubuntu installation. On my old laptop I have 10.04 32-bit. The following problem exists only on the new laptop.

Copying a local file to a samba share in my home network (mounted with smb4k or manually with mount.cifs, makes no difference) with dolphin is painfully slow. The transfer speed is only 60k/sec. There's no other activity on the samba share.

If I do the same file copy in a terminal with cp (or smbclient without mounting the share), the transfer speed is 2.5-3 MB/sec, which is what I'm used to with samba shares here, An scp between the two laptops reaches up to 10 MB, which should be close to the max on the 100 Mbit network that I have. Don't know why samba makes only 3 Mbit/sec. Anyway, that speed is fine with me,

Copying FROM the samba share to a local disk is fast in dolphin too, but why is copying TO the samba share so slow?

---

### Post by mstreibe on 2011-01-21
Copying to the samba share without mounting, but rather by using the Networking features, which I guess is smbclient based, is fast. Maybe it has to do with the refreshing done by dolphin on local files. It probably thinks the smb-mounted target is a local FS, and polls with high frequency for changes for changes in the displayed files, which slows down my (not so fast anyway) NAS drive.

---

