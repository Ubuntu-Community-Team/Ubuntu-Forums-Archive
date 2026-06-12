---
title: "Samba With Windows Domain through &quot;Network&quot;"
date: 2005-01-27
forum: Networking &amp; Wireless
---

### Post by m0bilitee on 2005-01-27
Hi, I'm trying to get to my windows shares through Computer->Network.   I'm choosing File -> Connect to Server, and picking a service type of Windows share.  I type in my server name, the share.

My username is on a Windows domain. How do I specify it so it works? I've tried the format MYDOMAIN/MYUSERNAME and MYDOMAIN\MYUSERNAME, but  neither of them seem to work.  

I'm more used to doing this through KDE/Konquerer, and it deals with domains and workgroups a little easier. I'm not sure if the Name to user for connection field means something as far as the domain/workgroup, or is there a different syntax for specifying this on the share.

Sorry, it's really a newbie question!

M0b

---

### Post by Kopf on 2005-01-27
I have never connected to a Windows share this way but I am pretty sure the "Name to use for connection" is just an arbitrary name for the connection.  It has nothing to so with domain/workgroups.  You should just put in the Server name, share name, and user name.  Hope this helps.

Kopf

---

### Post by hndrcks on 2005-01-27
I expect your problem is related to an ongoing challenge in gnome-vfs-utils. Try this as an experiment

Open Network

Type Ctrl-L 

In the box type in smb://servername/sharename (typing the share name is important)

Then you should get the login, domain, password fields for the keyring

Currently there is some sort of problem with browsing windows shares unless they are set to allow anonymous access from anyone (which is why you can browse a win2k server and see the netlogon directory without specifying it)

---

### Post by m0bilitee on 2005-01-27
Yep, using the CTRL-L route does give me a chance to use the domain name, and I get right in. I am able to browse the network anonymously, but all my authentication to the shares is done through my domain login.  This works well enough for me, but long term this is something I suspect the gnome folks will fix.  Cool nonetheless.

Thanks!  I'm not much of a Nautilus user--yet.

M0b

---

