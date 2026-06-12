---
title: "share a hard drive over a network"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by Flyboy712 on 2010-03-15
I am having problems sharing a NTFS hard drive over my home network.  I have 2 hard drives in a karmic machine one is the file system (ext4) the other is a extra storage drive (NTFS) and I want to share it with one other karmic machine and a windows vista machine.  I can see it on the network just cant connect to it, with either machine.  Not authorized etc...

I am guessing it is a password thing and I cant figure out how to get around it.  I can access/mount the drive with the machine it is installed in but requires my password to do it.  I would like to get rid of the password for this drive completely if I can and be able to share it with my other two computers.

I have shares enable with samba. I am able to print with all machines, (using the first karmic as a print server). 

p.s. I have tried google and the search threads with no luck.

Thanks,
Mike

---

### Post by Morbius1 on 2010-03-15
> I have shares enable with samba.What samba method are you using?
Nautilus-share ( right click > "Sharing Options")
or Classic-share

This is most likely not a samba issue but a linux permissions issue. Oddly enough we can use samba to fix it.

The easiest way out of this is to add one line to one file and restart a service. Where to add the line depends on the answer to the question above.

The NTFS partition is mounting with you as owner and permissions to access it confined to you only. You may have set up samba to allow others to access it but samba can't over rule linux file permissions. To fix it with samba AND assuming you're using Nautilus-share:

Open **Terminal**
Type **gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = flyboy
```[COLOR=Blue]*Change flyboy to your local ubuntu username.*[/COLOR]

Save the file, exit gedit, and back in the terminal type: [B]sudo service samba restart

[/B]What this will do is create a mask that will convert the remote user to you for that share.

If you're using Classic-share you need to add the force user line to the share definition itself in smb.conf

---

### Post by Flyboy712 on 2010-03-15
I did the force user = username edit and no such luck. Still no access?
I can't right click sharing option on the drive there is no option for that. I used settings- administration- samba to set up the share. 

I'm just trying to give any user full control over the drive.

---

### Post by Morbius1 on 2010-03-15
You must not be using Gnome. 

Please post the output of the following command:

**testparm -s**

---

### Post by Flyboy712 on 2010-03-15
I am using gnome I'm running Ubuntu 9.10. As soon as I get home I'll post my results. 

Thanks for the help,
Mike

---

### Post by Morbius1 on 2010-03-15
Actually, the force user in the global section will still work it's just not in the conventional place for Classic-share which is what you're using.

Also, you need to make sure the drive is mounted locally first before you try to access it remotely.

---

### Post by Flyboy712 on 2010-03-15
Here you go.  Let me know what's next.

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[Shazam]"
Processing section "[Share Drive]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = BAXTER
    server string = Home Network
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
    force user = dad

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[Shazam]
    comment = Network Printer
    path = /var/lib/samba/printers
    read only = No
    guest ok = Yes

[Share Drive]
    comment = Share Drive
    path = /media/Share Drive
    read only = No
    guest ok = Yes

---

### Post by Flyboy712 on 2010-03-15
Morbius1,

I got it going.  I think you were right with the force user =.  I had it put in the global section at the bottom of the section I moved it to just under the [GLOBAL] and it is working now.

I can access with both Vista and my other Karmic machine.  

Now if I can only convince the wife to get rid of her Vista laptop we'll be good!!:p

---

### Post by Objekt on 2010-03-16
I was messing about with this last night & noticed something possibly important.

If you open Nautilus by, for example, going to "Computer" under the "Places" menu, then right-click on one of the drives in the list on the left- there's no "sharing" option in the resulting menu.

However, if you navigate to the /media folder, all your drives are shown as folders on the right.  You can then right-click on them and choose the "Sharing" option.

My NTFS volumes are not "owned" by me (presumably this has to do with file permissions).  That was the gist of an error message that occurred when I first tried to share my NTFS volumes over the local network.  I had to edit the smb.conf file, then restart Samba, as detailed above, to share my NTFS volumes over the network.

I still can't see my Ubuntu machine on the network from a different machine running Windows XP.  Probably I got the workgroup name wrong in smb.conf or something like that.  I know the default workgroup name changed from "Workgroup" in older Windows versions to "MS Home" in Windows XP.

---

