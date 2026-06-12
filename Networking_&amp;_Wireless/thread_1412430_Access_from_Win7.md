---
title: "Access from Win7"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by .salo on 2010-02-21
Hi all,

I not sure I have unique issue, but I can't found a solution, so please help me.

I have two computers in my local network one with Ubentu Karmic 64 and one with Win7 64. The problem is in file sharing. I would like to be able to have access from one computers to another in both ways. But now I have only access from ubuntu to windows shares. On win machine I'm able to view ubuntu shared folders and printers but not able to browse them (or use printers from windows). I tried to change  samba configuration, but my knowledge is to poor to solve this problem ((

Thanks in advance.

---

### Post by abdusamed on 2010-02-21
yea.. i have a same problem.. trying to connect to a adhoc network created by a vista machine. The whole thing freezes on 'obtaining dhcp [something like that] address'  I can't tell you what the error is cause I'm using wins7 right now but it freezes on obtaining dchp somehting IP value

---

### Post by .salo on 2010-02-21
maybe it is windows related issue?

---

### Post by northd_tech on 2010-02-21
There is a thing called Samba that allows Linux to interact with the Windows Networking "universe."  From what I've read, Win7 is much more difficult to connect to than WinNT, XP, Vista were.

Here is a quick overview of Samba:

[http://learn.clemsonlinux.org/wiki/Samba_client](http://learn.clemsonlinux.org/wiki/Samba_client)

The Wiki isn't too terrible for this one:

[http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29)

Here is the main Samba page with tons of stuff:

[http://www.samba.org/](http://www.samba.org/)

Searching for "samba" threads here will probably find a lot of threads too.

---

### Post by .salo on 2010-02-22
> **northd_tech said:**
> There is a thing called Samba that allows Linux to interact with the Windows Networking "universe."  From what I've read, Win7 is much more difficult to connect to than WinNT, XP, Vista were.

Here is a quick overview of Samba:

[http://learn.clemsonlinux.org/wiki/Samba_client](http://learn.clemsonlinux.org/wiki/Samba_client)

The Wiki isn't too terrible for this one:

[http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29)

Here is the main Samba page with tons of stuff:

[http://www.samba.org/](http://www.samba.org/)

Searching for "samba" threads here will probably find a lot of threads too.

As I said I already tried to change samba configuration, My english isn't so gud to configure client by myself. Thanks for help...

---

### Post by Hydrohs on 2010-02-22
How did you get Ubuntu to see Windows shares? I got the opposite to work just fine but I have yet to be able to get Ubuntu to see Windows.

---

### Post by sarlaccpit on 2010-02-22
> **.salo said:**
> Hi all,
I tried to change  samba configuration, but my knowledge is to poor to solve this problem 

Sounds like a permissions issue in samba. 
First i'd check the file you wish to share. If you look at the file you wish to share and do an ls -al it should show you what permissions are set.

Then i'd check the smb.conf file to ensure your windows user has permissions to access it.

---

### Post by Jive Turkey on 2010-02-22
The linux file permissions on the shared folders are very important, samba can't (shouldn't) share them if the permissions are too restrictive.  After that (if not resolved) you should look at your share definitions in smb.conf (they are usually at the bottom of the file.

A rough example of one share definition that should work:
```
[sample-share]
        comment = Shared files on computer X
	path = /home/jiveturkey/sampleshare
	valid users = jiveturkey
	read only = No
        browseable = Yes

```
You could also remove the "valid users" directive and put "guest ok = Yes" if you want everyone to be able to access it, and I do mean everyone.

---

### Post by Jive Turkey on 2010-02-22
I should add that Windows 7 by default has an added feature you must drill down to find where it specifies something about using 128 bit encryption instead of 48 or 56 bit.  IME the samba clients work only with the lower encryption setting.  I also always disable the "Windows Homegroup" crap and set it to share with username / password instead.  I wouldn't hold my breath waiting for the samba developers to build compatibility for this stuff either, fix it on the windows side of things for now.

---

### Post by CaptainCalvin1987 on 2010-02-22
So i have lowered the encrytion and disabled the homegroup. my home network page looks like this.[IMG]http://farm5.static.flickr.com/4069/4379868521_0c0734f604_o.png[/IMG]

"Calvin-Server" being my Ubuntu 9.10 desktop and the "Calvin-Quad" being my home windows 7 machine. When i log into that "server" with my ubuntu username and password it just says invalid credentials. you see in the image that it has domain:CALVIN-QUAD, would that be the problem?

Thanks

---

