---
title: "Peer to peer file sharing - Samba"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by Shellbak3 on 2012-12-14
I've been trying to get Samba running for peer to peer file sharing among 4 computers, all but one running Ubuntu 11.10 and the other Scientific Linux 6.

I've downloaded & installed (apt-get) and tweaked using suggestions from forums and web articles to the point where I am now just attempting to get 2 Ubuntu machines to share folders and files:  they don't.  I have two folders on each machine that I want to share /home/public and /home/imager/var/jars.  They folders have permissions for all to read, write, and execute, the all belong, as do the users, to the Workgroup workgroup and both machines use the same /etc/smb.conf file.  

The machines are all physically attached to the same router and use DHCP.

Here's the output from testparm -s:
```
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

[public]
	path = /home/public
	read only = No
	guest ok = Yes

[jars]
	path = /home/imager/var/jars
	read only = No
	guest ok = Yes

```
I'm new to LINUX

---

### Post by Morbius1 on 2012-12-14
> I am now just attempting to get 2 Ubuntu machines to share folders and files:  they don'tI don't know what "they don't" means.

One machine can't see the Ubuntu machine?
Then post the output of this command from your ubuntu machine:
```
smbtree
```One machine can see the ubuntu machine but can't access the shares?
Then post the output of these commands:
```
ls -dl /home/public
``````
ls -al /home/imager/var
```

---

### Post by Shellbak3 on 2012-12-14
Thanks, I'm a bit frustrated ...

Here's the output of smbtree from machine "blue":
```
WORKGROUP
	\\BLUE           		blue server (Samba, Ubuntu)
		\\BLUE\applications   	
		\\BLUE\IPC$           	IPC Service (blue server (Samba, Ubuntu))
		\\BLUE\jars           	
		\\BLUE\public         	

```
Here is the output of ls -dl /home/public
```
drwxrwxrwx 2 programmer workgroup 4096 2012-12-13 09:34 /home/public

```
and here is the last, the output of ls -al /home/imager/var
```
drwxrwxrwx  3 imager root      4096 2012-11-26 10:23 .
drwxr-xr-x 19 imager imager    4096 2012-12-12 15:21 ..
drwxrwxrwx  2 imager workgroup 4096 2012-12-14 08:45 jars

```

Blue can't see the other machine I'm working with at this time. 
The other machine didn't start smbd when I rebooted but with smbd running it doesn't see any machines including itself.

---

### Post by Morbius1 on 2012-12-14
If the other machine didn't start smbd it may not have stared the name server either:
```
sudo service nmbd restart
```After that smbtree from blue may list it.

If you have done anything on the other machine's firewall you might want to disable it just to see if it's getting in the way.

---

### Post by dannyboy79 on 2012-12-14
i don't see workgroup defined in your smb.conf file.

---

### Post by Morbius1 on 2012-12-14
Remember this is the output of testparm. If you specify workgroup = WORKGROUP it won't show up in testparm since that is the default samba value. The default samba settings aren’t in smb.conf only overrides or additions.

Besides, it doesn't matter what the workgroup is unless he has these machines in different subnets. Smbtree should show every workgroup and within every workgroup every host - just like Nautilus would.

---

### Post by Shellbak3 on 2012-12-14
smbd and nmbd were running on both machines.

Now the other machine "hpnotebook" sees this one "blue" and I can create files in the two folders.  Good!  

But this is what I get when I rerun smbtree on blue:

```
WORKGROUP
	\\HPNOTEBOOK     		hpnotebook server (Samba, Ubuntu)
cli_start_connection: failed to connect to HPNOTEBOOK<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
	\\BLUE           		blue server (Samba, Ubuntu)
		\\BLUE\applications   	
		\\BLUE\IPC$           	IPC Service (blue server (Samba, Ubuntu))
		\\BLUE\jars           	
		\\BLUE\public         	

```

---

