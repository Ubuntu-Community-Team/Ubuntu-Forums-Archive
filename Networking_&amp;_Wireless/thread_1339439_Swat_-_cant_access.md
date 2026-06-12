---
title: "Swat - cant access"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by Sniffer on 2009-11-27
Hi fellows,

Have installed swat in my Ubuntu 9.10 Server (Text mode) as it says here:

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

Everything seems perfect but when i try to access him with [Http://localhost:901](Http://localhost:901)

It ask me the username and password, i use the user you are forced to create in ubuntu installation...but no access, it keeps me asking the password...

Thanks for the help in advance.

---

### Post by imashley on 2009-11-27
I have the exact same problem with the same setup.

---

### Post by Sock puppet on 2009-11-27
> **Sniffer said:**
> Hi fellows,

Have installed swat in my Ubuntu 9.10 Server (Text mode) as it says here:

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

Everything seems perfect but when i try to access him with [Http://localhost:901](Http://localhost:901)

It ask me the username and password, i use the user you are forced to create in ubuntu installation...but no access, it keeps me asking the password...

Thanks for the help in advance.

Are you using the same machine ubuntu sever is on? If not the you need "http://[the ip of the server]:901"

---

### Post by Sniffer on 2009-11-28
> **Sock puppet said:**
> Are you using the same machine ubuntu sever is on? If not the you need "http://[the ip of the server]:901"

First of all thanks for your help, but you make me laugh....:D

My server is in text mode...so i could not use it to browse swat, only if i want text browser...nahhh don't think so.

I have tried all of the ways..at least that i Know

[http://ip:901](http://ip:901)
[http://nameofubuntuserver:901](http://nameofubuntuserver:901)

It always ask me of the password and username, i put it and always get error 401 invalid login...when it's correct, and yes the user i use its member of admin group.

In conclusion AND I LOVE GNU, and this maybe offtopic...but ubuntu in many ways, in company ways, professional ways it's BROKE.

1 - YOU TRY OFFLINE FILES (Windows 7) TO Ubuntu (Dont Work), you active oplocks and DONT WORK.
2 - YOU TRY SWAT (because it's not only me that work in my company) following the "Official" tut step by step..EXACTLY and DON'T WORK.

And the forum It's not what it was WAY BACK IN 2004, lack of support, more complex threads get no reply's...and so on....

Not that i have the time to help as well (my fault) BUT I MISS WARTY fellows.

---

### Post by Iowan on 2009-11-28
A couple of months ago, I decided that it was finally time to upgrade my Breezy server. Rather than upgrade to the latest bleeding edge, I opted to go for relatively stable LTS - so installed Hardy. Samba started evolving with this version, but it's had awhile to stabilize. Especially for a server, I think I'll continue the LTS - LTS upgrade path.  
There are a few threads mentioning the login loop. I haven't seen (or I misplaced) the fix-all solution - or I'd be happy to link you to it.
For what it's worth (and strictly my opinion), the six month development cycle is pushing out versions that aren't quite ready. Hardy and Intrepid had problems with Network Manager. Jaunty seems more stable than I'd expect (laptop has had sound issues). Karmic may be great once several of the bugs are squashed.

---

### Post by Sock puppet on 2009-11-28
> **Sniffer said:**
> First of all thanks for your help, but you make me laugh....:D

My server is in text mode...so i could not use it to browse swat, only if i want text browser...nahhh don't think so.

I have tried all of the ways..at least that i Know

[http://ip:901](http://ip:901)
[http://nameofubuntuserver:901](http://nameofubuntuserver:901)

It always ask me of the password and username, i put it and always get error 401 invalid login...when it's correct, and yes the user i use its member of admin group.



Oh come on. You're not hardcore if your not using a text browser :). Did you try SSHing in and using
```
smbpasswd -a <username> 
```

to make sure your username and password are set right in Samba

---

### Post by Sock puppet on 2009-11-28
Another thought. You might also want to try [eBox]("http://www.ebox-platform.com/"). It sits on top of Ubuntu's last LTS release. Much more advanced than swat but you would have to reinstall the os

---

### Post by Sniffer on 2009-11-28
> **Sock puppet said:**
> Oh come on. You're not hardcore if your not using a text browser :). Did you try SSHing in and using
```
smbpasswd -a <username> 
```

to make sure your username and password are set right in Samba

My samba it's using Winbind, so authenticate against the M$AD, even so i have 150% sure i'm using the right password.

Thanks for the ebox idea..i tought as well on webmin..tough swat it's only samba oriented and would feet my needs if it works.:D

PS: even as a hardcore i thank everyday for the GUI developers, god bless you. I remember the early days of red hat 6.0 when to install a app we need to satisfy all the dependecies...MANUALLY.

Not fun my friend, we all have a personal life..and like to see the sun as well.

---

### Post by Sniffer on 2009-11-28
> **Iowan said:**
> A couple of months ago, I decided that it was finally time to upgrade my Breezy server. Rather than upgrade to the latest bleeding edge, I opted to go for relatively stable LTS - so installed Hardy. Samba started evolving with this version, but it's had awhile to stabilize. Especially for a server, I think I'll continue the LTS - LTS upgrade path.  
There are a few threads mentioning the login loop. I haven't seen (or I misplaced) the fix-all solution - or I'd be happy to link you to it.
For what it's worth (and strictly my opinion), the six month development cycle is pushing out versions that aren't quite ready. Hardy and Intrepid had problems with Network Manager. Jaunty seems more stable than I'd expect (laptop has had sound issues). Karmic may be great once several of the bugs are squashed.

You are right. On servers LTS on ubuntu seems the way to go.

I like bleeding edge and i tought karmic server was at least stable...i see it's not.

Maybe debian it's also a solution...but i have also problems in AD integration on samba...

---

### Post by imashley on 2009-11-30
My swat now works OK following a system reboot.
If you need me to check any settings please let me know

---

### Post by Sniffer on 2009-11-30
> **imashley said:**
> My swat now works OK following a system reboot.
If you need me to check any settings please let me know

I'm at least curious how you get it working...what you have done exactly.


Thanks
Sniff.

---

