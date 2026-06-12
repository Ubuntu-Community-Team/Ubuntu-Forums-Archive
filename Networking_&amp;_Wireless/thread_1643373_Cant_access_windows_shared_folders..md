---
title: "Cant access windows shared folders."
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by drazelian on 2010-12-11
We have a windows 7 computer with a wired connection and a printer. We are connected to our wifi network on an ubuntu laptop. Using samba, we were able to enter the username and password for the win7 pc, and gain permanant access to the use of the printer. During that time, if i went to Places, Network, it would show the icon with a stack of drives, with the name of the win7 pc, and I could go in there and access the shared folders from windows 7. There was a second folder, called Windows Network, which if I went inside, would bring me to a folder called WORKGROUP, inside that it would show the same stack of drives and bring me to the win7 shared folders.

When I restarted the laptop, I still had access to the printer, but those shared folders are gone.
There is still the Windows network folder, which I can enter to show the folder called WORKGROUP. If I try to enter the folder, it tells me that it failed to receive the share list from server. 

I am assuming that this is because I did not enter the necessary credentials, but it does not give me a pop up box to do so.

I think it worked before because I entered the credentials to access the Printer, but the printer permanently remembers the password, so I can't re-enter them, nor would I want to every time I want to access the shared folder.

What can I do to make my computer recognize the shared folders, and to keep them mounted when I restart.
Thanks.

---

### Post by drazelian on 2010-12-12
bump

---

### Post by drazelian on 2010-12-12
Things are a bit different today. If I go into WIndows Network, the WORKGROUP, I can see the PC I am trying to connect to SAM-PC, but can not enter it.

I tried using connect to server, chose windows share.
Heres the info about the Pc that I have but I can seem to configure it right.
Name of PC = SAM-PC
Password for share = *****
Ip adress (both the pc and laptop share it) = 75.68.205.91
Name of shared folder = Public
Username: sam
I don't know the workgroup name but I am assuming it is workgroup

So how would I fill this out?
Server:
Share:
Folder:
User Name:
Domain Name:
[] add bookmark
bookmark name :

---

### Post by drazelian on 2010-12-12
Also, I disabled the printer to see if i could enable it again, and with that get my shared folders. At this point I cant get the printer back, it can't be found.

---

### Post by drazelian on 2010-12-13
Bump

---

### Post by Sef on 2010-12-14
[Duplicate]("http://ubuntuforums.org/showthread.php?p=10236019#post10236019") Thread, so locked.

---

