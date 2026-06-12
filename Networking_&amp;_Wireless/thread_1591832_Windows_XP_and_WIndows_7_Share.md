---
title: "Windows XP and WIndows 7 Share"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by atlantajake on 2010-10-09
I recently decided to try out Ubuntu and to be honest the installation was easy and everything worked including printing to Windows Shared Printers and Windows Files Servers and then after two days of everything working fine the network connection to Windows stopped. Now I can't see any windows networks, no windows shares and no windows printers.
 
I have edited the /etc/samba/smb.conf file to include my Windows Workgroup name and added a "netbios name = workstation name" entry.
 
I have re-installed Ubuntu several times today on different machines just to see if the problem persist, it does. No hardware changes of any kind and all the Windows units are working normally.
 
I can ping windows computers from my Ubuntu workstations but that is about it.
 
My question.
 
- How does one configure samba to allow Ubuntu to connect to Windows File servers and Printers. I have found some documents on the Internet regarding this but it is not complete.
- I installed a GNOME Network Manager applet but I don't know how access it, the doc's it is in the system tray yet I don't see it. I must be overlooking the obvious. If someone could tell me how to access it that would be great.
- I tried to connect directly to the Windows server by going to "Places-connect to server" and typing in the server name and share name to no avail.
- Lastly for the heck of it I put new network adapter in the machine with the same results.
 
I guess that is it and thank in advance for helping.

---

### Post by capscrew on 2010-10-10
> **atlantajake said:**
> I recently decided to try out Ubuntu and to be honest the installation was easy and everything worked including printing to Windows Shared Printers and Windows Files Servers and then after two days of everything working fine the network connection to Windows stopped. Now I can't see any windows networks, no windows shares and no windows printers.
 
I have edited the /etc/samba/smb.conf file to include my Windows Workgroup name and added a "netbios name = workstation name" entry.
 
I have re-installed Ubuntu several times today on different machines just to see if the problem persist, it does. No hardware changes of any kind and all the Windows units are working normally.
 
I can ping windows computers from my Ubuntu workstations but that is about it.
 
My question.
 
- How does one configure samba to allow Ubuntu to connect to Windows File servers and Printers. I have found some documents on the Internet regarding this but it is not complete.

This would make the Ubuntu host a client of the Windows Server.  The package for this is *"smbfs"*.  This package should have been part of the default installation.  This is a set of utilities that allows Ubuntu to mount Windows shares. Check the Synaptics package manager for *smbfs* and make sure it is still installed.  > 
- I installed a GNOME Network Manager applet but I don't know how access it, the doc's it is in the system tray yet I don't see it. I must be overlooking the obvious. If someone could tell me how to access it that would be great.
Network manager has nothing to do with Samba or Windows Shares.  N-M automates the IP connections for Ethernet and Wireless. > 
- I tried to connect directly to the Windows server by going to "Places-connect to server" and typing in the server name and share name to no avail.

Try this again using the IP address of the Windows server instead of its COMPUTERNAME. Example: //IP_Address/share > 
- Lastly for the heck of it I put new network adapter in the machine with the same results.
 
I guess that is it and thank in advance for helping.
If you have a firewall running, try turning it off while you are testing.  If this solves the problem then you will need to configure it to have the following TCP/UDP ports open: 137,138,139 and 445.  On the Windows Server, I believe this is a Windows Network Discovery and File Sharing setting.

In the end the Samba Server on the Ubuntu machine is for sharing files FROM the Ubuntu host.  The smb.conf file is for configuring this server.  Not really relevant if you only have shares on a Windows server.

Think Client/Server:
[LIST]
[*]Client = [COLOR="DarkGreen"]**Requesting**[/COLOR] a service (File Shares)
[*]Server = [COLOR="Red"]**Providing **[/COLOR]a service (Hosting the File Share)
[/LIST]

---

### Post by atlantajake on 2010-10-10
Well - I installed smbfs and then I got a network hub out of storage and connected one Ubuntu machine and one Windows box, rebooted all of course. Problem persist Ubuntu still can not see the windows box and Ubuntu is ignoring the smb.conf file. I say it is ignoring because at the very least the unit should recognize the workgroup defined in smb.conf and it doesn't.

---

