---
title: "The thing that I like most about Samba"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by DeusExM1 on 2009-06-03
is that no matter how hard You try, or how much work you put into setting it up, it will never work properly. Its like a constant challenge that keeps me busy, and tests my anger capacity from time to time. 

I recently tried to set up Samba following directions here [http://blog.taragana.com/index.php/archive/install-samba-and-share-folder-in-ubuntu-904-jaunty-jackalope/](http://blog.taragana.com/index.php/archive/install-samba-and-share-folder-in-ubuntu-904-jaunty-jackalope/)
Believe it or not this worked, but only temporarily - upon reboot i could no longer see my computer on the network, or the network itself. I also could not browse my Share. I then moved on to try this [http://www.jonathanmoeller.com/screed/?p=889](http://www.jonathanmoeller.com/screed/?p=889). Now it works on a whim : Sometimes when i reboot i can see the computer and access the shares, however 75% of the time i cannot. I noticed that *sometimes* if I wait about 5-10 minutes, and then browse the network folder it appears as configured. 



Here is the sudo test parm output:

domce@V-1500:~$ sudo testparm
[sudo] password for domce: 
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[UShare]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
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

[UShare]
    path = /home/domce/UShare
    valid users = domce
    read only = No
    guest ok = Yes
domce@V-1500:~$ 


Any ideas ?

EDIT: It seems to be working if i wait long enough. I guess you cant just start looking at the network once the computer boots. I see if i give it some time it usually shows up. So i guess thats good enough.

---

### Post by Iowan on 2009-06-03
If I recall correctly, Windows networks can take awhile for updates to propagate.

---

### Post by DeusExM1 on 2009-06-04
It seems to be working fine now if i let it load for as long as necessary. I tried to set it up on my dads machine (Which is identical to mine in every respect) and it just refuses to work. Go figure. At least it works on mine i guess.

---

