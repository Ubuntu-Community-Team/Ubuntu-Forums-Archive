---
title: "Newbie and SAMBA"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by elite1967 on 2011-10-06
Hi all,
just setup an Ubuntu server 10.04 on a Atom D510 with 2GB.

I am trying to configure Samba properly.
What I want to do is:
1) to have a directory that can be seen (read-only) by everyone without entering any username/password 
2) to have a directory that can be seen only by me (read-write) with username and password.

this is my smb.conf:
```
[global]
workgroup = MSHOME
security = user
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
interfaces = 192.168.1.1/8

[Music Read-Only]
comment = Music Read-Only
path = /media/2TBa/Music
browsable = yes
read only = yes
guest ok = yes
guest account = ftp
guest only = yes

[2TBa Full Access]
comment = 2TB (A) Full Access
path = /media/2TBa
writeable = yes
create mask = 0777
directory mode = 0777
#locking = yes
browsable = yes
valid users = ubuntu
admin users = ubuntu
inherit permissions = Yes

```

But, the problem is, when I try to access the ubuntu-server from a W7 machine I always get a box asking for a username and password.

Am I missing something?

thanks

---

### Post by lcman on 2011-10-06
> **elite1967 said:**
> Hi all,
just setup an Ubuntu server 10.04 on a Atom D510 with 2GB.

I am trying to configure Samba properly.
What I want to do is:
1) to have a directory that can be seen (read-only) by everyone without entering any username/password 
2) to have a directory that can be seen only by me (read-write) with username and password.

this is my smb.conf:
```
[global]
workgroup = MSHOME
security = user
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
interfaces = 192.168.1.1/8

[Music Read-Only]
comment = Music Read-Only
path = /media/2TBa/Music
browsable = yes
read only = yes
guest ok = yes
guest account = ftp
guest only = yes

[2TBa Full Access]
comment = 2TB (A) Full Access
path = /media/2TBa
writeable = yes
create mask = 0777
directory mode = 0777
#locking = yes
browsable = yes
valid users = ubuntu
admin users = ubuntu
inherit permissions = Yes

```But, the problem is, when I try to access the ubuntu-server from a W7 machine I always get a box asking for a username and password.

Am I missing something?

thanks

You've setup samba to require password. Take a look at:
```
https://help.ubuntu.com/community/Samba
```

You should find what you're looking for!

---

### Post by Morbius1 on 2011-10-06
Windows will send ( without your knowledge ) the actual Windows user's local login user name and password when it browses the network. When it reaches the Samba server it tries to authenticate those credentials against it's database because you have a line missing from your smb.conf file.

Add a line to the [global] section of smb.conf:
```
map to guest = Bad User
```Save the file and then restart samba:
```
sudo service smbd restart
```Without that line Samba defaults to: " map to guest = Never " which looks exactly like what it's doing.

---

### Post by elite1967 on 2011-10-06
> **Morbius1 said:**
> Windows will send ( without your knowledge ) the actual Windows user's local login user name and password when it browses the network. When it reaches the Samba server it tries to authenticate those credentials against it's database because you have a line missing from your smb.conf file.

Add a line to the [global] section of smb.conf:
```
map to guest = Bad User
```Save the file and then restart samba:
```
sudo service smbd restart
```Without that line Samba defaults to: " map to guest = Never " which looks exactly like what it's doing.

Thanks a lot Morbius1,
I did what you suggested and it worked.

But, now I have the following problems:
1- the server name does not show up in the network neighborhood: only if I enter the ip address it shows the shared directories
2- when I try to access a **_protected_** shared directory , it takes ages before prompting for the username and password.

Any ideas?

---

### Post by Morbius1 on 2011-10-06
From the server itself post the output of the following command:
```
smbtree
```
All it does is list the shares available on the network including it's own and may give some error messages if something is wrong.

---

### Post by elite1967 on 2011-10-06
> **Morbius1 said:**
> From the server itself post the output of the following command:
```
smbtree
```
All it does is list the shares available on the network including it's own and may give some error messages if something is wrong.

Hi,
thanks for your reply.

The command does not output anything:

```

ubuntu@ubuntu-server:~$ sudo smbtree
[sudo] password for ubuntu:
Enter root's password:
ubuntu@ubuntu-server:~$

ubuntu@ubuntu-server:~$ smbtree
Enter ubuntu's password:
ubuntu@ubuntu-server:~$

```

What am I doing wrong?

---

### Post by Morbius1 on 2011-10-06
Because you are running Ubuntu Server which I clearly ignored. Install smbclient:
```
sudo apt-get install smbclient
```
And try it again

---

### Post by elite1967 on 2011-10-06
> **Morbius1 said:**
> Because you are running Ubuntu Server which I clearly ignored. Install smbclient:
```
sudo apt-get install smbclient
```
And try it again

Hi Morbius1,
just installed the new package, restarted smbd service and tried again.

No luck.
Same result.

I'm using a static IP address, if this can help.

Funny thing is that whichever password I type for user "ubuntu" and user "root" the result is the same, I mean there is no message saying 'password error...' if I type a wrong password.

