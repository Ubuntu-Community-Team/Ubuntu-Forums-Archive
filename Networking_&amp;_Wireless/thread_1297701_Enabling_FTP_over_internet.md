---
title: "Enabling FTP over internet"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by bivab on 2009-10-22
Hello, please bear with me, as I'm fairly new to the world of networking. I recently set up a ubuntu box that acts as a file server, with both ftp and samba running. I've been able to successfully access it from another computer through FTP when connected to the same local network. This box connects wirelessly to a router, which is connected to cable internet.

I am wondering how to configure this setup so that I can access FTP from anywhere, not just within the local network. I vaguely know that I'm supposed to forward ports in my router, so I forwarded port 21. Not sure where to go from here, though...

---

### Post by SoftwareExplorer on 2009-10-22
Do just not know the address to ask for when you want to get to your computer over the internet? Because if so, you can find out at whatismyip.org from the file server.

---

### Post by bivab on 2009-10-22
Hey, SoftwareExplorer, thanks for the help. In any case, I think I figured it out (before you posted!) I had ownership problems with the default ftp directories. Essentially, the same problem listed here:
[http://linux.derkeiler.com/Newsgroups/alt.os.linux/2004-03/2100.html](http://linux.derkeiler.com/Newsgroups/alt.os.linux/2004-03/2100.html)

Anyway, I think everything seems to be working now. I just have to test it from afar.

---

### Post by SoftwareExplorer on 2009-10-22
> **bivab said:**
> Hey, SoftwareExplorer, thanks for the help. In any case, I think I figured it out (before you posted!) I had ownership problems with the default ftp directories. Essentially, the same problem listed here:
[http://linux.derkeiler.com/Newsgroups/alt.os.linux/2004-03/2100.html](http://linux.derkeiler.com/Newsgroups/alt.os.linux/2004-03/2100.html)

Anyway, I think everything seems to be working now. I just have to test it from afar.

Oh good. Hope it works :)

---

