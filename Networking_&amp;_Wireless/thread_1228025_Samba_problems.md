---
title: "Samba problems"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by diogobaeder on 2009-07-31
Hi there,

My machine, using Ubuntu Jaunty (9.04), is not seeing the windows machines, even though I have set all of them to the same workgroup. The win machines also don't see my machine, and don't see themselves, and I noticed that they work correctly if I turn off the Ubuntu machine.

Any ideas of what it might be? Can it be something with the WINS configuration?

Thanks!

---

### Post by LowSky on 2009-07-31
how did you setup SAMBA? what tutorial if any  did you use? what version of windows do the other machines use?

---

### Post by dmizer on 2009-07-31
> **diogobaeder said:**
> Hi there,

My machine, using Ubuntu Jaunty (9.04), is not seeing the windows machines, even though I have set all of them to the same workgroup. The win machines also don't see my machine, and don't see themselves, and I noticed that they work correctly if I turn off the Ubuntu machine.

Any ideas of what it might be? Can it be something with the WINS configuration?

Thanks!

Please see the 6th link in my sig.

---

### Post by diogobaeder on 2009-07-31
> **LowSky said:**
> how did you setup SAMBA? what tutorial if any  did you use? what version of windows do the other machines use?

LowSky, I followed various tutorials in the net, after trying only with the Ubuntu main tools. I'm posting the smb.conf here.

dmizer, I followed all your steps and still no success. Could you please take a look at my config file and see if there's anything that I'm missing?

Thanks,

Diogo

---

### Post by dmizer on 2009-07-31
The Windows machines do not see your Ubuntu machine because you have this option commented out in your share definition (highlighted in red)
```
[share]
	path = /home/diogo/share
	writeable = yes
[COLOR="Red"];	browseable = yes[/COLOR]
	guest ok = yes
```
Remove the semicolon ";" to make this option active.

Please post the output of:
```
sudo iptables -L
```

---

### Post by diogobaeder on 2009-07-31
Right... I updated this line, and the WinXP box sees the Ubuntu machine, but when I try to open the machine in Windows Explorer, to see the shares, it doesn't allow me... Is there something wrong with the share level? I don't have any concerns with the "/home/diogo/share" security, I want it to be writable, readable, everything for everyone, without the need for logins or anything like that.

Now what should I do?

Thanks a lot for the help, dmizer! :-)

---

### Post by dmizer on 2009-07-31
In the "Authentication" section, below the line that says, "#   security = user", add this line:
```
security = share
```

Restart samba or reboot after making the change. Also, as I requested before, please post the output of:
```
sudo iptables -L
```

---

### Post by diogobaeder on 2009-07-31
Hi, dmizer,

Despite line 103, containing the security type, is commented out, line 242 already has "security = share". Nevertheless, I commented line 242, uncommented line 103 and changed it to "security = share".

Sorry for forgetting to give the command output, here it is:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

Like can be seen, no firewall rules... any other idea?

Thanks for the help! :-)

Diogo

---

### Post by dmizer on 2009-08-01
Sorry, I missed the "security = share" option listed under Misc. My bad.

What is the output of:
```
smbtree
```

What about firewalls on your Windows computers?

---

### Post by diogobaeder on 2009-08-01
smbtree: ```

Password: 
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK

```

No firewalls running on the machines, only the native WindowsXP one, but I've not set any rule to block local machines...

Thanks again!

Diogo

---

### Post by dmizer on 2009-08-01
Try commenting out all the printer stuff for the time being.

Also, add this option to the Misc section somewhere:
```
local master = no
```

---

### Post by diogobaeder on 2009-08-01
Changed. Same issue: can see, but cannot enter. I'm thinking of disabling all security functions in the router firewall, what do you think of it?

---

### Post by dmizer on 2009-08-01
> **diogobaeder said:**
> Changed. Same issue: can see, but cannot enter. I'm thinking of disabling all security functions in the router firewall, what do you think of it?

