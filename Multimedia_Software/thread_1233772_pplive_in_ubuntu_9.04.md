---
title: "pplive in ubuntu 9.04?"
date: 2009-08-07
forum: Multimedia Software
---

### Post by ilovejazzmusic on 2009-08-07
I can't find anything on installing pplive on ubuntu 9.04.
Does this mean it's impossible? Or that I just didn't find the information?
Anyone got pplive running successfully on linux?
Thanks
Nik

---

### Post by ilovejazzmusic on 2009-08-07
[http://www.cnbeta.com/articles/90406.htm](http://www.cnbeta.com/articles/90406.htm)

this site looks to contain instructions but i can't really understand them (because the instructions are in chinese). can anyone help out with this?

---

### Post by hblaw on 2009-08-07
wa. I'll try this.

---

### Post by afrodeity on 2010-06-10
would be great if we could get this to work on lucid

[http://forum.ubuntu.org.cn/viewtopic.php?f=73&t=219084](http://forum.ubuntu.org.cn/viewtopic.php?f=73&t=219084)

---

### Post by afrodeity on 2010-06-10
I installed  the pplive deb available from [here ]("http://forum.ubuntu.org.cn/download/file.php?id=73796&sid=6f633a67539349e8a960c8b9d2980497")

There seems to be a bit of a dependency problem.

Then followed this solution to download and install first: [http://ftp.us.debian.org/debian/pool/main/h/hildon-fm-l10n/hildon-fm-l10n-engb_3.0.r4450.debian-1_all.deb](http://ftp.us.debian.org/debian/pool/main/h/hildon-fm-l10n/hildon-fm-l10n-engb_3.0.r4450.debian-1_all.deb)

Then download and install: [http://ftp.us.debian.org/debian/pool/main/libh/libhildonfm/libhildonfm2_1.9.49.debian-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/libh/libhildonfm/libhildonfm2_1.9.49.debian-1_i386.deb)

However I got some errors about the symbols in the libraries.

When trying to run pplive I get this:

```

pplive
pplive: symbol lookup error: /usr/lib/libhildonfm.so.2: undefined symbol: gtk_file_system_cancel_operation

```

There must be an easy fix to this. Any ideas?

---

