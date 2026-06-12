---
title: "Samba - large share - clients don't see all files."
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by RoosterHam on 2012-12-10
Summary: I have an Ubuntu 12.04 server, Samba version 3.6.3. One share is a single folder containing 601 files. Accessing the share from my Ubuntu/Mint clients only lists 524 files.

Details: The 601 files I am trying to share reside on a 1.4TB xfs partition/LV. When first set up I could only see 124 files, most of them uppercase+mangled. At this stage I added 'mangle case = no', 'mangled names =no', 'mangled stack = no', 'fstype = Samba', 'hide dot files = no', 'hide special files = no', 'hide unreadable = no', 'hide unwriteable files = no', 'protocol = NT1'. That bumped the visible files up to 524. testparm told me the 'mangle/d' options don't mean or do anything so commented them out... still 524 of 601 files visible.

Guessing that the fix will be some option in the [global] segment, I have been scouring the interweb for clues as to what will help. No luck yet...

Motive: While this particular share can be migrated to NFS (so much easier to configure and secure) I do have Windows users that would benefit from access to this share (read-only) and whom I will continue to provide separate network storage shares per user. I also don't want this to become an issue they bring to me regarding their network shares either.

Question: What is causing this mangle/hide behaviour? is the 'mangle stack = ' option replaced or removed? should Samba be right for 'fstype="? what about 'protocol = NT1'?

Thank you in advance.

---

### Post by RoosterHam on 2012-12-10
contents of smb.conf
```

[global]
        server string = D@### C0###
        workgroup = D###
        security = user
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
        ;usershare allow guests = no
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        ;mangle case = no
        ;mangled names = no
        ;mangled stack = no
        fstype = Samba
        hide dot files = no
        hide special files = no
        hide unreadable = no
        hide unwriteable files = no
        protocol = NT1


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

[e###-storage]
        comment = Space on the IBM server for E### to store or backup files
        path = /mnt/set0/backups/e###
        create mask = 0750
        browseable = yes
        guest ok = no
        ;read only = no
        read list = e###
        write list = e###
        admin users = r###

[h###-backup]
        comment = Space on the IBM server for H### to store or backup files
        path = /mnt/set0/backups/h###
        create mask = 0750
        browseable = yes
        guest ok = no
        ;read only = no
        read list = h###
        write list = h###
        admin users = r###

[shared-movies]
        comment = Shared Movies
        path = /home/samba/Film
        create mask = 0750
        browseable = yes
        guest ok = no
        ;read only = no
        read list = m###, e###, h###, r###
        write list =
        admin users = r###

[shared-tvshows]
        comment = Shared TV Shows
        path = /home/samba/Television
        create mask =0750
        browseable = yes
        guest ok = no
        ;read only = no
        read list = m###,e###,h###,r###
        write list =
        admin users = r###


```

---

