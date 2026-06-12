---
title: "Printing to a Vista shared printer?"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by hardyn on 2009-04-04
Summary:

Vista home basic 32 host with shared HP PSC.

Ubuntu 8.10 samba client

Problem:

I can share files between the two machines just fine (a little slow 1.5mb/sec, but that is another story) but cannot print.

I am able to attach to the shared printer, even to the point where the printer clunks around a little bit.  64kb into the 7Mb (which seems large) test page file, the windows machine throws an error, and that is about it... about as far as it get.

any help would be appreciated.

---

### Post by superprash2003 on 2009-04-05
could you post the exact error which the windows machine gives..

---

### Post by hardyn on 2009-04-05
from the spooler, it simply said "printing-error" and i don't know how to get a more verbose message out of windows.

attached is the spooler menu, it really looks like the spooler is expecting more, and waiting.  These jobs are almost impossible to kill as well, they will report being canceled until next reboot.

I have printed in the reverse direction vista->ubuntu before; but this is not an option this time.  the desktop/server/print server will be primarily running Vista; but i do have a Jaunty beta partition on the machine.

---

### Post by Rinias on 2009-04-07
If you check your printer status in cups (or the Ubuntu print thingy) does that give an error ?

Just out of curiosity, how is your printer set up in Ubuntu ? Did you use a Samba-shared configuration or activate the Unix spooling for Windows and do an lpr/lpd connection ? I've tried both, personally, and never got anywhere.  I always get an NT_STATUS_ACCESS_DENIED error with one setup and some other connection error if I try lpr/lpd. It's rather frustrating.

Rinias

PS : On a side note, why can Debian (stable) access shares directly through nautilus and Ubuntu just can't ?

---

### Post by hardyn on 2009-04-07
with enough updates ubuntu can.... it was broken for a while but seems to be okay now.

no, it says its a valid connection.
samba-shared.
i could try the latter.

---

