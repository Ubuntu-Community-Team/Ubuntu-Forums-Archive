---
title: "retrieving html code in bash"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by xspace on 2009-05-10
I need a command, something like nslookup that will dump the entire html code of a website in bash?

---

### Post by xspace on 2009-05-10
bump

---

### Post by doas777 on 2009-05-10
i'm really not sure what you are asking. you cannot "dump" all the html from a website, because you must format handler requests for each page. usually they call programs that attempt to visit (and possibly retreive) every page on a site, Crawlers. most crawlers just try to hit all links available from each page, so they can't get to non-linked content, unless you tell them what the address of the page is. 

as for nslookup, I have never seen it function in the way you describe. it just returns one result, unless your doing a zone transfer i guess (and that would only work because the server was programmed to work that way).

now if you want to download a page, and analyze it's source, you can use the wget command to download the page. I've written a few scripts that will download the page, and look for a link to the next, so that it can recurse until there are no more refered pages, but that has to be written for each and every site, and may be easily rendered impossible by the web developers. check out this thread for that approach: [http://ubuntuforums.org/showthread.php?t=1109463&highlight=download+comics](http://ubuntuforums.org/showthread.php?t=1109463&highlight=download+comics) 

do some googleing on webcrawlers and see what you find.

---

