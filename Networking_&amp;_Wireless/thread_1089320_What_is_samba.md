---
title: "What is samba?"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2009-03-07
I am trying to share files between my windows XP laptop and my Kubuntu PC. I came across something called SAMBA in many tutorials. What is samba and why do I need it to share files with windows machines? 
(The seem to remember that there's a dance called a samba but I don't think that's relevant. ;):D)
EDIT:
just after posting the above I checked out the samba web site and went to the official HOW TO. Just looking at the table of content was scary. I would really like a brief introduction cos I don't know a thing beyond the very basics of networking

---

### Post by sgosnell on 2009-03-07
Not much to it.  Install samba (if it's not installed, it should be) and set sharing options for the directories you want to share.  You can do it in the file manager, by right-clicking on the directory, selecting Properties, then the Share tab.  Check the box to set the sharing.

---

### Post by prshah on 2009-03-07
> **mahela007 said:**
> What is samba and why do I need it to share files with windows machines? 

Samba is the linux implementation of Windows networking. Linux's networking service is called NFS, and other types include SSHFS, FTP and so on.

But when you are working with a Windows network, you need Samba, which is a linux equivalent to access Windows-based networks.

---

### Post by mahela007 on 2009-03-07
so what's the service used in windows?

---

### Post by prshah on 2009-03-09
> **mahela007 said:**
> so what's the service used in windows?

In Windows, the service is called "Windows Networking".

Looks to me like you are getting a little confused; here's a quick-and-dirty hands-on guide.

Set up your Windows machine for network access (Setup a network, Share a folder, make allowances in Windows Firewall); you don't need to do this if you already have a network setup.

On your linux machine:

a) Install samba; open a terminal (Applications-Accessories-Terminal), and give the command ```
sudo apt-get install samba
```

b) Important step: Log out and log back in (or simply restart the machine).

c) Click on Places->Connect to Server.

d) In the window that pops up: 
[indent]Change "Service Type" to "Windows Share". 
For "Server", enter the IP address of the Windows machine, 
For "Share", enter the sharename as set up in the Windows machine
Ignore the rest, just click the connect button.[/indent]

With luck, you should now have a window opening up with the given share.

Another shorter way: Click Places-Home, then in the "Location" bar, give the command```
smb://192.168.1.4/mydocs
``` (Replace the IP address with the actual ip address for your Windows machine, and the sharename [mydocs] with whatever you have setup as the sharename on your Windows machine).

Post back with details if you run into difficulties.

---

