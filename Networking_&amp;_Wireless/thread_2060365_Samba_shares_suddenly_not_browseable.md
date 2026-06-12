---
title: "Samba shares suddenly not browseable"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by jack454 on 2012-09-20
Network consists of four computers. They are running Ubuntu 12.04, Debian 6, Bodhi 2, and Xbuntu 12.04. Everything has been normal up till today. None of them show up in any file browser. And smbtree returns nothing. smb//xxx.xxx.x.x/sharename connects fine. As a side note 2 different android phones are able to browse the network normally. As far as I know nothing has been changed in any of the config. files. Any help will be greatly appreciated.

---

### Post by Morbius1 on 2012-09-20
I suppose it's possible that all four machines don't have nmbd running. Having one machine with that problem is more likely than all four of them though. Restart the service on at least 2 of these machines and try it again:
```
sudo service nmbd restart
```[COLOR=Blue]**Note**[/COLOR]: Since 3 of these machines are either Ubuntu or Ubuntu based and since it's likely Debian is also so equipped you really don't have to browse to these machines. You can access them directly by name bypassing the Samba netbios name resolution mechanism.

Let's say the machines are named ubuntu12, deb6, bodhi2, and xubuntu12:

From ubuntu12 run the following command:
```
nautilus smb://xubuntu12.local
```When Nautilus opens up to to the Xubuntu 12.04 machine bookmark it: Bookmark > Add bookmark.

For this to work you need to make sure avahi is running: **sudo service avahi-daemon status**
And that port 5353/udp is open

One quick way to determine if all your machines are avahi compliant is to run the following command: 
```
avahi-browse -at
```It will list all of the machines that can be accessed via this hostname[COLOR=Blue].local[/COLOR] mechanism.

---

### Post by jack454 on 2012-09-20
Thanks for the reply. Restarting nmbd didn't help. The machines can all connect with the second command. And the third command shows all connected machines, including one of the phones. Do you have a suggestion how I can get things working like before. Thanks again for the help.

---

### Post by Morbius1 on 2012-09-20
If you want the standard way to work I'll need more information. Please post from whatever machine you are on the output of the following commands:
```
smbtree
``````
net usershare info --long
```[COLOR=Blue]**EDIT**[/COLOR]: Sorry, forgot the most important one that I need to see:
```
testparm -s
```*As a side note: I can show you a way to have all these machines show up in "Browse Network" using the Avahi way if you are interested.*

---

### Post by jack454 on 2012-09-20
Here is output from first command.
```
jack@jack-g7:~$ smbtree
Enter jack's password: 
jack@jack-g7:~$]
```Here is the second.
```
jack@jack-g7:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/public is not a well formed usershare file.
info_fn: Error was Path is not a directory.
jack@jack-g7:~$
```

Here is third.
```
jack@jack-g7:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[jack]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = CEL
    server string = %h server (Samba, Ubuntu)
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
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[jack]
    path = /home/jack
    valid users = jack
    read only = No
jack@jack-g7:~$ 
```

---

### Post by Morbius1 on 2012-09-20
I don't see anything wrong with your smb.conf. Try disabling your firewall if you did anything with it and try it again.

If that doesn't work edit smb.conf and add a line under the workgroup line:
```
name resolve order = bcast lmhosts host wins
```Then restart the samba services again:
```
sudo service smbd restart
sudo service nmbd restart
```Wait about 5 minutes or so and run smbtree again. You need to at least see the the name of the machine you are running on.

---

### Post by jack454 on 2012-09-20
There are no firewalls running except on the router. Added line to smb.conf and restarted services. smbtree returns the same output.
```
jack@jack-g7:~$ smbtree
Enter jack's password: 
jack@jack-g7:~$
```Did this on Ubuntu 12.04 and Debian with same results.
Is it possible the router could be causing this?
DHCP is on in the router, but I have each systems IP reserved.

---

### Post by Morbius1 on 2012-09-20
This is strange problem. Unless you are consistently doing something odd to each one of these machines it would suggest that the router is somehow blocking netbios name transfer but why today and not yesterday.

smbtree either gives you the correct list or it outputs errors. The only time it produces nothing in my experience is when smbd and nmbd are not running but that's not the case here. I'll try to reproduce this error in a VM and see what I can find out. 

In the mean time you might try something different:

Create a file as root:
```
gksu gedit /etc/avahi/services/samba.service
```And add this to the file:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">SMB %h</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```After you save the file open Nautilus > Browse Netork.

You should see a "SMB jack-g7". See if that works.

---

### Post by jack454 on 2012-09-20
I created the file and SMB jack-g7 shows up in nautilus. And I don't understand why the problem started suddenly. As far as I know nothing has been changed on the computers or the router. Also I wonder why the android phones can browse the network like normal.
Thank you very much for you time and help.

---

### Post by jack454 on 2012-09-20
Morbius1 thanks for the help. It appears something has gone screwy with my router. I hooked up an old netgear and everything is back to normal. Don't know why I didn't try that first. Anyway thanks very much. I learned some new things from your help. ):P

---

### Post by JKyleOKC on 2012-09-20
Just a FYI, mainly for Morbius1: I was getting the same no-results response from smbtree, and discovered that inputting the command as ```
smbtree -N -d=10
```gave enough output to show me where things were running into trouble. The "-N" suppresses the password prompt, and the "-d=10" causes the maximum amount of debugging output to appear at the terminal. This includes all internal error messages.

In my case, the program's attempt to get the full list of hosts on the network was failing when trying to connect to the master browser via port 139. That led me to look more closely for a firewall at either end of the connection, but finally restarting the smbd daemon solved my problem.

Your trouble was probably caused differently, although the router might have been blocking any or all of ports 445, 137, and 139 and thus preventing smbtree from getting the data -- and also preventing the browsing!

---

### Post by jack454 on 2012-09-20
> **JKyleOKC said:**
> Just a FYI, mainly for Morbius1: I was getting the same no-results response from smbtree, and discovered that inputting the command as ```
smbtree -N -d=10
```gave enough output to show me where things were running into trouble. The "-N" suppresses the password prompt, and the "-d=10" causes the maximum amount of debugging output to appear at the terminal. This includes all internal error messages.

In my case, the program's attempt to get the full list of hosts on the network was failing when trying to connect to the master browser via port 139. That led me to look more closely for a firewall at either end of the connection, but finally restarting the smbd daemon solved my problem.

Your trouble was probably caused differently, although the router might have been blocking any or all of ports 445, 137, and 139 and thus preventing smbtree from getting the data -- and also preventing the browsing!

Thanks for this information.

---

