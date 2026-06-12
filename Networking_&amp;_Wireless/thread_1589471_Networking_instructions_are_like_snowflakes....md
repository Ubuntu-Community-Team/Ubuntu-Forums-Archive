---
title: "Networking instructions are like snowflakes..."
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by hipnerd on 2010-10-06
...no two are alike.

So I recently purchased a new quad-core PC to replace my aging Athlon system. Since we're so close to release, I installed the 10.10 RC.

I am attempting to network this machine with my wife's Windows XP system for the purposes of file and printer sharing. This appears to be impossible.

I had this working on my old Ubuntu PC somehow. I remember it being a giant pain in the butt there as well, but I forget what I did.

On the new box, I joined the same workgroup as my wife's PC and I can see it and her shares under "Places -> Network." However I cannot see my PC, shares or printer on my PC or more importantly hers.

There are built-in tools in the Ubuntu GUI that say things like "sharing." I assume they are strictly ornamental, as they serve no useful purpose that I can discern. 

Although there is no "official" docs, I have found dozens of tutorials and tips on how to configure smb.conf. Many of them directly contradict each other. None have worked. After trying 2-3 tips, smb.conf is no longer trustworthy and I have to replace it with a fresh copy and start over.

This is the most annoying aspect of Ubuntu by far. I know that I could get this working with two Windows PCs in a matter of a minute or two. 

Any help out there?

---

### Post by Morbius1 on 2010-10-06
> On the new box, I joined the same workgroup as my wife's PC and I can  see it and her shares under "Places -> Network." However I cannot see  my PC, shares or printer on my PC or more importantly hers.Please explain. Can you or can you not see her (WinXP) shares?

If you can't see your own shares then there may be a couple of initial reasons:

(1) nmbd is not running.
Check to see if it's running:
```
sudo service nmbd status
```If it's not then start it:
```
sudo service nmbd start
```(2) It's possible that your smb.conf is at this point completely discombobulated or your using both samba sharing methods at the same time and they conflict with one another. The output of the following commands will tell us what method you are using and how you are using it:
```
net usershare info
``````
testparm -s
```(3) Firewall's getting in the way. If you run the following command it will tell you what ports are open:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it twice: Once with your own ip address and again with WinXP's.
Look for the following ports to see if they are all open:
> 139 445 137 138Note: you may need to install nmap first:
```
sudo apt-get install nmap
```

---

### Post by capscrew on 2010-10-06
> **hipnerd said:**
> ...

Although there is no "official" docs, I have found dozens of tutorials and tips on how to configure smb.conf. Many of them directly contradict each other. None have worked. After trying 2-3 tips, smb.conf is no longer trustworthy and I have to replace it with a fresh copy and start over.
No documentation?  There is plenty of "official" documentation.  See [**_The Official Samba 3.5.x HOWTO and Reference Guide_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/") for up to date information.  For more information I would suggest checking out all the Documentation at the [**_Samba.org_**]("http://samba.org/samba/docs/") site. > 

This is the most annoying aspect of Ubuntu by far. I know that I could get this working with two Windows PCs in a matter of a minute or two. 

Any help out there?

How about [**_Samba By Example_**]("http://www.samba.org/samba/docs/man/Samba-Guide/") or maybe [**_Google?_**]("http://lmgtfy.com/?q=samba+docs")

---

### Post by hipnerd on 2010-10-06
> **Morbius1 said:**
> Please explain. Can you or can you not see her (WinXP) shares?

I can see hers. I cannot see my own when browsing the Windows network on either machine.

> 
(1) nmbd is not running.
Check to see if it's running:

It's running.

> It's possible that your smb.conf is at this point completely discombobulated

I backed it up and replaced my junked up version with a clean copy a few times. I upgraded to 10.10 RC from 10.04 and it asked to overwrite smb.conf. I allowed that. It seemed to work, although it remembered my workgroup somehow.

> or your using both samba sharing methods at the same time and they conflict with one another. The output of the following commands will tell us what method you are using and how you are using it:
```
net usershare info
```

Output:

```
[shared]
path=/home/john/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

> ```
testparm -s
```

Output: 

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Shared]"
Processing section "[Shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = BIZNERDS
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
	name resolve order = lmhosts wins bcast host
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Shared]
	path = /home/john/Shared
	valid users = john
	read only = No

```



> (3) Firewall's getting in the way. If you run the following command it will tell you what ports are open:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it twice: Once with your own ip address and again with WinXP's.
Look for the following ports to see if they are all open:
Note: you may need to install nmap first:
```
sudo apt-get install nmap
```

Port 138 is not open on my Wife's PC. The rest are all open.

One other thing. I am currently using DHCP. I'm not enough of a networking guy to say if that makes any difference. But I thought I would mention it.

---

### Post by hipnerd on 2010-10-06
> **capscrew said:**
> No documentation?  There is plenty of "official" documentation.  See [**_The Official Samba 3.5.x HOWTO and Reference Guide_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/") for up to date information.  For more information I would suggest checking out all the Documentation at the [**_Samba.org_**]("http://samba.org/samba/docs/") site. 

I find the official SAMBA docs to be obtuse and unhelpful for average users who do not want to become network administrators. I think I'm not alone which is why there is such a proliferation of independent guides and HOWTOs.

I've used Ubuntu exclusively for 4-5 years now, but I am extremely jealous of the ease at which you can create simple peer-to-peer networks in Windows.

> How about [**_Samba By Example_**]("http://www.samba.org/samba/docs/man/Samba-Guide/") or maybe [**_Google?_**]("http://lmgtfy.com/?q=samba+docs")

As mentioned in the original post. I have already tried many HOWTOs that I pulled from Google. They aren't working for me.

Since Googling hasn't worked, I thought I'd try the official Ubuntu help forum for networking. That seemed very logical to me. 

Responding to a request for help with "look it up yourself" would seem counter to the purpose of this forum.

---

### Post by Morbius1 on 2010-10-06
***[1]*** Let's go after the easy one first. There are two completely different methods of using Samba to share folders. You are using both at the same time and their definitions conflict with one another.
This is a nautilus-share ( usershare ):
> [shared]
path=/home/john/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=yYou're allowing guest access and write permissions.

This is a Classic-share:
> [Shared]
    path = /home/john/Shared
    valid users = john
    read only = NoYou're allowing write access only to john.

If I were you I would get rid one one or the other. If you keep the classic share you will have to create a samba password for john. I like to keep things simple in the beginning and the nautilus-share is the simplest. But that's up to you.

***[2]*** Unfortunately that may not be enough to fix the problem that Ubuntu cannot see itself. What is the output of the following command:
```
smbtree
```It should list all the shares from everyone on the network including yours on the Ubuntu machine. It will also output error messages. Maybe it's something simple like your hostname being greater that 15 characters long.

---

### Post by hipnerd on 2010-10-06
> **Morbius1 said:**
>  Maybe it's something simple like your hostname being greater that 15 characters long.

Ding! Ding! Ding! We have a winner. All the trouble stemmed from this. A hostname that was 16 characters long.

Thank you.

---

### Post by Iowan on 2010-10-06
> **hipnerd said:**
> Ding! Ding! Ding! We have a winner. All the trouble stemmed from this. A hostname that was 16 characters long.

Thank you.
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

