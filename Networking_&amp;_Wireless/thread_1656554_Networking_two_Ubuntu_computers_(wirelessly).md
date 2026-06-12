---
title: "Networking two Ubuntu computers (wirelessly)"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by poubelle on 2010-12-31
Hi there,

I have a desktop and a netbook, both running Maverick, and I'd like to network them using wifi. I'm not sure where to start, and searching just returns results about Internet access. Can anyone give me a step-by-step runthrough?

My goal is to be able to access/copy files in both directions.

Thanks!

---

### Post by PatchesTheCaveman on 2010-12-31
Do you have a wireless router?  Or an Internet connection you want to share?

Or do you just want to share files via a direct wireless connection between the two computers?

---

### Post by poubelle on 2011-01-01
Both computers have wireless cards and Internet access, but like I said, I just want to share files.

---

### Post by MrDetermination on 2011-01-01
If you can browse the web from both of them today then the hard part is over.

Are they both online?  You can browse the web from both of them already?

Do you just want to have a directory on each of them shares so you can move files back and forth between the two?

I.e. from Box 1 you can see \\Box2\Share

and vice versa?

Or do you need something more elaborate than that?

---

### Post by gordintoronto on 2011-01-01
The computers are already networked, you just have to do something about file sharing.

In Places, create a folder to share. Then right-click on the folder and select "sharing options." Select "share this folder" and give it a simple name. (I use "shared".) Also click the other two boxes, and then "Create share." I would reboot at this point, but I'm pretty sure I don't need to.

From the other computer, select the "place" called "network" Double-click on "windows network," then the workgroup name, then the computer name, then the share name. You can copy files either way, to or from the folder.

At some point in the above process, you might be prompted to install some software. Do that, and start that step again from the beginning.

---

### Post by poubelle on 2011-01-03
Thanks to you both, but neither of these things work.

I want to share files between computers. ie, transfer files back and forth.

I can share folders using the right-click > "sharing options" dialogue. (When I go to System > Administration > "Shared folders" dialogue, however, nothing is listed. Is this to be expected?)

When I try Places > "Connect to server...", I get this error:

"Could not display "smb://myusername@othercomputername/othercomputersharename/".
Error: Failed to mount Windows share
Please select another viewer and try again."

I'm not sure what they mean by viewer...

Maybe I'll just get a high-capacity USB key instead...

---

### Post by PatchesTheCaveman on 2011-01-03
Try connecting to your Linux computer via its IP address.  Sometimes connecting by hostname doesn't work too well.

If you continue to have trouble, I suggest you use *system-config-samba* to configure file sharing from the host machine.  I find that works better than the file sharing built into Nautilus.  To install it, run
```
sudo apt-get install system-config-samba
```

---

### Post by gordintoronto on 2011-01-04
> **poubelle said:**
> I can share folders using the right-click > "sharing options" dialogue. (When I go to System > Administration > "Shared folders" dialogue, however, nothing is listed. Is this to be expected?)


I also have nothing listed in "Shared folders," but other computers can see my shared folder.

---

### Post by gordintoronto on 2011-01-04
> **poubelle said:**
> When I try Places > "Connect to server...", I get this error:


I suggested:

From the other computer, select the "place" called "network" Double-click on "windows network," then the workgroup name, then the computer name, then the share name. You can copy files either way, to or from the folder.

"Connect to server" was not part of that. To use "Connect to server" you must know the server name.

---

