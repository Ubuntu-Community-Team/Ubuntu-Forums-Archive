---
title: "Puzzling problem accessing samba shares by name - Ubuntu 11.04"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by SanjayPethe on 2011-08-23
I have a puzzling problem trying to access samba shares by name using Nautilus in Ubuntu 11.04.

System Configuration:
ComputerA and ComputerB running Ubuntu 11.04 and Samba 3.5.8. ComputerA has defined shares User1A and User2A and ComputerB has defined shares User1B and User2B. Both are dual boot computers that also have Windows 7, and they have shares User1AW User2AW on ComputerA and User1BW and User2BW on ComputerB defined in Windows 7 as well.

An Iomega® 1TB StorCenter&#8482; ix2-200 Network Storage device running EMC LifeLine&#8482; described as "A fully-developed Linux operating environment and suite of applications". This device is named "IOMNAS" and has several shares defined on it e.g. User1NS, User2NS.

A Netgear WGT624 wireless router.

All devices get IP addresses via DHCP from the router. ComputerA and ComputerB connect via a wireless connection. The Iomega device is a wired connection. IP addresses for discussion are as follows:
ComputerA: 192.168.0.10
ComputerB: 192.168.0.11
IOMNAS:	   192.168.0.100
Netgear Router: 192.168.0.1


Problem: I can see all devices in my Network folder in Nautilus, but I cannot mount any shares on ComputerA and ComputerB by double clicking on their icons or selecting Open from the right click menu in Nautilus, nor can I access them using smbclient with the \\ComputerName format. I can however access all shares and have everything work just fine from Nautilus by specifying the location smb://IPAddress directly. I can also see all shares with smbclient if I use the \\IPAddress format.   - e.g.

=================================================================
>smbclient -L \\ComputerB
>Connection to ComputerB failed (Error NT_STATUS_BAD_NETWORK_NAME)

-----------------------------------------------------------------
>smbclient -L \\192.168.0.11
Domain=[MYNETWORK] OS=[Unix] Server=[Samba 3.5.8]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	User1B		Disk      
	User2B		Disk      
	IPC$            IPC       IPC Service (ComputerB server (Samba, Ubuntu))
Domain=[MYNETWORK] OS=[Unix] Server=[Samba 3.5.8]

	Server               Comment
	---------            -------
	ComputerB        ComputerB server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	MYNETWORK            
=================================================================

This works fine with the IOMNAS, and I can also mount the IOMNAS shares using Nautilus by double clicking on the IOMNAS icon.

=================================================================
>smbclient -L \\IOMNAS
Domain=[MYNETWORK] OS=[Unix] Server=[Samba 3.0.32]

	Sharename       Type      Comment
	---------       ----      -------
	User1NAS	 Disk      
	User1NAS         Disk      
	IPC$            IPC       IPC Service (Iomega StorCenter Device)
Domain=[MYNETWORK] OS=[Unix] Server=[Samba 3.0.32]

	Server               Comment
	---------            -------
	ComputerB        ComputerB server (Samba, Ubuntu)
	IOMNAS           Iomega StorCenter Device
	ComputerA        ComputerA server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	MYNETWORK            IOMNAS
=================================================================

When both machines are booted up in Windows 7, I am able to access the shares defined on each machine from the other by just double clicking on the machine icon.

ComputerA and ComputerB have identical smb.conf files as follows (for ComputerA):

=================================================================
[global]
	workgroup = MYNETWORK
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[User1A]
	path = /home/user1
	valid users = user1, user2
	read only = No

[User2A]
	path = /home/user2
	valid users = user1, user2
	read only = No
=================================================================

I am baffled by this - the fact that I can access shares by name on the IOMNAS and on both machines if they are booted in Windows 7 suggests to me that the problem has to do with the Samba configuration on ComputerA and ComputerB, but I can't think of what.

nmbd is running on both machines whenever samba is running.

I have tried adding the following lines to the smb.conf as well, but it has not helped:
    wins server = 192.168.0.1
    name resolve order = lmhosts host wins bcast


Any suggestions are appreciated - thanks in advance.

---

### Post by Morbius1 on 2011-08-23
Change this:
>      name resolve order = lmhosts host wins bcastTo this:
```
name resolve order = bcast lmhosts host wins
```Restart smbd and see if it works.

---

### Post by SanjayPethe on 2011-08-23
I tried that and get the same result. I also tried setting

netbios name = ComputerA

explicitly with no luck. However, I am not sure the netbios statement is being picked up because testparm did not show it in its output.

Thanks for the suggestion however Morbius1. Any other ideas anyone?

---

### Post by Morbius1 on 2011-08-24
Get rid of the following line in your smb.conf:
>      wins server = 192.168.0.1Once you do that restart samba ( sudo service smbd restart ) and post the output of the following command:
```
 smbtree
```But he fastest way out of your problem though is to assign each one of your machines a static ip address and then bookmark them in Nautilus instead of browsing to them in Nautilus.

Your router can do that - Netgear calls it "Address Reservation" - look in your manual. Each time ComputerA boots the router will assign it say ... 192.168.0.100. Each time ComputerB boots it will assign it ... 192.168.0.101, etc..

