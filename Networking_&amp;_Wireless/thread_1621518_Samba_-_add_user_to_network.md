---
title: "Samba - add user to network"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by demonboy on 2010-11-14
Hi,

I've spent the last four hours trawling through the net looking for a solution to this. I know it's out there, I just can't find it. Please could someone put me out my misery?

In Ubuntu 10.10 I have just created a windows network in Samba. I can see the network and my computer. 

The computer next to me can also connect to this Windows network. He can also see the network and he can also see me, but...

How does he join the network so that I can see him?

I know it's a simple answer but I just can't seem to add him. Any help appreciated.

---

### Post by puppywhacker on 2010-11-14
Samba users can be (=configurable) different than the linux users. So samba keeps them in it's own user table file. They can be sync'ed to the linux users as well, or come from a different source.

to add a password use a command like
```
smbpasswd -a theuser
```

you could also change the default configuration "security = user" to "security = public" to disable user management but that is of course not secure at all.

---

### Post by Zimmer on 2010-11-14
Have you added SAMBA users?

Q: How to add/edit/delete network users?
This will tell you to do the following...
#

sudo smbpasswd -a system_username
sudo gedit /etc/samba/smbusers

# Insert the following line into the new file

system_username = "network username"

I will translate this bit for you (cos it confused me at the start)
If your Ubuntu user name is called 'scribe' 
Then in the Terminal type:
sudo smbpassword -a scribe (and it will prompt you for a password, which does not have to be the same as your Ubuntu user password, and confirmation)
then
sudo gedit /etc/samba/smbusers
...and type the following into the new file..
scribe = "network username"
save the file
You now have a Samba user called scribe..
You need then to add other users to the file...
eg
 anotheruser = "network username"

(hope this is still the case,  I stopped messing with this stuff in 2005 !)

---

### Post by Morbius1 on 2010-11-14
Your using the term "join the network" and user in such a way that your getting these rather odd responses. Looking at your other post it appears you are using Userhshares to create a share on your Ubuntu machine so it looks like you are more in a peer-to-peer samba situation.

Why not post the output of the following commands so we can see how you are set up and it may be clearer what you are trying to do:
```
net usershare info --long
``````
testparm -s
``````
smbtree
```

---

### Post by demonboy on 2010-11-16
Hi, my apologies for not replying sooner. 

Here are the results:

> 
jamie@jamie-NC10:~$ net usershare info --long
[ubuntudocs]
path=/home/jamie/Documents/UbuntuDocs
comment=
usershare_acl=Everyone:R,JAMIE-NC10\jamie:F,
guest_ok=n



> 
jamie@jamie-NC10:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[UbuntuDocs]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = DADANDJAMIE
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = avahi
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
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[UbuntuDocs]
    comment = Jamie's Ubuntu Help Files
    path = /home/jamie/Documents/UbuntuDocs
jamie@jamie-NC10:~$ 



> 
jamie@jamie-NC10:~$ smbtree
Enter jamie's password: 
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
jamie@jamie-NC10:~$ ^C
jamie@jamie-NC10:~$ 



I think the clue is in that last one...

---

### Post by Morbius1 on 2010-11-16
Let's start with the easy one first:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Change the following line by adding a # sign in front of it so that it looks like this:
```
     #security = SHARE
```
Save the file and restart samba:
```
sudo service smbd restart
```

---

### Post by demonboy on 2010-11-16
OK, done that, but I think I am missing something very basic.

I have created a Windows network and I want to add the computer next to me. How do I do that in Samba? 

Going to Preferences and Add User I do not see the other person's Unix name so I can't add them.

What I'm struggling to get my head around is that he can see the other (proper) windows network. In fact we both can see that proper windows network. But he can't see my samba network and I can't see him as a user...

---

### Post by Morbius1 on 2010-11-16
I don't know what you mean by " I created a windows network" There is no windows network and there is no Samba network. There is simply the network.
>  Going to Preferences and Add User I do not see the other person's Unix name so I can't add them.Are you talking about the remote user that you cannot see? You have to Add him and then set a samba password for him.

As for not seeing the other machines what does the output of smbtree say now.

---

### Post by demonboy on 2010-11-16
OK, I'll admit there is a bit of RTFM going on here but...

When I go to add user it gives a drop-down list of Unix names, from avahi to bin to kernoops to nobody etc etc. In fact before avahi there is a massive blank space. Strange. So how do I assign a Unix name? It looks like it is forcing me to assign a pre-defined name from a strange list. That's the first thing I don't understand.

---

### Post by Morbius1 on 2010-11-16
I don't know where you are. There is no dropdown list in add user.

System > Administration > Users and Groups > Add

You'll be presented with a "Create a New User" dialog box asking you 
for the name of the new user.

---

### Post by Morbius1 on 2010-11-16
I finally figured out where you are. You're in

System > Administration > Samba > Preferences > Samba Users > Add

Creating a samba user is a two step process. First you have to create a local user on the server itself and then you need to add the samba password to that user.

So Add the local user as I outlined in my previous post and then you will see him in System > Admin > Samba

---

### Post by demonboy on 2010-11-16
Aha, then you've answered my question. I was in Samba trying to create a new user, not Admin! Now I'm starting to get somewhere. Thanks.

---

### Post by demonboy on 2010-11-16
OK, scrap that last comment. I'm getting confused as hell here. Now that I have added a user the person on the other machine can no longer see my machine at all.

Can anyone point me to a step-by-step guide, specifically for 10.10, on how to configure a network using Samba?

And whilst I am here perhaps someone could let me know whether I am getting muddled up between sharing a folder and a network? When I first set the two machines up and shared folders I thought they could see each others shared folders. Now that I have set up a network they can't. I'm also struggling to get my head around users created on one machine and whether they correlate to the user with the same name on the other. So generally, I'm really confused!

---

### Post by Morbius1 on 2010-11-16
What is the output of smbtree please.

---

### Post by demonboy on 2010-11-16
smbtree

> 
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED


I don't think the problem is with my machine, however, I think it is the other one. When I share a folder on the other machine, that machine doesn't appear in my list.

When I created my network I gave it a name via my machine and that network, to which I belong, appears in my Windows networks. What I haven't done is get that other machine to join my network.

---

