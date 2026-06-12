---
title: "Unsure how to upload to an ftp server"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by Kurir on 2012-08-08
Hi guys,

I have set up a vsftpd server to be login only, and I am struggling to find a way to upload to the server without going into the command line, as most people who will be using it wont have access to command line.

Any ideas?

On a side note, I am having a weird issue where if i set anonymous on and give it an anon root path, it forces me to log in(ok, its how I want it in the end) and takes you to the root path specified. 

If I remove the root path line and just leave in the local_root line, it lets me go straight in without a login and to the default path.

And if I turn off anon access, it doesnt let me access the server at all.

All this is tested from a browser. Any ideas as to why this happens or how I can set this up properly is appreciated.

Kurir.

P.S. This probably isnt in the right section, and apologies for that.

---

### Post by hakermania on 2012-08-08
Not sure for the logins etc, but you should try Filezilla for uploading to your ftp server, if you don't like the command line...

---

### Post by albandy on 2012-08-08
> **Kurir said:**
> Hi guys,

I have set up a vsftpd server to be login only, and I am struggling to find a way to upload to the server without going into the command line, as most people who will be using it wont have access to command line.

Any ideas?


nautilus (the file browser) have the ability to connect to ftp servers:

open any folder, and in the window menu select "File" --> "Connect to Server"

---

### Post by Kurir on 2012-08-08
Thanks for the suggestions guys.

I was hoping for a browser based way if possible?

The people who will be using it often wont have a computer in front of them and would have to upload/download things while onsite, say on their phones or such.

Kurir

---

### Post by albandy on 2012-08-09
> **Kurir said:**
> Thanks for the suggestions guys.

I was hoping for a browser based way if possible?

The people who will be using it often wont have a computer in front of them and would have to upload/download things while onsite, say on their phones or such.

Kurir


I think that ftp is not a solution for you. Mabye a php script to upload and download files is a better solution in this case.

---

### Post by Kurir on 2012-08-09
Thanks for the suggestion, didnt think of that. I think I can work with that.

---

