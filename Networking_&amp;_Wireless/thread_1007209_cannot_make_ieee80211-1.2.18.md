---
title: "cannot make ieee80211-1.2.18"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by Ameades on 2008-12-10
Hey, I have been searching the internet for hours trying to find a solution so I figured it is time to post.  

I am trying to update my ieee80211 module so that I can patch my wireless card with ipw2200-1.2.2 and so that I can inject packets.  The except when I am following these directions from aircrack's sit, I cannot get past making ieee80211-1.2.18.

Here are the instructions I am following:

from [http://www.aircrack-ng.org/doku.php?id=ipw2200](http://www.aircrack-ng.org/doku.php?id=ipw2200)

wget [http://superb-west.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.17.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.17.tar.gz)
tar zxvf ieee80211-1.2.17.tar.gz
cd ieee80211-1.2.17
sudo make
sudo make install

when I go to make it I keep getting this error.

/home/andrew/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/andrew/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/andrew/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/andrew/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/andrew/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [modules] Error 2


that is part of it.

I guess I am missing something to compile the module but I do not know what it is.

Any help at all would be greatly appreciated.  Thank you.

---

### Post by Ameades on 2008-12-10
Please let me know if you need some more information.  Cheers

---

### Post by Ameades on 2008-12-12
anyone have any idea?

---

