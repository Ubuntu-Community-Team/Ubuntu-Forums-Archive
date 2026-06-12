---
title: "network shares not writable after reboot"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by Laryllan on 2009-06-21
I am trying to build a mixed network with two Ubuntu and one WinXP machine. One of the computers serves as a file server using samba. It is needed that the shares on this computer are accessible.

I used the gnome network shares function.
It works well, but after I reboot the system not any one share is writable anymore. Some of them show the "hand" icon on the folder, others don't.

Does anyone experience the same problem?


I searched the board and found that the shares are created using **net usershare**. The command *net usershare list* gives a segmentation fault.

```
~$ net usershare list
Segmentation fault
```

Any help would be appreciated.

---

### Post by swerdna on 2009-06-21
The usershares' configurations are housed in directory /var/lib/samba/usershares

Typically the contents of a file in the directory "usershares" is like this:
```
#VERSION 2
path = /home/john/sharename
comment = 
usersahre acl=S-1-1-0:F
guest_ok=y
```

So check out that directory and the shares inside the directory and see if they're configured properly. If not then re-do them using Nautilus.

Also, check that smb.conf contains this line in the [global] stanza:
```
usershare allow guests = yes
```

---

### Post by Laryllan on 2009-06-21
My smb.conf states *usershare allow guests = yes* and my shares look exactly like the one you posted - at least the ones not writable by guests. I tried to unshare and reshare afterwards, the problem persists.

If I set them writable, nothings changes in the /var/lib/usershares file.
I wonder if this is how it should be. If these usershare files are the only info about my shares, then they have to differ if they are writable.


Can you try this please:
1. create a share, make it writable to guests (all buttons checked)
2. reboot
3. check the share - is it still writable?

What is the output of *net usershare list* on your machine?

---

### Post by swerdna on 2009-06-21
> **Laryllan said:**
> My smb.conf states *usershare allow guests = yes* and my shares look exactly like the one you posted - at least the ones not writable by guests. I tried to unshare and reshare afterwards, the problem persists.

If I set them writable, nothings changes in the /var/lib/usershares file.
I wonder if this is how it should be. If these usershare files are the only info about my shares, then they have to differ if they are writable.

If I make one that's not writeable, but it does have guest access, then it's like this:
```
#VERSION 2
path = /home/john/sharename
comment = 
usershare acl=S-1-1-0:R
guest_ok=y
```
Note that this is different from the one I posted previously for a wrtiteable share. the letter F changes to R
> 
Can you try this please:
1. create a share, make it writable to guests (all buttons checked)
2. reboot
3. check the share - is it still writable?
[/QUOTE
Yes it is
[QUOTE]
What is the output of *net usershare list* on your machine?
```
john@ubuntu:~$ net usershare list
documents
pictures
john@ubuntu:~$
```

Looks like yours is in real trouble. I hope some other suggestions are forthcoming. 

Also I ahve one thought: please post the return you get after running this command in a terminal:```
testparm
```

---

### Post by Laryllan on 2009-06-21
Here it is:

```
~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = FRANKEN
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	guest account = laryllan
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

---

### Post by swerdna on 2009-06-21
That looks OK. Ttry it without this: ```
guest account = laryllan
```but I don't really think that's the problem

---

### Post by Laryllan on 2009-06-21
No, it isn't. I experienced the behaviour before I changed the guest account.

---

### Post by swerdna on 2009-06-21
OK, you have a flawed/broken sharing tool in Nautilus. And fixing the problem at that level is well beyond me. So if no one else chimes in I suggest you turn off the shares that you made with Nautilus and re-make them using the classical method of putting stanzas, one for each share, into smb.conf. That should be OK.

If you post here the contents of the files in the directory /var/lib/samba/usershare, I'll tell you what to put in smb.conf so the classical versions can work for you instead of the usershares versions.

But first make sure all the available updates have been applied, just in case there was a fix issued for whatever bug is causing this problem.

---

### Post by dmizer on 2009-06-22
Please post the output of:
```
sudo iptables -L
```

---

### Post by sahabcse on 2009-06-22
Follow below url this may be help

[http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html](http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html)

---

### Post by Laryllan on 2009-06-22
```
~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I didn't mess with the firewall.
It's really nice how you people like to help me. I appreciate that. :)

---

### Post by dmizer on 2009-06-22
When you have trouble accessing the share, are you logged in? Since this is a usershare, you will have to log in with your user before the share can be made available. If you want a dedicated file server, you should probably configure a dedicated share.

Otherwise, you may have success by adding an option to smb.conf. Please edit /etc/samba/smb.conf and add:
```
netbios name = your-server-name
```
Where "your-server-name" can be anything you like as long as it uniquely identfies your server. Add this line just below the "workgroup = FRANKEN" line.

---

### Post by Laryllan on 2009-06-23
> When you have trouble accessing the share, are you logged in?
Sure.

I tried your suggestion adding *netbios name* - no effect, same behaviour.

I am beginning to think that it's not a Samba problem but rather one with Nautilus/GVFS. Yesterday I installed a new system showing the same behaviour (after reboot the hand symbol disappears, still a segmentation fault as answer for *net usershare list*). This is what differs from a standard Ubuntu installation:
* newest Wine version from their repo - it installed **winbind**. May that one be the troublemaker?
* I am connecting via WLAN.

---

