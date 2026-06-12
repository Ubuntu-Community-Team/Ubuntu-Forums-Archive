---
title: "SMB Share"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by RRahl on 2010-06-15
I have given this my best effort but seem to be failing at every corner. Hoping someone here can help me.  What I have is a plain vanilla install of Ubuntu 10.4 with all updates and samaba3 installed.
ALL I want to do is create a share Accessible from windows 7, 2003 and 2008.  That is it, no fancy restrictions, no synchronizing, nothing. 
However this seems to be a MONUMENTAL task in 10.4.  Compounded by likewise not being compatible.
I have a windows box that is a member of domain.com and my Ubuntu box is a vanilla install in WORKGROUP.
I have been through:
[http://oreilly.com/catalog/samba/chapter/book/ch04_06.html](http://oreilly.com/catalog/samba/chapter/book/ch04_06.html)
[http://www.samba.org/samba/docs/Samba24Hc13.pdf](http://www.samba.org/samba/docs/Samba24Hc13.pdf)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)
and a number of others.  
I have created shares in smb.conf and tried to create a share through the GUI on the desktop and sharing it. I have tried editing the hosts.allow file to contain my subnet as well and created allow IPs in SMB.conf.

In every case I get rejected as:
"The account is not authorized to log in from this station."
at one time I was able to get prompted for a username and password but it would then give me another error that I cannot remember.  I have even tried a variety of known working smb.conf files from people in forums.
Can someone please help me?  I cannot imagine that this is supposed to be this difficult.  I haven't tried rolling back to 9.4 yet to see if it is some new security feature.

---

### Post by 4llf0rn0t on 2010-06-15
Hi can you post the result of
 ```
sudo netstat -llptun
``` 
and testparm


thanks

---

### Post by RRahl on 2010-06-16
sorry wasnt notified of your post :)
-----------[TESTPARM]-----------------

acton_it@odin:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	interfaces = 192.168.10.101/255.255.255.0
	bind interfaces only = Yes
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
	hosts allow = 192.168.20., 192.168.10., localhost

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

[Test]
	comment = Test Share
	path = /home/acton_it/Desktop/Test
	force user = root
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes
	locking = No
acton_it@odin:~$

---

### Post by RRahl on 2010-06-16
------------------[NETSTAT]----------------------------

acton_it@odin:~$ sudo netstat -llptun
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.10.101:139      0.0.0.0:*               LISTEN      829/smbd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1775/cupsd      
tcp        0      0 192.168.10.101:445      0.0.0.0:*               LISTEN      829/smbd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1775/cupsd      
udp        0      0 0.0.0.0:54586           0.0.0.0:*                           782/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           782/avahi-daemon: r
udp        0      0 192.168.10.101:137      0.0.0.0:*                           1104/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1104/nmbd       
udp        0      0 192.168.10.101:138      0.0.0.0:*                           1104/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1104/nmbd       
acton_it@odin:~$

---

### Post by 4llf0rn0t on 2010-06-17
Hi,

I assume you have added your system user (acton_it) to samba  using **smbpasswd -a acton_it**?

Could you please try this on a terminal: ```
acton_it@odin:~$**smbclient //localhost/Test -U acton_it**
```

while tailing the results of your samba log on another terminal
```
acton_it@odin:~$**sudo tail -f /var/log/samba/log.odin** or **sudo tail -f /var/log/samba/192.168.10.101**
```

Thanks

---

### Post by RRahl on 2010-06-17
Thanks for your reply

--------------------[SMBCLIENT]--------------------------
acton_it@odin:~$ smbclient //localhost/Test -U acton_it
Enter acton_it's password: 
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)
acton_it@odin:~$ 

with IP instead of localhost
acton_it@odin:~$ smbclient //192.168.10.101/Test -U acton_it
Enter acton_it's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]
smb: \>

127.0.0.1 and Odin do not work either
--------------------[TAIL]-------------------------------

acton_it@odin:~$ sudo tail -f /var/log/samba/log.odin
[sudo] password for acton_it: 
[2010/06/15 14:40:54,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/test failed. Permission denied
[2010/06/15 14:40:54,  1] smbd/service.c:1063(make_connection_snum)
  odin (::ffff:127.0.0.1) connect to service test initially as user Test (uid=1001, gid=1001) (pid 2316)
[2010/06/15 14:41:16,  1] smbd/service.c:1240(close_cnum)
  odin (::ffff:127.0.0.1) closed connection to service test
^C
acton_it@odin:~$

---

### Post by 4llf0rn0t on 2010-06-17
Hi

There seems to be nothing unusual with your log. Anyways, are you running an Active Directory domain?

[https://help.ubuntu.com/9.04/serverguide/C/samba-ad-integration.html]("https://help.ubuntu.com/9.04/serverguide/C/samba-ad-integration.html")

---

### Post by RRahl on 2010-06-17
I am in an AD forest yes,  2008R2,  however the ubuntu box itself is not a member.

---

### Post by 4llf0rn0t on 2010-06-17
Hi. 

Maybe you need to read on Likewise Open [https://help.ubuntu.com/9.04/serverguide/C/likewise-open.html]("https://help.ubuntu.com/9.04/serverguide/C/likewise-open.html")

and 
How to add Ubuntu to Active Directory Domain
[http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html]("http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html")

and
How to Integrate windows Active Directory and Samba in Ubuntu
[http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html")

---

### Post by RRahl on 2010-06-17
Thanks for the suggestion, but I have already been down that road:
[http://ubuntuforums.org/showthread.php?t=1455924](http://ubuntuforums.org/showthread.php?t=1455924)
I think 10.04 might be a release I skip.  Going back to 9 right now to see if it fixes the issues.

---

### Post by RRahl on 2010-06-18
Tried 9.04 and still isn't working. However, 9.04 is a lot easier to work with than 10.  I think I need to research what was changed with the init.d directory.  Much nicer to be able to restart the services with a simple "sudo /etc/init.d/samba restart" why doesn't this work in 10?
Anyway so an idea I have is that I force all machines to use NTLMv2.  From what I read Samba does NTLMv2 naively.  However, do I need to disable LM communication?  All Google searches for "The Account is not authorized to log in from this station samba" turns up the same thing...password encryption.  
Any thoughts on this?

---

### Post by RRahl on 2010-06-21
No ideas here?  Do I need to start a new thread with this new information?

---

