---
title: "minidlna database empty after a reboot"
date: 2015-02-02
forum: Multimedia Software
---

### Post by anchnk on 2015-02-02
Hello, 

I am running **ubuntu 14.10 TLS**, I've downloaded minidlna (which is know as ReadyMedia) from sourceforge official repository (version 1.1.4).

Built the program from sources and install it at default location (which is **/usr/local/sbin/minidlnad**).

The problem I am facing is that each time I reboot the laptop, the database seems empty. 
If i am checking the log nothing wrong pops-up however no files are shown either on the TV either on the web interface localhost:8201 (i've choosed that port in minidlna config)

If i am running **/etc/init.d/minidlna restart** everything works fine again.

I am not sure how does that service gets started in that flavor of ubuntu so any hint appreciated,
I have modified the daemon script in /etc/init.d/minidlna to match the directories.

Here's an extract of my log file:

```
[2015/02/02 18:55:32] minidlna.c:1026: warn: Starting MiniDLNA version 1.1.4.
[2015/02/02 18:55:32] minidlna.c:355: warn: Creating new database at /var/cache/minidlna/files.db
[2015/02/02 18:55:32] minidlna.c:1065: warn: HTTP listening on port 8201
[2015/02/02 18:55:32] playlist.c:125: warn: Parsing playlists...
[2015/02/02 18:55:32] playlist.c:259: warn: Finished parsing playlists.
```

---

