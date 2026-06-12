---
title: "Can't connect Ubuntu to a Mac"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by DallasTxSoftwareMan on 2012-06-08
I have a new Mac Lion and a new install of Ubuntu 12.04.  Ubuntu is running under VMware on the Mac.  I want to be able to get to some of the shared directories on the Mac.  I also have WindowsXP running under VMware on the Mac and have sucessfuly set it up to see shared folders on the Mac.  Because WindowsXP and Ubuntu are both running in VMware, I assume VMware is handling the networking between them and the Mac.[/SIZE][/FONT][/COLOR]
 
The Mac has file sharing turned on for both AFP and SMB.  The Mac accounts I am using are setup for sharing only.  I have these Users defined to share the Mac directories.[/SIZE][/FONT][/COLOR]
 
On the Ubuntu side, I am using the file manage Nautilus to try to connect.  Using Browse Network, I can see my Windows XP virtual machine and 2 connections to my Mac.  One of these Mac connections seems to be for AFP and one for SMB.  I haven't installed any kind of networking software on the Mac or Ubuntu system.[/SIZE][/FONT][/COLOR]
 
In order to connect I do File/Connect to Server.  I put in:[/SIZE][/FONT][/COLOR]

IP address of the Mac[/SIZE][/FONT][/COLOR]
Type:        Windows share[/SIZE][/FONT][/COLOR]
Share:     blank[/SIZE][/FONT][/COLOR]
Folder:    / (the default)[/SIZE][/FONT][/COLOR]
Domain Name: HOME (I think this is the same thing as the workgroup)[/SIZE][/FONT][/COLOR]
User Name:    The user name I created on the Mac that is for sharing only.[/SIZE][/FONT][/COLOR]
Password:    THe password.[/SIZE][/FONT][/COLOR]

After clicking Connect, I get a message: &#8220;Please verify your user details.&#8221; in the Connect to Server dialog box.[/SIZE][/FONT][/COLOR]
 
If I try doing the below in a terminal window I get:[/SIZE][/FONT][/COLOR]
nautilus [smb://IPAddressofMac]("smb://IPAddressofMac/")[/SIZE][/FONT][/COLOR]
It brings up a similar dialog box and I get a Password required for &#8230; message.[/SIZE][/FONT][/COLOR]

---

### Post by wyliecoyoteuk on 2012-06-08
you may need to specify the full username, as in nameofmac\username

e.g.mac1\fred

---

### Post by DallasTxSoftwareMan on 2012-06-08
> **wyliecoyoteuk said:**
> you may need to specify the full username, as in nameofmac\username

e.g.mac1\fred

Tried various combinations of doing that and it didn't work.

---

### Post by wyliecoyoteuk on 2012-06-09
Other issues may include:

spaces, odd characters (e.g. hyphens or spurious slashes in the foldername (yes, macs can have slashes in file names!)underscores are usually better)
names are Case Sensitive, domain or workgroup names should really be UPPERCASE.

---

### Post by DallasTxSoftwareMan on 2012-06-09
> **wyliecoyoteuk said:**
> Other issues may include:

spaces, odd characters (e.g. hyphens or spurious slashes in the foldername (yes, macs can have slashes in file names!)underscores are usually better)
names are Case Sensitive, domain or workgroup names should really be UPPERCASE.

None of that is a problem here.  Is there a log on the Mac or Ubuntu that will tell me what the problem is?

I noticed my original post had some formatting codes in it.  What I input is:

Server: IP address of the Mac
Type:        Windows share
Share:     (I leave this blank)
Folder:    / (the default)
Domain Name: HOME (I think this is the same thing as the workgroup)
User Name:    The user name I created on the Mac that is for sharing only.
Password:    The password.

---

### Post by wyliecoyoteuk on 2012-06-09
Also, I think you need to enter the sharename (as in the broadcast name of the shared folder), at the moment you are leaving that blank.

Ubuntu defaults to MSHOME as the workgroup/domain name, not sure what macs do.

---

### Post by DallasTxSoftwareMan on 2012-06-09
Thanks for the help [wyliecoyoteuk]("http://ubuntuforums.org/member.php?u=553677").  I had rebooted before but decided to try it again and that fixed the problem.  I'm not sure, but it could be that the connect having once failed, gets in a state where you have to reboot to clear it.

---

### Post by wyliecoyoteuk on 2012-06-10
Windows sharing (SAMBA on Linux and Mac) only refreshes network settings every 15 minutes, so that may have something to do with it too

---

