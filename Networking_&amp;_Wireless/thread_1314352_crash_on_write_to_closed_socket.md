---
title: "crash on write to closed socket"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by BipolarJunction on 2009-11-04
For some reason, my program crashes when I call write() on a closed socket.  It doesn't spit out an error or anything, it just terminates my program.

Here's the code around where it dies:

char* nl = "\n";
printf("Sending NL\n");
write(fd, nl, strlen(nl));
printf("Sent NL\n");

It manages to print "Sending NL", but terminates before printing "Sent NL".  Any ideas?

---

### Post by Elfy on 2009-11-05
closed - duplicate [http://ubuntuforums.org/showthread.php?t=1315779](http://ubuntuforums.org/showthread.php?t=1315779)

---

