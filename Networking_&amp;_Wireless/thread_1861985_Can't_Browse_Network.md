---
title: "Can't Browse Network"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2011-10-16
I upgraded to 11.10 64-bit on my desktop, but now I can no longer browse my network.

I installed 11.10 32-bit on my server and shared some folders and can browse the network from it as well as copy files from my Windows 7 laptop to it.  I was also able to browse and see the server from my laptop and copy files from it.  When I Browse Network from my desktop, I can see the WORKGROUP folder, but can't open it.  I get the error, "Unable to mount location  Failed to retrieve share list from server".  I've rebooted my desktop and tried again without success.  I checked the Network, Network Connections, and Network Tools and everything looks ok.  I can ping the server as well as the laptop.

---

### Post by capscrew on 2011-10-16
> **HDTimeshifter said:**
> I upgraded to 11.10 64-bit on my desktop, but now I can no longer browse my network.

When I Browse Network from my desktop, I can see the WORKGROUP folder, but can't open it.  I get the error, "Unable to mount location  Failed to retrieve share list from server". 

I installed 11.10 32-bit on my server and shared some folders and can browse the network from it as well as copy files from my Windows 7 laptop to it. 

I was also able to browse and see the server from my laptop and copy files from it.  

 ...
I rearranged your thoughts for clarity.  It looks like you just need to modify the /etc/samba/smb.conf as shown below. The one caveat is: When you substitute your machine's hostname for the NETBIOS name it should be less than 15 characters long.

Add this to the [global] section of the /etc/samba/smb.conf

```
netbios name = <hostname>
name resolve order = bcast host

```
Then either restart the smbd and nmbd services or reboot the system.

You should now be able to browse the network shares.

---

### Post by Kevin Kent on 2011-10-16
Thank you this has helped solve same issue I was having. :D

---

### Post by HDTimeshifter on 2011-10-16
> **capscrew said:**
> I rearranged your thoughts for clarity.  It looks like you just need to modify the /etc/samba/smb.conf as shown below. The one caveat is: When you substitute your machine's hostname for the NETBIOS name it should be less than 15 characters long.

Add this to the [global] section of the /etc/samba/smb.conf

```
netbios name = <hostname>
name resolve order = bcast host

```
Then either restart the smbd and nmbd services or reboot the system.

You should now be able to browse the network shares.

When I searched through smb.conf, I noticed the following:
```
# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

```
Did the above cause the problem?

Your solution worked, however.  Thanks.

---

### Post by capscrew on 2011-10-16
> **HDTimeshifter said:**
> When I searched through smb.conf, I noticed the following:
```
# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

```
Did the above cause the problem?

Your solution worked, however.  Thanks.

That parameter only is in effect when the *nmbd *daemon is also functioning as a WINS server.  By default this is not the case, so the setting is irrelevant.

