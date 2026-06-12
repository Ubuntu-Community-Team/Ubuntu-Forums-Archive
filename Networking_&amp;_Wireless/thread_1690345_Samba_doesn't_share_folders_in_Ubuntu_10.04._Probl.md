---
title: "Samba doesn't share folders in Ubuntu 10.04. Problems with the password."
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by vedovatti on 2011-02-18
Hi there,

I have been looking in the forums but I found no solution for my problem.

I already configured Samba and I am sharing folders, printers, etc. (Samba, authentification mode = user, guest account = nobody, share the folder give access to them, enable the permission to access, write, etc.) and seems to be working well.

I am trying to connect a Windows to my shared folder in Ubuntu. **The only problem is that Samba rejects it and doesn't ask for the password.** It just drop the users (from Windows and Ubuntu systems) that try to access to my folders.

So when it do in a Terminal 

sudo smbpasswd -a USERNAME

and I type no password, then it works they everybody can access to those shared but when I type any password then it comes back to the same problem that Samba never asks for passwords and rejects the users.

So the solution would be just give no password to share the files, but the other problem is that every time I restart the user session (restarting the computer, logging out, etc.) it just comes back to the same problem that **Samba drops the users and doesn't ask for the password**. Seems that every time I restart the system just forgets that I set no password.

Another thing is that when I set authentication mode = share. Then nothing works. No password, no access just is possible to see it.

Any ideas from the community?

Thanks.

---

### Post by Morbius1 on 2011-02-18
See if this describes your situation: [http://ubuntuforums.org/showthread.php?t=1672373](http://ubuntuforums.org/showthread.php?t=1672373)

The problem is one package that is new in the default install : libpam-smbpass

Libpam-smbpass is a solution in search of a problem ;)

If that's not the problem then post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```

---

### Post by Stephann on 2011-02-18
Kindly post your /etc/samba/smb.conf (feel free to change any personally identifiable information to 'generic' information, so long as it's consistent.)

---

### Post by vedovatti on 2011-02-19
Hi guys,

Thank you very much for your fast replies. I really appreciate the help.

So I checked the other thread and didn't the solution. But today I have been just trying all the solutions I found. (maybe I shouldn't have done it).

