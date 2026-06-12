---
title: "Kill SFTP connections"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by Zilioum on 2010-02-20
I want to use a cron job to backup my files to my server. Now when I run the script manually, I get an error when backing up (something and sftp file being used or so). I only get this when I'm simultaneously connected to my server with sftp. So to be sure that this doesnt happen when I wont be there anymore to look at the log, I would like to know if there is a command to kill all sftp connections. I would put this command in the backup scrip cron uses.

---

### Post by davec64 on 2010-02-20
I've not used it but have a look at TCPKILL, it may do what you require! :)

---

### Post by Zilioum on 2010-02-20
Looks nice, but will scp still work?

---

### Post by davec64 on 2010-02-21
Not sure, try at the command line and see. :)

---

### Post by Zilioum on 2010-02-21
Doesnt seem to work at all, when I use ```
sudo tcpkill -i eth0 host 192.168.0.4
``` nothing happens. I get ```
tcpkill: listening on eth0 [host 192.168.0.4]

``` but nothing appears. On my notebook (192.168.0.4) I can still do everyting I want (especially open SFTP connections). Is this a problem with tcpkill or do I have to find another solution for my problem?

---

