---
title: "Password protected directory networkdrive"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by TheBosBird on 2011-12-09
I have a CHD3NET harddisk in my network. It works perfectly on a Windows machine and on Ubuntu. I have mounted it with ```
gvfs-mount smb://drive-name/path
```. The only thing that is not working is when I put a password on a directory. This because I want to use the harddisk as backup for my userfiles. 
 
When I go to the password protected directory from in Windows I get a little window asking me for a password. The username is greyed out so I can't change this one (drive-name\Gast). When I give the password I can see de files of the directory. No problems. 
 
When I try this from Ubuntu, the little window that pops up, asks for username and password. I tried for the username: Gast, Guest, gast, guest, nothing, admin but nothing works. When I remove the protection there is no problem. The only problem that remains is it not secure!
 
So my question is, what can I fill in for the Username? Or is there another solution?
 
Harddisk CHD3NET is Grab'nGo Conceptronics. Latest firmware 0.14. 
 
Anybody?

---

### Post by TheBosBird on 2011-12-18
My solution for the problem: backup files with lftp. I enabled the ftp server on the networkdrive for this. So now I can backup my files to a ftp-server (on the networkdrive). 
 
```
 
lftp -u 'user,password' networkdrive-IP -e 'mirror --no-umask -p -n -R source-directory target-directory; exit'

```
 
Finaly make a cronjob for it.

---

