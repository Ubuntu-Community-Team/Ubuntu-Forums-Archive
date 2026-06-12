---
title: "user-class of &quot;pxelinux&quot; in dhcpd.conf??"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by nobluesky on 2012-05-17
I saw dhcpd.conf example like this:

if exists user-class and option user-class = "iPXE" {                 filename = concat("[http://${next-server]("http://$%7Bnext-server")}/cm/engine/boot_ipxe.php?FILENAME=",binary-to-ascii(16, 8, ":", substring (hardware, 1, 6)));
               ** execute("script");**
 } else {                 filename "ipxe/undionly.kpxe";       }


the script is executed when only ipxe is loaded.

the problem is that I am using pxelinux.

so I want to know how can I execute script only when pxelinux is loaded or tftp situtation.

sorry for poor english

---

