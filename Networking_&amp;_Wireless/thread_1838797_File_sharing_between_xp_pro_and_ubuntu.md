---
title: "File sharing between xp pro and ubuntu"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by jameshezzy on 2011-09-04
Hi,i hope this is the right place to post this. So my problem is that i have 3 machines connected to the same network,two of which run xp pro sp3 and the other runs ubuntu 11.04.i have set up samba on the ubuntu machine using the gui method as i am still not quite familiar with terminal commands.the problem is that on the xp machines they can see the samba server but cannot access it, they give this error in the attached image.to the best of my knowledge everything is correct,but of course something must wrong somewhere.i would appreciate any help and if anymore info is needed i will do my best to help provide it.Thanks

---

### Post by Morbius1 on 2011-09-04
If the machine name of your ubuntu install is in fact this:
> james-poweredge-2650No other machine can communicate with it because it's 20 characters long. It must be 15 characters or less.

The easiest way to fix this for samba purposes is through samba itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - under the "workgroup" line:
```
netbios name = poweredge-2650
```[COLOR=Blue]*Doesn't have to be that exact name but keep it at or below 15 characters.*[/COLOR]

Save smb.conf and then restart samba:
```
sudo service smbd restart
```

---

### Post by jameshezzy on 2011-09-04
> **Morbius1 said:**
> If the machine name of your ubuntu install is in fact this:
No other machine can communicate with it because it's 20 characters long. It must be 15 characters or less.

The easiest way to fix this for samba purposes is through samba itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - under the "workgroup" line:
```
netbios name = poweredge-2650
```[COLOR=Blue]*Doesn't have to be that exact name but keep it at or below 15 characters.*[/COLOR]

Save smb.conf and then restart samba:
```
sudo service smbd restart
```

ok thanks i'll try that tomorrow and see if it works.

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> If the machine name of your ubuntu install is in fact this:
No other machine can communicate with it because it's 20 characters long. It must be 15 characters or less.

The easiest way to fix this for samba purposes is through samba itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - under the "workgroup" line:
```
netbios name = poweredge-2650
```[COLOR=Blue]*Doesn't have to be that exact name but keep it at or below 15 characters.*[/COLOR]

Save smb.conf and then restart samba:
```
sudo service smbd restart
```
i have done that now and it seems to have changed it in windows but i am now getting the error:

---

### Post by Morbius1 on 2011-09-05
Disable your linux firewall if you have done anything to it.

Run the following command:
```
smbtree
```

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> Disable your linux firewall if you have done anything to it.

Run the following command:
```
smbtree
```

my linux firewall should be the same from the original ubuntu install.when i run that command this happens:
james@james-PowerEdge-2650:~$ smbtree
Enter james's password: 
WORKGROUP
	\\JAMES-POWEREDGE-		Ubuntu Server
		\\JAMES-POWEREDGE-\IPC$           	IPC Service (Ubuntu Server)
		\\JAMES-POWEREDGE-\Documents      	
		\\JAMES-POWEREDGE-\print$         	Printer Drivers
	\\IROKO001       		Mum Computer
cli_start_connection: failed to connect to IROKO001<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\0F89288E7AC74CF		James Computer
cli_start_connection: failed to connect to 0F89288E7AC74CF<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
james@james-PowerEdge-2650:~$

and i still get the same error in windows

---

### Post by Morbius1 on 2011-09-05
Post the output of the following command please:
```
testparm -s
```

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> Post the output of the following command please:
```
testparm -s
```

james@james-PowerEdge-2650:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = Ubuntu Server
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Documents]
	path = /home/james/Documents
	read only = No
	guest ok = Yes
james@james-PowerEdge-2650:~$

---

### Post by Morbius1 on 2011-09-05
You're missing the netbios line:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf 
```
Add the following line to the [global] section - under the "workgroup" line:
```
netbios name = poweredge-2650 
```
Save smb.conf and then restart samba:
```
sudo service smbd restart
```

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> You're missing the netbios line:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf 
```
Add the following line to the [global] section - under the "workgroup" line:
```
netbios name = poweredge-2650 
```
Save smb.conf and then restart samba:
```
sudo service smbd restart
```

ok i've added it in there and it shows up in the testparm -s command,but windows is still throwing up the path not found error

---

### Post by Morbius1 on 2011-09-05
Nope, a # comments the line out so samba doesn't read it. Just place the line like I posted right under the "workgroup =" line.

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> You're missing the netbios line:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf 
```
Add the following line to the [global] section - under the "workgroup" line:
```
netbios name = poweredge-2650 
```
Save smb.conf and then restart samba:
```
sudo service smbd restart
```

ok i've addded it in there and it shows up in the testparm -s comand but windows is still giving me the same error as before

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> Nope, a # comments the line out so samba doesn't read it. Just place the line like I posted right under the "workgroup =" line.

so do i need to remove the # from all the required lines in the config file?

---

### Post by Morbius1 on 2011-09-05
No

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> No

ok but i'm still getting the same error.when i change the samba config file to add the net bios in terminal it says:james@james-PowerEdge-2650:~$ gksu gedit /etc/samba/smb.conf

(gedit:2514): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3JPE1V': No such file or directory

(gedit:2514): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2514): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.27E80V': No such file or directory

(gedit:2514): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
james@james-PowerEdge-2650:~$

---

### Post by Morbius1 on 2011-09-05
But it does open gedit, yes?

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> But it does open gedit, yes?

yes

---

### Post by Morbius1 on 2011-09-05
Then ignore the error messages and add the line to smb.conf.

---

### Post by jameshezzy on 2011-09-05
> **Morbius1 said:**
> Then ignore the error messages and add the line to smb.conf.

it shows those after i've added the line,saved and closed gedit

---

### Post by Morbius1 on 2011-09-05
Run testparm -s again and verify that your netbios line has been added.

If it did then test your share.

---

### Post by jameshezzy on 2011-09-06
> **Morbius1 said:**
> Run testparm -s again and verify that your netbios line has been added.

If it did then test your share.

i just tested it today,the netbios line showed up and the share works after the windows machine had been restarted.thanks for your help.
(this is why i'm in college trying to learn this stuff :P)

---

