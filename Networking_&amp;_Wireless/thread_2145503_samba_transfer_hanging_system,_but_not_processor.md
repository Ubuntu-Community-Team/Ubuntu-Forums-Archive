---
title: "samba transfer hanging system, but not processor"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by Anivair on 2013-05-15
Here's a strange problem that I'm having for the first time today.  Setup: 

Office network, static IP (100.100.100.xxx)
Ubuntu 10.04, hasn't been patched in a while, but no changes have been made either
Windows desktop systems using samba (though the problem persists when I use a 12.04 linux machine accessing the samba share as well. 
Problem seems to persist (though is less obvious) when using ssh.

I have a share (which we will call /data/legal for ease) and in it is a file.xls (221.2 KB).  I get into the share and try to open this file and the process hangs (ie: I get a live libreoffice splash screen and then it goes grey for a very long time).  On the server itself the desktop also hangs and running processes greyscreen.  So far, that looks normal, though irritating. 

If I'm running a top command when this happens, I see nothing.  The processor keeps on trucking as normal.  No stress. 
If I run a free command I have plenty of ran free, plus all my swap space.  No stress there. 
If I run sudo iptraf I see some traffic move to my ip and then it halts for a long while.  Then it progresses a bit more (grey screen) and some more traffic moves and then it halts.  More progress (dark grey) and I move a bit more data.  Then a long time passes, finally the file opens (blank, I might add) and the rest of the data moves. 

I COULD just be looking at a corrupt file, but I have a hard time believing that the file is truly corrupt.  it opens and I see tons of blank tabs.  rarely does a file corrupt JUST in the cell data.  Thoughts?

---

### Post by Anivair on 2013-05-15
I forgot:  
smbd -V 3.4.7
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009

Also, I just tried to copy the file to my desktop and it bombed out.  maybe it's just a crap file?

---

