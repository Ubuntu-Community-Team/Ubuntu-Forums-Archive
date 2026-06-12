---
title: "Homenetwork Linux Ubuntu 10.10 / Windows XP SP2"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by ewickly on 2012-01-02
So.
My Dad loves Ubuntu, but I have a hard time understanding why it does or doesn't do certain things. I'm not saying windows is perfect, it's just what I understand. And even that's marginal some days.
So, like the title says, I'm trying to network Ubuntu 10.10 with Windows XP SP2.
My Dad has his system set up so I should be able to access it, and I have mine set up so he should be able to access it, yet we still can't get across to each others systems.
What are some basics I should cover? Is there any tricks we haven't tried yet?
Sharing on Windows is very simple to me. And I would assume that Ubuntu can access windows no problem considering how 'awesome' my Dad says it is. And I don't doubt it. I just don't understand it. Whenever I try to access the shared folder my Dad set up it says something along the lines of "You might not have permissions to view this folder, check with Admin blahblahblah." When I try to access my system from my Dads I get "Unable to mount location: failed to retrieve share list from server."
I for one don't know how to make my system any more accessible to Him, and my Dad tried setting up every possible "Let everyone on network access folder" way to get it to work. We have failed. May I ask for help?

---

### Post by spiky001 on 2012-01-02
How are you trying to connect to each other? are they connected can you ping, have a look at samba shares. Have you allowed sharing on the windows box Ubuntu should be able to see that in nautilus network something something , I havn't got windows on at moment

---

### Post by ewickly on 2012-01-02
Oh yeah. I am using Samba to try and connect them. Windows doesn't have any extra software helping it, just the basic stuff you get when you install windows.
We have a home network set up. I connect to it, and am able to access all the other windows machines. I can see what the Linux machines share, I just don't have permission to access them.

---

### Post by spiky001 on 2012-01-02
How is the connection made through a router, have you set the windows to allow sharing, linux to windows is normally easy it,s the other way round that causes problems

---

### Post by ewickly on 2012-01-02
Yes. I am using a router. Netgear.

---

### Post by fdrake on 2012-01-02
> 
I can see what the Linux machines share, I just don't have permission to access them. On the Linux machine.

so you mean you can see the file from windows but you cannot open/play the file?

---

### Post by N00b-un-2 on 2012-01-02
> **ewickly said:**
> And I don't doubt it. I just don't understand it. Whenever I try to access the shared folder my Dad set up it says something along the lines of "You might not have permissions to view this folder, check with Admin blahblahblah." When I try to access my system from my Dads I get "Unable to mount location: failed to retrieve share list from server."

Two issues here and both have to do with your /etc/samba/smb.conf file.  The "Failed to retrieve share list from server" error has to do with resolve order.  The resolve order line should read like this 

```
name resolve order = bcast host lmhosts wins
```

The "You might not have permissions to view this folder" error is just that, a permissions issue.  First, the permissions of the folder need to be set properly, and then the smb.conf file has to be configured accordingly.  There is no one right way to set up Samba, but there are a million and one ways that are wrong.  I wrote a simply how to for setting up samba on XFCE but it applies to Nautilus as well.