(BTW what is the root's password under ubuntu server? I have used the setup password for the setup user, that for me is 'ubuntu').

---

### Post by Morbius1 on 2011-10-06
I don't think I've ever come across a situation where smbtree returned nothing. Well, unless your firewall is blocking all samba communication. 

Turn it off and see if it runs. If it doesn't I'm at a loss at the moment.

Unfortunately I have to shut down for the day so maybe someone on 2nd shift can find the problem.

Your smb.conf deviates from the default configuration quite a bit ( at least from a default Ubuntu desktop perspective ) but I'm not sure it's enough to cause the problems you are seeing.

---

### Post by elite1967 on 2011-10-07
> **Morbius1 said:**
> I don't think I've ever come across a situation where smbtree returned nothing. Well, unless your firewall is blocking all samba communication. 

Turn it off and see if it runs. If it doesn't I'm at a loss at the moment.

Unfortunately I have to shut down for the day so maybe someone on 2nd shift can find the problem.

Your smb.conf deviates from the default configuration quite a bit ( at least from a default Ubuntu desktop perspective ) but I'm not sure it's enough to cause the problems you are seeing.

I don't use a firewall.
And consider that I am sending the command from the terminal of the server itself...

I have created the smb.conf from scratch.
It could be that there is something wrong.

I hope someone could point me to the right direction.

regards,

---

### Post by Morbius1 on 2011-10-07
Edit your smb.conf and put a # sign in front of the following line so that it looks like this:
>  [COLOR=Blue]**#**[/COLOR]interfaces = 192.168.1.1/8Then restart samba:
```
sudo service smbd restart
```

---

### Post by Morbius1 on 2011-10-07
There is one more thing and that's your Public share: [Music Read-Only] .

If all your clients are Linux systems that might work but if you have any Windows clients in the lan it will not because you have removed the mechanism for them to be converted to the guest account. So add the following to the [global] section of smb.conf:
```
map to guest = Bad User
```
And then restart samba again.

---

### Post by elite1967 on 2011-10-07
> **Morbius1 said:**
> Edit your smb.conf and put a # sign in front of the following line so that it looks like this:
Then restart samba:
```
sudo service smbd restart
```

> **Morbius1 said:**
> There is one more thing and that's your Public share: [Music Read-Only] .

If all your clients are Linux systems that might work but if you have any Windows clients in the lan it will not because you have removed the mechanism for them to be converted to the guest account. So add the following to the [global] section of smb.conf:
```
map to guest = Bad User
```
And then restart samba again.

OK. Excellent tips!
Did added the *map to guest = Bad User* and removed the line *#interfaces = 192.168.1.1/8*

So here the result:
```
ubuntu@ubuntu-server:~$ smbtree
Enter ubuntu's password:
MSHOME
        \\STEFANO-PC
ubuntu@ubuntu-server:~$
```

The open issues are:
1) \\UBUNTU-SERVER does not appear in the Network Neighbourhood
2) the ubuntu shares do not appear in the smbtree command (above)
3) When I access the protected shares (using the IP address), it takes a lot of time for the dialog box to appear asking for the credentials.

Almost there.
Really: thanks a lot!

---

### Post by Morbius1 on 2011-10-07
> 1) \\UBUNTU-SERVER does not appear in the Network Neighbourhood
2) the ubuntu shares do not appear in the smbtree command (above)
Check to see if nmbd is running:
```
sudo service nmbd status
```
If it's not running start it:
```
sudo service nmbd start
```

---

### Post by elite1967 on 2011-10-07
> **Morbius1 said:**
> Check to see if nmbd is running:
```
sudo service nmbd status
```
If it's not running start it:
```
sudo service nmbd start
```

Excellent: nmbd wasn't running!
solved items 1 e 2:
```
ubuntu@ubuntu-server:~$ smbtree
Enter ubuntu's password:
MSHOME
        \\UBUNTU-SERVER                 Samba 3.4.7
                \\UBUNTU-SERVER\IPC$            IPC Service (Samba 3.4.7)
                \\UBUNTU-SERVER\Stefano Server  Private dir stefano
                \\UBUNTU-SERVER\2TBb Full Access        2TB (B) Full Access
                \\UBUNTU-SERVER\2TBa Full Access        2TB (A) Full Access
                \\UBUNTU-SERVER\Music Read-Only Music Read-Only
        \\STEFANO-PC
ubuntu@ubuntu-server:~$

```

Any idea why it takes so long to display the login credentials?

Thanks again.

---

### Post by Morbius1 on 2011-10-07
> Any idea why it takes so long to display the login credentials?That I do not know. If I had to guess I would suspect it's this:
> smb passwd file = /etc/samba/smbpasswdHave you set up your own password file instead of using the default?

The corresponding lines in a default samba configuration looks like this:
> obey pam restrictions = Yes
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes*BTW, There's a copy of the original default smb.conf here: /usr/share/samba/smb.conf*. *It does have one odd mistake in it in that it sets "encrypt passwords" to no.*

In fact your smb.conf looks so far removed from the default I have to ask you if you are using SWAT. That would explain a lot.

---

### Post by elite1967 on 2011-10-07
> **Morbius1 said:**
> That I do not know. If I had to guess I would suspect it's this:
Have you set up your own password file instead of using the default?

The corresponding lines in a default samba configuration looks like this:
*BTW, There's a copy of the original default smb.conf here: /usr/share/samba/smb.conf*. *It does have one odd mistake in it in that it sets "encrypt passwords" to no.*

In fact your smb.conf looks so far removed from the default I have to ask you if you are using SWAT. That would explain a lot.

Hi,
thanks for replying.

I changed my customized file with the original one and the delay times are the same.
Never mind, it only occurs the first time I connect.

So for me this thread is closed and SOLVED.

Thanks again for your precious help.

---

