---
title: "Samba stopped working"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by rwoods3 on 2011-06-17
Been searching for hours and looked at several other threads but still can't figure this out. We have 4 folders being shared from a Ubuntu 10.4.2 LTS Server using Samba. A couple days ago two computers in the office lost access to these shares. The other computers in the office are fine. So far as I know nothing has changed on the server. I can putty into the server still but I can't map a drive or open a window through run (\\server_name\etc).

Below is a snapshot of my smb.conf file. I've tried messing with the following lines in the file as was suggested by another thread but to no avail:

interfaces = 127.0.0.0/8 etho0
bind interfaces only = yes

I commented both these lines out, restarted the smbd and nmbd service and rebooted the server and my winXP machine and still no access. Only the error: 

"\\server_name is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The specified server cannot perform the requested operation."

[IMG]http://www.horse-magazine.info/test/smb.conf.jpg[/IMG]

I've also tried disabled iptables on the server and windows firewall on the the windows xp machines. Still no luck. What am I doing wrong? Like I said, so far as I know there have been no changes to the server whatsoever. One day it was working and the next it just stops.

HELP!

---

### Post by dandnsmith on 2011-06-18
If access stopped 2 days ago for a couple of machines, the place to look is on those machines - after all you've said the server hasn't been changed, and other machines can still access.

Look at any updates/changes on the clent PCs - start with firewalling, as MS updtaes have a nasty habit of changing things without warning.

---

### Post by Morbius1 on 2011-06-18
You have a parameter:
> encrypt passwords = false
Change it to:
> encrypt passwords = [COLOR=Blue]**true**[/COLOR]
Then restart samba:
```
sudo service smbd restart
```

You might think that it shouldn't matter since these are all guest shares but remember Windows is sending a user name and password by default.

---

### Post by rwoods3 on 2011-06-19
I changed encrypt passwords to true and sure enough that did the job. Must have been some kind of automatic update on the two windows machines that required that. Don't know, in any case it's working.

Thanks
:)

---

