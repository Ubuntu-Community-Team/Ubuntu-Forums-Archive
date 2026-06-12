---
title: "Samba - Settings share &amp; user"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by Tobse82 on 2009-12-01
Hi all


at this moment i am setting up a samba-server on my 9.04.

I want a share, that can be accessed only by one special user!  ( projects ) 
This work so far.

And now i want to share a directory for all my colleagues, where we can exchange files and that can be accessed by everyone without entering a password. (Shares)
But this doesnt work. WindowsXP wants them to enter a password... 

What is wrong with the second share, that it can't be accessed by guests without entering a pwd ?

> [global]
    server string = MyUbuntu
    obey pam restrictions = Yes
    guest account = nobody
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    syslog = 0
    security = share
    log file = /var/log/samba/log.%m
    os level = 64
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes

[Projects]
    comment = Projects
    path = /home/toby/Projects
    read only = no
    writable = yes
    valid users = toby
    create mask = 0700
    directory mask = 0700
    browseable = no
    guest ok = no

[Shares]
    comment = Shares
    path = /home/toby/shares
    read only = no
    writable = yes
    guest ok = yes
    public = yes
    create mask = 7777
    directory mask = 7777
greetings toby

---

### Post by inobe on 2009-12-01
i'm pretty new on the second share thing but **read only** is set to **no**


warning: i may be wrong but i hope it works none the less.

edit: it should say **no**


also look at guest account

---

### Post by Tobse82 on 2009-12-01
I think "read only = no" is ok, since i want anyone to be able to write in the "shares"...

I have another idea: The "shares" directory is in my home  ( home/toby ), so maybe guests wont be able to access this directory...

---

### Post by inobe on 2009-12-01
i was reading samba's howto page on File, Directory, and Share Access Controls and it's a lot to read and seems difficult understanding.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html)


now from my understanding if the pass was never set anyone could have access to the directory, been there, done that.

this seems to be affecting both shares, it must be a specific way.

i am looking at your setup and noticed how you have the permissions.

i'm not have any permission issues using this setup.

```
testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shares]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[shares]
	path = /home/bob/shares
	valid users = bob
	read only = No
	guest ok = Yes
```

i will try a second share and see how that goes.

---

### Post by inobe on 2009-12-01
i still get prompted for a pass on the second share, there must be a needed line, maybe something that separates shares from pass program.


i will keep trying

---

### Post by Tobse82 on 2009-12-01
> [shares]
    path = /home/bob/shares
    valid users = bob
    read only = No
    guest ok = Yes
You have got a share, that everyone can access ( guest ok = Yes ), 
but also a "valid users"-entry. Sounds strange. ;)
I'll also try to remove the "create mask" and "directory mask" of my config,
but i dont expect this, to be the problem....



Edit:
> 
maybe something that separates shares from pass program

yeah thats what i am looking for... 

Thanks so far for your help :)

---

### Post by inobe on 2009-12-01
i haven't been much help but i think google is steering me because i want what you want.

[http://www.webmasterworld.com/forum40/349.htm](http://www.webmasterworld.com/forum40/349.htm)


from here 

[http://www.google.com/search?q=single+share+no+samba+password&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=single+share+no+samba+password&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)


that first looks promising :)

---

### Post by Tobse82 on 2009-12-01
> **inobe said:**
> i haven't been much help but i think google is steering me because i want what you want.

[http://www.webmasterworld.com/forum40/349.htm](http://www.webmasterworld.com/forum40/349.htm)


from here 

[http://www.google.com/search?q=single+share+no+samba+password&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=single+share+no+samba+password&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)


that first looks promising :)

I read the first thing. The author has got the problem as we do.
He has set "security = share" and "guest ok = yes", equal to my setup, but it didnt help...

---

### Post by inobe on 2009-12-01
i noticed this too, i am looking here now just down the list in the second link.

[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

---

### Post by Tobse82 on 2009-12-01
i tried adding
> usershare path = /home/toby/Shares

and deactivated my additional guest-share. But don't see the "Shares" in the windows-network...

---

### Post by inobe on 2009-12-01
did you restart samba


```
sudo /etc/init.d/samba restart
```

and run

```
testparm
```

---

### Post by Tobse82 on 2009-12-01
yep, i did

---

### Post by Tobse82 on 2009-12-01
I solved the problem.

The public share was inside my home directory. Now i created a directory "/shares", did "chmod 777" on it and declared this directory as a share inside the smb.conf!
So maybe public shares for everybody inside the home of a special user dont really seem to work. 

It works!

> 
[global]
        server string = Handelssystementwicklung
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        security = share
        log file = /var/log/samba/log.%m
        os level = 64
        panic action = /usr/share/samba/panic-action %d
        usershare allow guests = yes
        guest account = sambauser
        invalid users = bin daemon adm sync shutdown halt mail news uucp operator admin boot

; my private share. Only for me!
[projects]
        comment = Projekte
        path = /home/toby/projects
        read only = no
        writable = yes
        valid users = toby
        create mask = 700
        directory mask = 700
        browseable = no
        guest ok = no

; The public share, for everybody
[Shares]
        comment = Shares
        path = /Shares
        read only = no
        writable = yes
        guest ok = yes
        public = yes
        create mask = 777
        directory mask = 777
        available = yes


---

### Post by inobe on 2009-12-02
thanks so much for sharing :)

---

