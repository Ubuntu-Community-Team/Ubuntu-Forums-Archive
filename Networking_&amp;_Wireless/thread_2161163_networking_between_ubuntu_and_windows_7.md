---
title: "networking between ubuntu and windows 7"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by Raynor_ni on 2013-07-09
Hi all, I'm trying to network between my ubuntu desktop and my win 7 laptop.

Best results so far is I can see windows from ubuntu but all i get is connection refused and on the windows side i get nothing at all. Anyone care to render some assistance?

---

### Post by papibe on 2013-07-09
Hi Raynor_ni.

Could you explain a little bit more?

What you do mean by 'see'? Are you trying the access a share using samba/nfs, or a remote connection using ssh?

Regards.

---

### Post by Raynor_ni on 2013-07-09
yes sorry, using samba.

workgroup is set the same on both machines, tried different access settings to see if that would help but hasn't thus far.

---

### Post by papibe on 2013-07-09
Thanks.

Could you post the result of these commands from the Ubuntu machine?
```
sudo testparm

sudo smbtree
```
Regards.

---

### Post by Raynor_ni on 2013-07-09
sudo testparm gives:

```
Load smb config files from /etc/samba/smb.conf
limit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
 Processing section "[printers]"
Processing section "[print$]"
Processing section "[complete]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = LINUX
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        guest account = windows
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
        guest ok = Yes

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

[complete]
        path = /home/thomas/Downloads/complete
        valid users = windows
```

and smbtree responds with:
```
LINUX
        \\THOMAS-SYSTEM-PR              thomas-System-Product-Name server (Samba, Ubuntu
                \\THOMAS-SYSTEM-PR\print$               Printer Drivers
                \\THOMAS-SYSTEM-PR\complete       
                \\THOMAS-SYSTEM-PR\IPC$                 IPC Service (thomas-System-Product-Name server (Samba, Ubuntu))
        \\THOMAS-LAPTOP  

```

---

### Post by papibe on 2013-07-09
Thanks.
```

[complete]
        path = /home/thomas/Downloads/complete
        valid users = windows
```
Does the user 'windows' exist in your Ubuntu system? or Was it created using smbpasswd?

Is user and password being asked when you try to access the share from your Windows laptop?

Regards.

---

### Post by Raynor_ni on 2013-07-09
yes the users exists in Ubuntu and in samba. From the windows laptop all I get is a "network path cannot be found" error :(

---

### Post by CharlesA on 2013-07-09
> **Raynor_ni said:**
> yes the users exists in Ubuntu and in samba. From the windows laptop all I get is a "network path cannot be found" error :(

Try accessing the server via \\ip.address.goes.here\sharename

---

### Post by Raynor_ni on 2013-07-09
using ip address worked straight away :)

edit: changing the ubuntu machine's hostname to just "Ubuntu" made it appear in windows network.

Many thanks [**[COLOR=#C61919][B]papibe**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=774785") & [**[COLOR=#C61919][B]CharlesA**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=923868")

---

### Post by CharlesA on 2013-07-09
Huh. It shouldn't matter what name the machine has, as long as Windows can broadcast and find the IP of the server.

Was "ubuntu" already set up in DNS or something?

---

### Post by Raynor_ni on 2013-07-09
Nope don't think so.

The hostname was thomas-system-product-name from install since I couldn't be bothered to change it.

Maybe/probably its just coincidence but as soon as I changed it up pops Ubuntu in windows network. go figure .. :shrug:

---

### Post by CharlesA on 2013-07-09
Maybe. You could try pinging the old host name form Windows and see what it says. It will probably say "unknown host" but if changing the name worked, just run with it. :)

---

