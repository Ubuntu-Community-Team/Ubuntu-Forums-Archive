---
title: "Help Networkin USB HDD"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by iiDopDop!! on 2011-03-26
Hey all,

I'm having a bit of trouble sharing a 500gb USB Hardrive, what I'm trying to do is share to particular folders on there because I cant gain ownership of the drive :S. I can see them over the network, but whenever I try access them I get an error saying "share does not exist".

i can mount it and access the drive and open all folders just not through any network, i have UTFSE but all information i've found hasnt seemed to help.

heres the results of testparm if it would be usefull, as u can see ive tried adding force user = host but all that did was make the shares invisible over the network

[global]
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
	map to guest = Bad User
	obey pam restrictions = Yes
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
	force user = home

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[music 0001]
	path = /media/Expansion Drive/music 0001
	read only = No
	guest ok = Yes

[movies 0002]
	path = /media/Expansion Drive/Storage/movies 0002
	read only = No
	guest ok = Yes

---

### Post by mikewhatever on 2011-03-26
I wonder if it's because of the white spaces in the directory path.
```

[music 0001]
**path = /media/Expansion Drive/music 0001**
read only = No
guest ok = Yes

```

---

### Post by iiDopDop!! on 2011-03-26
i'll give that a go and let you know, would hyphens be better as in "music-001"? 

because the external HDD is also being used by the windows partition, and is being used over the network on windows and i need certain time frames to change it all otherwise i have annoyed people yelling at me, we stream it to 5 different xbox's running XBMC.

---

### Post by mikewhatever on 2011-03-26
I don't know enough about Samba, but perhaps someone else will suggest whether there is a way of working around this easily. Perhaps something like this: path = "/media/Expansion Drive/music 0001"?
If you are going to remove the white spaces, note that there are two, in 'Expansion Drive', and in 'music 0001'.

---

### Post by iiDopDop!! on 2011-03-28
changing the name of the folder didn't do anything, i think its because Linux cant determine the permissions of the drive, so over the share where guest accounts are aloud they cant get in because theres no ownership of the drive..  

i can still share the USB HDD when on vista but, i like Ubuntu better and sharing the HDD is the only thing stopping the swap over.

---

