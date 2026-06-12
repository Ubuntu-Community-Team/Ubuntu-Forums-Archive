---
title: "Canon IP1600 via Samba doesn't work for me."
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by The_Loko on 2011-12-02
Hi, this is my first message here, but i have been reading for a long time.
My problem is that my printer connected to a Windows computer doesn't print the stuff that I send from here with xubuntu 11.10 and a laptop that have other distro based in ubuntu 10.10.
Everything is configured, and when I push print in a document, it shows that is sending the document to printer, the icon appear and show printer is connected and then it says the document is printed; but the printer does not work.
Same with the laptop. With windows on this computer, the printer works.
I have tried with the drivers of the data base and compiling my own, but I got the same result.
My printer is a Canon Pixma Ip1600

---

### Post by The_Loko on 2011-12-03
Now I have test with testparm -s and I have this output:

```
julio@julio-HP:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Julio RED]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = CASA
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Julio RED]
	comment = Carpeta en el ordenador de Julio
	path = /home/julio/Julio RED
	read only = No
	guest ok = Yes

```

I don't know if it is correct. Julio RED is a shared folder, and I can connect from Windows and ubuntu computers.

---

### Post by dandnsmith on 2011-12-03
The first thing to note is that using testparm is completely irrelevant, as you don't need to install Samba to print on your Windows PC printer - the smbclient comes as part of the standard install, and nothing needs to be done to get the printing working.

You probably need to remove any printer setup you've made so far, as it isn't working, and then go through the setting-up exercise again. Tell it to find a network printer, and select manufacturer and model - then you should be able to print a test page

---

### Post by The_Loko on 2011-12-03
> **dandnsmith said:**
> The first thing to note is that using testparm is completely irrelevant, as you don't need to install Samba to print on your Windows PC printer - the smbclient comes as part of the standard install, and nothing needs to be done to get the printing working.

You probably need to remove any printer setup you've made so far, as it isn't working, and then go through the setting-up exercise again. Tell it to find a network printer, and select manufacturer and model - then you should be able to print a test page

I have done this, and it find my printer, but the printer doesn't do anything, yes it is strange. Maybe any problem in the windows computer? It have XP

---

### Post by dandnsmith on 2011-12-03
If you can find the printer, that suggests that it is shared by the XP PC (the first hurdle). If you can get the indications that the printing is sent to the XP machine (pause and network traffic, followed by a report that it has been sent), then it may be the printer model which is wrong.
IRIRC the IP1600 does have usable linux drivers (where my other printer IP1200 doesn't)
It's worth checking to see that the firewall at the XP end isn't giving problems - the number of times I've seen the XP firewall turned on where it should have been off (because another firewall is in use) or incorrectly set!!
Just for your confidence, I've no problems with UB10.04, Ub10.10, Ub 11.10 or Mint11 (and some other, non-relevant distros)

---

### Post by The_Loko on 2011-12-03
I have disabled the firewall, and I still have the problem. Also, I have checked that I have the guest account enabled. The problem should be in the XP machine... but where?

---

### Post by The_Loko on 2011-12-04
I have to set an user and password when I set the printer? Or leave it blank??

---

### Post by dandnsmith on 2011-12-04
Whether you need username and password depends on how the XP end of things has been set up.
Since I now know it's XP, are we talking about XP Home or XP Pro - there's a difference in what each can do in the way of networking. Home can only do simple networking, whereas Pro can be rather more complicated in the networking setup. I've engineered installations with each type having the printer, but simple networking is easier (and I think my personal XP Pro has been set to use that, for various reasons).

---

### Post by The_Loko on 2011-12-04
> **dandnsmith said:**
> Whether you need username and password depends on how the XP end of things has been set up.
Since I now know it's XP, are we talking about XP Home or XP Pro - there's a difference in what each can do in the way of networking. Home can only do simple networking, whereas Pro can be rather more complicated in the networking setup. I've engineered installations with each type having the printer, but simple networking is easier (and I think my personal XP Pro has been set to use that, for various reasons).

It's XP Pro. I have 2 user accounts and guest.
Now I have seen that my documents are show in the print queue in the Windows computers, and they can't print until I cancel my archives from any Windows computer (Here says that is printed, but in Windows says Processing)

---

### Post by dandnsmith on 2011-12-05
> **The_Loko said:**
> It's XP Pro. I have 2 user accounts and guest.
Now I have seen that my documents are show in the print queue in the Windows computers, and they can't print until I cancel my archives from any Windows computer (Here says that is printed, but in Windows says Processing)

If it appears in the Windows print queue, that should be sufficient. If then there is no printing, it could be paused, the queue content could be unprintable (usually then get some garbage rather than nothing.

I do understand what you mean about cancelling the archives - in context, that just confuses me I'm afraid

---

### Post by The_Loko on 2011-12-07
> **dandnsmith said:**
> 
I do understand what you mean about cancelling the archives - in context, that just confuses me I'm afraid

Forguet that, I don't know what I did,:P but I don't have this error now. The queue in the Windows computers says that the files are printed.

Also, I have connected the printer here, and the computer showed a message that said No controller found for this printer, then I selected it, and printed a document. The led of the printer start flashing, but it didn't do nothing :(

It's really annoying, thanks anyway.](*,)

---

