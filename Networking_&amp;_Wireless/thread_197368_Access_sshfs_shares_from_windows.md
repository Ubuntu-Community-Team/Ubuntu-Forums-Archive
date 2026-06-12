---
title: "Access sshfs shares from windows?"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by temcat on 2006-06-15
Hi all, 

I've read about sshfs and wonder if it's possible to access sshfs shares on Linux from Windows as easy as Samba ones, when Samba does work? Like going to Network Neighbourhood or clicking on network drive letter... I've googled, but haven't found a definite answer to that question. I know however that Microsoft has Services for Unix using which you can install openssl and openssh on Windows.

Any hints?

---

### Post by Akita on 2006-06-15
I use WinSCP, a free Windows Explorer-like app that does scp/sftp. 

[http://winscp.net](http://winscp.net)

There's also a product ($$$) that integrates with the shell and does drive mappings using various protocols but i don't remember the name off hand. Something like WebDrive or somesuch.

---

### Post by temcat on 2006-06-15
[QUOTE=Akita]I use WinSCP, a free Windows Explorer-like app that does scp/sftp. 

[http://winscp.net](http://winscp.net)

There's also a product ($$$) that integrates with the shell and does drive mappings using various protocols but i don't remember the name off hand. Something like WebDrive or somesuch.[/QUOTE]

Thanks, however, this is not quite what I want. Anyway, I've just answered my own question: sshfs is possible only from Linux to Windows, since sshfs must be installed on local machine, not remote one. A pity, because Samba on Dapper leaves much to be desired :-(

---

### Post by namit on 2007-07-10
I would also like to know if there is some way of mounting ssh shares on windows machines.

---

### Post by geirha on 2007-07-10
If there existed a way to use sshfs in windows, it would most likely be implemented in cygwin, but a quick google search on this suggests that this is very complicated, and you most likely won't see this in any near future.

[http://www.cygwin.com/ml/cygwin/2006-02/msg00910.html](http://www.cygwin.com/ml/cygwin/2006-02/msg00910.html)
[http://cygwin.com/ml/cygwin/2006-10/msg01074.html](http://cygwin.com/ml/cygwin/2006-10/msg01074.html)

---

### Post by [woodstock] on 2007-10-23
Searching for the same issue, I stumbled upon [http://www.sftpdrive.com/index.php]("http://www.sftpdrive.com/index.php"), which supposedly ca mount ssh shares. It is commercial software and I haven't tried it yet.

---

### Post by mcrae on 2007-10-23
> **temcat said:**
> .... A pity, because Samba on Dapper leaves much to be desired :-(

may be you should give Samba another try...for me at least it works perfect on Dapper - I have a Samba share which I can eesily mount on WinXP, Mac OSX, Linux...it simply appears in the network
as far as I understood you need this, and not just transfering the files with smth like WinSCP...

---

### Post by mblythe on 2008-01-22
I don't know if anyone is still watching this thread, but I've found a solution that looks like it should work for me.

Novell developed some software called NetDrive that can map a WebDAV, FTP, SFTP, etc. share to a windows drive letter.  It is now abandonware, so it's no longer maintained (and not available on the Novell website), but it's free to use.  See here: [http://www.novell.com/coolsolutions/qna/999.html](http://www.novell.com/coolsolutions/qna/999.html) I found quite a few available to download by searching for "netdrive.exe"  I actually downloaded a few and compared their md5sums to make sure that I was getting a common (and hopefully safe) version.

Hope this helps!

---

### Post by dlj on 2008-01-30
Thank you, netdrive works !
(maybe not with vista, though). Ftpdrive also exists.

I wonder if any of them is compiled with the HPN patch (high performance network patch).

---

### Post by uffela on 2008-03-09
> **temcat said:**
> Hi all, 

I've read about sshfs and wonder if it's possible to access sshfs shares on Linux from Windows as easy as Samba ones, when Samba does work? Like going to Network Neighbourhood or clicking on network drive letter... I've googled, but haven't found a definite answer to that question. I know however that Microsoft has Services for Unix using which you can install openssl and openssh on Windows.

Any hints?

Hi, I just found this great article [http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/]("http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/") - it gave me some ideas for my home network.

Hope it helps

///Barbapappa

---

