---
title: "File Sharing"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by robn30 on 2012-02-18
I have two Linux machines and am trying to file share between them.  One is wired and the other is wirelessly connected.  I can't get either one to see the other.  Hopefully someone can explain the steps to do this.  I have Samba installed but don't know if it is needed or not since it is two Linux machines.  If there is already some instructions out there please point me to them.  Thanks.

---

### Post by papibe on 2012-02-18
Could you post these commands from both machines?
```
ifconfig

testparm
```
Regards.

---

### Post by SteveDee on 2012-02-19
> **robn30 said:**
> I have two Linux machines and am trying to file share between them....  If there is already some instructions out there please point me to them.  Thanks.

You've posted under Lubuntu, so take a look at this: [http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba](http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba)

The procedure in post #1 works for versions 10.10 to 12.04alpha.

---

### Post by robn30 on 2012-02-19
> **SteveDee said:**
> You've posted under Lubuntu, so take a look at this: [http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba](http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba)

The procedure in post #1 works for versions 10.10 to 12.04alpha.

I meant Ubuntu but I will look at the post anyway, it could be helpful.  Thanks.

---

### Post by Morbius1 on 2012-02-19
If this is Ubuntu and not Lubuntu you can create Samba shares directly from the File Manager - Nautilus.

As far as not being able to see the other machines we need to understand what you have done so far so please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```
```
smbtree
```

---

### Post by robn30 on 2012-02-19
> **Morbius1 said:**
> If this is Ubuntu and not Lubuntu you can create Samba shares directly from the File Manager - Nautilus.

As far as not being able to see the other machines we need to understand what you have done so far so please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
``````
hostname
``````
smbtree
```

Ok so I can see the other machines shared folders if I go to Nautilus--> select connect to server--> change it to Windows Share and set server to smb://ip address of machine in question.  Shouldn't I be able to just select browse network and see this shared folder?  I will post the data requested in the following post.  Thanks.

---

### Post by robn30 on 2012-02-19
[COLOR=Red][COLOR=Black]BTW to be exact with the Linux version it is Linux Mint 12 which is based off Ubuntu Oneiric 11.10.  This is from the machine that is sharing the folder DT-Videos.  Thanks.[/COLOR]
**_testparm -s_**[/COLOR]
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[DT-Videos]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, LinuxMint)
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
    read only = No
    guest ok = Yes

[DT-Videos]
    path = /home/rob/Videos
    read only = No
    guest ok = Yes

[COLOR=DarkOrange]**_net usershare info --long_**[/COLOR]
[dt-videos]
path=/home/rob/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=n


[COLOR=RoyalBlue]_**hostname**_[/COLOR]
rob

[COLOR=DarkGreen]_**smbtree**_[/COLOR]
WORKGROUP
    \\ROB                    rob server (Samba, LinuxMint)
        \\ROB\Print_to_PDF       Print to a PDF File
        \\ROB\Photosmart-8200-series    HP Photosmart 8200 series
        \\ROB\print$             Printer Drivers
        \\ROB\DT-Videos          
        \\ROB\IPC$               IPC Service (rob server (Samba, LinuxMint))

---

### Post by Morbius1 on 2012-02-19
[1] smbtree only shows ROB and it doesn't even report any errors. Is the other machine on the network? If it is then turn off all firewalls on both machines and try smbtree again.

[2] There are two ways to create a samba share:
This is a Classic share:
> [DT-Videos]
    path = /home/rob/Videos
    read only = No
    **[COLOR=Blue]guest ok = Yes[/COLOR]**This is a Samba Usershare:
> [dt-videos]
path=/home/rob/Videos
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]**guest_ok=n**[/COLOR]You can see that who can access that share differs between the two and I have no idea who samba is listing to for direction so I would get rid of one or the other. Just use whatever method you used to create the share to "un-share" it.

---

### Post by nothingspecial on 2012-02-19
> **robn30 said:**
> I meant Ubuntu

Fixed  :)

You should use ssh, you don't need samba to connect 2 linux machines.

Install openssh-server on both machines. Then use nautilus to connect from the menu, file > connect to server.

For information on securing ssh, see here

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by robn30 on 2012-02-19
> **nothingspecial said:**
> Fixed  :)

You should use ssh, you don't need samba to connect 2 linux machines.

Install openssh-server on both machines. Then use nautilus to connect from the menu, file > connect to server.

For information on securing ssh, see here

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

I already have them connected via SSH for remote desktop operations.  I was just wanting to quickly access the other machines shared files.  I also used the same method you just mentioned to create a Windows Share bookmark which now lets me access the files without having to connect to the server every time.  I still believe the shared folders should appear under the Browse Network area but maybe I am wrong.  Unless Linux Mint has a built in firewall I am not running one on either machine.  I do not have firewall enabled either.

---

### Post by Morbius1 on 2012-02-19
Run the following command from rob:
```
nautilus smb://192.168.0.100
```
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the other machine.*[/COLOR]

Do you gain access and get a list of available shares or do you get an error message?

---

### Post by robn30 on 2012-02-19
> **robn30 said:**
> I already have them connected via SSH for remote desktop operations.  I was just wanting to quickly access the other machines shared files.  I also used the same method you just mentioned to create a Windows Share bookmark which now lets me access the files without having to connect to the server every time.  I still believe the shared folders should appear under the Browse Network area but maybe I am wrong.  Unless Linux Mint has a built in firewall I am not running one on either machine.  I do not have firewall enabled either.

I now see what you mean using the SSH method.  It does work quite well, and I once again set a bookmark in Nautilus and it works perfect.  I always have done Remote Desktop stuff and didn't know about the file browsing using Nautilus.  Thanks for the information.

---

### Post by robn30 on 2012-02-19
> **Morbius1 said:**
> Run the following command from rob:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the other machine.*[/COLOR]

Do you gain access and get a list of available shares or do you get an error message?

Using that command works with no errors.  It shows the directories I have shared.  So the sharing is working, I just can't see it via browse network.

---

### Post by Morbius1 on 2012-02-19
> Using that command works with no errors.  It shows the directories I  have shared.  So the sharing is working, I just can't see it via browse  network.     This is a netbios name resolution problem although smbtree should have given you an error message that told you that ( after a fair amount of interpretation ).

If you're still interested in pursuing this:

Check the hostname of the other box and count the number of characters. If it 15 or less than that's not the problem. If it's 16 or more then it's too long - at least for samba. You can correct that in smb.conf if you want.

You also might want to see if the name server is running on the other box:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```Even if these are the problems it's still odd that smbtree did not give you an error.

---