---

### Post by SanjayPethe on 2011-08-24
Morbius1,
I did not mention it in my last post, but I had already commented out the wins server line.
 
As for address reservation - I have already set that up in my router - have had it for years, but for some reason it does not always work. It seems to work 80% of the time, but not all the time - and I am not sure why. This would not be an issue at all if the machine names could be resolved.
 
If I was to go to static/fixed addresses as you recommend, I assume I have to enter the name-IP information in /etc/hosts and have the name resolve order have host as the first method?
 
I see this as a workaround, but I'm VERY surprised that Samba/Ubuntu does not have a way of dealing with this extremely common configuration. Most people I know will not want to be messing around with address reservation or host definition files when setting up their home networks.
 
Is it supposed to be this way or is something broken in the current suite of samba/nautilus tools? Has anyone got browsing by name in a true DHCP environment (no address reservation or static IP addresses) to work on their systems, and if so can you please post your smb.conf file?
 
Thanks for your time and comments.

---

### Post by Morbius1 on 2011-08-24
> As for address reservation - I have already set that up in my router -  have had it for years, but for some reason it does not always work. It  seems to work 80% of the time, but not all the time - and I am not sure  why.Never seen that happen but I've never used a netgear. See if there are any firmware updates.
> If I was to go to static/fixed addresses as you recommend, I assume I  have to enter the name-IP information in /etc/hosts and have the name  resolve order have host as the first method?You can put them in /etc/hosts but only if you are obsessed with browsing to the remote shares. If you run the following command:
```
nautilus smb://192.168.0.100/share-name
```Once Nautilus opens to that share you can bookmark it: Bookmark > Add Bookmark.
> I see this as a workaround, but I'm VERY surprised that Samba/Ubuntu  does not have a way of dealing with this extremely common configuration.  Most people I know will not want to be messing around with address  reservation or host definition files when setting up their home  networks.It does. It's called broadcast. It's the "bcast" in the "name resolve order" line in smb.conf. It's the only method that works out of the box in Samba and luckily it's also a default method in Windows. Now things can get in the way of broadcast doing it's thing:

* Firewall
* Machine names in excess of 15 characters in length.
* Permissions along the entire path to the shared directory have to allow access.
* The nmbd service needs to be running on all linux machines.
* Broadcast only works if all the lan members are in the same subnet - connected to the same router and getting their ip address from that router.
* Sometimes the router itself can get in the way.

---

### Post by SanjayPethe on 2011-08-24
Thanks.

I'll go ahead and do what you suggest for now, though it is maddening that its not working - and now has become more of a challenge :) to get it to work.

After reviewing the things you mention that can get in the way of bcast, only the "Permissions along the entire path ..." remains. There is no firewall on the Ubuntu machines (only in router), the machine names are < 15 chars, nmbd is running on both machines, and everything is on one subnet - there is only one router. If the router itself was getting in the way either because of the built in firewall or otherwise, it would not be possible to browse shares by name on the IOMNAS or when booted in Windows, since everything goes through the router.

What permissions do you need along the entire path - read for everyone or write for everyone or something else? Is there a reference you can point me to - don't want to dump my homework on you!

The one other thing I noticed in the smbclient dumps below is that the IOMNAS machine reports itself as the master of the MYNETWORK, wheras the other machines have this field blank:
=================================================
>smbclient -L \\IOMNAS
....

Workgroup Master
--------- -------
MYNETWORK IOMNAS


vs.

>smbclient -L \\192.168.0.11
....

Workgroup Master
--------- -------
MYNETWORK 
=================================================

I am not sure why this is the case or if it is significant.

For what its worth, here is the dump from smbtree you requested:

>smbtree
Enter User1's password: 
MYNETWORK
	\\COMPUTERA  		COMPUTERA server (Samba, Ubuntu)
		\\COMPUTERA\IPC$           	IPC Service (COMPUTERA server (Samba, Ubuntu))
		\\COMPUTERA\User1A   	
		\\COMPUTERA\User2A    	
	\\IOMNAS  		Iomega StorCenter Device
		\\IOMNAS\IPC$           	IPC Service (Iomega StorCenter Device)
		\\IOMNAS\User1NS         	
		\\IOMNAS\User2NS           	
	\\COMPUTERB  		COMPUTERB server (Samba, Ubuntu)
cli_start_connection: failed to connect to COMPUTERB<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME

Thanks for all your help.

---

### Post by Morbius1 on 2011-08-25
> What permissions do you need along the entire path - read for everyone  or write for everyone or something else? Is there a reference you can  point me to - don't want to dump my homework on you!Let's say I want to share the following directory : /home/morbius/Public

In order for the remote user to gain access then:
/home/morbius/Public must have permissions of 755
/home/morbius must have permissions of 755 or even just 711
/home must have permissions of 755 or 711

Each parent directory of the shared directory must have the execute bit enabled so that the "folder can be opened". Without it the share doesn't exist to the remote ( or other local ) user.

>  cli_start_connection: failed to connect to COMPUTERB<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAMEIt looks like yo still have a problem with this machine. Did you do the "name resolve order" edit on all your machines?

---

