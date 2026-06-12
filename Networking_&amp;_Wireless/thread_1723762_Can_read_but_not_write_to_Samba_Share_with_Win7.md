---
title: "Can read but not write to Samba Share with Win7"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by wagoner on 2011-04-07
I set up a samba share on my desktop running kubuntu Lucid.  I used the samba config tool set up my share folder. I have a home network with a router and three computers.

I can access the share from laptop running Win7 and I can read files, but I cannot write to the share.  The last lines of my smb.conf are:

[ShareName]
path = /home/username/
#read only = no
writeable = yes
browseable = yes

I set the security level of the share to "Share"  from a list of 
(Share, User, Server, Domain, ADS).

I accomplished the above from the samba instructions at kubuntuguide.  What should I do next?

---

### Post by Morbius1 on 2011-04-07
> [ShareName]
path = /home/[COLOR=Blue]username[/COLOR]/
#read only = no
writeable = yes
browseable = yesYour share has two problems unless you did some other things that you didn't post.

It's not allowing guest access so you needed to create a samba user for access.

Even if you did create a samba user the only one that would allow write access is "[COLOR=Blue]username[/COLOR]" because of the underlying Linux file permissions of the path.

By default, your home directory has permissions of 755. The owner can read and write ( the "7" ) and everyone else can only read ( the "5"'s ).

So you can set up a samba user for "username", 

Or change the permissions on the target to 777:
```
sudo chmod 0777 /home/username
```Or add a line to the share definition to convert the remote user to username:
```
force user = username
```Then restart samba.

---

### Post by wagoner on 2011-04-07
I created a samba user for username
```
sudo smbpasswd username
Old SMB password:
New SMB password:

```

Also, I chmod /home/username
```
sudo chmod 0777 /home/username
```

I didn't try your last suggestion to force user = username.

Then I restarted samba server
```
sudo service smbd restart
sudo service nmbd restart
```

I got the same result from windows7.  Shouldn't I get a prompt for the samba username and password from windows explorer?  I'm using Win7 home.  I also tried from another desktop running winXP professional and I got an error saying that write protected or disk is full.

---

### Post by Morbius1 on 2011-04-07
This isn't some encrypted home directory, is it?

If not then post the output of the following commands so we can see what's up:
```
testparm -s
```
```
ls -dl /home/username
```

---

### Post by wagoner on 2011-04-07
Here is testparm

[HTML]
adam@dell16:/home$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[ADAM]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = WAGON
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        logon path = \\%25N\%25U\profile
        logon home = \\%25N\%25U
        domain master = No
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        guest ok = Yes

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

[ADAM]
        path = /home/adam/
        read only = No
adam@dell16:/home$ 
[/HTML]

and here is ls -dl

```
adam@dell16:/home$ ls -dl /home/adam
drwxrwxrwx 58 adam adam 4096 2011-04-07 15:20 /home/adam

```

**[COLOR="RoyalBlue"]I think the problem is that I can't create a samba user.[/COLOR]**:confused:

---

### Post by Morbius1 on 2011-04-08
Now that I see your entire smb.conf I notice that you have in your [global] section the following parameter:
> guest ok = yesSince it's in the global section it will apply to all shares unless you override that in the share definition itself - which you have not. So your share is allowing guest write access and needs no samba user.

The remote guest should have the ability to write to that share - meaning the ability to add to or delete from that share. It's unlikely that he will be able to write to the contents of that share - i.e., edit a file - since the linux permissions on a particular file would not allow it. 

So just to be clear, are you talking about adding a file to the share or are you talking about editing a given file within that share. If it's the latter then "force user = adam" in the [ADAM] share is the easiest way out of this.

---

### Post by wagoner on 2011-04-08
I am just trying to write a new file into the share.  I added force user=adam and it works!:)  Thank you so much!

I am still confused about adding a user to samba.  I tried to add the user adam to samba with sudo smbpasswd command on the CLI.  It doesn't return any errors, but it doesn't seem to work either.  I use KDE and there is a nice GUI in system setting to configure samba.  The user that I added is not listed in system settings, so I don't think it was ever successfully added.

I am replacing my linux samba server.  The samba share on my old install used to prompt me for a username and password when I accessed it from a remote windows computer.  I would prefer to set it up that way again.

---

### Post by Morbius1 on 2011-04-08
Adding a samba user is a two step process:

First you need to create a local user on the server itself.
Then you need to add the samba password to the database:
```
sudo smbpasswd -a user-name
```There's two things that confuses it's use however.

(1) Windows will actually pass it's local login user username and password when it browses the network. They must think that is some kind of feature. If you set up a user and samba password on a Linux server that matches the Windows login user name and password then the Windows user is allowed in without being prompted for authentication because it's already been sent.

(2) Linux is not without it's own insanity though. Since 10.10 an package called libpam-smbpass is installed by default. It's purpose is to override whatever you set in smbpasswd with the actual login password for that user on the server. I can think of no circumstance where one would want to do that so I uninstall it.

---

### Post by bab1 on 2011-04-08
> **Morbius1 said:**
> Adding a samba user is a two step process:

First you need to create a local user on the server itself.
Then you need to add the samba password to the database:
```
sudo smbpasswd -a user-name
```There's two things that confuses it's use however.

(1) Windows will actually pass it's local login user username and password when it browses the network. They must think that is some kind of feature. If you set up a user and samba password on a Linux server that matches the Windows login user name and password then the Windows user is allowed in without being prompted for authentication because it's already been sent.

Why is this a bad thing?  If you are previously authenticated (logged in), why would you need to do that again?> 

(2) Linux is not without it's own insanity though. Since 10.10 an package called libpam-smbpass is installed by default. It's purpose is to override whatever you set in smbpasswd with the actual login password for that user on the server. I can think of no circumstance where one would want to do that so I uninstall it.

