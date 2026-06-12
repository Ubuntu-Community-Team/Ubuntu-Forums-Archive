---
title: "Bizarre issue with google chrome"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by akwatve on 2010-03-29
hi,

I am seeing a bizarre problem with google chrome.

I have a link ~/bin/firefox which was earlier pointing to my stable FX installation. I recently removed firefox and installed chrome instead. As most of my shortcuts use the link ~/bin/firefox I just updated it to point to chrome installation i.e.

foo@bar:~/bin$ ls -lht
total 8.0K
lrwxrwxrwx 1 foo foo 22 2010-03-29 21:05 firefox -> /usr/bin/google-chrome

Now, whenever I try to run chrome by typing firefox on the console, it start zillion processes named "chrome" and my machine becomes unusable unless I kill them all.

The funny thing is if i just rename the link from firefox to something else, everything works normally. I cannot convince myself that the name firefox is jinxed in chrome. I am wondering if there is any config issue which results in this. Not that this is a show stopper. For now I have renamed the link to chrome and life is normal. But it is just a curious problem in first place.

Any help would be greatly appreciated.

Thanks in advance

---

