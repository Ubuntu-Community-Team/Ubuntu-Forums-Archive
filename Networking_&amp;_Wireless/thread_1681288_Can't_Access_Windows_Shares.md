---
title: "Can't Access Windows Shares"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by ConLoco76 on 2011-02-03
Running Ubuntu 10.10 M-M

Running Network, my machine sees my Windows Workgroup, and even the machines on the workgroup. 

But...

When I try to access those machines, I get a message "Failed  to retrieve share list from server."

I've been able to mount other machines by using straight IP accesss, but that is of little use since IP addresses are not Static. 

Any instructions/advice/hints?

Cold Canadian...:p

---

### Post by papibe on 2011-02-03
Could you post the result of the following command?
```
$ testparm
```
Regards.

---

### Post by ConLoco76 on 2011-02-04
[global]
    workgroup = JANSSEN HOME
    server string = UServer
    encrypt passwords = No
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

[Test Folder]
    path = /home/stephen/Desktop/Test Folder
    read only = No
    guest ok = Yes

---

### Post by dmizer on 2011-02-04
Please see the 6th link in my sig. :)

---

### Post by Morbius1 on 2011-02-04
You do have one error in your smb.conf that needs fixing:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Change the following line from this:
>      encrypt passwords = No
to this:
>      encrypt passwords = **[COLOR=Blue]Yes[/COLOR]**
Save the file and restart samba:
```
sudo service smbd restart
```

---

### Post by ConLoco76 on 2011-02-04
Hmmmm..


I don't passwords among the wired machines in my Workgroup. Since I don't use them, is there a reason I have to have them encrypted?

---

### Post by ConLoco76 on 2011-02-04
Thanks dmizer, your process worked. Problem solved!

---

