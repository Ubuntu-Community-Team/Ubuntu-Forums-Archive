---
title: "Cannot connect to own FTP server via any browser"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by prshah on 2009-11-21
Hello all,

I am using VSFTPD on my home server to allow users to connect and access/manipulate their files remotely.

I am able to connect to the VSFTPD server using the command line and using nautilus's [ftp://.](ftp://.).. I can access and manipulate my files correctly.

However, when I try to connect through a browser (testing Firefox and Windows IE), I am unable to connect. I get the prompt for username and password, which I then enter correctly, and I get the response (in firefox) "Error 550: Permission Denied". In IE, I get "200 switching to ASCII mode   550 Permission Denied"

Other ftp clients work well.

Any suggestions on what I need to do to get FTP access via the browser?

Tech level: Intermediate, comfortable with command line, vi, etc.

Thanks in advance...

---

### Post by sanderj on 2009-11-21
To check, I installed vsftpd. Result:

I can use the command line ftp to access localhost, however only anonymously with account 'ftp'
I can access vsftpd using firefox via [ftp://localhost/](ftp://localhost/)

As you're required to fill out a username/password, I wonder whether you changed the default config?
Can't you get in anonymously?
```


sander@quirinius:~$ ftp localhost
Connected to localhost.
220 (vsFTPd 2.2.0)
Name (localhost:sander): ftp
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
226 Directory send OK.
ftp> bye
221 Goodbye.
sander@quirinius:~$ 

```

---

