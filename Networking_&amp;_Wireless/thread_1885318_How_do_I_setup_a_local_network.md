---
title: "How do I setup a local network?"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by Bogdanovist on 2011-11-23
I need the basic details on setting up a local network with Ubuntu. I have two machines at home running ubuntu and they connect to the net using wireless with a Netcomm ADSL modem and wireless router. I want to be able to access files on one machine using the other across the network.

I'm very familiar with ssh, scp etc as a user, but I don't know how to setup the network in the first place. I've tried pinging the machines I few ways I could think of but I don't really know what I'm doing...

Any tips or links?

---

### Post by Paddy Landau on 2011-11-29
If you just want to share files, it's quite easy (though not quite straightforward) to set up.

The following instructions are basic and let anyone on the network (though not outside the network) access the shared folders.

On **each** machine:

[LIST=1]
[*]Set the machine name.
[LIST]
[*]Press Alt-F2 and type```
gksudo gedit /etc/hostname
```
[*]Change whatever is there for the computer name that you want. The name must be no more than 15 characters, and should be a simple name with no spaces. This name is case-sensitive. The two machines must have a *different* name from each other.
[*]Save and close.
[/LIST]
 
[*]Duplicate the machine name into the network.
[LIST]
[*]Press Alt-F2 and type```
gksudo gedit /etc/hosts
```
[*]Find the line that starts with [FONT=Fixedsys]127.0.1.1[/FONT].
[*]Change whatever comes after [FONT=Fixedsys]127.0.1.1[/FONT] to the same name that you put in [FONT=Fixedsys]/etc/hostname[/FONT].
[*]Save and close.
[/LIST]
 
[*]**Reboot (do this now).**
[/LIST]
 
Now, on **both** machines:

[LIST=1]
[*]Install [samba]("apt:samba"), [smb-client]("apt:smb-client") and [nautilus-share]("apt:nautilus-share").
[*]Create a folder that you want to share with the other computer and allow read-write to everyone. I use [FONT=Fixedsys]/public[/FONT]; if you want to do the same, enter the commands (from a terminal):```
sudo mkdir /public
sudo chmod a+rwx /public
```
[*]Run Samba (from the menu or from Dash).
[*]Preferences > Server Settings > Workgroup (choose a name that must be the same on both machines)
[*]File > Add Share:
[LIST]
[*]Directory > (choose the directory to share)
[*]Share name > (choose a simple name, no more than 15 characters)
[*]Description > (type a meaningful description)
[*]Writable > (tick)
[*]Visible > (tick)
[/LIST]
 
[*]**Reboot.**
[/LIST]

Now, if you open Nautilus and go to Network, you should be able to find the other computer's share, and have read-write access to it.

If you have any problems, post back here.

---

### Post by Morbius1 on 2011-11-29
**@ Bogdanovist,**
If you want to use ssh give this a shot:

Install the following package on the machine you want to access:
```
sudo apt-get install openssh-server
```On the client:

Nautilus > File > Connect to Server:

Service type:    ssh
Server:        ip address of server
Folder:        exact path to folder ( like /home/username/Documents )
User Name:    user name on the server
Select "Add Bookmark"

The first time you run it it will error with something like this:
> The identity of the remote computer (192.168.0.110 (192.168.0.110)) is unknown.This happens when you log in to a computer the first time.

> The identity sent by the remote computer is e0:d7:18:9c:58:5a:47:d6:99:d6:c5:6f:7f:e8:3f:8c. If you want to be absolutely sure it is safe to continue, contact the system administrator.> Select "Log In Anyway"

** @ Paddy Landau,**

May I ask why you have steps 1,2, and 3.

He already has a netbios name linked to his hostname by default in Samba so why make him change it? Are you just assuming it's longer that 15 characters and being preemptive?

I would think just asking him to look at the output of:
```
hostname
```Have him count the number of characters and if it's greater than 15 have him change it with a "netbios name = " addition to smb.conf would be easier.

---

### Post by Paddy Landau on 2011-11-29
> **Morbius1 said:**
> **@ Paddy Landau,**

May I ask why you have steps 1,2, and 3.

He already has a netbios name linked to his hostname by default in Samba so why make him change it? Are you just assuming it's longer that 15 characters and being preemptive?
Just being pre-emptive. But I'm happy with your alternative suggestions.

---

