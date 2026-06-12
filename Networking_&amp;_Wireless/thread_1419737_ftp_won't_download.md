---
title: "ftp won't download"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by nelsonhogg on 2010-03-02
This is a longstanding issue with my setup that remains after several upgrades of ubuntu. I can't download via ftp using any of a number of clients (fireftp, ftp from terminal, gftp, filezilla). I can connect to the directory on the server but files there won't download! Very frustrating and I am finally seeking help from you wizards. Anything I can check and report back to you? Thanks! Nelson

P.S. Downloading via http works just fine.

---

### Post by MaindotC on 2010-03-02
Can you describe what happens when you connect to the ftp server and try downloading a file?  Are you using the "get" command?  Is this a permissions issue?

---

### Post by nelsonhogg on 2010-03-02
I don't believe it is a permissions issue. Using ftp from a terminal I can navigate down to the appropriate directory but "dir" or "ls" will not show me the files available. Using a graphical client (e.g. fireftp or gftp) the files are revealed but, in general, nothing happens when I try to transfer them (except I will be notified if one with that name already exists on my machine). Interesting, though, very small files (about 10KB or less) will transfer.

---

### Post by MaindotC on 2010-03-02
What troubleshooting have you done?  Where's your documentation of each step you've taken to try and resolve the issue so I know where to start and don't repeat a procedure?  In my experience "ls" will not show what is in the directory due to permissinos.

---

