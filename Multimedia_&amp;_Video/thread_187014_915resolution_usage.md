---
title: "915resolution usage?"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by bemenaker on 2006-06-02
Ok, I have added my entry to /etc/default/915resolution to get the proper resolution for my screen.  I saw in another posting, that 915 does run until after the GDM has started.  How do I make this run before, so I don't have to hit crtl-alt-bckspc before signing in?

---

### Post by ajack on 2006-06-04
[QUOTE=bemenaker]Ok, I have added my entry to /etc/default/915resolution to get the proper resolution for my screen.  I saw in another posting, that 915 does run until after the GDM has started.  How do I make this run before, so I don't have to hit crtl-alt-bckspc before signing in?[/QUOTE]

Hi there,

The 915resolution program has been incorporated into X windows in Dapper, you should not need to install the 915resolution proggy.  I solved a similar problem by running dpkg-reconfigure command, but you will need to do a search in this section of the dapper beta secti9on for the full command as I am typing this from memory.

:-k

Edit: Did a search for you... try:

sudo dpkg-reconfigure xserver-xorg

---

