---
title: "Mounting Synology DS110J does not work"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by wimduk on 2010-03-20
Dear Reader, 
I want to use the 1.5tb of my DS110J for data storage [and sharing] of all my Linux computers attached to my local network.  
 

 **The Facts**
 Synology DS110J NAS Server
 
[LIST=1]
[*]Samsung SpinPoint F2EG HD154UI 1.5     terabyte mounted
[*]Linux Installation script executed     including formatting of the HDD
[*]NFS function activated (via the     webinterface)
[*]Shared folder created     [Data_wimduk]
[*]NFS rights set to Data_wimduk      
[r/w, Root squash: No, Client: wim-laptop-ibm (=hostname     laptop)]
[*]IP-adres : 192.168.1.7
[*]Volume1 is the root directory [I     suppose?]
[/LIST]
 

 Laptop working under Ubuntu 9.04
 
[LIST=1]
[*]NFS installed [apt-get install     nfs-common]
[*]Created folder     /media/Synology
[drwxr-xr-x  2 root root  4096 2010-03-20 09:34     Synology]
[*]IP adres     :  192.168.1.8
[*]Hostname : wim-laptop-ibm
[*]ping 192.168.1.7 gives a reply so     the DS110J is connected to the network
[/LIST]
 

 **My Problem**
 The command &#8220;sudo mount 192.168.1.7:/volume1/Data_wimduk /media/Synology&#8221; gives the error &#8220;mount.nfs: access denied by server while mounting  192.168.1.7:/volume1/Data_wimduk&#8221; I want to mount  manually first before updating the fstab file for automatic mountig on system startup.
 

  What do I wrong and who can help me to solve this problem? Many thanks in advance.
 wimduk

---

### Post by rogererens on 2010-05-19
> **wimduk said:**
> Dear Reader, 
...
[LIST=1]
[*]Samsung SpinPoint F2EG HD154UI 1.5     terabyte mounted
[*]Linux Installation script executed     including formatting of the HDD
[*]NFS function activated (via the     webinterface)
[*]Shared folder created     [Data_wimduk]
[*]NFS rights set to Data_wimduk      
[r/w, Root squash: No, Client: wim-laptop-ibm (=hostname     laptop)]
[*]IP-adres : 192.168.1.7
[*]Volume1 is the root directory [I     suppose?]
[/LIST]
 
...
 wimduk

Hello Wim,

did you have any luck on this?

Did you also create a local user with a user name that you also use on the laptop.

And does it work when you use the IP-nr instead of wim-laptop-ibm in your NFS-rule? It did for me, and changing back to hostname again, it seemed to continue working (didn't restart yet, though, so I'm not sure it will last).
If IP-nrs are needed, maybe you can assign your laptop a static IP in your router or whichever device assigns the IPnr to your laptop.

Roger

---

### Post by wimduk on 2010-05-22
Hi Roger,

Thanks for your reply and yes it works for me now :)
I did the following

[LIST=1]
[*]I gave the synology a fixed IP number
[*]Besides the group i also gave the named users (wim, ria, guest) full access to the shared drives
[*]Gave all computers 192.168.1.* acces via NFS to the synology
[/LIST]

The only problem I am experiencing now is that Open Office rejects to update files on the shared drives. I have to create a new copy of the file om my local drive and copy this new file to the shared drive afterwards (no problem with copy, rename and delete on the shared drives!). This only happens with Open Office so i think it has something to do wit settings

Kind regards 
wimduk

---

### Post by andymnc on 2011-01-22
the problem is permissions and groups.
every synolgy assigns to "users" those files. so automatically when you save a file there, it becomes of "users"
the solutions could be two:
1. in your ubuntu pc, put your personal user into the "users" group (leave it into his own but put him also into the "users" one) of the ubuntu machine itself. 

or

2. create the directory ypu whant to share into the synology machine, create a group like the one your user in ubuntu is (for example, if your user is andrew, the group'd be probably "andrew").
then assign this group to the shared folder and don't share to "users".

or
some other combination, as you wish, of the earlier 2.

hope it could be useful

---

