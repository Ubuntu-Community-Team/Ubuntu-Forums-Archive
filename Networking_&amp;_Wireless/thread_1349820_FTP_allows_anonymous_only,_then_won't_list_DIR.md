---
title: "FTP allows anonymous only, then won't list DIR"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by rpaskudniak on 2009-12-08
Greetings, family.

Preface: Both boxes mentioned in this post are behind a router.  Hence, their IP addresses are the predictable 192.168.2.*n*, as assigned by the router and shown by running ifconfig. (This is as opposed to the IP address of the router, displayed by [[COLOR="Blue"]whatismyip.com[/COLOR]]("http://www.whatismyip.com/").)

I have edited /etc/hosts on his machine to include my machine, chief, with that touter-assigned IP address.  I can enter the command
[FONT="Courier New"]$ ftp chief[/FONT]
and get the ftp-login prompt.  (I have the vsftp daemon running so that my son's Ubuntu box could access files on my box. He has not yet returned the compliment. :p )

FWIW, chief is plugged into the router, all others connect wirelessly.

Now the problem (with multiple parts, as is my wont :rolleyes: ):
[LIST]
[*]When I get the ftp-login prompt and enter my userid, it complains that only anonymous ftp is permitted.
[*]When I login as anonymous (and just press [ENTER] at the password prompt), it will tell me I am in directory / but will not give me a directory listing. At the dir command, it tells me "Here comes the listing" and then... nothing. (Well, the next [FONT="Courier New"]ftp>[/FONT] prompt.)
[/LIST]
I have attached my vsftpt.conf file (renamed with .txt suffix for this forum' requirement), which is untouched since I first looked at it.  I may simply need someone to tell me what setting to uncomment; I must have missed the setting that enables ordinary folks to FTP into the box.

BTW, I also tried sftp to chief but that gets [FONT="Courier New"]Connection refused[/FONT] (error 22) so I may need to be running a different daemon to allow sftp to work.  But I'll jump off that bridge when I come to it.

Thanks much for the correct pointer and, better, if you show me where I could have found the answer myself.  You know, *Teach a man to fish and he'll eat forever, wearing a funny hat*.

---

### Post by JCSalomon on 2009-12-09
See [this thread (vsftpd won't restart)]("http://ubuntuforums.org/showthread.php?t=93503").

Services like vsftpd are controlled by a wrapper script in /etc/init.d, so try ```
sudo /etc/init.d/vsftpd restart
``` or, if that fails, ```
/etc/init.d/vsftpd stop
/etc/init.d/vsftpd start
``` (sudo as needed).

---

### Post by rpaskudniak on 2009-12-09
Thank you, JC. :p

I have done the restart but this was only after enabling ```
local_enable=YES
```in /etc/vsftpd.conf. Now, with the vsftpd running on both hosts, ftp works the way I come to expect.

Of course, local ftp now works as well, but why would I want to do that?  As a solution to my remote-login problems, this was highly counter-intuitive.  BUt it solved the problem.

Now, on to NFS...

---

