---
title: "Strange samba problems, folder contents could not be displayed"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Anessen on 2009-01-01
Hello

I am experiencing a strange issue with samba between two machines. Neither machine can browse the other one, throwing up either a "Could not be mounted" error or "Folder Contents Could Not Be Displayed".

The odd thing is that both of them can access a third machine just fine, and they are both using almost exactly the same smb.conf configuration file as this good machine.

The two problematic computers are this Ubuntu 8.10 machine and a Debian Testing machine. The computer which works perfectly is running Debian Etch. None of the computers are running software firewalls. The shared folders on all of the computers were created with 777 permissions and are owned by the main user account (a regular user, not root). All of the machines have network connectivity - I can use VNC between the two problem computers.

The smb.conf files on the computers look like this:
```

[global]
security = share
workgroup = myworkgroup
netbios name = computername
server string = main computer
browseable = yes
hosts allow = 192.168.0.

[Main Share]
	comment = Guest Access Share
	path = /home/username/Public
	browseable = Yes
	read only = No
	guest ok = Yes

```
I don't think there is anything wrong with this, as I said it works fine on one of these computers.

I know that all three computers are running different versions of Samba, could this be the problem?

---

### Post by Iowan on 2009-01-01
> **Anessen said:**
> I know that all three computers are running different versions of Samba, could this be the problem? *Probably* not, but what versions are they?  Ubuntu Samba seemed to change personality (just my opinion) between Gutsy and Hardy. I presume the machines all have the same users (and Samba users).

---

### Post by superprash2003 on 2009-01-01
are you able to see the shared folders of the machine?? or you only have a problem with the content inside a particular shared folder?

---

### Post by mpokrywka on 2009-01-01
You can use command line tool with debugging turned on to see what the problem is (instead of cryptic "Folder Contents Could Not Be Displayed"):
**smbclient -d 3 //debian_etch/sharename**

---

