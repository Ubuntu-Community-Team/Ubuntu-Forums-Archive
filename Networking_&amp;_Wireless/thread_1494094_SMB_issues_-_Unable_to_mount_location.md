---
title: "SMB issues - Unable to mount location"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by ahendric on 2010-05-26
Unable to mount location
Failed to retrieve share list from server

Good afternoon,

I have been having this issue with Ubuntu 9.x and now with 10.  I have a windows 7 box that I need to access the files on from an Ubuntu 10 box.  Linux to windows.  I have edited the smb.conf file to change the workgroup to match up with what my workgroup is called.  I have restarted/reinstalled smb, but still get the error.  I am fairly knowledgeable of Unix and Windows, but this has me scratching my head.

Any help or direction is greatly appreciated.

Thanks
Andy

---

### Post by Iowan on 2010-05-26
Unfortunately, that error message is about as generic as the old "Syntax error". [This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To touches on it- accessibility could mean undefined username, etc. Can you ping the machine  (name/address)? I'll look for better answer...

---

### Post by ahendric on 2010-05-26
Iowan,

That is about what I figured - syntax error, based on my google searches.  I can ping the ip address of the windows box I am trying to access.  

I am the person who set up the workgroup and windows box and ubuntu box, so I don't think I am typing the username/password incorrectly, but I don't even get that far, when I go to Places > Network and double click on the Windows Network icon, I get the error.  I have tried to connect using Places > Connect to Server and selecting windows share and using the admin username sends me into a loop for the password, but I get the same error when I cancel the password.

Thanks for the help.
Andrew

---

### Post by capscrew on 2010-05-26
> **ahendric said:**
> Iowan,

That is about what I figured - syntax error, based on my google searches.  I can ping the ip address of the windows box I am trying to access.

The error message "*Failed to retrieve share list from server*" has nothing to do with authentication.  It simply says that the server (Browse Master) can't find the names for the Samba resources you requested. Then it states why: *"Failed to retrieve share list from server"*.

Using the browse capability to the view the share requires that proper name services are set up.  This means NetBIOS over TCP  (broadcast) or WINS or DNS.  What are you using for name services ? >  

I am the person who set up the workgroup and windows box and ubuntu box, so I don't think I am typing the username/password incorrectly, but I don't even get that far, when I go to Places > Network and double click on the Windows Network icon, I get the error.  I have tried to connect using Places > Connect to Server and selecting windows share and using the admin username sends me into a loop for the password, but I get the same error when I cancel the password.

Thanks for the help.
Andrew

Before Samba can work as expected you must have a consistent name service scheme (i.e NetBIOS (broadcast) or WINS or DNS) in place.  you should be able to ping by name every host in the network.

---

### Post by tsucol11 on 2010-05-26
> **ahendric said:**
> Unable to mount location
Failed to retrieve share list from server

Good afternoon,

I have been having this issue with Ubuntu 9.x and now with 10.  I have a windows 7 box that I need to access the files on from an Ubuntu 10 box.  Linux to windows.  I have edited the smb.conf file to change the workgroup to match up with what my workgroup is called.  I have restarted/reinstalled smb, but still get the error.  I am fairly knowledgeable of Unix and Windows, but this has me scratching my head.

Any help or direction is greatly appreciated.

Thanks
Andy

On your Linux box are the folders you are trying to share NTFS or Ext? In my case I have a dual boot with most of my files on NTFS partitions. I share these partitions to my other window XP computers by adding the following line:

# Add to smb.conf (/etc/samba/smb.conf) under global settings.

#======================= Global Settings =======================

# [global]

# brian add line below to permit sharing NTFS file system
usershare owner only = False


As an after thought,did you set up shares for the folders /directories?

Brian

---

### Post by ahendric on 2010-05-27
Brian,

What I have is just the opposite, I want to access windows shares from my ubuntu box.  

Update to what I specified earlier, I can ping the ip address of the windows box, but when I ping the name of the windows box I get an unknown host.

The ip address is dynamic, how do I specify the name and ip in the hosts file for a dynamic ip?

Thanks,
Andy

---

### Post by ahendric on 2010-05-27
capscrew,

I didn't set up anything special on either box, basically plugged the cables in and was able to access the internet from both machines.  Now I just want to be able to get to the windows box from the ubuntu box.

Any suggestions where to look next?

Thanks,
Andy

---

### Post by walkman88 on 2010-05-27
same issue here....thanks for the post..

---

### Post by Iowan on 2010-05-27
> **ahendric said:**
> The ip address is dynamic, how do I specify the name and ip in the hosts file for a dynamic ip? Check that link I provided:> Problem 3:
Ubuntu is unable to browse Windows host names by default. Enabling this ability will also require a conf file edit...

---

### Post by capscrew on 2010-05-28
> **ahendric said:**
> capscrew,

I didn't set up anything special on either box, basically plugged the cables in and was able to access the internet from both machines.  
 

Now I just want to be able to get to the windows box from the ubuntu box.

Any suggestions where to look next?

Thanks,
Andy


I'm curious; how did you setup the addressing scheme?  Is it handled by the router?  DHCP maybe?

How did you set up sharing?  Did you just right click> share this file, etc, etc...?  Or did you configure via the /etc/samba/smb.conf file?

Although the internet has nothing to do with Samba they have some technologies in common.  In both cases you need name services.  

The local LAN name service can be DNS or WINS or /etc/host files or by NBT (NetBIOS over TCP) broadcast.  How Samba uses (and in some cases even supplies some services) is configured in the /etc/samba/smb.conf file.   

This is not a case of hunt and peck.  You really need to understand how the Samba suite works.

---

### Post by ahendric on 2010-05-28
Iowan,

I had gone through those steps, when I had 9.04.  I will go through them later today.  Thanks.

capscrew

> >>I'm curious; how  did you setup the addressing scheme?  Is it handled by the router?  DHCP  maybe?

What ever the defaults are when you start up a computer and hook it to a router.  My setup is a cable modem to a router to the various computers.  The router does have DHCP enabled and it assigns the ip addresses to the various computers, laptops.  I don't have any issue getting to the computer in question (win 7) from the laptops running windows.  The only one I have problems with is the ubuntu box.

> >>How did you set up sharing?  Did you just right click> share this  file, etc, etc...?  Or did you configure via >>the /etc/samba/smb.conf  file?

Yes, I have established shares on the windows box using right click > share...  I didn't make any changes to the smb.conf file except to change the workgroup to the one I have the windows boxes on.

> >>Although the internet has nothing to do with Samba they have some  technologies in common.  In both >>cases you need name services.  


Yes, the reference to the internet connection was just a point that I can seem to have the network correct through the router.

> >>The local LAN name service can be DNS or WINS or /etc/host files or by  NBT (NetBIOS over TCP) >>broadcast.  How Samba uses (and in some cases  even supplies some services) is configured in the >>/etc/samba/smb.conf  file.   

Not certain how the windows box is set up, but I have looked at the smb.conf file and most of it is beyond my networking knowledge.

> >>This is not a case of hunt and peck.  You really need to understand how  the Samba suite works. 	  	

That is why I decided to ask here.  I can vi with the best, but my unix experience is limited to sun os from a few years back.

Thanks for the help.
Andy

---

### Post by BASH-full on 2011-02-02
FYI, I was having the "Unable to mount location" error message issue with 10.10 attempting to connect to an XP laptop.  After following the various instructions on Iowan's link I found that the suggestion to install windbind fixed it.  Thank you, Iowan.

---