So now the facts are more ore less the same. Everybody can see the folders I share (and doesn't ask for passwords to browser, they can see it), but it doesn't ask for the password. Thus, I have at home 3 computers: 1 Ubuntu (mine), 2 Windows. And the 2 Windows share with no problem. Now, the problem still the same just that now the no password doen't work on the windows computers.

Now something that I didn't realise up today is that when I try to access to the shared folder of windows it just doesn't ask me for password or anything just: Unable to mount location. While between the other 2 windows PC they ask for the passwords to access. So it is a problem of my configuration. Not the other PCs.

So from what hire my configuration of samba:

```
carlos@Linux-Ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
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
	read only = No

[Public]
	comment = Shared
	path = /home/carlos/Public
	read only = No

```
```
carlos@Linux-Ubuntu:~$ net usershare info --long
[public]
path=/home/carlos/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

Another funny thing is that I have a Windows XP in Virtual Box on my computer and when I try to access to the shared files in Ubuntu it works! it can see my shared folder and then double-click and ask for password and then access.

I still have the libpam-smbpass, I reinstalled as it didn't help. Should I still remove it?

Any recomendations?

Thanks again

---

### Post by Morbius1 on 2011-02-19
One problem. There are two different ways to use Samba to share folders: Usershare ( via nauilus-share ) and Classic-share ( via smb.conf ). You are using both methods on the same target. For the sake of your own sanity you might want to get rid of one or the other.

Although it doesn't look like it you have configured both shares to allow guest access ( in the case of smb.conf share it's because you have "guest ok = yes in the global section ) so the remote client should never be asking for a username or password.

So the only thing stopping the remote client from writing to that share is the linux permissions on that share. Nautilus-share would have automatically modified the permissions to 777 but in case it didn't for some reason you can check it:
```
ls -dl /home/carlos/Public
```It should come back with:
> drwxrwxrwx

---

### Post by vedovatti on 2011-02-21
Ok, so I had another frustrating day. I didn't have any success. I tried again all the different solutions I found on other threads. I even tried to purge the whole samba and reinstall, but still the same.

So, I uninstall nautilus-shares (including config. files) and libpam-smbpass.

So I type:ls -dl /home/carlos/Public
```

drwxrwxrwx 3 carlos carlos 4096 2011-02-17 11:30 /home/carlos/Public

```

But still the same problem. Seems permissions are ok. I checked already the Firestater (firewall). So I have to say that I activate in >System>Preferences>Personal file sharing, the "Share public files on Network" with password. And I have installed apache2.2-bin and libapache2-mod-dnssd.

Any more ideas? I have to say that I am working in Ubuntu since 6.06 and in all this time with every upgrade (now I am on 10.04) it has solved all the problems I had, except this with Samba. A pity.

I will keep trying. Thanks

---

### Post by Morbius1 on 2011-02-21
> >System>Preferences>Personal file sharing, the "Share public  files on Network" with password. And I have installed apache2.2-bin and  libapache2-mod-dnssd.Personal File Sharing ( PFS ) is not Samba. It's a baby apache file server that announces it's share ( it's only designed to share one folder - "Public" ) using avahi. So now you have PFS and Samba sharing the same folder. Windows is going to have a hard time connecting to the PFS share since it requires something to be installed on Windows to make it work.

You need to state what your specific requirements are:

Do you only want to share /home/carlos/Public ?
Do you want to allow anyone to access it ?
Do you only want those with the right username and password to access it?

---

### Post by vedovatti on 2011-02-21
Thanks again for the fast reply.

Now I set no password and tried to access from a Windows computer to my "Public" folder and now doesn't give any access to anyone. The only one can access now is my Windows XP on the Virtual Box. All this experimenting I have been doing... I guess.

What I would like to do is that to have my "Public" shared with the other two windows computers and that is requested a password to have access to it.

> 
Do you only want to share /home/carlos/Public ?
Do you want to allow anyone to access it ?
Do you only want those with the right username and password to access it?


The answers are yes/no/yes.

About the PFS I think I put it so my mobile could have access through Bluetooth to this files (in fact, it can access to "Public" folder). You think I should uninstall it?

Anyway I read on another thread that on the configuration of Firestarter on /etc/firestarter/inbound/setup should add another line like that (just the second one):

```

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

```

In order to stop rejecting sub-mask (255.255.255.0) IP connections under a router.

But still rejecting the other users with or without password set up. By the way the smb.conf still the same.

---

### Post by Morbius1 on 2011-02-21
I'm sorry but I'm still confused.

If you only want the share to be accessible by authenticated users then your share definition is wrong. It should look like this:
> [Public]
    comment = Shared
    path = /home/carlos/Public
    read only = No
[COLOR=Blue]    guest ok = no[/COLOR]You will need to create a local login user and then add him to the smb password database.

EDIT: As far a Firestarter is concerned I'd disable it until this is resolved. Firestarter is no longer maintained to my knowledge.

---

### Post by vedovatti on 2011-02-22
Finally, a lot of work has given me results. Is solved and works beautifully. I have to thank Morbius1, you really helped me. So I will publish my solution completely so it may help somebody on the future.

The problem with Samba was not just one, there were 5 problems. Actually the Thread was just about the password but it was solved in the first suggestion I got so I will explain it step by step.

1) The problem that every log-on the system forgets the password established by 
```
sudo smbpasswd -a USERNAME
```
Solution: Uninstall libpam-smbpass. I don't know what is needed for but in my case it just didn't.
(actually, the thread was already solved here)

2) The conflict of modifying the samba settings through the "nautilus-share" and the smb.conf (or Samba GUI, I use the graphical interface). So I uninstall the nautilus-share, and set the Samba GUI like: Workgroup=workgroup, security=user, password encrypted=yes, guest account=nobody.

3) The conflict between "Share public files on Network(SFN)" (apache2.2-bin and libapache2-mod-dnssd) and Samba. So SFN uses /home/user/Public folder to share it on the network and bluetooth as well. So I created another folder /home/user/Shared and give the permission to other to modify it. And I added through the Samba GUI.

4) The Firewall (firewall) was blocking the Samba connection. I know that is not maintained anymore but is a good GUI to manage the ports (if you know how to do it). So, I thought I set it up correct but just half. So the settings are to open the Firestarter in the tab policy allow the Samba(SMB) service on ports 137-139 445, to edit preferences and in advanced options>Broadcast traffic to unmark the option: Block Broadcast from internal network. But I found out (or at least is what I think) that when other computer try to communicate with mine they don't use the Samba ports they do other so to solve the problem I added to /etc/firestarter/inbound/setup should add another line like that (just add the second one line):
```

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

[COLOR="Red"]# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT[/COLOR]

```
And it worked. Not it allowed to the other computer to connect and sent back the petitions for password to have access to their shared folders. I think that is the reason I didn't get requests for passwords and was rejected.

5) the configuration of the Shared folder in Samba. So Morbious1 point out that I have to change the guest ok=no, so now I have the folder:
```

[Shared]
	comment = shared
	path = /home/carlos/Shared
	read only = No
	[COLOR="Red"]guest ok = No[/COLOR]

``` 

After all this I can happily share my files through Samba and Apache (SFN, that Windows can see but not access) and they ask me for passwords and get asked for passwords as well.

Thanks again. After 5 years I finally solved, but basically I was my fault for installing a lot of (unnecessary) stuff. Greetings from New Zealand

---

