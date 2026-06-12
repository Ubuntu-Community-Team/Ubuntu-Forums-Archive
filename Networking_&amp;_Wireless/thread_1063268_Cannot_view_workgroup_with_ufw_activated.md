---
title: "Cannot view workgroup with ufw activated"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by empty_spaces on 2009-02-07
I have a desktop running WinXP and a laptop running 8.04.2. Both WinXP and 8.04.2 are members of the same workgroup.
I have UFW set as -> "sudo ufw default deny" and set the WinXP ip address in the allow list.
When I click on Places -> Network, I cannot see my workgroup.
If I then change UFW to -> "sudo ufw default allow", I can then see my workgroup.

Is there anything else I need to add to the exceptions list in ufw so that I can view my workgroup from ubuntu even when ufw is set to "default deny"?

Note: If I directly enter smb://winxp-ipaddress in Nautilus with ufw set to "default deny", I can browse my shared folders on WinXP.

---

### Post by empty_spaces on 2009-02-08
Bump.
My current workaround to access shares easily with ufw enabled is to bookmark the WinXP machine share.
But my original question still remains.

---

### Post by superprash2003 on 2009-02-08
try opening port 139 or 137-140

---

### Post by empty_spaces on 2009-02-09
thanks for the suggestion.
I tried ports 137-140 first, and it seemed to work for a while.
After restarting the computer though, now Nautilus does not want to browse any windows shared folders unless I enter smb://ipaddress-of-winxp-machine.

In the past, clicking on the "Windows Network" icon would have shown me the WInXP machine, but now it just comes up blank. It won't even show the animated gnome icon which tells me that its searching the network, it just directly shows a blank.

This is definitely a Nautilus issue, because I also tried Konqueror and it works flawlessly. It shows me my workgroup, folder shares etc. and I never have to type any addresses or hostnames.

---

### Post by superprash2003 on 2009-02-10
yea.. nautilus does have a few bugs!!!

---

### Post by anibalojeda on 2009-04-21
> **empty_spaces said:**
> thanks for the suggestion.
I tried ports 137-140 first, and it seemed to work for a while.
After restarting the computer though, now Nautilus does not want to browse any windows shared folders unless I enter smb://ipaddress-of-winxp-machine.

In the past, clicking on the "Windows Network" icon would have shown me the WInXP machine, but now it just comes up blank. It won't even show the animated gnome icon which tells me that its searching the network, it just directly shows a blank.

This is definitely a Nautilus issue, because I also tried Konqueror and it works flawlessly. It shows me my workgroup, folder shares etc. and I never have to type any addresses or hostnames.

have you reported this as a bug?
got the same here.

---

### Post by squibs on 2009-04-21
I found the information at [http://log.logfish.net/node/31]("http://log.logfish.net/node/31") to be useful when I had a similar issue.

---

