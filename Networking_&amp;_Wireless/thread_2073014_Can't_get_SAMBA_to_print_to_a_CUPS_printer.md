---
title: "Can't get SAMBA to print to a CUPS printer"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by nclucid on 2012-10-18
Hi all,

I have a SAMBA server with file and printer shares (through CUPS). I can see my shares, but it seems like SAMBA is unable to communicate with CUPS to control the printer. 

Some info already:

smb.conf
```

[global]
        server string = "My Server"
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        load printers = Yes
        printing = cups
        printcap name = cups
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        security = user
        guest ok = Yes

[printers]
        comment = Home Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        public = Yes
        #printcap name = /etc/printcap
        print command = /usr/bin/lpr -P%p -r %s
        printing = cups
        guest ok = Yes

[print$]
        comment = Printer Drivers
        #path = /etc/samba/drivers
        path = /var/lib/samba/printers
        browsable = Yes
        public = Yes
        read only = Yes
        write list = admin

[music]
        comment = Music
        path = /srv/media/music
        write list = admin
        read only = Yes

[videos]
        comment = Videos
        path = /srv/media/videos
        write list = admin
        read only = Yes

[share]
        comment = File Share
        path = /srv/share
        read only = No
        writeable = Yes

```I can print a test page from the CUPS web portal just fine. What I CAN'T do is:

```

$ sudo smbclient //myserver/myprinter
Enter root's password:
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]
smb: \> echo "TESTING" | print
echo failed: NT_STATUS_IO_TIMEOUT

```As you would expect, I get a connection error when trying to add the printer in Win7. I've Googled the crap out of this but can't figure it out. 

Suggestions? Thank you!

---