### Post by Morbius1 on 2012-12-14
On both blue and the other machine you are going to have to edit smb.conf directly as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line - ironically right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```Save smb.conf and restart samba on both machines:
```
sudo service smbd restart
```Then pray [-o<

Note: after starting smbd on both machines it may take a few minutes for things to settle down so ...

---

### Post by Shellbak3 on 2012-12-15
> **Morbius1 said:**
> On both blue and the other machine you are going to have to edit smb.conf directly as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line - ironically right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```Save smb.conf and restart samba on both machines:
```
sudo service smbd restart
```Then pray [-o<

Note: after starting smbd on both machines it may take a few minutes for things to settle down so ...

It appears to have worked - mostly.  All three machines have identical smb.conf files and after rebooting all machines "hpnotebook" and "orange" see all three machines.  "blue" sees itself and "orange" but before I rebooted it saw "hpnotebook".  For sure it's slow. Hmm.

Next to see if I can cajole "maroon" which runs Scientific Linux (derived from Red Hat) to join.

Thanks

---

### Post by Morbius1 on 2012-12-15
> "blue" sees itself and "orange" but before I rebooted it saw "hpnotebook".  For sure it's slow. Hmm.hpnotebook seems to be a reoccurring problem for some reason. If this persists there are other ways to do this:

** Use your router to assign static ip addresses to all the clients so you don't have to browse to them any more. You can issue a:
```
nautilus smb://192.168.0.100
```Then bookmark the darn thing.

** If static ip addresses are not possible then you can use zeroconf ( avahi ) to find these hosts. Avahi can find samba hosts very quickly but everyone has to be running avahi and you need to set up an avahi service config file ( 9 line config file - identical on every host ) on every host for this to work.

[COLOR=Blue]**Edit**[/COLOR]: Actually, all of your Ubuntu machines should have the avahi-daemon already running so although you cannot use avahi to "browse" to find the samba share you should be able to connect to the machines by an mDNS qualified host name. Try this:
```
 nautilus smb://hpnotebook.local
```And please don't ask me about anything related to RedHat. It's been years but they used to do strange things with samba over there and I'd just as soon not start drinking heavily again.

---

### Post by JRV on 2012-12-15
Try this:
```

nautilus sftp://USER@HOSTNAME/PATH/TO/FOLDER

```
You can substitute an IP address for HOSTNAME.

---

### Post by Morbius1 on 2012-12-15
> nautilus sftp://USER@HOSTNAME/PATH/TO/FOLDEREvery machine ( there are 4 at my count ) would have to create a "USER" corresponding to every other machine on the network.

And unless those users are dingbats all they have to do is:
> nautilus sftp://USER@HOSTNAMEAnd they would have at a minimum read access to the entire box.

---

### Post by Shellbak3 on 2012-12-15
The only reason I'm using a descendent of Red Hat is that a frame grabber I need to install was sold as support LINUX.  After we got it we found that what it really ment was either Red Hat or SUSE and only kernel 2.6.  To install the driver it must be compiled and then some kernel files edited and then the kernel recompiled.  The only reasonable Linux appears to be Scientific Linux so I'm trying that.  Before I attempt to install the driver etc. I want it working properly with any apps I need installed.  It's a pain because of so few users.  When I boot it doesn't boot to a log on screen and I only know that it is ready for log on is when the mouse works.  Then I press return and get a log in screen.  After the log in the user desktop doesn't appear.  One must wait for the cursor to stop being "busy" and then press META-P.   I don't get a warm fuzzy feeling about this...

Thanks for your help and the help of the posts following yours.  I'll keep on plugging on Monday.

---

### Post by dannyboy79 on 2012-12-15
> **Shellbak3 said:**
>  The only reasonable Linux appears to be Ubuntu Linux so I'm trying that.
I fixed it for you. LOL

---

### Post by Shellbak3 on 2012-12-17
Thanks to you all.

After checking all the shared folders and, in Nautilus, un-sharing them it all works!  Perhaps the recalcitrant attitude of hpnotebook moderated over the weekend. :popcorn:

---

