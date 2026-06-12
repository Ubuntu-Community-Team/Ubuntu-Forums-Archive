---
title: "Why can't I get shared files to open?"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by Janeleaper on 2010-06-15
Lucid. Two desktops, both Dell 530's.  

Desktop A has wired connection to router, was a fresh install of 9.10 upgraded to 10.04. Has printer attached - HP deskjet 845C.

Desktop B has fresh install 10.04 and wireless connection to router.  Has problem free internet connection through the router.

Both computers have sharing services installed and a shared folder (called "Public").

I'd like both computers to be able to see the public folder on the other computer, and I'd like computer B to be able to use computer A's printer.

When I try to open a shared folder on one computer from the other computer I just keep being asked for my password. Which password is this?  I enter the user password for the computer which is the same on both computers) but that does not seem to work.  I've also tried the password for the router, but that does not work either.

---

### Post by doas777 on 2010-06-15
are you using classic or userspace samba (the gui stuff)?

I use classic, and usually when I get this error, it is because I forgot to associate the "server" side user account with a Samba account. so I just run:
```
sudo smbpasswd -a <username>
```and that clears it up.

i;m not sure how this would react for userspace sharing. It may work either way. if you try it and it doesn't, try the same command but with -x instead of -a to delete the account from teh samba authentication database.

---

### Post by Morbius1 on 2010-06-15
Please post the output of the following commands so we can see how you are set up:

```
net usershare info 
testparm -s
```I'm assuming you attempted to create a guest share that anyone can access without requiring a username and password.

---

### Post by Janeleaper on 2010-06-15
[public]
path=/home/jane/Public
comment=
usershare_acl=Everyone:F,
guest_ok=n

---

### Post by Janeleaper on 2010-06-15
Doas: I don't know which Samba I'm using.

---

### Post by Morbius1 on 2010-06-15
What about the output from **testparm -s**

The **net usershare info** indicates that you have created a share that requires the remote user to supply a username and password to gain access. Is this what you want it to do or was your intent to create a public "Public" share that anyone can access without a username and password?

---

### Post by Janeleaper on 2010-06-15
The latter - a "public" public share that anyone can access.

---

### Post by Janeleaper on 2010-06-15
jane@jane-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
jane@jane-desktop:~$

---

### Post by Janeleaper on 2010-06-15
I should add this terminal is on computer A, which I'm sat at.  I can get reading from terminal on B too if that will help.

---

### Post by Morbius1 on 2010-06-15
You need to back into Nautilus and check that last box:

---

### Post by doas777 on 2010-06-15
> **Janeleaper said:**
> Doas: I don't know which Samba I'm using.
it looks like you are using the new userspace interfaces. it's all good. 

the rlimit error from your testparm output is safe to ignore.
from your testparm it does look like you could register the account with samba using the command I mentioned above, if you want to restrict the share to known users, but since you want to allow guests, my recommendation is go back to the folder, and rclick on it to get to the Sharing Options. then check "Guest Access".

---

### Post by Janeleaper on 2010-06-15
OK.  Thank-you.  I'm even dimmer than I thought.

So, now I've got file-sharing.  Is there a way of allowing Computer B to use the printer on computer A?

---

### Post by Morbius1 on 2010-06-15
First you have to "share" and "publish" the printer on Computer A:

Step 1: Enable Sharing for that Printer.
Administration  > Printing > Right Click the attached printer > Properties >  Policies
Check Enabled, Accepting Jobs, and Shared

Step 2:  Enable Publishing of the Shared Printer
Administration >  Printing > Server > Settings > Check "Publish Shared Printers  connected to this system"

Now see if Computer B can "see" the printer on A:
Administration > Printing > New
[COLOR=Blue]EDIT: Sorry, that should be Administration > Printing > Add[/COLOR]

---

### Post by Janeleaper on 2010-06-15
OK.  

Following your advice computer B can now "see" the printer on computer A.

But, I can't get the printer to print documents from computer B.  I've gone through the printer troubleshooter and the problem seems to be "no authentication data provided"

---

### Post by Morbius1 on 2010-06-15
I have never seen that error message before. Did a quick search and there are some bug reports about it but I haven't investigated further. 

I hate to do this to you but I have to quit for the day. I'll do some research on this problem and if I find anything I'll bet back to you tomorrow. 

You might want to post the Printer model and type and what it is your printing. There seems to be a problem with printing PDF's in 10.04. Hopefully someone else with that printer knows of a workaround or solution.

Again, Sorry for leaving you in a bind like this.

---

### Post by Janeleaper on 2010-06-15
No problem Morbius.  This is not a big deal.  The printer is very old (bought second hand) and although it has colour and black cartridges I've only ever been able to get it to print with black.

I think I'm going to give up on this. My partner can always print by transferring documents to my machine, or alternatively it's about time we got a new printer anyway!

Thanks for your help yet again. At least our household machines can share documents now, which has always defeated me up to now.

---

