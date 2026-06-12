---
title: "Network issues"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by Castarmax on 2011-01-09
Yes I have Googled and searched. I have been at this for 3 days:)

I'm trying to network a Ubuntu 10.04 laptop (192.168.0.11) with a VistaHome 64 desktop (192.168.0.10). I have full access to files from Ubuntu either connecting through Network or by Connect to Server. From Vista I can see linux-laptop under the network. I am trying to share /home/john/movies, /home/john/pictures, and /home/john/music. When I open linux-laptop I can see my shares. However when I try to access  a folder lets say movies which is actually located at /home/john/movies I get the error "windows can not access \\linux-laptop\movies". This stands true all shares. I think the path is defined incorrectly somewhere. To test this theory I created a file called john2 at root and shared it. I placed a nondescript .txt file in there. When I opened linux-laptop from Vista I saw among the other shares john2. When I tried to open that it allowed me and I was able to see the text file. I believe I have an incorrectly set path for shares somewhere on Ubuntu. I'm not sure if Im using samba or nfs or both. I can post smb.conf if needed.
Also, sometimes Vista ask for a password. I have only 2 users on both machines with identical usernames and passwords both with admin access. Sometimes I get not allowed access error or i get users can not access more than one share at a time error.
Help please,
Thanks

---

### Post by PatchesTheCaveman on 2011-01-09
Try adding a
```
force user = john
```
line for each of the affected shares to your *smb.conf* file.

If that doesn't work, please post your *smb.conf* file.

---

### Post by Castarmax on 2011-01-10
sorry double post

---

### Post by Castarmax on 2011-01-10
> **PatchesTheCaveman said:**
> Try adding a
```
force user = john
```
line for each of the affected shares to your *smb.conf* file.

If that doesn't work, please post your *smb.conf* file.


Thanks Patches!!!!
I read a lot on how this is done. Never ran across this command. Does this affect other users? There are 2. I assume since identical accounts on both machines both will always connect via john? Below is my sbm.conf. Any other issues you see?

Interestingly enough, now from Ubuntu machine I can only connect to other machines through Connect to Server. I can not reach them via Network.


[global]
	netbios name = LAPTOP-LINUX
	server string = Samba,Ubuntu
	encrypt passwords = yes
	smb passwd file = /etc/smbpasswd
;	socket options IPTOS_LOWDELAY TCP_NODELAY
	force user = john
	workgroup = workgroup
	security = user
;	wins support = yes
;	wins server = 192.168.0.11
	username map = /etc/samba/smbusers
	guest ok = no
	guest account = nobody
[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[homes]
	browseable = yes
	map archive = yes

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[movies]
	path = /home/john/movies
	writeable = yes
	browseable = yes
	valid users = john, mediatomb, melmo, nobody

[music]
	path = /home/john/music
	writeable = yes
	browseable = yes
	valid users = john, mediatomb, melmo, nobody

---

### Post by Castarmax on 2011-01-10
double post sorry

---

### Post by PatchesTheCaveman on 2011-01-11
> Does this affect other users? There are 2. I assume since identical accounts on both machines both will always connect via john?

The other users can access the share with their accounts.  But they will have all the read and write rights of *john* within the shared directories once they've logged in with their normal account.  This is necessary because the folders are located in *john*'s home directory.

If that's a problem for you, you should consider moving the shared directories to a different location outside *john*'s home directory and then make that writable by the other users.

---

