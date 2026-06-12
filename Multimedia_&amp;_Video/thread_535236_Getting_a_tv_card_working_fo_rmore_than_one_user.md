---
title: "Getting a tv card working fo rmore than one user?"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by captainpotato on 2007-08-26
Hello all,

I'm having a frustrating problem getting my tv card recognised with Ubuntu 7.04. Well, that is, getting it work with more than one user. The card is recognised and works fine with Kaffeine for one user, but if I change users, none of the other users can use the tv card (Kaffeine's other functions still work though). If I load Kaffeine using the CLI, it doesn't spit out any errors, (other than '0' and '4' on separate lines, but nothing else).

I've given the other user the same privileges as the main user using the 'users and groups' menu item and included the second user in the group of the first, but all to no avail.

Any ideas?

---

### Post by captainpotato on 2007-08-27
Replying to my own question - the problem was that the user wasn't a member of the 'video' group. ie:

In the file /etc/group

video:x:82:<username>

---

