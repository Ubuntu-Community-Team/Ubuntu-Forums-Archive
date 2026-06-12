---
title: "Problems with apache and internet explorer"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by xain on 2006-05-12
Hi, I'm experiencing the following problem:

I'm serving my web site with apache2, and when I use firefox everything goes smoothly. However, when I use explorer 6, all I get is a blank page. The access log shows a 304 http code every time the program requesting the page is an internet explorer. This doesn't happen when IE requests a https-protected page.

Has anybody had a problem like this ? Is this a known bug ? Is there a way to disable the cache when the bowser is a IE (like a browsermatch directive)?

I'm running the web server behind a DSL router, and the problem persists when accessed from an "internal" address (I suspected the issue had to do with having the same IP - the router's - requesting the page).

The Apache version is 2.0.54 and I also tried with a 1.3.33 with the same results.

Thanks in advance

---

### Post by xain on 2006-05-21
FYI, I finally solved it. The problem was explorer not being able to deal with international characters (such as accents). Firefox gave no problems, showing them correclty, Opera replaced them with squares, but IE simply displayed a blank page. Once I replaced thing like í with &iacute; it worked OK.

---

### Post by adamkane on 2006-05-21
Where were the international characters?

---

