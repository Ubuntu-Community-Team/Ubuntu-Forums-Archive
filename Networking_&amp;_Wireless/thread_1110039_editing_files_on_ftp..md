---
title: "editing files on ftp."
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by redders on 2009-03-29
Hi everyone. 

I can connect to my website via ftp using Pure-FTPd. I was wondering if it was possible using this, or another ftp daemon, to edit php/text files directly on the ftp site. 

I could download a file, edit it, then upload it, but when I am making a lot of small changes I want to check, I'd rather not have to do this.

Thanks in advance,

Redders.

---

### Post by squaregoldfish on 2009-03-29
The gFTP program allows you to specify your favourite editor. You can then right-click on a file, select Edit, and it will download and open the file. Once you close, the editor, gFTP sends the updated file back to the server.

This is an option I know of - doubtless some text editors can do this directly, and there are probably other options too.

Steve.

---

### Post by redders on 2009-03-31
Thanks steve, I tried this, it worked fairly well.

What I found preferable was to connect to the FTP site by going to Places>Connect to Server

This mounted my ftp site as a drive, so I could do whatever I liked with the files on it. (Open them with an editor!)

Works nice and neatly, as when I save, it uploads it to the ftp site.

---

### Post by squaregoldfish on 2009-04-01
That's a much better solution. I haven't explored the Places stuff much, but it sounds pretty much spot on.

Steve.

---

