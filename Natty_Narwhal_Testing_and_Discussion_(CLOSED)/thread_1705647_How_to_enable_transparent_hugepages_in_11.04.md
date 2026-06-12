---
title: "How to enable transparent hugepages in 11.04"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bhaskar on 2011-03-12
11.04 has a 2.6.38-6-generic kernel which should have transparent hugepages enabled.  But it doesn't seem to be.  According to [http://lwn.net/Articles/423592/]("http://lwn.net/Articles/423592/") I should see a /sys/kernel/mm/transparent_hugepage subdirectory, but there is no such subdirectory.  Is the transparent huge pages enabled by default or do I need to do something to activate it?

---

### Post by mörgæs on 2011-03-12
Better to search in this forum:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by s.fox on 2011-03-14
Thread moved to  [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

### Post by bhaskar on 2011-03-25
It looks like the generic kernel is not compiled with transparent hugepages.

$ grep TRANSPARENT_HUGEPAGE /boot/config-2.6.38-7-generic 
# CONFIG_TRANSPARENT_HUGEPAGE is not set
$ 

Bummer.  Is the server kernel built with this option enabled?  Thanks.

-- Bhaskar

---

### Post by bhaskar on 2011-03-25
No, the server is also not compiled with the option turned on.

-- Bhaskar

---

