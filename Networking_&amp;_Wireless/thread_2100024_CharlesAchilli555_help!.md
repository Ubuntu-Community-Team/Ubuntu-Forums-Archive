---
title: "CharlesA/chilli555 help!"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by KegHead on 2012-12-31
Hi!

Does bleach bit and Ubuntu tweak erase all internet downloads and visited sites?

Just curious as bleach bit shows files unable to open.

Thanks!

KegHead

---

### Post by WasMeHere on 2012-12-31
> **KegHead said:**
> Hi!

Does bleach bit and Ubuntu tweak erase all internet downloads and visited sites?

Just curious as bleach bit shows files unable to open.

Thanks!

KegHead
Hi again,

Long time no see :-)

I think you can get rid of the visited sites, but the downloads are there as files until you remove them yourself. I doubt that there is a tool that will recognize them, particularly if you have moved them after downloading.

But there are ways to find new files (created or touched after a certain date, for example during the last week).

```
alias veckans='sudo find * -ctime -7 -type f'
```

This alias looks for files within the current directory tree. Modify it if you want to find also hidden files!

---

### Post by KegHead on 2012-12-31
Hi Olle!

Happy New Year!

I'll check it out.

KegHead

---

### Post by KegHead on 2013-01-01
Hi!

Anyone else?

KegHead

---

### Post by KegHead on 2013-01-02
Hi!

Thanks for replies.

Closing out.

KegHead

---

