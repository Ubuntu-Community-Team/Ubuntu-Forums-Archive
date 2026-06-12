---
title: "Network shares not showing up"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Mindzai on 2008-12-28
Hi

I've been suffering from very bad reliability when trying to access network shares since doing a clean install of 8.10.

On my network I have my laptop with 8.10, a server with debian lenny, a vista machine and an XP machine. From the debian, vista and XP machines, I can see all of the network shares on all other machines (including my ubuntu laptop). However from my laptop I can't see any of the other machines on the network.

If I run XP as a virtual machine on my laptop, I can access all of the shares straight away so this is not a physical connection problem. Furthermore, it doesnt seem to matter if I connect via wireless or ethernet. I do have internet connectivity under ubuntu and I can log in to my router so it defintely seems to be a software problem.

To make matters even more confusing very occasionally the shares do appear when I go to Places > Network, but trying to access them is hit and miss and pretty soon they just stop working all together.

Any ideas gratefully received.

---

### Post by albinootje on 2008-12-28
> **Mindzai said:**
> 
To make matters even more confusing very occasionally the shares do appear when I go to Places > Network, but trying to access them is hit and miss and pretty soon they just stop working all together.

You're not running firewall software on the Ubuntu laptop ?

Can you test the following :
```

sudo apt-get install smbclient
smbclient -L 192.168.1.55
smbclient //192.168.1.55/share-name -U username

```
Where 192.168.1.55 is representing a machine with shares, share-name is the name of a share, and username is the username of an account which is allowed to use the share.

And after smbclient -L 192.168.1.55 you can hit <enter>, no password needed.

If you find it more pleasant to work with a GUI, install konqueror, and type in the url-field :
smb://username@192.168.1.55/share-name

The idea of all this is, amongst others, to see whether you have a problem with the share functions in Nautilus.

---

### Post by Mindzai on 2008-12-29
Thanks for the help albinootje.

> **albinootje said:**
> You're not running firewall software on the Ubuntu laptop ?

I haven't installed one. If a firewall ships with Intrepid and is enabled by default then I haven't disabled it, but I don't think that's the case. I can't see anything related to firewall in the settings and applications menus.

Since I made my first post I havent been able to see any shares at all. Also I should add because I forgot to clarify before, I did used to be able to access the shares from my laptop, it only stopped working recently (im not sure when exactly so I cant link it with a specific event such as installing or uninstalling something).

> 
Can you test the following :
```

sudo apt-get install smbclient
smbclient -L 192.168.1.55
smbclient //192.168.1.55/share-name -U username

```
Where 192.168.1.55 is representing a machine with shares, share-name is the name of a share, and username is the username of an account which is allowed to use the share.

And after smbclient -L 192.168.1.55 you can hit <enter>, no password needed.

If you find it more pleasant to work with a GUI, install konqueror, and type in the url-field :
smb://username@192.168.1.55/share-name

The idea of all this is, amongst others, to see whether you have a problem with the share functions in Nautilus.

Here is the result of those operations:

```
karl@apollo:~$ smbclient -L 192.168.0.7
Enter karl's password: 
Domain=[MEDIACENTRE] OS=[Windows Vista (TM) Ultimate 6001 Service Pack 1] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C               Disk      
	C$              Disk      Default share
	D               Disk      
	D$              Disk      Default share
	IPC$            IPC       Remote IPC
session request to 192.168.0.7 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
karl@apollo:~$ smbclient //192.168.0.7/D -U "Media Center"
Enter Media Center's password: 
Domain=[MEDIACENTRE] OS=[Windows Vista (TM) Ultimate 6001 Service Pack 1] Server=[Windows Vista (TM) Ultimate 6.0]
smb: \> 

```

---

### Post by albinootje on 2008-12-29
> **Mindzai said:**
>  Here is the result of those operations:
```

session request to 192.168.0.7 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
karl@apollo:~$ smbclient //192.168.0.7/D -U "Media Center"
Enter Media Center's password: 
Domain=[MEDIACENTRE] OS=[Windows Vista (TM) Ultimate 6001 Service Pack 1] Server=[Windows Vista (TM) Ultimate 6.0]
smb: \> 

```

You are successfully logged in here, you can do "ls" to see the files.

Can you digg into the "NetBIOS over TCP disabled -- no workgroup available" error/warning yourself ?

And if you haven't done anything with firewall software in Ubuntu, then you're not running a firewall, you can check that with :
```

sudo ufw status
sudo iptables -L -n
sudo iptables -L -n -t nat

```

---

