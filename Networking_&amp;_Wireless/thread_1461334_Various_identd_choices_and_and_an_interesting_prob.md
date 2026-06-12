---
title: "Various identd choices and and an interesting problem"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Cypher1101 on 2010-04-24
I've done fairly extensive googling for documentation on any of the different daemon choices for ident, and I've never really found anything beyond how to turn it on and assume default configuration will work. Unfortunately, defaults won't work for me. It seems that  my Linksys wrt54g router decided to block all communication on port 113 (default Identd port) and not give me the option to change that setting (it's ticked and grayed out.)

I want an Identd running because some IRC servers require it, and I don't want to be forced to boot into Windows and run Mirc (which has its own implementation of ident that is mysteriously able to bypass my router's block on port 113, if it actually uses the default.)

Is there a way around this without using another firmware (like tomato, or openwrt) on the  router. If so, what daemon would be best (preferably chosen from the repositories) and how would i go about setting it up, especially with regard to using a different port?

Thanks
~Cypher

---

### Post by kardworx on 2011-12-16
I am sorta new to Ubuntu. Used it 3 or 4 years ago and now again (hate the new version). Did you ever get this figured out?

---

