---
title: "uninstalled zeitgeist, now dash cannot search"
date: 2011-04-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by canabal on 2011-04-27
Hey all,

A while ago I was messing around and in doing so I uninstalled zeitgeist to test a few things.  I have since re-installed it to the best of what I remember what was installed in terms of each package, but now my dash comes up empty when searching anything.  I can search anything from firefox, web browser, home, etc. and no matter what I search it always comes empty.

I have a feeling I just need to rebuild a database or I am missing a package, but any tips would be great.

---

### Post by canabal on 2011-04-27
In case this will help:

name@machine:~$ ps -aux | grep zeitgeist
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
nicholas  1397  0.0  0.1  48080  4768 ?        Sl   Apr25   0:00 zeitgeist-datahub
nicholas  1411  0.0  0.2  17080  9372 ?        S    Apr25   0:00 /usr/bin/python /usr/bin/zeitgeist-daemon
nicholas  1735  0.0  0.0      0     0 ?        Z    Apr25   0:00 [zeitgeist-datah] <defunct>
nicholas 14548  0.0  0.0   5308   856 pts/0    S+   21:28   0:00 grep --color=auto zeitgeist

name@machine:~$ ps -aux | grep unity
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
nicholas  1782  0.0  0.2  31488 11344 ?        Sl   Apr25   0:07 /usr/bin/unity-window-decorator
nicholas  1788  0.0  0.4 118220 19612 ?        Sl   Apr25   0:40 /usr/lib/unity/unity-panel-service
nicholas 14550  0.0  0.0   5304   856 pts/0    S+   21:28   0:00 grep --color=auto unity

---

