---
title: "rtorrent kills networking"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by FearlessPc on 2009-02-19
Hello

Whenever i start rtorrent it kills all my networking capability except web surfing.

All the details are in [here]("http://ubuntuforums.org/showthread.php?t=1059932"), the only difference is now i have to restart my PC to get things back to normal.

Thanks

---

### Post by yoyoned on 2009-02-19
limit the upload speed of the torrents

---

### Post by FearlessPc on 2009-02-19
> **yoyoned said:**
> limit the upload speed of the torrents

I'm on 1.5Mb dsl, max upload is 12k rtorrent is set to 10k .

---

### Post by superprash2003 on 2009-02-19
bring that limit down to a little more and try

---

### Post by FearlessPc on 2009-02-19
Ok, upload is now on 8k, i will test and report.

You believe rtorrent is choking my connection ?

---

### Post by superprash2003 on 2009-02-20
yes

---

### Post by FearlessPc on 2009-02-21
So far so good, it seems that everything is working fine until now.

I wonder why rtorrent stopped enforcing the upload limit.



Thank you for the help, i hope it will be the end of it.

---

### Post by FearlessPc on 2009-02-23
Problem solved

I had to drop the upload limit to 4k.
I use conky to see the upload and when rtorrent is set to 4k it uses 10k .

at least I'm not alone: "[rtorrent choking my internet connection]("http://www.mail-archive.com/linux-il@cs.huji.ac.il/msg49346.html")"

---

