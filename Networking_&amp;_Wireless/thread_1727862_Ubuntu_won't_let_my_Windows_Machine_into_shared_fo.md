---
title: "Ubuntu won't let my Windows Machine into shared folders"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by eldonkr on 2011-04-13
I configured Samba so that this laptop running Maverick would show up on the network so I could share files between the two. When I view the network on the laptop the windows shares show up, and I can access them; but when I view the network on Windows is when the problems start.

I view the network in Windows and this laptop shows up, but every time I try to open the Public folder (only folder shared) it won't let me in. I get some sort of Windows error message about being unable to access the folder and how I might not have permission to access it, and then at the very bottom it says something like 'file path not found'.

I tried to change the permissions in the properties for my public folder but I every time I tried to change the settings in the access box it would reset it back to blank (-) immediately after I changed it.

I'm not sure what the issue could be. Prior to purchasing this new laptop I was running Karmic on my old laptop and the networking between the two machines worked flawlessly. I'm hoping someone on the forum can help me with this problem.

---

### Post by wjp.reg on 2011-04-13
You didn't mention it so...

Did you add a windows user to samba on the linux machine:

> sudo smbpasswd -a [username]

---

### Post by eldonkr on 2011-04-13
I didn't know that I had to do that. I don't remember having to do that on my last laptop, is it new? How do I go about doing that?

---

