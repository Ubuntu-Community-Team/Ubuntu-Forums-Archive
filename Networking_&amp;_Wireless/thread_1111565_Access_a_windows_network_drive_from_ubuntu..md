---
title: "Access a windows network drive from ubuntu."
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by kernel89 on 2009-03-30
On my vista there is a shared folder which I would constantly use when I had Windows XP. I could easily access the content in the Vista Shared Folder.

However, now that I have Ubuntu I don't know how to map a drive to my Vista?
When I go to Places>Connect to Server, change the Service type to Windows Share, I have absolutely no idea what to fill it up with. Can I check my Vista to see what to add, if so where would I get the info?

Also, when I do to Places>Network, and double click on the "Windows Network" icon, I see my Vista, but when I click on it I get the following message:

**_Unable to mount location_**
Failed to retrieve share list from server.

Thanks in Advance; *still new to the Ubuntu Ways...*

---

### Post by lisati on 2009-03-30
An alternative might be to use Places->Network and work your way to the particular machine. 

Having recently reogranized my computer gear into one corner of the lounge, I can appreciate the frustration. Trying to get all 4 machines talking to each other properly has its challenges and rewards. I found that giving the systems a few minutes to discover each other on the network is sometimes necessary to be able to access the shared files and folders on other machines.

---

### Post by kernel89 on 2009-03-30
> **lisati said:**
> An alternative might be to use Places->Network and work your way to the particular machine. 
That's what I did but I get the error message.

> **lisati said:**
> Having recently reogranized my computer gear into one corner of the lounge, I can appreciate the frustration. Trying to get all 4 machines talking to each other properly has its challenges and rewards. I found that giving the systems a few minutes to discover each other on the network is sometimes necessary to be able to access the shared files and folders on other machines.
I gave it a week which seems great enough :P

---

### Post by kernel89 on 2009-03-31
I've tried changing the network sharing options on the vista...still no luck :(

---

### Post by nickmcg on 2009-04-01
If you haven't already, install samba and winbind - this will allow you to browse the windows network, although you will also need to edit /etc/nsswitch.conf and add 'wins' to the end of the line beginning 'hosts'
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins

```
It might also help to install system-config-samba to configure workgroups etc.

HTH

Nick

---

### Post by Schammy on 2009-04-01
Thanks!!! I had this problem and followed your steps to get it fixed.  I had to re-boot before it took effect.  

In addition to the adding and configuring winbind, I used system-config-samba to rename the network to match my windows network name.

---

### Post by Xyphoid on 2009-04-04
Hya all,

Does anybody know the difference between "Network" and "Connect to server"?? And which one is better? I can use both, but both sometimes loose connection when copying large files.

---

### Post by hzrunner on 2009-04-04
I have basically the same problem, except that I want to connect from Ubuntu (on a Dell Inspiron 2650) to a Windows XP home network. I could download Samba and winbind_i86, but winbind didn't install. Did I get the correct winbind version, there are many. Assuming that I find a version that works, how do I then ge to the code edit. Last, what do you mean by "install system-config-samba"?
Thanks in advance.
Meanwhile I could install winbind using the Synaptic Package Manager, but winbind doesn't seem to show up anywhere (not in the Applications, Places, System menus). How do I get to it?

---

### Post by nickmcg on 2009-04-07
From synaptic, install winbind, samba and system-config-samba.

From a terminal session
```
sudo apt-get install samba winbind system-config-samba
```
again, from terminal ```
sudo gedit /etc/nsswitch.conf
``` and edit the line as above.

The only visible additions to the menu are from system-config-samba which adds System->Administration->Samba so that you can set workgroups etc.

HTH

Nick

---

### Post by inobe on 2009-04-07
hey guys i setup samba with very few steps and access to the linux machines are secure.

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

a walk in the park

---

### Post by nickmcg on 2009-04-07
Great guide - the problems you have mentions when connecting windows machines are solved by installing winbind, editing nsswitch.conf & restarting the network.

Nick

---

### Post by fmw on 2009-04-07
I finally resolved my networking problems last night after a week of fussing with it.  The problem?  I didn't have Samba installed.  I installed it and another application called smb4k.  The latter application is like a file browser for a network and it allows you to mount network notes with a mouse click. Each one you mount shows up on the desktop and allows you to click on it and brose the contents of the node. Make sure you have Samba and, if you do, install smb4k.  I can't tell you much about smb4k because it is a KDE application and I'm using Gnome.  It works with Gnome but the documentation isn't available without KDE.

---

### Post by inobe on 2009-04-07
> **fmw said:**
> .  It works with Gnome but the documentation isn't available without KDE.

the smame procedure for kubuntu except it requires some gnome applications to be installed, i have it setup for ubuntu and kubuntu.

---

### Post by nickmcg on 2009-04-08
fmw, it might be an idea to post your comment about samba to the other threads that you've raised your problems on, so that anyone following those threads has the solution too.

Nick

---

### Post by dsmithnc on 2009-04-28
> **nickmcg said:**
> From synaptic, install winbind, samba and system-config-samba.

From a terminal session
```
sudo apt-get install samba winbind system-config-samba
```
again, from terminal ```
sudo gedit /etc/nsswitch.conf
``` and edit the line as above.

The only visible additions to the menu are from system-config-samba which adds System->Administration->Samba so that you can set workgroups etc.

HTH

Nick

Trying the first instruction I received this error message:

Errors were encountered while processing:
 samba
 system-config-samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ideas,

Dick

using 9.04

---

### Post by nickmcg on 2009-05-09
The only time I've had this type of message, the database was corrupt on my machine.

Can you ```
sudo apt-get update
sudo apt-get upgrade
```?

If not, follow its suggested fix.

If you can, I'm at a loss as samba is in the main repository (unless there's a missing dependency)

Nick

---

### Post by yogm2k on 2009-07-09
you run following command in terminal

gksudo gedit /etc/nsswitch.conf

---

