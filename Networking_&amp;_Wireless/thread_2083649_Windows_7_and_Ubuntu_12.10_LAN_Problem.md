---
title: "Windows 7 and Ubuntu 12.10 LAN Problem"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by gonejack on 2012-11-13
My roomate can access my public files with typing \\ipaddress on his windows 7 computer.

And I can access his public flies by typing smb://ipaddress

the problem is both of us can't see my computer.

I can't see my computer with a name like xx-pc in nautilus network and he can't see my computer on windows explorer as well. but I can see my roomate's computer on nautilus.

what can I do to make my computer visual on other computer?

need help

sorry, poor english. I am Chinese.:popcorn:

---

### Post by mikewhatever on 2012-11-13
To be able to "see" an Ubuntu computer, you need to install samba, file and print server for Linux. That said, just "seeing" would probably not be enough, and you'll want to actually share some files. To do that:

- right click the folder you want to share
- select Sharing Options
- check the box next to Share this folder

That will ask permission to install samba, if it is not installed.

When done, you should be able to access that folder over the network.

---

### Post by gonejack on 2012-11-13
> **mikewhatever said:**
> To be able to "see" an Ubuntu computer, you need to install samba, file and print server for Linux. That said, just "seeing" would probably not be enough, and you'll want to actually share some files. To do that:

- right click the folder you want to share
- select Sharing Options
- check the box next to Share this folder

That will ask permission to install samba, if it is not installed.

When done, you should be able to access that folder over the network.
thank you.

but the truth is I can share my files with my roomate without samba(maybe samba has been installed but when I run sudo service samba start it say I didn't install that commond.

and when I share a folder with friend, Ubuntu  never ask me to install samba.but I can success finish the share, my friend just need to type \\myipaddress to access my files.

---

### Post by mikewhatever on 2012-11-13
Then I don't understand the problem. What do you mean by "both of us can't see my computer"?

If you already have shared folders, then samba is installed. There is no need to install it again. There is also no need to start it manually, because it autostarts.

---

### Post by critin on 2012-11-13
This link is very good.  Note the Samba package that it installs and be sure to do that.  It's different than the automatic install of samba that is installed when creating 'share'.     If all permissions and shares are done, you won't need to type in the ip address any longer.

[http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/](http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/)


See attached images in these post to see network from ubuntu and windows 8 only using Samba.  Working computer names are DellPrecise 'ubuntu' and tinas8.  Second link is working with ubuntu/winXP

[http://ubuntuforums.org/showthread.php?p=12348998#post12348998](http://ubuntuforums.org/showthread.php?p=12348998#post12348998)
[http://ubuntuforums.org/showthread.php?t=2082924&page=2](http://ubuntuforums.org/showthread.php?t=2082924&page=2)

---

