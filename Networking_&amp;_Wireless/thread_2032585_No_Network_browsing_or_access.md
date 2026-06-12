---
title: "No Network browsing or access"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by drakuel on 2012-07-24
Hi , I am running Ubuntu 12,04, but seem to be having a problem browsing networks. My linux machine is on a network with windows 7 machines, and when I browse the network I can see some machines on the network, but i can't access them, why would this be? I know the pcs have shared files, because I can access them from other windows pcs. 

When I try to access them from the linux machine I get "Failed to retrieve share list from server"

Please help

---

### Post by Morbius1 on 2012-07-24
Well, if you can see the machines but can't access them it may be because Win7 is being a jerk.

Um ... let me rephrase that ... Win7 assumes that everyone else on the LAN is another Windows machine. Windows clients do something that Linux clients do not and that is they pass the Windows user's actual local login name and password when they initially try to connect to a share.

You might try to replicate what the Windows client does in Linux:
```
nautilus smb://morbius@servername
```OR:
```
nautilus smb://morbius@servername.local
```OR, As a last resort:
```
nautilus smb://morbius@192.168.0.100
```Change morbius to a login user name on the Windows machine and 192.168.0.100 to the ip address of the Windows machine you are trying to access.

---

### Post by mdwy62 on 2012-07-27
Thanks for this. In the past week, I have been unable to connect to windows shares by their windows names on a windows network, that I previously had no trouble with. Connecting by IP address still works, with the "Connect to Server" nautilus dialog.

I am using 12.04 without proposed or unsupported repositories, and yet I thought there was some update this past week that might have messed up name resolution. I know there was a kernel update.

I tried the command ```
 nautilus smb://myname@machine.business.corp/share
``` and was prompted for password and domain name, which when entered allowed me to connect. If I did not add a share as above, I could not connect. Prior to this last week, I could just use ```
smb://machine/share
``` in the nautilus address bar and I would be connected. 

What is this long network name (with the dots, e.g., machine.business.corp) for a windows machine called? Is there a way to regain browsing abilities? Previously, I thought I could uncover this long network name by pinging the ip address. Now the long network name is no longer returned.

---

### Post by mdwy62 on 2012-07-30
I solved my problem by reading the info entry for resolvconf. Seems that due to some other WIFI network problems I was having, I moved /etc/resolv.conf to a backup file. Under 12.04 this is a bad idea, as /etc/resolv.conf is supposed to be a symbolic link to /run/resolvconf/resolv.conf. On my broken system, /run/resolvconf/resolv.conf did not exist. Nevertheless, I created /etc/resolv.conf as a symlink to this (missing file) and rebooted. Immediately, names were resolved when I had an ethernet connection to the network.

---

### Post by Kirk Schnable on 2012-07-30
> **mdwy62 said:**
> I solved my problem by reading the info entry for resolvconf. Seems that due to some other WIFI network problems I was having, I moved /etc/resolv.conf to a backup file. Under 12.04 this is a bad idea, as /etc/resolv.conf is supposed to be a symbolic link to /run/resolvconf/resolv.conf. On my broken system, /run/resolvconf/resolv.conf did not exist. Nevertheless, I created /etc/resolv.conf as a symlink to this (missing file) and rebooted. Immediately, names were resolved when I had an ethernet connection to the network.

If you try connecting directly to the IP address of the computer, as Morbius1 suggested in an earlier post, that should help you determine whether DNS is the problem or not.

Kirk

---

