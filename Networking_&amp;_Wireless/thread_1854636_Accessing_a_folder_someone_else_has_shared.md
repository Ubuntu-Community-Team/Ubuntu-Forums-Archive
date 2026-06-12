---
title: "Accessing a folder someone else has shared"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by lesliek on 2011-10-04
I'm on a network with three computers, two running Ubuntu 10.04 and one running Windows XP.

On one of the Ubuntu computers, I installed the two services required to share files in Windows and Linux. I then ran shares-admin and made a folder available to the other two computers.

On the computer running Windows XP, I then went to Network Places (My Network Places? I can't remember the precise name.). There was the shared folder and I was able to open it and the files in it.

However, I can't figure out where on the second Ubuntu computer (on which I also installed the two necessary services) to find the shared folder. The file-sharing document on the Ubuntu site tells you how to make folders available, but not how to access them when someone else has shared them with you.

I'd be grateful for the necessary information.

Thanks for reading this.

Leslie

---

### Post by capscrew on 2011-10-05
> **lesliek said:**
> I'm on a network with three computers, two running Ubuntu 10.04 and one running Windows XP.

On one of the Ubuntu computers, I installed the two services required to share files in Windows and Linux. I then ran shares-admin and made a folder available to the other two computers.

On the computer running Windows XP, I then went to Network Places (My Network Places? I can't remember the precise name.). There was the shared folder and I was able to open it and the files in it.

However, I can't figure out where on the second Ubuntu computer (on which I also installed the two necessary services) to find the shared folder. The file-sharing document on the Ubuntu site tells you how to make folders available, but not how to access them when someone else has shared them with you.

I'd be grateful for the necessary information.

Thanks for reading this.

Leslie

I assume you mean "how to access them when someone else has shared them with **[to]** you.

On a Gnome system go to Places>>Network and you should see the shares listed.  If not then you need to do some more work.  To see the shares from the terminal (Applications>Accessories>>Terminal) you can try this command```
smbtree
```

---

### Post by lesliek on 2011-10-05
Thanks for your reply, capscrew.

Yes, I did mean how to access a folder when someone else has shared it TO me.

I did the things you suggested.

When I went to Places, Network, I saw (among others) an icon named "Ubuntu". When I clicked on it, only a folder called "print$" appeared.

When I used the command "smbtree", I got the results shown in the image below.

UBUNTU is the computer from which I'm trying to share. ACER-... is the Windows computer to which I've successfully shared from UBUNTU. LESLIE-LAPTOP is the Ubuntu computer to which I'm so far unable to share from UBUNTU.

I see that WORKGROUP\\UBUNTU shows more branches than I got by using Places, Network.

I remember also that, on the Windows computer, I had an icon for UBUNTU in My Network Places and, when I clicked on it, I was able to access successfully the folder that I'd been attempting to share.

If any of the above suggests something that I should be doing on LESLIE-LAPTOP to be able to access the shared folder from UBUNTU that I can access on the Windows computer, I'd be very grateful for the suggestion.

Thanks again for your reply.

Leslie

---

### Post by capscrew on 2011-10-05
> **lesliek said:**
> Thanks for your reply, capscrew.

Yes, I did mean how to access a folder when someone else has shared it TO me.

The easiest way to describe the various computers/devices and their functions is to follow these simple conventions.
```

# This can be a computer or router or wireless AP, etc. on the network
[COLOR="DarkOrange"]**Host**[/COLOR] = Any device with an OS that you can communicate with.

# Supplies Files, DHCP services, SSH services, etc
[COLOR="Green"]**Server**[/COLOR] = any host that provides resources

# Asks for files, DHCP IP address, DNS resolution, etc. 
[COLOR="Blue"]Client[/COLOR] = Any host that requests resources

```

With the above in mind and noting that any host can be both a server and a client at the same time, we have the this:

1. A host named UBUNTU functioning as a server.  The printer driver share is installed by default on all Samba server installs. This host also has a printer attached -- Photosmart....  This host could also function as a client.

2. A host named LESLIE-LAPTOP functioning as a server.  The printer driver share is installed by default on all Samba server installs. This host seems to be configured to share 2 printers -- Cannon... and Lexmark...  This is a client that could also be a server.

3. A host named ACER-F......... I believe this host has a name that is more than 15 Characters.  This appears to be the reason it can't connect.  
> 
 
I did the things you suggested.

When I went to Places, Network, I saw (among others) an icon named "Ubuntu". When I clicked on it, only a folder called "print$" appeared.

When I used the command "smbtree", I got the results shown in the image below.

UBUNTU is the computer from which I'm trying to share. ACER-... is the Windows computer to which I've successfully shared from UBUNTU. LESLIE-LAPTOP is the Ubuntu computer to which I'm so far unable to share from UBUNTU.

I see that WORKGROUP\\UBUNTU shows more branches than I got by using Places, Network.

I remember also that, on the Windows computer, I had an icon for UBUNTU in My Network Places and, when I clicked on it, I was able to access successfully the folder that I'd been attempting to share.

If any of the above suggests something that I should be doing on LESLIE-LAPTOP to be able to access the shared folder from UBUNTU that I can access on the Windows computer, I'd be very grateful for the suggestion.

Thanks again for your reply.

Leslie

I think at this point I need more information.  I don't see any file shares on the host UBUNTU.  Since I can see the printer share, this means that sharing works (The server UBUNTU is running).  The host LESLIE-LAPTOP seems to be able to see UBUNTU as you successfully ran the command *smbtree* from that host.

Let's concentrate on getting the file shares working on UBUNTU (see the need for simple descriptive names).  From the command line of UBUNTU run ```
net usershare info --long
```

This will show any shares you created using the GUI interface (GNOME).

From that same host (UBUNTU) please post the contents of the */etc/samba/smb.conf* file.  This is how Samba is configured traditionally.

I hope I haven't confused you too much.  If you have problems with this let me know.

---

### Post by lesliek on 2011-10-07
I closed my browser by mistake when I'd almost finished a lengthy post. AAARGH! So to summarise ...

First, thank you so much for taking the time to help me over this.

I can now share a folder from each Linux computer to each other Linux computer and to the Windows computer. I haven't tried to share from the Windows computer to the two Linux computers, wanting to get the Linux side fixed first, if I can.

(I think, but am not sure, that, when I unsuccessfully used shares-admin at first, its default was that I should use the NFS service, rather than the Samba one, and I didn't change that. In any event, when I kept playing around and changed the service, things finally worked.)

However, I find that there are some files in the shared folder I can't open on the shared-to computer. I get a message saying that access is denied.

When I look at the end of the smb.conf file on UBUNTU, it says:

[Turner_letter]
path = /home/leslie/Desktop/Turner_letter
available = yes
browsable = yes
public = yes
writable = yes

The end of the smb.conf file on LESLIE-LAPTOP is similar, but obviously showing a different folder name.

In my ignorance, I see nothing there that would stop any files in the relevant folder from being accessed. Is there some kind of permissions problem? Can I fix it by editing smb.conf on both Linux computers?

Thanks again for your replies,

Leslie

---

### Post by capscrew on 2011-10-07
> **lesliek said:**
> I closed my browser by mistake when I'd almost finished a lengthy post. AAARGH! So to summarise ...

Don't ya just hate that!  I don't know how many BRILLIANT ideas I've had go... *poof!* for just that very reason. > 

First, thank you so much for taking the time to help me over this.

You're very welcome.> 

I can now share a folder from each Linux computer to each other Linux computer and to the Windows computer. I haven't tried to share from the Windows computer to the two Linux computers, wanting to get the Linux side fixed first, if I can.
The windows hosts will, er...just work!  By default they are setup to broadcast their presence on the LAN.> 

(I think, but am not sure, that, when I unsuccessfully used shares-admin at first, its default was that I should use the NFS service, rather than the Samba one, and I didn't change that. In any event, when I kept playing around and changed the service, things finally worked.)

I hate GUI interfaces.  After a while you will find that it is faster and you have more control by editing the smb.conf file.  :D  Also you learn how Samba works.  I have annotated your share configuration in red below.  All of the configuration information is located on the web [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html").> 

However, I find that there are some files in the shared folder I can't open on the shared-to computer. I get a message saying that access is denied.

When I look at the end of the smb.conf file on UBUNTU, it says:

```
[Turner_letter]
path = /home/leslie/Desktop/Turner_letter
available = yes  **[COLOR="Red"]#This is the default -- you do not need to declare it[/COLOR]**
browsable = yes **[COLOR="Red"]# this also is the default (no hides the share)[/COLOR]**
public = yes **[COLOR="Red"]This is a synonym for the more popular: guest ok ( the default is *guest ok = no*([/COLOR]**
writable = yes
```

The end of the smb.conf file on LESLIE-LAPTOP is similar, but obviously showing a different folder name.

In my ignorance, I see nothing there that would stop any files in the relevant folder from being accessed. Is there some kind of permissions problem? Can I fix it by editing smb.conf on both Linux computers?

Thanks again for your replies,

Leslie
Think of Samba as a service that *augments *The basic Linux permissions.  If you have been _authenticated_ by Samba you still need the file permissions (_authorization_) for read write or execute (rwx).

Here are the permissions on one of my shares```
drwsrwsr-t 14 cap    smbusers 4.0K 2011-09-22 23:20 .
drwxrwsr-t  8 cap    smbusers 4.0K 2011-04-15 16:36 ..
-rw-rw-r-t  1 rhonda smbusers 159K 2011-09-22 09:28 GeneralMills2011SepB.pdf
-rw-rw-r-t  1 rhonda smbusers 409K 2011-09-22 09:18 GeneralMills2011Sep.pdf
-rw-rw-r--  1 cap    smbusers  15K 2011-09-21 09:17 Resume
drwxrwsr-x  2 cap    smbusers 4.0K 2011-05-19 10:47 Scan

```

I'm pretty sure we will have to make some adjustments to the file (and folder) permissions.
From your home directory of the host UBUNTU (using the terminal) post the output of this command  ```
ls -al /home/leslie/Desktop/Turner_letter
```

Then post the output of this command```
testparm -s 
```
Then I can ask you some questions and we can make the mods you need.

---

### Post by lesliek on 2011-10-17
Well, if I was once unable to open on LESLIE-LAPTOP any file in the folder Turner_letter, shared by UBUNTU, I no longer have that problem, though I've tried to duplicate it numerous times now. Maybe my problem arose in connection with some different files I was trying to share from UBUNTU to LESLIE-LAPTOP or maybe it arose in connection with some files I was trying to share from LESLIE-LAPTOP to UBUNTU. In any event, your clear explanation about Samba augmenting the regular permissions makes me understand what to do in future--I'll check the permissions of any file I want to share between UBUNTU and LESLIE-LAPTOP and change them beforehand if necessary.

I don't know whether you're still willing to have a look at the output of testparm -s, given that I've been so slow in replying, but in case you are, here it is:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Turner_letter]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Turner_letter]
	path = /home/leslie/Desktop/Turner_letter
	read only = No
	guest ok = Yes

Thanks again for all your help,

Leslie

---

### Post by capscrew on 2011-10-17
> **lesliek said:**
> Well, if I was once unable to open on LESLIE-LAPTOP any file in the folder Turner_letter, shared by UBUNTU, I no longer have that problem, though I've tried to duplicate it numerous times now. Maybe my problem arose in connection with some different files I was trying to share from UBUNTU to LESLIE-LAPTOP or maybe it arose in connection with some files I was trying to share from LESLIE-LAPTOP to UBUNTU. In any event, your clear explanation about Samba augmenting the regular permissions makes me understand what to do in future--I'll check the permissions of any file I want to share between UBUNTU and LESLIE-LAPTOP and change them beforehand if necessary.

I don't know whether you're still willing to have a look at the output of testparm -s, given that I've been so slow in replying, but in case you are, here it is:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Turner_letter]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Turner_letter]
	path = /home/leslie/Desktop/Turner_letter
	read only = No
	guest ok = Yes

Thanks again for all your help,

Leslie

Everything looks fine with the share definitions.  One thought to ponder:  Permissions of files and folders can change when moving or copying.  This is because you are creating a new file or folder at the destination and then erasing the old one in the case of a move.  The new file or folder always uses the destination user and the system permissions.

---

### Post by lesliek on 2011-10-18
Thanks so much for all your help capscrew.

Your explanations were so clear!

Leslie

---