### Post by atlantajake on 2010-10-10
Lastly, I tried to connect to the windows share by using the IP address and it failed as well.

---

### Post by capscrew on 2010-10-11
> **atlantajake said:**
> Well - I installed smbfs and then I got a network hub out of storage and connected one Ubuntu machine and one Windows box, rebooted all of course. 
How was it connected before?  Did you loose the ability to ping between the Ubuntu host and the Windows Server?
> 
Problem persist Ubuntu still can not see the windows box and Ubuntu is ignoring the smb.conf file. I say it is ignoring because at the very least the unit should recognize the workgroup defined in smb.conf and it doesn't.
Is the the workgroup you defined in the smb.conf file different from what is defined in the WIndows Server? > 

[QUOTE=atlantajake]Lastly, I tried to connect to the windows share by using the IP address and it failed as well.
But you can still ping between hosts?

Are both of the hosts on the same subnet?  What is the IP address and subnet mask of the Ubuntu client and Windows Server?

Please post the results of the following from the command line```
testparam -s
```

Is Samba running on Ubuntu?  Post the results of this```
ps -ef | grep mbd
```

---

### Post by apocolpse on 2010-10-13
I am having the same issue too. Here is the output of mine. 

> 
ps -ef | grep mbd
root      5521     1  0 Oct12 ?        00:00:00 nmbd -D
root      5572     1  0 Oct12 ?        00:00:00 smbd -F
root      5575  5572  0 Oct12 ?        00:00:00 smbd -F
root      5656  5572  0 Oct12 ?        00:00:00 smbd -F
cecil     7532  7448  0 19:37 pts/0    00:00:00 grep --color=auto mbd



> 
testparm -s
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


I can ping the machines. My Ubuntu workgroup is the same as my windows workgroup. The netbios name in the smb.conf is set to my host name. I still can't connect

---

### Post by capscrew on 2010-10-13
> **apocolpse said:**
> I am having the same issue too...

That you have the same issue does not necessarily mean you have the same root cause.

The output you posted looks fine.  It appears that you are using Nautilus generated usershares.  The configuration files are at /var/lib/samba if I'm not mistaken.  I don't use this type of share so I have no advice one way or another.> 

I can ping the machines. My Ubuntu workgroup is the same as my windows workgroup. The netbios name in the smb.conf is set to my host name. I still can't connect
You should not hijack the OP's thread.  Start your own.  Post what you have (how you installed and created the shares) and what you have done try and fix it.

---

### Post by apocolpse on 2010-10-17
Sorry .. figured we shared the same issue

---

### Post by inobe on 2010-10-17
i want to know how samba was installed and configured, yes, tell us what you did and please include your smb.conf.

also tell us how they are connected whether or not they are wired or wireless.

if it's ics or hoc forget it.

---

### Post by inobe on 2010-10-17
> **apocolpse said:**
> I am having the same issue too. Here is the output of mine. 








I can ping the machines. My Ubuntu workgroup is the same as my windows workgroup. The netbios name in the smb.conf is set to my host name. I still can't connect

skip what you have already installed and configured.

this works for me no matter what.

install samba

```
sudo apt-get install samba
```

we need to create a samba user name and password in order for outsiders to access your kubuntu/ ubuntu shares, be sure to replace username with actual user name.

```
sudo smbpasswd -a username
```

we need to make a shared folder that outsiders will have access to, you can name the shares folder to any name you want' just don't forget about adding your actual user name to that path

```
mkdir /home/username/shares
```

we need to backup your current smb.conf encase you didn't follow these direction well' you can at least fix what is broken.

```
sudo cp /etc/samba/smb.conf ~
```

now lets edit your smb.conf

```
sudo gedit /etc/samba/smb.conf
```

when gedit opens up with your smb.conf' scroll down to the end and add this replacing username with your actual user name.

```
[shares]
path = /home/username/shares
available = yes
valid users = username
read only = no
browsable = yes
public = yes
writable = yes
```

now lets restart samba

```
sudo /etc/init.d/samba restart
```

lets test for errors

```
testparm
```

that command will check smb.conf for errors, if the output says "loaded services file ok" you are in good shape.

if you have problems even after restarted network services or rebooting it's a windows issue, these issues can be easily remedied.

---

