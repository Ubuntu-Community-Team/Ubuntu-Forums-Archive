---
title: "Samba Sharing"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by lunarben on 2010-02-05
Hey All!

I have a server at home running Ubuntu sharing out some folders with Samba. I would like to be able to access all of these shares from my workplace. I can get in using Putty SSH but i would like to be able to browse my files as if they were on the windows machine.

I don't know if I am missing something? I have tried mapping the remote machine to network drive however windows keeps prompting me for a password when i know the user and password exists and is correct. Im not really sure, I dont think this is the right way of going about it?

Any Suggestions?

Thanks,

---

### Post by alienprdkt on 2010-02-05
Best way I think to shares files at your work place would be to setup an ftp server I use vsftp, set up with virtual users. Then with an ftp client like filezilla you can access your ftp directory and either download or upload to that directory.

Links that may help you out:

[URL="http://www.howtoforge.com/vsftpd_mysql_debian_etch"]to to setup vsftpd with virtual users in Ubuntu
[/URL]

[http://filezilla-project.org/]("http://filezilla-project.org/")

Hope this helps.

---

### Post by lunarben on 2010-02-06
I didn't even think of that..

Thanks!

---

