---
title: "Tries to go through localhost for everything."
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by themarker0 on 2010-06-06
So i was trying to Wget some files from a server to test how much i know about Wget. Running Karmic

I turned up this error

> tm0@linutop:~$ wget -r [http://XXXXXX/XXXX/XcXXX/](http://XXXXXX/XXXX/XcXXX/) /home/tm0/Music
--2010-06-06 16:15:55--  [http://XXXXX.com/XXXX/XXXX/](http://XXXXX.com/XXXX/XXXX/)
Resolving localhost... 127.0.0.1, ::1
Connecting to localhost|127.0.0.1|:48080... failed: Connection refused.
Connecting to localhost|::1|:48080... failed: Connection refused.
/home/tm0/Music: Unsupported scheme.
tm0@linutop:~$ wget -r XXXXXXXXXXXXXXXXXXXx /home/tm0/Music
--2010-06-06 16:16:44--  XXXXXXXXXXXXxxx/XXXXXc/
Resolving localhost... 127.0.0.1, ::1
Connecting to localhost|127.0.0.1|:48080... failed: Connection refused.
Connecting to localhost|::1|:48080... failed: Connection refused.
/home/tm0/Music: Unsupported scheme.
tm0@linutop:~$ 
I think it connecting to localhost is wrong right?

---

### Post by themarker0 on 2010-06-07
20 hours, can i bump?

---

### Post by iponeverything on 2010-06-07
Is it only wget that doing this?

---

### Post by themarker0 on 2010-06-07
> **iponeverything said:**
> Is it only wget that doing this?

Also the update manager, or anything trying to connected for downloading. I can browse and irc fine though.

---

### Post by iponeverything on 2010-06-07
what is the output of:

```
export | grep -i proxy
```

---

### Post by themarker0 on 2010-06-07
Nothing happened at all.

---

