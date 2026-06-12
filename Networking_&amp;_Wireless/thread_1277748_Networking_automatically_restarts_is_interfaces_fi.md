---
title: "Networking automatically restarts is interfaces file is edited"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by KeithHansen on 2009-09-28
I was working on a remote ubuntu server and I edited the /etc/network/interfaces file to change an interface configuration from eth5 to eth6. Once I did a ":wq" I lost network connectivity and I cannot access the system anymore. (I am in USA server is in Belgium)
Why would networking automatically restart just due to the file edit?
Can this be stopped from happening?

---

### Post by Iowan on 2009-09-29
That's not the way it's *supposed* to work... I'm not aware of a "reload configuration on change" option (but that doesn't mean there isn't one).

---

