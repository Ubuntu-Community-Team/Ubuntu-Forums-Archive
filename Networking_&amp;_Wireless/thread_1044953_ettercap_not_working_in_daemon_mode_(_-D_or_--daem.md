---
title: "ettercap not working in daemon mode ( -D or --daemonize)"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by shan23 on 2009-01-19
Hi. I'm using Hardy and whenever i'm trying to use ettercap in the daemon mode, it gives me an error , saying:

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA



BUG at [ec_ui.c:ui_register:339]

 ops->input == NULL

Can anyone help me to fix it ?

---

### Post by shan23 on 2009-01-26
I guess this problem doesn't have a simple solution, coz this is the first time any of my queries on this forum has gone unsolved for about a week !!!

I also think the problem is more related to ettercap than Ubuntu, so i can understand the lack of a reply. Lets hope they fix it in their next release, and its updated in the repos as well !!

---

### Post by felipe1982 on 2009-06-23
I get the same error on openSUSE 11.1(this thread was a google search result)```
sudo ettercap -DTqi wlan0 -l /tmp/etter.log -M arp:remote -P autoadd /10.1.1.2-9/ /10.1.1.1/
```Gives```
BUG at [ec_ui.c:ui_register:339]

 ops->input == NULL
```I think they haven't made any more releases (or even nightlies) since 1994 (just kidding, 2004, but 19xx sounded cooler)

---