[http://ubuntuforums.org/showthread.php?t=1891590]("http://ubuntuforums.org/showthread.php?t=1891590")

Hope it helps.

---

### Post by ewickly on 2012-01-02
Hmm... I am trying to follow your guide, but I'm not able to get into my SMB.conf file. I can OPEN it, but it won't let me edit it. And when I try to open it in terminal, it says I don't have permission. This is really annoying...

---

### Post by ewickly on 2012-01-02
> **fdrake said:**
> so you mean you can see the file from windows but you cannot open/play the file?

Yes. I can see them, I just can't access them.

---

### Post by N00b-un-2 on 2012-01-02
it's a system file, duh.  You need root permission to edit smb.conf.

hit alt+f2 and type
```
gksu gedit /etc/samba/smb.conf
```

then type in your password.

---

### Post by ewickly on 2012-01-02
Ok so, I did all that. And it made it so when I try and access to the windows computer, it asks for a username and password, so I put in ubuntu's username and password and it then asks again. No success. I tried getting into Ubuntu from windows and no change there.
Was there some information in that tutorial that I needed to change to my computer's setup? I kept my computer's workgroup as it should be, but other than that, I didn't know if there was anything I needed to change.

---

### Post by fdrake on 2012-01-02
> **ewickly said:**
> Ok so, I did all that. And it made it so when I try and access to the windows computer, it asks for a username and password, so I put in ubuntu's username and password and it then asks again. No success. I tried getting into Ubuntu from windows and no change there.
Was there some information in that tutorial that I needed to change to my computer's setup? I kept my computer's workgroup as it should be, but other than that, I didn't know if there was anything I needed to change.

if you are trying to access FROM ubuntu the windows machine you need to insert the username + password of the windows user not the ubuntu user!

also when to make you files accessible from windows you need to change their permissions to 755, so, for example.
```
sudo chmod -R 755 /home/user/my_shared_dir
```
be careful do not change the ownership of config/system files, the above command will change the permissions of all the files/subdir inside that folder so think twice!

---

### Post by ewickly on 2012-01-03
I did what you said, but there was no change.

---

### Post by ewickly on 2012-01-07
Seriously people? Is there no fix for me? Hows come no one has continued to reply? Am I on my own in trying to fix this?

---

### Post by Morbius1 on 2012-01-07
On whatever machine that has Ubuntu installed please post the output of the following commands:
```
hostname
``````
smbtree
``````
testparm -s
``````
net usershare info --long
```

---

### Post by N00b-un-2 on 2012-01-09
It would seem that your samba is installed and correctly configured.  At this point it seems to be a permissions issue on both sides of the network.
When using the Ubuntu computer, when you try to open the shares from the Windows XP machine, you need to put in the username + password for the Windows machine.  Also, check to make sure that the share permissions are set correctly on the Windows machine.

From the Windows XP computer, if it asks you for a username and password, put in the username and password for the Ubuntu machine.  You will also need to double check that permissions for the directory you are trying to access are set properly (chmod 755 -R).  You also need to make sure that the share is configured properly in your smb.conf.  Using the example that I posted in my guide will indeed work.

If you still have issues, please post your /etc/samba/smb.conf here and we'll take a look at what is going on here.

---

### Post by Morbius1 on 2012-01-09
We don't actually know if Samba is set up and configured correctly becasue we don't have the output of the testparm and net usershare commands. As for passing user names and passwords to and fro we don't know if any of these shares require it. They could be Guest shares for all we know. 

> You will also need to double check that permissions for the directory you are trying to access are set properly (chmod 755 -R)2 things wrong with that:

* If he wants write access to anyone other than himself that wont work.

* A chmod 755 -R made every directory and every file executable. That's good for directories but not so good for files. Use the Jedi way instead:
```
chmod -R a+rwX,go-w 
```Directories will be executable - files will not unless they were executable to begin with. If it's a writeable share then it would be:
```
chmod -R a+rwX
```But we're really getting ahead of ourselves without some information which is why I asked for it.

---

### Post by ewickly on 2012-01-09
Thank you for the replies! I thought everyone had given up on me for some strange reason pertaining to my router.

```
g3@g3:~$ hostname
g3
g3@g3:~$ smbtree
Enter g3's password: 
7DSLAN
	\\WINBOX         		WINBOX
	\\MOM            		Tamra's Computer
		\\MOM\shared         	
		\\MOM\mom            	
		\\MOM\SharedDocs     	
		\\MOM\print$         	Printer Drivers
		\\MOM\IPC$           	Remote IPC
		\\MOM\Documents and Settings	
	\\G3             		g3 server (Samba, Ubuntu)
		\\G3\Epson-WorkForce-615	Epson WorkForce 615
		\\G3\print$         	Printer Drivers
		\\G3\Data Server    	
		\\G3\IPC$           	IPC Service (g3 server (Samba, Ubuntu))
g3@g3:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Data Server]"
Processing section "[data server]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = 7DSLAN
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
	name resolve order = bcast host lmhosts wins
	dns proxy = No
	wins support = Yes
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

[Data Server]
	comment = data server
	path = /media/Data Server
	read only = No
	create mask = 0755
	guest ok = Yes
g3@g3:~$ net usershare info --long
[data server]
path=/media/Data Server
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

And just while I'm at it, I attatched the conf file as a txt file.

---

### Post by Morbius1 on 2012-01-09
Well, that's unfortunate because everything looks textbook correct.

You may or may not be able to actually access the "Data Server" share ( and please try to avoid putting spaces in things in Linux :wink: )  because of permissions so post the permissions of the whole media directory please:
```
ls -al /media
```
[COLOR=Blue]**EDIT**[/COLOR]: Um ... is /media/Data Server sitting on an NTFS or FAT32 partition by any chance?

---

### Post by Morbius1 on 2012-01-09
I've got to shut down for the day so after all the talk about guessing I'm going to take a guess:

You created 2 samba shares using 2 different methods. This one in particular was created from Nautilus:
> [data server]
path=/media/Data Server
comment=
usershare_acl=Everyone:F,
guest_ok=yThe thing with Nautilus is that it changes permissions to 777 automatically - unless it's an NTFS or fat32 partition then it can't. So if it is NTFS or FAT32 one way around this is to add a parameter to smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to the local login user name on that box and place it in the [global] section - right under the workgroup line.*[/COLOR]

Then restart samba and wait about 5 minutes before trying to access the share:
> sudo service smbd restart[COLOR=Blue]**BTW**[/COLOR] It's generally not a good idea to create samba shares from 2 different methods so I would get rid of either the nautilus share by going into Nautilus and just unshare it.

Or get rid of the classic share:
> [Data Server]
    comment = data server
    path = /media/Data Server
    read only = No
    create mask = 0755
    guest ok = YesThat share wouldn't have worked the way you wanted it anyway. If the remote user added a file it would end up with ownership = "nobody". The local login user would be able to read the file but not edit the file.

---

### Post by N00b-un-2 on 2012-01-10
+1 on not using spaces in Linux.  just use dashes or underscores where necessary.  Other than that, your smb.conf does appear to be correct.  The only thing I can figure at this point as was already stated was that using the Nautilus share configuration vice doing things the right/hard way with the smb.conf

---

### Post by Morbius1 on 2012-01-10
Nautilus-share or what Samba calls Usershare is not a better or worse way it's simply another way. It does have some advantages to the "right/hard" way:

* Nautilus-share automatically changes permissions on the target folder.
* It mimics the way you do a Simple Share in WinXP and beyond.
* You can change and / or modify share definitions without restarting the smbd daemon
* If all you're sharing is something you own then you don't have to become root.
* It ( usershare itself ) available to anyone regardless of DE since it's in samba by default.

It does not however have the flexibility or configurability of the Classic Samba Share so it really depends on what you want the share to do. 

In this particular example the OP would either have to add "force user" to the global section of smb.conf, keep the nautilus-share, and remove the classic-share. Or, remove the nautilus-share and fix the Classic-share:
> [Data Server]
    comment = data server
    path = /media/Data Server
    [COLOR=Blue][COLOR=Black]read only = No[/COLOR]
    #create mask = 0755[/COLOR]
[COLOR=Blue]force user = morbius[/COLOR]
guest ok = Yes Even if this share was pointing to a linux folder and not an NTFS folder he would have to do something like a "force user" or the server user would not be able to write to any of the files added by the client user.

---

### Post by ewickly on 2012-01-17
> **Morbius1 said:**
> Well, that's unfortunate because everything looks textbook correct.

You may or may not be able to actually access the "Data Server" share ( and please try to avoid putting spaces in things in Linux :wink: )  because of permissions so post the permissions of the whole media directory please:
```
ls -al /media
```
[COLOR=Blue]**EDIT**[/COLOR]: Um ... is /media/Data Server sitting on an NTFS or FAT32 partition by any chance?

```
total 50
drwxr-xr-x  6 root root  4096 2012-01-14 20:29 .
drwxr-xr-x 23 root root  4096 2011-03-01 05:15 ..
drwx------  3 g3   g3     152 2012-01-13 08:54 ****
drwx------  1 g3   g3    8192 2011-10-03 02:18 Data 500
drwx------  1 g3   g3   24576 2011-03-13 21:54 Data Server
drwx------  1 g3   g3    8192 2010-12-30 01:09 System
```

Also, I've added everything you've told me.

So! It now lets me into Data Server from windows... Now windows won't let Linux access it? It never has thus far, but I'm just saying, but problem still isn't completely resolved. When I try to log into the windows folder from linux, it comes up with a username and password prompt. There is no password on the windows machine. So I put in the windows username, and then no password. And it just comes up again, like it didn't do anything.

---

### Post by Morbius1 on 2012-01-17
Did you set up a WinXP "Simple Share"?

My Computer > Tools > Folder Options > Use simple file sharing

EDIT: Here's a resource you might want to look at:
[http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)

---

