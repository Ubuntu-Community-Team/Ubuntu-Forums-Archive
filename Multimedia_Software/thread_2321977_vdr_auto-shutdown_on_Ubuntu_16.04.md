---
title: "vdr auto-shutdown on Ubuntu 16.04"
date: 2016-04-25
forum: Multimedia Software
---

### Post by jtkarvo on 2016-04-25
hi!

What is the right way to configure acpi shutdown for Ubuntu 16.04?

I tried by uncommenting the 
--shutdown=/usr/lib/vdr/vdr-shutdown.wrapper

line in /etc/vdr/conf.d/00-vdr.conf

However, using journalctl I cannot find any log entries for the vdr process even trying to run shutdown-hooks.

---

