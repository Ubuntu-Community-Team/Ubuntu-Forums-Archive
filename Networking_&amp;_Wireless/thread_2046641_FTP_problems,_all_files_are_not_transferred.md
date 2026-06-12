---
title: "FTP problems, all files are not transferred"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by danba185 on 2012-08-23
Hi, I have created a FTP server according this tutorial:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Generally is seems to work fine when uploading and the downloading files if there is only one user active. But when many users downloads the same folder simultaneously, some of the files is not transferred to all of them. What do you think, is it a problem in the FTP server or the FTP client? Right now we are using Filezilla as the client. I have attached the proftpd.conf file

---

### Post by Kirk Schnable on 2012-08-23
Your FTP server is configured to do some logging, as indicated here in your config:

```
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log
```

It may be useful to attach these logs.  The Transfer log will probably be useful in determining why file transfers aren't finishing.

Is there any particular error in the text console of FileZilla when the transfer fails?

Does this problem occur all the time, or only when the FTP server is under heavy load (as you seem to indicate...)

Kirk

---

### Post by danba185 on 2012-08-25
Thank you for the reply, I looked in the log files as you recommended and realised that the problem was the limit of concurrent instances,  I simply increased the maximum number of instances and it seems to be working nice now. 

/Dan

---

