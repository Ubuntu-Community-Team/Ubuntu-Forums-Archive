---
title: "Samba 4 not starting up"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Vkec on 2009-07-13
When I start samba in the ternimal it gives me this

Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
smbd version 4.0.0alpha6 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009


What does this mean and how do i fix it.

---

### Post by PryGuy on 2009-07-13
It seems you're trying to run samba4 with old (samba3?) config file. Just a thought, never tried samba4 yet...
My general advice is to roll back to a good old stable samba3 instead of using samba4 alpha. It works just brilliant for me. Open Terminal, type 'testparm' without quotes and post output here.

---

### Post by Vkec on 2009-07-13
this is what i get 
testparm
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Loaded smb config files from /etc/samba/smb.conf
lp_load: refreshing parameters from /etc/samba/smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Processing section "[printers]"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Processing section "[print$]"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Loaded services file OK.
ERROR: pid directory /var/run/samba does not exist
Press enter to see a dump of your service definitions

The only reason I have samba 4 is because I couldn't figure out how to install samba 3

---

### Post by Ryuho on 2010-09-10
I have Ubuntu 10.04 desktop but I ran into the same problem.

I tried running samba by typing "samba", it told me samba is not installed, but suggested installing samba4 (apt-get install samba4). I installed it, and then tried running samba again, and came up with Vkec's error message.

"Samba4 development is moving very rapidly, but there is still much work to be done." --(Samba4 current status [http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)) 

So why is Ubuntu suggesting to use alpha stage software when samba3 is there?


**EDIT:**

Welp, I didn't understand that 'samba' (the program) was already installed under a different name, my bad.

```

:~$ smb
smbcacls          smbcquotas        smbpasswd         smbstatus.samba3
smbclient         smbd              smbspool          smbtar
smbcontrol        smbget            smbstatus         smbtree

```

---

### Post by naaano on 2011-04-11
because samba 4 is a very powerful full featured needed monster ;)

---

