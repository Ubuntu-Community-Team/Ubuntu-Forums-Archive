---
title: "Cannot FTP"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2008-12-14
In my Ubuntu I cannot FTP my Yahoo webserver. I cannot type in the FTP URL into Nautilus or Konqueror. I can only connect running [Beyond Compare]("http://bestwikiever.wikidot.com/Beyond_Compare") from XP in a VM, I cannot use BC from Wine to connect. I can also access it from Firefox, but that's only useful for downloading files.

I have created and FTP Test URL:
[ftp://test@operation420.net@ftp.p2.webhosting.yahoo.com/](ftp://test@operation420.net@ftp.p2.webhosting.yahoo.com/) (password "test")

If someone could figure out how I can access it from Ubuntu that would be appreciated.

I can access my Xbox's FTP from Nautilus....

[http://ubuntuforums.org/showthread.php?t=1025860](http://ubuntuforums.org/showthread.php?t=1025860)



EDIT: It works for [Beyond Compare]("http://ubuntuforums.org/showthread.php?t=726554") but not Nautilus or Konqueror so I assume there is something wrong with them...

---

### Post by nixscripter on 2008-12-14
Try the ftp command in Terminal: ```
 ftp server.wherever.com
```

It will ask for username and password. Then use **ls**, **get** and **put** commands, along with several others (like **passive** and file modes) in the manual pages:

[http://linux.about.com/od/commands/l/blcmdl1_ftp.htm](http://linux.about.com/od/commands/l/blcmdl1_ftp.htm)

Hope this helps.

---

### Post by RealG187 on 2008-12-14
> xg@MIKED5:~$ ftp [ftp://test@operation420.net@ftp.p2.webhosting.yahoo.com/](ftp://test@operation420.net@ftp.p2.webhosting.yahoo.com/)
ftp: [ftp://test@operation420.net@ftp.p2.webhosting.yahoo.com/:](ftp://test@operation420.net@ftp.p2.webhosting.yahoo.com/:) Unknown host


I get that

---

### Post by Ayuthia on 2008-12-14
> **RealG187 said:**
> I get that

Try doing this from the Terminal:
```
ftp ftp.p2.webhosting.yahoo.com
```
When it asks you for the username, use:
```
test@operation420.net
```
Then use test as the password.

---

