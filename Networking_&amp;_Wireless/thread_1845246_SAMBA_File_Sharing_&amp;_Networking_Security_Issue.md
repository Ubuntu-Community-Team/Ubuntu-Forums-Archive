---
title: "SAMBA File Sharing &amp; Networking Security Issue"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by micromike09 on 2011-09-16
Hello, I have basic Ubuntu Linux experience and I already installed SAMBA on my Ubuntu 10.4 Desktop PC. I was able to create a shared folder which I can access from my Windows XP computer via a private network. Now, the network and the sharing works perfectly except, I want to secure it. I do not want anyone without a password to access this folder from my Windows computer.

I did the following:

sudo smbpasswd -a joe

then I entered the password and everything is OK.

Then I modified the smb.conf file to enable the [share] portion and add the user joe to the file.

Restarted samba and tried to enter the shared folder from my Windows computer. No luck. Keeps asking me for the correct username and password. 

I tried my admin password, my admin user name, etc, nothing works. 

Any suggestions?

---

### Post by dougguod on 2011-10-18
I've got the same problem, I hope we can find some who knows how to fix it. D

---

### Post by RyanRahl on 2011-10-20
Im not sure what all you have done so far so I'll suggest the following:

Make sure your shared folder contains the executable bit

Make sure the user 'joe' has system permissions as well as samba permissions (this is helpful: [http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html))

Make sure your share at least contains the following:
```

[Joe]
path = /home/joe
comment = Joe's Folder
guest ok = no
browseable = yes
write list = joe

```

You should post/paste your smb.conf file so we can check for problems. I would re-enter the password for 'joe' while you're at it. Maybe check to see if some other program is making modifications to your config file, like Nautilus or something.

---