The libpam-smbpass synchronizes the 2 passwords to the users system password. In a single sign on system (Samba PDC or MS Active directory) isn't this what you would want?  I'm confused about your two points.  Am I missing something here?

---

### Post by Morbius1 on 2011-04-08
> (1) Windows will actually pass it's local login user username and  password when it browses the network. They must think that is some kind  of feature. If you set up a user and samba password on a Linux server  that matches the Windows login user name and password then the Windows  user is allowed in without being prompted for authentication because  it's already been sent.> Why is this a bad thing?  If you are previously authenticated (logged in), why would you need to do that again?John has a Windows uername of john and he logs into his Windows machine with a password of johnpw. When he goes to browse the network his machine is passing uername=john : password=johnpw automatically. That's unique to Windows. If you want to take advantage of that you can but that would mean that Mary ( the owner of the share that John wants to access ) has to know John's Windows login password.

> (2) Linux is not without it's own insanity though. Since 10.10 an  package called libpam-smbpass is installed by default. It's purpose is  to override whatever you set in smbpasswd with the actual login password  for that user on the server. I can think of no circumstance where one  would want to do that so I uninstall it. 
> The libpam-smbpass synchronizes the 2 passwords to the users system  password. In a single sign on system (Samba PDC or MS Active directory)  isn't this what you would want?
A true single sign on system is going to use a completely different mechanism and once again to bring this to the level of the home lan which is more peer-to-peer in nature we have the same conundrum as before. Mary sets up a share that requires John to pass a password. She sets up a local user named john on her machine and gives it some password - maybe even her own since she doesn't expect john to ever log into her machine. She then creates a samba password for john. At the next reboot john's samba password has been overridden by john's login password on Mary's machine. Mary can live with that if she wants to but then John has access to Mary's physical machine. 
```
sudo apt-get remove libpam-smbpass
```

---

### Post by bab1 on 2011-04-09
> **Morbius1 said:**
> 

...Linux is not without it's own insanity though. Since 10.10 an package called libpam-smbpass is installed by default.

I guess what I don't see as productive is the notion that Linux is insane or even illogical.  I would think the developers look to the larger *system administrated* installations for development solutions.  The libpam-smbpass package is a needed part of those installations.


I don't see the* libpam-smbpass* PAM module installed by default at all.  I have checked the installs of my 10.04 DE installs.  They do NOT have this PAM module installed at all.  It is not listed in 10.10 or 11.04.  These Samba packages do not list libpam-smbpass as a dependency or a part or the Samba 3.5.x package.

---

### Post by Morbius1 on 2011-04-09
> **bab1 said:**
> I guess what I don't see as productive is the notion that Linux is insane or even illogical.  I would think the developers look to the larger *system administrated* installations for development solutions.  The libpam-smbpass package is a needed part of those installations.
In a true Samba File Server where there are many clients, users don't have local login capability to the server itself ( they have user accounts without passwords or home directories ) so libpam-smbpass has nothing to sync with rendering it harmless. It should be up to the discretion of the SysAdmin in my opinion if he/she wants such a thing and deploy the utility as they see fit.
> I don't see the* libpam-smbpass* PAM module installed by default at  all.  I have checked the installs of my 10.04 DE installs.  They do NOT  have this PAM module installed at all.  It is not listed in 10.10 or  11.04.  These Samba packages do not list libpam-smbpass as a dependency  or a part or the Samba 3.5.x package.     I have personally installed 10.10 on 7 machines and it installed libpam-smbpass on each one by default. These were Gnome desktop installs so maybe it's only on the Gnome version that this is happening. It was never installed by default prior to 10.10. It's quite possible I keep making the same mistake somewhere during or post install adding it without realizing it. I'm getting old and feeble minded so that's a distinct possibility ;)

---

### Post by bab1 on 2011-04-09
> **Morbius1 said:**
> ...

I have personally installed 10.10 on 7 machines and it installed libpam-smbpass on each one by default. These were Gnome desktop installs so maybe it's only on the Gnome version that this is happening. It was never installed by default prior to 10.10. It's quite possible I keep making the same mistake somewhere during or post install adding it without realizing it. I'm getting old and feeble minded so that's a distinct possibility ;)

Morbius,

I don't think you are feeble minded at all.  Your *libpam-smbpass* experience was my interest.  It turns out that we are both looking at the same animal from different angles.  

The *libpam-smbpass* package is not installed when the Samba package is installed.  It is installed when you configure shares using Gnome (i.e. right click, etc, etc,).  I believe you use this method (usershares).  See [_[U][COLOR="Blue"]here[/COLOR]_[/U]]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/609092") for the devs explanation (see post #4).  I never configure my shares using Gnome.  I use the smb.conf file.  This appears why I never see the *libpam-smbpass* package on my systems.

---

### Post by Morbius1 on 2011-04-09
> **bab1 said:**
> The *libpam-smbpass* package is not installed when the Samba package is installed.  It is installed when you configure shares using Gnome (i.e. right click, etc, etc,).  I believe you use this method (usershares).  See [_[U][COLOR=Blue]here[/COLOR]_[/U]]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/609092") for the devs explanation (see post #4).  I never configure my shares using Gnome.  I use the smb.conf file.  This appears why I never see the *libpam-smbpass* package on my systems.
Well, that explains it. You are correct, after years of using Classic shares on the server ( little "s" ) and and fstab on the client end I now use a combination of classic share and usershare ( depending on the box and what I'm sharing ) on the server end and Gigolo of all things to auto mount remote shares.

Not quite sure I understand the developers assessment that libpam-smbpass "makes sense as a default behavior" with usershares but at least I understand why It appeared to be in the default install on every box I set up.

---

