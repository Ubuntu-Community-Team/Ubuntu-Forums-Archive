---
title: "smbclient much faster then smbmount/ nautilus/ dolphin ???"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by mkonline on 2009-12-15
Hi,
I have a sambaserver running ubuntu server 9.10 and a gigabit network. Downloading files with smbclient in a terminal is twice as fast than using nautilus or dolphin smbmount (smbfs) (66MByte/s against 30MB/s). I tried with a ubuntu 9.10 and opensuse 11.2 client. Same with upload (30 against 20). When I use instead an opensuse 11.2 server - the same :-(
Why is smbclient so much faster and how can I accelerate the the X application to the same performance?

Generally performance with Samba is unsatisfying. With FTP I get + 100MB/s in both directions. I do not use Jumbo packets (switch can not handle those).

Any idea?
thanx

---

