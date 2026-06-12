---
title: "Samba Windows Seven User Permissions"
date: 2012-04-08
forum: Networking &amp; Wireless
---

### Post by burgiking on 2012-04-08
Hi I've been tracking the internet for ages for a solution to my problem. I've had no success this time for samba installation and sharing.

Problem: I'm sharing a test folder; can access the folder's on windows 7, traverse through directories but creating folders and viewing files is a no-go. The error *'you need permission to perform this action'*.

Here's some data: 
smbusers:
```
root = administrator admin
nobody = guest pcguest smbguest
samba = "samba"
```

smb.conf:
```
  workgroup = WORKGROUP
        server string =
        netbios name = *****.*******.com
        announce version = 5.0
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

 security = user
        passdb backend = tdbsam
        null passwords = true
        username map = /etc/samba/smbusers
        name resolve order = hosts wins bcast
        follow symlinks = yes
        unix extensions = no
        browsable = yes
        wide links = yes

[TEST]
        path = /media
        create mask = 0644
        directory mask = 0755
        read only = no
        writable = yes
        valid users = burgiking root samba

[MNT]
        path = /mnt
        create mask = 0644
        directory mask = 0755
        read only = no
        writable = yes
```



I have the user:samba and group:samba. Added the samba user to group root as well (for testing). 

mnt:
```

drwxrwxrwx.   3 root  root     4096 Apr  8 16:44 mnt

```

/mnt/test
```
drwxrwxrwx. 2 root root 4096 Apr  8 17:06 test

```

/mnt/test/hi.txt
```
-rwxrwxrwx. 1 root root 0 Apr  8 17:07 hi.txt

```


I used the command smbpasswd -a and -e

Any ideas? Hope I've given enough data for you guys to help. 
Many thanks

---

### Post by Stason on 2012-04-08
I get the same error. My setup is only different that I have guest access enabled. I presume it is some win7 purpose built-in incompatibility issue.

---

### Post by burgiking on 2012-04-08
It must be, what kind of set-up do you have?

When I had a virtual box with a nat connection it worked fine. Once I moved to a physical server connected to the router my laptop can't access the shares. [I'm re-reading this as a whining girl]

---

### Post by CharlesA on 2012-04-08
Can you connect via IP?

I have been able to connect fine using the default smb.conf (after adding the share definitions) and running:

```
sudo smbpasswd -a username
```

EDIT: The reason you are unable to create files in /media is because it is owned by root which means you don't have access to it.

Try pointing that share to a folder you created yourself.

---

### Post by Stason on 2012-04-16
The directory I am trying to give guest acces to is not owned by root, but by user. I am able to access it both from android and MacOS creating/deleting files without problem, but not from Win7.

---

### Post by CharlesA on 2012-04-16
Are you trying to connect via IP or hostname?

---

### Post by Stason on 2012-04-16
via IP

---

### Post by CharlesA on 2012-04-16
Have you added the user via:

```
sudo smbpasswd -a username
```

---

### Post by Morbius1 on 2012-04-16
> The directory I am trying to give guest acces to is not owned by root,  but by user. I am able to access it both from android and MacOS  creating/deleting files without problem, but not from Win7.Windows sends the local login user's username and password when it browses a samba / smb share forcing the server to deal with it in some way. If you set up a guest share you have one of 2 choices:

** Set up the Win7 user as an actual user on the Linux server with an smbpasswd so he has something to authenticate himself against.

** Or do none of that and make sure you have the following line in the [global] section of smb.conf:
```
map to guest = Bad User
```The Win7 user will come across with credentials, Samba will not find a match to his user name, he will be tagged a "Bad User", and then converted to the guest account.

*[COLOR=Blue]Side note[/COLOR]*: Have we given up on the OP. It's fine by me since I haven't a clue what his issue is ;)

---

### Post by CharlesA on 2012-04-16
> **Morbius1 said:**
> *[COLOR=Blue]Side note[/COLOR]*: Have we given up on the OP. It's fine by me since I haven't a clue what his issue is ;)

