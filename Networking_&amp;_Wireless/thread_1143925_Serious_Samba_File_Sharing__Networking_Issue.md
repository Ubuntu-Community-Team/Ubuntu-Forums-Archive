---
title: "Serious Samba File Sharing / Networking Issue"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by R.M.C on 2009-04-30
Hello, I'm very very new to Linux and apologize if this is a double post, but I need some help.

I've done research on this problem from days on end, and it seems many people are having the same problem without luck.

Ok Here goes:

Background:
2 Ubuntu (9.04 freshly installed) Linux Machines and one windows XP machine on the same network and in the same workgroup.

Samba is installed and configured to share a folder called "documents" on both linux computers, and the windows machine is setup fully for file and print sharing  

When I click on "Places" --> "Network" nothing seems to work properly.
   1) It will tend to hang and first and then magically pop up. Sometime it will list all the computers on the network and sometimes it want. Many times all I will see is "window network"
   2) When I click "Window Network"...the same thing happens. sometimes it will hang, sometime it will display the workgroup and other times nothing happens.
  3) on the rare occasion when it does work and displays all the computers in the work group, it wont let me browse any of them. A message box will appear telling me its trying to establish a connection. 60 seconds later, another message box appears and states folder cannot be mounted - failed to retrieve share list from server.
 4) I've Searched the internet for days on this problem and can't find a fix yet.
 5) I've tried everything, installing and configuring winbind, installing gufw and making sure the firewall is disabled and even installing pyneighborhood and tried to mount that way...nothing works at all

HOWEVER, HERE IS THE STRANGE THING:
1) I can get on the window xp box and see the linux machines and shares all day long with no issue. I have transfered massive files to the linux machine from windows without any problems
2) This is even stranger. back on the linux machines, I can go to "places" --> "connect to server" and enter in the computer name and the shared folder name and it connects and mounts the folder to my desktop without issue as well. 

I have no idea whats causing this. Everything works except when you try to browse for it under network...thats when it hits the fan without fail.

pyneighborhood can see the workgroup computers and even there shares sometimes...when its not screwing up as well, but it can't mount them at all.

I have tried every freakin thing I've read in every forum relating to file sharing and networking, with no luck yet.

Also, if anyone knows how or where I can find a thorough begining-to-end guide on how to setup NSF file sharing, I would be happy. I basically know nothing about it or how to use it. Any help would be appreciated

Question for the day: Why does Linux have to be so nebulous and convoluted?

---

### Post by R.M.C on 2009-04-30
As I continue to read through the forum, I'm seeing the same things over and over again. There does seem to be some serious issues revolving around networking. 

Any shed light would be helpful.

Thanks

---

### Post by linuxdave1 on 2009-04-30
No shedding light, just fix it Ubuntu, and soon! These problems did not exist in 8.10. :(

---

### Post by StuartN on 2009-04-30
I don't have any problem with Windows (various), Mac and Ubuntu on the same network, but my guess is that if you uncomment and re-order the name resolution in /etc/samba/smb.conf to put wins first then it should behave more consistently:
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```
A machine running Windows would have to be present to provide the name service.

---

### Post by R.M.C on 2009-04-30
STATUS: OMG I fixed it

Winbind was the key. I thought I had restarted the proper services after I included "wins" on the "hosts" line in /etc/nsswitch.conf file. I guess I didn't. I restarted my computer and it worked like a charm...so far.

OK...to who it concerns try this:

1)install winbind
2)edit the /etc/nsswitch.conf file to include "wins" after files on the "hosts" line
3)save and restart your computer...and bobs your uncle!

It pisses me off that everything doesn't just work right out of the box. You shouldn't have to hunt for days to find the solution for a problem that you shouldn't have to begin with. It should come packaged with everything needed on first boot. I understand that some intial configuration is always needed, but this was just rediculous!

---

