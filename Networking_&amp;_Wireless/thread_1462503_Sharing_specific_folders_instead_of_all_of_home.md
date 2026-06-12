---
title: "Sharing specific folders instead of all of /home"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by ShakeyJake on 2010-04-25
Hey all,

I've being following [this]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4") guide, which is great, and currently my samba.conf looks like this:

```
[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "Name"
netbios name = "Server name"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700
```

As you can (maybe) see, my entire /home folder is shared. For various  reasons, I'd prefer it if only say my music and videos were shared, how do I do that? I've looked around the web and seen some other people's samba.conf files but mine looks totally different and I don't want to lose the functionality I have by messing around with it.

Cheers,
Jack

---

### Post by ShakeyJake on 2010-04-27
Just in case anyone has the same problem:
I asked on the samba irc channel and was told the (obvious in hindisight) solution. I used the homes share as a template (in this case commented out as I don't want to share my entire /home) and just specified the new shares using the same syntax. My samba.conf now looks like this:

```
[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "WORKGROUP"
netbios name = "jack-desktop"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no
wide links = no

#Share Definitions

#[homes]
#        comment = Home Directories
#        browseable = yes
#        writable = yes
#        security mask = 0700
#        create mask = 0700

[Music]
        comment = Jack's Music
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700
	path = /home/jack/Music

[Videos]
        comment = Jack's Videos
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700
	path = /home/jack/Videos

[Other]
        comment = Jack's Other Stuff
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700
	path = /home/jack/Other


```

---