I guess so. They haven't been back in a week. I'm not sure what their problem is either. :confused:

---

### Post by Stason on 2012-04-17
> **Morbius1 said:**
> 

** Set up the Win7 user as an actual user on the Linux server with an smbpasswd so he has something to authenticate himself against.


Did that
> **Morbius1 said:**
> 
 make sure you have the following line in the [global] section of smb.conf:
```
map to guest = Bad User
```

It is there

---

### Post by Morbius1 on 2012-04-17
Then neither the Windows user or "nobody" has access to the underlying Linux directory. What are the ownership and permissions of the folder:
```
ls -dl /path/to/folder
```

---

### Post by Stason on 2012-04-17
drwxrwxrwx 3 myusername myusername 4096

---

### Post by Morbius1 on 2012-04-17
And you're getting the same error as the OP:
> Problem: I'm sharing a test folder; can access the folder's on windows  7, traverse through directories but creating folders and viewing files  is a no-go. The error *'you need permission to perform this action'*.

[COLOR=Blue]**EDIT**[/COLOR]: It would have been nice to actually see the path but is this in your home directory and is it encrypted by any chance?

---

### Post by Stason on 2012-04-18
It is the same thing, although I can view and copy the files from the directory, but not into it. The error is the same. The directory is not encrypted and it is not in home directory, it is actually on a separate drive that I use for all the media files.

Once again, it all works fine if I connect from my Mac Air or from the Android-based smart-phone.

---

### Post by Morbius1 on 2012-04-18
I can't think of one thing that fits all your symptoms so you can either post the output of the following commands so we can see how you are set up:
```
testparm -s
``````
net usershare info --long
```**Or you can do the following:**

