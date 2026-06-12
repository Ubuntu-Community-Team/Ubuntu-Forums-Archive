---
title: "server disk space and information on server"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2009-01-26
I have an Ubuntu 8.04 Server which I am using as a file and web server.

How can I find out out much space I have left on the hard disk on the server?

The server is a CLI and I have 2 hard drives; one for the OS and one for the files. Only the files' hard drive is available via Samba (actually the web directories are too, but I'm going to move that to come from the 2nd hard drive as well once I figure that out).

---

### Post by pytheas22 on 2009-01-26
You can type:
```

df
```

to see how much space is available on all mounted partitions.  Type:
```

df -h
```

if you want the units to be megabytes, rather than bytes (recommended).

---

### Post by Dragonbite on 2009-01-27
> **pytheas22 said:**
> You can type:
```

df
```

to see how much space is available on all mounted partitions.  Type:
```

df -h
```

if you want the units to be megabytes, rather than bytes (recommended).

Thanks!  My drive is only 80 GB so I have a feeling all those .ISO images I've download are filling up the space fast! ;)  I'm thinking it's time to copy all of those onto a DVD since they don't change.

---

