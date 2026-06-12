---
title: "basic LIRC help: why doesn't it recognize multiple remotes?"
date: 2010-10-24
forum: Mythbuntu
---

### Post by tedder on 2010-10-24
I had the following /etc/lirc/lircd.conf:
include "/usr/share/lirc/remotes/streamzap/lircd.conf.streamzap"

I added two more remotes to it:
include "/usr/share/lirc/remotes/onkyo/RC-651M"
include "/usr/share/lirc/remotes/samsung/BN59-00599A"


They are in the same format: "begin remote" section with "name", "bits", etc. In fact, they are from [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/), it isn't like I created them or anything.

I've restarted lircd, and yet I don't see the other remotes available:
# irsend LIST "" ""
irsend: Streamzap_PC_Remote

What am I doing wrong? I tried concatenating the remote configs and replacing lircd.conf with those, no change- it still only sees the streamzap remote, not the other two. (in other words, I did this instead of the 'include' lines above).

I can post the remote configs, but I suspect I'm missing some important step.

---

### Post by xinix on 2010-10-24
this might help:

[http://www.mythtv.org/wiki/MultiLIRC](http://www.mythtv.org/wiki/MultiLIRC)

---

### Post by tedder on 2010-10-24
> **xinix said:**
> this might help:

[http://www.mythtv.org/wiki/MultiLIRC](http://www.mythtv.org/wiki/MultiLIRC)

The following indicates that patching and such shouldn't be necessary:
[http://www.commandir.com/content/view/40/61/](http://www.commandir.com/content/view/40/61/)

I'm not confident that the /MultiLIRC is any more than an outdated method used by one person. It seems only necessary if there are conflicting commands or multiple receivers. Further, the [LIRC format](http://winlirc.sourceforge.net/technicaldetails.html) says "The files may contain an unlimited number of ... remote blocks."

It's worth noting I can shut down lircd and irsend still lists one remote. Does it read /etc/lirc/lircd.conf directly? That makes me think irsend isn't seeing my changes.

---

### Post by tedder on 2010-10-24
Hmm. I trolled around and realized lircd was still running so it was ignoring my changes. I killed the existing, and now LIST shows all of my remotes. Woot!

---

