---
title: "Why can't I access my shared folders on my Win 7?"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by gregtheCdn on 2010-07-09
Hello all,

This may be only a temporary problem as I will soon be converting my Desktop (currently running Win 7 x64) to Ubuntu 10.04. 

But before I can do that, I would like to know why I can't access shared folders on the Win 7 computer from my laptop running Ubuntu 10.04.

_Quick overview: _

- I have installed and set up Samba and have no problem viewing folders on my laptop from the Win 7 desktop.

- I have shared the requisite folders in Win 7 and opened all the permissions. I have also disabled password protected sharing in Win 7 settings.

_Problem:_

When I go to: Places>Network>Windows Network>(my network name)>(desktop computer name)

I double click on the icon for my desktop computer and it immediately provides a box saying: "password required for (my desktop comp name)" and then asks for my username, domain, and password.

The problem is, I don't have a username or password set for this computer and I don't know how to either fix this, or bypass this so as to access the files on this computer over my network.

Any help would be MUCH appreciated.

---

### Post by meanmrmustard on 2010-07-09
Same problem here!

Samba setup is OK but no connection method, "Connect to server", Network or command line will let me have access.

I have even changed the Windows 7 password which did nothing, then disabled the password altogether, still no help.

What's up?

---

### Post by Morbius1 on 2010-07-09
Do you by any chance have "Windows Live Sign-In Assistant" installed on your Win7 box? : [http://social.technet.microsoft.com/For  ... 79a5597527]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527")

You may have to uninstall it.

---

### Post by gregtheCdn on 2010-07-09
> **Morbius1 said:**
> Do you by any chance have "Windows Live Sign-In Assistant" installed on your Win7 box? : [http://social.technet.microsoft.com/For  ... 79a5597527]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527")

You may have to uninstall it.


Bleepin' hell...that worked wonderfully! I will avoid the usually head-ache inducing question of "why??" and skip right ahead to the THANK YOU!

Cheers,

GtC

---

### Post by meanmrmustard on 2010-07-10
No sign-in assistant here.

---

