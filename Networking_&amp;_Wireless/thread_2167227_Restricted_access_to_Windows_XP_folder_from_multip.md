---
title: "Restricted access to Windows XP folder from multiple Ubuntu PC's"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by netherdragon on 2013-08-12
I am new to playing with Ubuntu networking, so if my question is old-hat I apologise for this.
I currently run three Ubuntu 12.04 LTS PC's and one Windows-XP (I need some legacy software that will not run under Wine) on a network, connected through a Netcomm NB604N Wireless/Modem/Router.
All machines have static IP addresses - I use MySQL with a Gambas3 frontend, and it makes it easier to access the database I want using static IP addresses.
All of this setup works fine - up to a point. The three Ubuntu PC's can access shared folders on each other without any problems.
The problem is with the Windows-XP machine.
I have found that the first Ubuntu machine I turn on can access the shared folders on the Windows-XP machine - but only two folders. If I try to access a third folder I am asked for a password, and cannot access the folder. However, if I unmount one of the WIndows-XP shared folders I have been accessing, then I can access another shared folder without any problem. The restriction appears to be that I can only access two folders at any one time.
Another issues is that the other two Ubuntu machines cannot access the WIndows-XP machine. Again, they are asked for a password, and nothing will work past this point.
I should add that it doesn't matter which of the Ubuntu machines I turn on first, it is the one that can access the Windows-XP machine.
Any ideas why this is happening? The two folder limit? The restriction to the first Ubuntu machine (turned on) being the only one that can access the Windows-XP machine?
 Any suggestions greatly appreciated.

---