### Post by wjp.reg on 2011-04-13
Please refer to the Windows Networking chapter in the Ubuntu documentation for the details.  For user account setup refer to the SAMBA client setup section:

 [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/windows-networking.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/windows-networking.html")

---

### Post by wjp.reg on 2011-04-13
This video may also help explain windows networking using samba/ubuntu

[http://www.youtube.com/watch?v=VuxSjiSVoBU]("http://www.youtube.com/watch?v=VuxSjiSVoBU")

good luck

---

### Post by eldonkr on 2011-04-19
I'm not sure what's going on but it still isn't working. I can see the linux machine on the Windows network view but when I try to access it I get the following error message:

```

\\Viper\public is not accessible. You might not have the permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.

```

And when I go into the network view on the linux machine and try to access my the same shared folder it throws this one at me:

```

Unable to mount location. Failed to mount Windows Share.

```

I'm totally clueless as to what I should try next.

I'm not sure if I mentioned this yet, but every time I try to edit the permissions tab under the properties for my shared folder it immediately changes the access boxes back to blank.

Any ideas?

---

### Post by The Guv. on 2011-04-20
I'm glad it's not just me that's finding it hard to set up samba sharing.

I'm trying to share a folder 'Shared', can see it on the Windows 7 PCs but when I try to enter the folder 'Shared' I get:

'Windows cannot access \\192.168.1.101\Shared. Check the spelling of the name. Otherwise, there might be a problem with your network. To try to identify and resolve network problems, click Diagnose.'

I've got a standard Samba conf with the share added using Samba Server Configuration GUI.

I have added the user 'nobody' to the group sambashare and I have been playing around with all sorts of advice/guides for days and still haven't got anything to work!

---

### Post by eldonkr on 2011-04-20
What if I booted up my old laptop and pasted the text from the smb.conf on that box into the smb.conf file on my new laptop. Because I know the sharing was working on that old laptop.

---

### Post by Morbius1 on 2011-04-20
A "failed to mount" is usually a Linux permissions problem not a samba problem.

The entire path has to allow a guest to open the directory so 
/home and /home/your-user-name have to have permissions like drwxr-xr-x.

I'm assuming that the share is at /home/your-user-name/Public

---

### Post by eldonkr on 2011-04-20
Yes, but my problem is that it isn't letting me change the permissions for any of the folders I have tried to change them in. I go to properties and click on the permissions tab and every time I try to modify the access field it changes back to blank the exact second after I change it.

---

### Post by collisionystm on 2011-04-20
Is the folder you are sharing on an EXT4 file system? Or is it an external drive attached to your Ubuntu? You cant set permissions on other types of file systems. You can only set it on linux native.
 
Just right click on the folder, hit share and hit enable guest access. try that.

---

### Post by eldonkr on 2011-04-20
I'm trying to share the public folder on Maverick. I have clicked share and done all that stuff already and it hasn't helped.

---

### Post by eldonkr on 2011-04-20
I just went in and double checked and for some reason Ubuntu wants to pretend that I didn't tell it to share this folder when I originally set up samba and everything else so I clicked 'share' and 'enable guest access' and clicked 'create share'

And Ubuntu gave me the finger in the form of this error message in the sharing options window:

[IMG]http://img52.imageshack.us/img52/9889/sharingfail.png[/IMG]

What do?

---

### Post by Morbius1 on 2011-04-21
It would appear that you are not authorized to use usershare. Make sure you are a member of the correct group:
```
sudo gpasswd -a your_user_name sambashare
```Then logout and login again.
[COLOR=Blue]
EDIT:[/COLOR] Either that or it already is shared but by another user - root perhaps? The output of the "net userhsare" command below will tell us if it's already shared.

You may have other things discombobulated here so it the above doesn't fix it post the output of the following commands:
```
testparm -s
net usershare info --long
```

---

### Post by eldonkr on 2011-04-22
Edit: Ok, I was wrong. It's still not working.

---

### Post by eldonkr on 2011-04-24
Any ideas? I'm still getting

```

'net usershare' returned error 255: net usershare add: failed to add share public. Error was Operation not permitted

```

every time I try to create a share.

---

### Post by Morbius1 on 2011-04-24
If you type the following command do you get "[COLOR=Blue]122(sambashare)[/COLOR]" listed:
```
id
```

---

### Post by eldonkr on 2011-04-24
This is what the terminal spit out when I entered that command:

```


eldonkr@Viper:~$ id
uid=1000(eldonkr) gid=1000(eldonkr) groups=1000(eldonkr),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)

```

It would also appear that I never posted the results of a couple of things so here those are:

testparm -s
```

eldonkr@Viper:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = FLEETNET
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

```

And net usershare info --long:
```


eldonkr@Viper:~$ net usershare info --long
[public]
path=/home/eldonkr/Public
comment=
usershare_acl=Everyone:R,Unix User\root:F,
guest_ok=y

```

And here's my [smb.conf file]("http://paste.ubuntu.com/598447/") in case anybody wanted to take a look at that.

---

### Post by Morbius1 on 2011-04-24
You are getting the error because you already shared the folder as root. Root now owns the share definition file so you as a regular user can't edit it. You can either live with it as it is since it is after all still shared or remove the share as root and recreate it as eldonkr .

In a terminal remove the share definition:
```
 sudo net usershare delete public
```Or just do a gksu nautilus and remove the share as root.

Then try to share it as eldonkr again.

---

### Post by eldonkr on 2011-04-24
Did what you said, it let me make a share, it also let me modify the permissions tab in properties but it still won't let Windows into the public folder.

---

### Post by Morbius1 on 2011-04-24
Post the output of :
```
ls -dl /home/eldonkr/Public
```[COLOR=Blue]**EDIT: **On second thought just do the following:[/COLOR]
Edit smb.conf as root:
```
 gksu gedit /etc/samba/smb.conf
```Add the following to the [global] section of smb.conf:
```
force user = eldonkr
```Save smb.conf, exit gedit, and back in the terminal restart smb.conf:
```
sudo service smbd restart
```Wait a few minutes ( seriously ) until the network settles down and try to access the share from Windows again.

Sorry, I have to shut down for the day. If you have any problems I'm sure 2nd shift will see what I'm trying to do.

---

### Post by eldonkr on 2011-04-24
```

eldonkr@Viper:~$ ls -dl /home/eldonkr/Public
drwxr-xr-x 4 eldonkr eldonkr 4096 2011-04-22 18:03 /home/eldonkr/Public

```

There's that. I'll follow the rest of the instructions given and update you later.

---

### Post by eldonkr on 2011-04-27
Sorry that it took so long for me to respond. I kept forgetting to test accessing the share on my Windows computer and every time that I remembered I was on the other end of the house doing something else.

Anywho, I'm not exactly sure what did it; but I just checked and I am able to access the Public folder on my netbook on my Windows box. Thanks for all of the assistance guys.

Was the issue really as simple as adding 
```

force user = eldonkr

```

to my smb.conf file?

---

### Post by Morbius1 on 2011-04-28
To be honest I guessed. Your original description of the error:
> I get some sort of Windows error message about being unable to access  the folder and how I might not have permission to access it, and then at  the very bottom it says something like 'file path not found'.
This is not a Samba error it's a Linux permissions error. Either /home, /home/eldonkr, or /home/eldonkr/Public didn't have the right permissions for a remote user to get to the share. 

Instead of wasing time to determine which level of the path was at fault I simply forced the remote user to appear as you for that share. Since you can access the folder as eldonkr so can the remote user.

"force user" doesn't always work as desired depending on how sophisticated or complex the share is defined but in this case it's set up as a guest share so it was good enough.

---

### Post by eldonkr on 2011-04-28
Well thanks, it's been driving me nuts for a while now. I'd totally send you a cake or something, but that would be kind of weird.

---

