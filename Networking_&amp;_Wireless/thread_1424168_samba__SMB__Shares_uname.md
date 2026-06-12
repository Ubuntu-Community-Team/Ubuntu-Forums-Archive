---
title: "samba / SMB / Shares/ uname"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by RasterBurn on 2010-03-07
hey there, i am just wondering something, its not a real big issue that i am wondering about, just a minor detail with a simple work around... anyways,my network is setup nicely the way i like it at the moment, my wifes computer runs ubuntu with samba, my computer runs ubuntu with samba and my son's laptop runs win xp, my wife and i can transfer files back and forth to our hearts content, my son on the other hand can send files to my computer but no where else in the network (nor can i send files to him) what I have stated is a minor issue to not worry about at the moment (I dont get my son that often) that covers the samba /smb / shares part of the network, now as goes the uname part, someone on the network sends a file to my computer, i go into my public folder that sits in my home folder and it has a lock in the top right corner of the file, i go into the properties and permissions and it shows nobody / nogroup as the owner of the file... a simple fix would be to change the permissions of the files via root...

what i am wondering is which of the 3 options are more viable and secure:
1) add my user account to the group "nogroup"
2) set samba to use my uname and group?
3) add "nobody" to my group on the computer?

---

### Post by Morbius1 on 2010-03-07
Please post the output of the following commands from the machine that has the "nobody" file:

**net usershare info**
[B]testparm -s

[/B]There may be a 4th option

---

### Post by RasterBurn on 2010-03-07
well, i dont think the output is really all that important seeing as we dont transfer with passwords each computer has a different account and a different password for login but anyways

```
michael@michael-desktop:~$ net usershare info
[public]
path=/home/michael/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

```
michael@michael-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
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

```

---

### Post by Morbius1 on 2010-03-07
One option is the following:

Open **Terminal**
Type **gedit /etc/samba/smb.conf**

Add the following line to the[COLOR=Blue]** [global]**[/COLOR] section of smb.conf:
```
 force user = michael
```Save the file, exit gedit, and back in the terminal type: **sudo service samba restart**

When the remote guest ( nobody ) saves the file, the ownership will be converted by "force user = michael" to you.

[COLOR=Blue]EDIT: The reason I asked for both commands was to see which method of sharing you where using. Since you're using Nautilus-share the force user has to go into the global section.[/COLOR]

---

