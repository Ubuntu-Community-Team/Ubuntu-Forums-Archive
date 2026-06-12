---
title: "Wireless network times out"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Elijah2104 on 2009-01-07
I've mistakenly posted this in the wrong category of this forum so I'll repost here and update the former.

My problem is that my wireless card keeps dropping.  I don't believe it's a simple signal loss, it appears that the card is timing out.  It has even happened whilst I've been using it.

The following commands wake it up again:

```
rmmod rtl8187
modprobe rtl8187
ifconfig eth0 up
ifconfig wlan0 up
```

Can anyone help me in stopping this?  As it's my MythTV server, it's important that I'm able to connect to it all the time.

Thanks in advance

---