The following can be found [**_[COLOR="Blue"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") in the official Samba documentation.```

**dns proxy (G) **

Specifies that nmbd(8) ***when acting as a WINS server*** and finding that a NetBIOS name has 
not been registered, should treat the NetBIOS name word-for-word as a DNS name and do 
a lookup with the DNS server for that name on behalf of the name-querying client.

Note that *the maximum length for a NetBIOS name is 15 characters*, so the 
DNS name (or DNS alias) can likewise only be 15 characters, maximum.
```

---

### Post by JerryReed on 2011-10-19
I have the same issue but adding the two lines including netbios=host name (replacing the host name with that of the 64 bit machine) did not solve the issue. The host name is exactly as that of the machine and is less than 15 characters. After restarting samba I select Browse Network, then Windows Network. I get an empty screen. Yet when I go to the 32 bit machines on the network, I do the same and can see and browse all of them. One has Ubuntu Studio 11.04  and the other Ubuntu 11.10  I compared smb.conf files and they are the same except for the host name and share name.  I am obsessed, but can't seem to solve this issue.  Could it be a bug in the 64 bit version of Ubuntu 11.10?

---

### Post by capscrew on 2011-10-19
> **JerryReed said:**
> I have the same issue but adding the two lines including netbios=host name (replacing the host name with that of the 64 bit machine) did not solve the issue. 

The host name is exactly as that of the machine and is less than 15 characters. After restarting samba I select Browse Network, then Windows Network. I get an empty screen. Yet when I go to the 32 bit machines on the network, I do the same and can see and browse all of them. One has Ubuntu Studio 11.04  and the other Ubuntu 11.10  

I compared smb.conf files and they are the same except for the host name and share name.  I am obsessed, but can't seem to solve this issue.  Could it be a bug in the 64 bit version of Ubuntu 11.10?

In a word...no!  The problem is somewhere else and we need to find it.

From the 64 bit host post the output of this```

smbtree
```

From that same machine also post the output of this```
testparm -s
```

---

### Post by BHEJU on 2011-10-20
I have the same issue. I tried few things but could not make it work. I will try the suggestions in this thread.
This is what I tried:
I have a second laptop with 10.10 (32 bit) which can access the network (and network shares) without any issues. So, I backed up my current samba config file and copied the one from 32 bit machine. It still did not work. I tired to find some logs to get the error messages but could not find any in /var/log or /var/samba.

I will tweak the config file as suggested here and post results.

Thanks,

---

### Post by BHEJU on 2011-10-20
This suggestion did not work for me.
I run 64bit 11.10. Also "HOME" is the name of the server where my shares are defined.

OutPut from smbtree:

> 
smit@ELITEBOOK:~$ smbtree
Enter smit's password: 
WORKGROUP
	\\HOME           		HOME server (Samba, Ubuntu)
cli_start_connection: failed to connect to HOME<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\ELITEBOOK      		ELITEBOOK server (Samba, Ubuntu)
		\\ELITEBOOK\IPC$           	IPC Service (ELITEBOOK server (Samba, Ubuntu))
		\\ELITEBOOK\print$         	Printer Drivers
smit@ELITEBOOK:~$ 





OutPut from testparm-s

> smit@ELITEBOOK:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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
	name resolve order = lmhosts host wins bcast
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
smit@ELITEBOOK:~$ 


---

### Post by capscrew on 2011-10-20
> **BHEJU said:**
> This suggestion did not work for me.
I run 64bit 11.10. Also "HOME" is the name of the server where my shares are defined.


I don't see where you have added the following to the [global] section of the smb.conf file```
netbios name = HOME
name resolve order = bcast host
```

I do see this though and its **NOT** what you want.```
name resolve order = lmhosts host wins bcast
```

---

### Post by BHEJU on 2011-10-20
Thank you Boss. It worked. First time I edited the config file, it wasn't saved (my bad).
Now, could you tell me why do I need to hard-code the name of the server?
I want Ubuntu to discover ANY and ALL the machines on my network automatically. Is there a way to accomplish that, where I don't have to hardcode it.

Thanks again

---

### Post by capscrew on 2011-10-22
> **BHEJU said:**
> Thank you Boss. It worked. First time I edited the config file, it wasn't saved (my bad).
Don't ya just hate that.  I'm paranoid and double check if I don't get the results I expected.  LOL. > 
Now, could you tell me why do I need to hard-code the name of the server?
Well now, first you have to understand that a host that is running Samba server actually has 2 names.  The machine should have a hostname for normal Linux functions.  This name is defined in the /etc/hostname file.  This is the name you see in the default prompt (e.g. @hostname).  If this is configured correctly then Samba converts this to a NETBIOS NAME.  This is because Samba ultimately uses NETBIOS NAMES to browse shares.  Why?  Because this is how Windows SMB/CIFS works and Samba needs to integrate with Windows.

The current Samba package (Debian/Ubuntu) is installed expecting that there already is a functioning LAN nameservice.  Unfortunately most home and SOHO installs do NOT use LAN side DNS.  This means you a need to either: a) install and/or configure LAN side DNS or: b) explicitly provide the Samba server with a NETBIOS name.  When you provide the host with a NETBIOS name you need to provide a method to announce this host's presence on the network (when you boot up).  This needs to be via bcast (broadcast) as the only other option would be via host (which is DNS), therefore you need to set the name resolve order to: bcast first.  The host parameter does nothing, but if I leave it out forum users become worried so I just tell 'em to put it in after bcast.  :D

That's it in a nutshell.  There certainly is more subtleties, but that would require a much longer response.  As you have already seen, it works.    
> 
I want Ubuntu to discover ANY and ALL the machines on my network automatically. Is there a way to accomplish that, where I don't have to hardcode it.

Thanks again
Nope, no way that's going to happen.  All discovery comes from broadcasts or some sort of database inquiries.  Only NETBIOS can operate with broadcasts.  DNS requires a database and only recently has it become dynamic and liked to DHCP.  There is no magic in networking.

Sorry for the late response.  It's been a busy week.

-Capscrew

---

### Post by cherryredz on 2011-10-22
Hi, got the same error message from 1st post on this thread, upgraded my laptop from 11.04 to 11.10, network was ok to browse in 11.04 but not after upgrade. 
The laptop also dual boots into Mint11 and that and my desktop running 10.04 can access network shares with no issues.

Been using ubuntu for a few years but I'm very much a novice.

I've included info requested from others in the hope that it may also help. 

craig@craig-M7x0K:~$ hostname
craig-M7x0K
  
craig@craig-M7x0K:~$ smbtree
Enter craig's password: 
WORKGROUP
	\\NEACLOSE       		
cli_start_connection: failed to connect to NEACLOSE<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\CRAIG-M7X0K    		craig-M7x0K server (Samba, Ubuntu)
		\\CRAIG-M7X0K\HP-Photosmart-7400	HP Photosmart 7400
		\\CRAIG-M7X0K\IPC$           	IPC Service (craig-M7x0K server (Samba, Ubuntu))
		\\CRAIG-M7X0K\print$         	Printer Drivers
HOME
	\\BTHUB3         		BT Home Hub 3.0A File Server
cli_start_connection: failed to connect to BTHUB3<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED

 
craig@craig-M7x0K:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
craig@craig-M7x0



Portion of the smb.conf file, that has been identified as requiring changing below ..... also are the lines suggested to be added just added on at the end of the "global section" or are some other line(s) required to be removed and would they need a # at the begining of each added line?

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


Apologies for the long post ... just hoping someone can help.

---

### Post by capscrew on 2011-10-22
And I thought I explained it pretty good.   :-(

> **cherryredz said:**
> ...

Portion of the smb.conf file, that has been identified as requiring changing below ..... also are the lines suggested to be added just added on at the end of the "global section" or are some other line(s) required to be removed and would they need a # at the begining of each added line?

You can put the lines anywhere in the [global] section.  I would put the 2 lines at the end.  You can add it just as is appears in red below in your example.  

The # or ; tells samba to ignore the line.  it effectively makes the line a comment only.> 

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
[B][COLOR="Red"]
# you can use any name as long as it is 15 characters or less
# for a netbios name
netbios name = craig-M7x0K
name resolve order = bcast host[/COLOR][/B]


---

### Post by cherryredz on 2011-10-22
Capscrew, you probably explained it very well, but you couldn't have anticipated "the technically challenged me" trying to resolve the problem.

Thanks for quick reply, will attack the issue with renewed enthusiasm and belief when I get home from work in a few hours.

---

### Post by cherryredz on 2011-10-22
Thank you Capscrew access to network achieved.

Your patience, understanding and help is greatly appreciated, My knowledge has possibly improved ever so slightly thanks to your help.

---

### Post by bkaplan on 2011-10-27
Just another shout-out to Capscrew to say thanks for your guidance.  This helped me, too.

That being said, I don't understand what changed with the upgrade to 11.10 to require this.  I don't remember ever having to do this on my workstations in past releases.

Anyway, thanks again.

---

### Post by djuliette on 2012-01-21
capscrew

Thanks for your solution!

I just was having this exact problem and and adding:
name resolve order = bcast host

to the smb.conf file fixed it immediately.
Thanks again.

Though I'm still wondering why I had to do this. I just did a fresh install of 11.10 a few days ago and the windows share was working right out of the box and then today it just would not work.

---

### Post by DK555 on 2012-05-17
Hi there
 
hope its ok to join thread and people still using it, as this is the problem I'm currenlty having. I have installed ubuntu server 12.04 and windows 7.
 
I tried adding the code;
 
```
 netbios name = <hostname>
name resolve order = bcast host

```
 
this did make the windows pc visable on the ubuntu sever but then in the windows network, I am now un able to see the ubuntu server.
 
when I removed the code from the smb.conf the ubuntu pc becomes visable on the windows pc again??
 
Any thoughts as to what this might be would be I would be very greatful.
 
many thanks

---

### Post by DK555 on 2012-05-18
seem to work if just put line
 
```
 
name resolve order = bcast host

```
 
to smb.conf
 
:)

---

### Post by tschiel on 2013-04-02
> **capscrew said:**
> I rearranged your thoughts for clarity.  It looks like you just need to modify the /etc/samba/smb.conf as shown below. The one caveat is: When you substitute your machine's hostname for the NETBIOS name it should be less than 15 characters long.

Add this to the [global] section of the /etc/samba/smb.conf

```
netbios name = <hostname>
name resolve order = bcast host

```
Then either restart the smbd and nmbd services or reboot the system.

You should now be able to browse the network shares.

Yes, I know it's traditionally bad form to post on a thread this old. 

 I received the same error after an update on 12.04 this past week.  Prior to the update, I had no problem navigating to my NAS or other Windows 7 machines on my local network. After the update, clicking on **Browse Network** or using the **Connect to Server** form resulted in the following error: 

```


Could Not Display network:/// 

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Please select another viewer and try again.


```

Thank you for your instructions.

---

### Post by capscrew on 2013-04-03
> **tschiel said:**
> Yes, I know it's traditionally bad form to post on a thread this old....
So why did you do it?

Start a new thread and post you problem there.

---

### Post by lisati on 2013-04-03
From the [forum rules]("http://ubuntuforums.org/misc.php?do=showrules"):
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