Router security functions are WAN side, not LAN side. The router should allow all LAN traffic by default, so no, this is not a good idea. Does the problem persist if you shut down the Vista computers on your network?

---

### Post by diogobaeder on 2009-08-01
You're right, I agree...

I only have XP boxes in the LAN, besides my Ubuntu one. Well, after all these changes we've made in the Ubuntu box, I'll try to connect to another LAN, at home (I was trying to connect to my girlfriend's home network), and then I post you the results, OK?!

dmizer, thank you very much, again, for the help... that's the kind of thing that makes open source community much more alive than proprietary software ones! :-)

Diogo

---

### Post by dmizer on 2009-08-03
> **diogobaeder said:**
> 
No firewalls running on the machines, **only the native WindowsXP one**, but I've not set any rule to block local machines...

The native XP firewall could very likely cause these problems. Try disabling the firewalls on the Windows machines. Also take a close look at the share configuration on the Windows side.

Do you get any different output now if you run the smbtree command?

---

### Post by diogobaeder on 2009-08-03
dmizer,

Now, at home, where there are 3 WinXP machines, they all share files with each other, but I get the same error message while trying to open my samba share. Is it really possible to be the Win firewall?

The output for the smbtree command is empty. It asks for a password, I type it, then it returns to the prompt.

Any other ideas? I'm sending again my smb.conf, just in case, after all these modifications. Also, I've backed up the original and removed all the comments from the new one, to make it easier to read.

Thanks again, dmizer!

Diogo

---

### Post by dmizer on 2009-08-03
Well, you changed your smb.conf significantly, and there's several things wrong with it now. First of all with "guest ok = no" you'll need to define allowed users to access the share, but you don't have any listed so no one can see the share. The create mask and force create mode options are not necessary and are likely causing you problems. You've also eliminated the "netbios name = diogo-laptop" option which allows your Ubuntu computer to be seen by the XP machines.

Try this share definition:
```
[share]
	path = /home/diogo/share
	writeable = yes
	browseable = yes
	public = yes
	guest ok = yes
```
Edit:
In fact, just use this smb.conf as I'm sure it should work:
```
#======================= Global Settings =======================

[global]
	workgroup = CASA
	netbios name = diogo-laptop
	server string = %h server (Samba, Ubuntu)
	dns proxy = no
	name resolve order = lmhosts host wins bcast

#### Debugging/Accounting ####

	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d

####### Authentication #######

	security = share
	passdb backend = tdbsam
	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	map to guest = bad user

#======================= Share Definitions =======================

[share]
	path = /home/diogo/share
	writeable = yes
	browseable = yes
	public = yes
	guest ok = yes
```

Make sure that /home/diogo/share has world read write execute permissions:
```
sudo chmod 777 /home/diogo/share
```
Restart samba or reboot

Really, the smb.conf file you posted earlier was much better. The only option I would have added (I missed it earlier) is "public = yes" in the share definition.

As for accessing the Windows shares: yes, even though the Windows machines can browse each other fine doesn't mean that their firewalls are not interfering with Ubuntu. Besides, if you have a router firewall in place there's not really a need for a local firewall on Windows.

---

### Post by diogobaeder on 2009-08-03
OK, here we go:

[LIST]
[*]Replaced smb.conf with your definitions
[*]Changed directory permissions recursively to 777
[*]Restarted Ubuntu, just to make sure
[*]Disabled firewall on the testing Windows machine
[/LIST]

Same thing. Win boxes see each other, and the Ubuntu machine, but can't enter on it to list the shares. Can it be something wrong with my samba package?

---

### Post by dmizer on 2009-08-04
Try making sure that samba is in fact installed:
```
sudo aptitude install samba
```
Nautilus provides for some basic samba server/client functionality out of the box, but since you're having problems it may be better to go with the full samba server package.

Have you rebooted your router any time recently? If not, please do.

---

