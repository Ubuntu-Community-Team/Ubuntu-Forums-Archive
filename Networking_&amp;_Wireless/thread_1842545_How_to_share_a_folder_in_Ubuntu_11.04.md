---
title: "How to share a folder in Ubuntu 11.04"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by futralistic on 2011-09-11
I am extremely confused about what seems to be a very simple process to share a folder in Ubuntu 11.04.

Let me say I have searched Google, Youtube, and this forum to find a specific answer to my problem to no avail.

I am running Ubuntu 11.04 on my desktop and my laptop. I am trying to share a folder on my desktop with my laptop over my home network. 

I have created the folder and set it to be shared.I downloaded the files necessary and restarted my session. The folder icon shows the two arrows, but I cant for the life of me figure out how to access it on my laptop.

Any help on this would be greatly appreciated.

---

### Post by aura7 on 2011-09-11
Here is the Ubuntu help on sharing a folder

[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

---

### Post by cap10Ibraim on 2011-09-12
can your laptop ping your desktop if yes ( or vice versa ) and 
```
service smbd status
``` showed that samba is running you should see other machine in the Network folder

---

### Post by Morbius1 on 2011-09-12
> I have created the folder and set it to be shared.I downloaded the files  necessary and restarted my session. The folder icon shows the two  arrows, but I cant for the life of me figure out how to access it on my  laptop.That sounds like a Samba Usershare ( created from Nautilus ). Please post the output of the following command so we can see how that share is set up:
```
net usershare info --long
```You might want to post the output of this command just in case there is something wrong with the main samba config file:
```
testparm -s
```Finally, post the output of this command which should show you all the shares available on your lan including your own:
```
smbtree
```

---

### Post by futralistic on 2011-09-12
Before I post the output of the code let me say I just found out I can access the shared folder I created on my laptop(test)from my desk top but I can not access the shared folder on my desktop.

When I click on Places->Network->Windows Network->Workgroup on my laptop I get the message 'Opening "WORKGROUP".You can stop this operation by clicking cancel.' A few seconds later I get the message 'Unable to mount location Failed to retrieve share list from server'

The following is the output from my laptop.


matt@matt-Satellite-L35:~$ service smbd status
smbd start/running, process 582


matt@matt-Satellite-L35:~$ net usershare info --long
[test]
path=/home/matt/test
comment=
usershare_acl=Everyone:F,
guest_ok=n


matt@matt-Satellite-L35:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
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


matt@matt-Satellite-L35:~$ smbtree
Enter matt's password: 
WORKGROUP
	\\MATT-SATELLITE-		matt-Satellite-L35 server (Samba, Ubuntu)
		\\MATT-SATELLITE-\test           	
		\\MATT-SATELLITE-\IPC$           	IPC Service (matt-Satellite-L35 server (Samba, Ubuntu))
		\\MATT-SATELLITE-\print$         	Printer Drivers
	\\MATT-DESKTOP   		matt-desktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to MATT-DESKTOP<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

---

### Post by gennatolls on 2011-09-12
I am too stuck on the issue, I'm glad to see Morbius1 is here.
I just followed your post here [http://ubuntuforums.org/showthread.php?t=1501320](http://ubuntuforums.org/showthread.php?t=1501320) and successfully got my macbook able to view shared folders on my ubuntu desktop. Now I'm trying to share with an Ubuntu laptop. Can't wait to get it working.

---

### Post by Morbius1 on 2011-09-13
Let's go after the easy one first and see if that will fix things by itself:

> matt@[COLOR=Blue]**matt-Satellite-L35**[/COLOR]:~$ service smbd statusBy default samba will use the host name to broadcast it's presence on the network but it comes with rules. One of them is that it can only be 15 characters long and yours is 18. The easiest way to fix this is leave the host name alone and change the name samba will use to broadcast itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - right under the workgroup line:
```
netbios name = matt-Sat-L35
```[COLOR=Blue]*Doesn't have to be that exact name but keep it at or under 15 characters long.*[/COLOR]

Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Wait a few minutes ( seriously ) for the network to settle down ( restarting samba throws the network into chaos for a few minutes ) and then see if this change alone fixes things.

---

### Post by futralistic on 2011-09-13
I changed the name Samba uses as you instructed and it did seem to have an effect. Now when I click on Network I get a window that shows my desktop and my laptop with a server icon above them and a folder called Windows Network. Unfortunately when I click on the desktop icon or the Windows Network folder I get the same error messages as before. 

I don't know if this is out of the norm but when I edited smb.conf, saved, and closed it, the terminal gave this output.


(gedit:1836): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1836): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3A0H1V': No such file or directory

(gedit:1836): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1836): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.947L1V': No such file or directory

(gedit:1836): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
matt@matt-Satellite-L35:~$ gksu gedit /etc/samba/smb.conf

(gedit:1898): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BG0O1V': No such file or directory

(gedit:1898): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1898): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.04EE1V': No such file or directory

(gedit:1898): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1898): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.V0GI1V': No such file or directory

(gedit:1898): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by cnbiz850 on 2011-09-13
> **futralistic said:**
> matt@matt-Satellite-L35:~$ smbtree
Enter matt's password: 
... ...	

\\MATT-DESKTOP   		matt-desktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to MATT-DESKTOP<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

I just had a very similar problem and got it resolved.  I tried to ping the "matt-desktop" in my case and found that the address of the "matt-desktop" is not my local address (I use google's 8.8.8.8 as my primary dns server). So I added an entry for the "matt-desktop" in /etc/hosts, and the problem solved.

---

### Post by Morbius1 on 2011-09-14
@futralistic, If the error you're talking about is this one:
> \\MATT-DESKTOP matt-desktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to MATT-DESKTOP<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFULEdit smb.conf as root again and add another line - right under the "netbios name" line:
```
name resolve order = bcast host lmhosts wins
```Then save it and restart smbd again.

You can also do what cnbiz850 suggested but you'd need to have static ip addresses on MATT-DESKTOP for this to work or else the next time it boots it may have another ip address. If you did have static ip addresses you could also just bookmark it.

---

### Post by futralistic on 2011-09-14
Thanks so much for all of your help guys!
 
I will give that a try as soon as I get home.

---

### Post by futralistic on 2011-09-14
It looks like that fixed the issue. I can now access my shared folders.

I can't thank you enough!

---

