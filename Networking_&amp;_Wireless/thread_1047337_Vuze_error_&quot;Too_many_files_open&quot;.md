---
title: "Vuze error: &quot;Too many files open&quot;"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by cong06 on 2009-01-22
In Vuze I decided to open up the connection per torrent so that I would be able to connect to more peers, and got this error:
```
Error Disk read error <file-path> (Too many open files), open fails
```

So, I checked my max file limit:
```
sysctl -a | grep "fs.file-max"
```
shows that apparently I can currently handle "282104"

Which shouldn't be any problem at all, I had set my max connections per torrent to 2000, later 1000, and currently I'm at 500 (it still threw that error overnight). It only uses this cap on downloading torrents (of which there were only 2) uploading torrents the cap is at 10.

My real question for Vuze is: How many files are created with each connection? I'm really just curious about this, it's not really an "issue."

---

### Post by Deathcon_1 on 2009-12-08
Instead of making a new thread for this topic, I'm going to bump this one because I'm running into the same issue.

```
sysctl -a | grep "fs.file-max"
fs.file-max = 197407
```

I don't see how I can possibly have more then 197,000 files open for just Vuze, and [legit] torrents are the only thing this box does.  Guys on the Vuze forums have bounced [us] to the Ubuntu forums looking for an answer.

---

