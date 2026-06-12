---
title: "Galleon not running"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by jasbur on 2007-10-12
I've also posted this in the Galleon forums.

Ok, I just downloaded 2.5.1 on my Ubuntu box. If I try to run the server the old way (using run.sh) I get an error:

.: 14: Can't open /etc/rc.d/init.d/functions

If I try to run a "sudo make install" from the root application directory I get:

chkconfig --add galleon
make: chkconfig: Command not found
make: *** [install] Error 127

Any ideas? I need to play my new Radiohead album :)

---

### Post by Kensey on 2007-10-20
I fixed this by editing run.sh to just say:

/usr/share/galleon/bin/galleon console

and by commenting out the "functions" line at the top of /usr/share/galleon/bin/galleon.

---