[1] Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```[2] Add the following line to the [global] section - right under the workgroup line:
```
force user = stason
```[COLOR=Blue]*Or whatever your local Ubuntu login name is.*[/COLOR]
[COLOR=Black]
[3] Then restart samba:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]

[COLOR=Blue][I]Note: When you restart samba the network has a fit so you need to give it some time. Other linux machines can recover in 60 seconds, WinXP can take up to 2 -3 minutes, But Win7 takes the prize for taking the longest.


[/I][/COLOR][/COLOR]

---

### Post by Stason on 2012-04-18
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[exchange]"
Loaded services file OK.
Server role: ROLE_STANDALONE
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[exchange]
	path = /media/BORDELLO/Exchange
	force user = stason
	read only = No
	guest ok = Yes

---

### Post by Stason on 2012-04-18
[exchange]
path=/media/BORDELLO/Exchange
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bordello]
path=/media/BORDELLO
comment=
usershare_acl=Everyone:R,STASON-UBUNTU\stason:F,
guest_ok=y

---

### Post by Morbius1 on 2012-04-18
This:
> [exchange]
    path = /media/BORDELLO/Exchange
    force user = stason
    read only = No
    guest ok = Yes     Conflicts with this:
> [exchange]
path=/media/BORDELLO/Exchange
comment=
usershare_acl=Everyone:F,
guest_ok=yAnd this.....:
> [bordello]
path=/media/BORDELLO
comment=
usershare_acl=Everyone:R,STASON-UBUNTU\stason:F,
guest_ok=y     ... Will be confusing to the client. Guests have read only access to /media/BORDELLO so If they access the bordello share and go to the exchange folder they do not have write access but if they go to the Exchange share directly they do.

At a minimum remove the share you created in Nautilus for /media/BORDELLO/Exchange.

---

### Post by Stason on 2012-04-18
I have already tried removing Nautilus share. Win7 gets no access to Exchange at all. Connecting to Exchange directly yields same issue with permissions.

It seems to me that smb.conf settings have no effect at all.

---

### Post by Morbius1 on 2012-04-18
You posted earlier that your symptoms were the same as the original poster so the Windows client does have access to the share just not write access. 

You put the "force user" in the share definition instead of in the [global] section so that should have fixed the problem as far as write access to that share - assuming the user stason has write access to the folder locally.

If this is not the case then I cannot reproduce your symptoms.

---

### Post by Stason on 2012-04-18
I do not want all users to have same access as the owner. I want just one directory to serve for uploads and the rest be read   only.

It should not be that complicated. Besides it works as supposed withev erything else  via Nautilus only.                                

I have put force user in global and it did not work anyway.

I feel that it is just easier to share the directory on win7 pc and access it from Ubuntu for needed files.

 Thank you for your help anyway.

---

### Post by Morbius1 on 2012-04-18
Permissions when using Samba come in 2 parts - the Linux part and the Samba part.

If I create a share that looks like this:
> [exchange]
    path = /media/BORDELLO/Exchange
    force user = stason
[COLOR=Blue]**     read only = Yes**[/COLOR]
    guest ok = Yes                      The remote guest will be allowed in first then converted to "stason" for that share but Samba will prohibit a write even if stason locally can write.

Samba is the gatekeeper - it determines who has access and what that user can do as long as it's not more permissions then the underlying Linux permissions. If the target Linux folder does not permit a write Samba cannot make it so. But if the target folder does allow write Samba can be used to prevent it.

---

### Post by Morbius1 on 2012-04-18
> **Stason said:**
> It should not be that complicated. 
I have Win7 Pro on another machine and I created a share just like yours on my Xubuntu box. Win7 has no problem accessing that share despite the fact that according to 99% of the HowTo's out there everything about my setup is wrong: The machines in question are in 2 different workgroups, they can't ping each other by name if my life depended on it ( but I can browse by name ), and I have not disabled HomeGroup on Win7.

The whole thing took 30 seconds - and that's because the Win7 machine is in another room.

There's something about your setup that I've missed or I haven't asked the right questions.

---

### Post by CharlesA on 2012-04-18
> **Morbius1 said:**
> I have Win7 Pro on another machine and I created a share just like yours on my Xubuntu box. Win7 has no problem accessing that share despite the fact that according to 99% of the HowTo's out there everything about my setup is wrong: The machines in question are in 2 different workgroups, they can't ping each other by name if my life depended on it ( but I can browse by name ), and I have not disabled HomeGroup on Win7.

The whole thing took 30 seconds - and that's because the Win7 machine is in another room.

There's something about your setup that I've missed or I haven't asked the right questions.
My set up the pretty much the same as yours then.

All I did was throw the share definitions in and it worked.

---

### Post by Stason on 2012-04-19
> **Morbius1 said:**
> I have Win7 Pro on another machine and I created a share just like yours on my Xubuntu box. Win7 has no problem accessing that share despite the fact that according to 99% of the HowTo's out there everything about my setup is wrong: The machines in question are in 2 different workgroups, they can't ping each other by name if my life depended on it ( but I can browse by name ), and I have not disabled HomeGroup on Win7.

The whole thing took 30 seconds - and that's because the Win7 machine is in another room.

There's something about your setup that I've missed or I haven't asked the right questions.

Can you copy a file from win7 to that share and then delete it all from win7 pc?

---

### Post by CharlesA on 2012-04-19
> **Stason said:**
> Can you copy a file from win7 to that share and then delete it all from win7 pc?
I can, yes.

Do it all the time actually - my main desktop is Win7 and my file server is Ubuntu 10.04.

---

### Post by Stason on 2012-04-19
Perhaps the issue is that my win7 laptop's primary network is not that where I am trying to connect it to Ubuntu.

Anywas I found a more straightforward solution above.

---

### Post by Morbius1 on 2012-04-19
> **Stason said:**
> Perhaps the issue is that my win7 laptop's primary network is not that where I am trying to connect it to Ubuntu.
If you mean the workgroups are different it shouldn't make any difference. In my example the workgroups were different. If you mean one is in a different subnet than the other then I'm not sure how you are browsing to the other box at all.

But either way, unless I've completely misread your symptoms, you can find and access the Linux share you just can't write to it. Based on how you defined the share:
> [exchange]
    path = /media/BORDELLO/Exchange
    force user = stason
    read only = No
    guest ok = Yes                      Samba is not stopping the write - Linux is. But for the life of me I can't figure the source of the problem.

---

