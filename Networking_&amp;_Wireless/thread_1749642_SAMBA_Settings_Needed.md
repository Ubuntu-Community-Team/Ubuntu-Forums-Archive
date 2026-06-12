---
title: "SAMBA Settings Needed"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by stevedude on 2011-05-04
Background: I initially upgraded from Maverick to Natty and found Natty broke my previous system. I did a clean install of Natty and in doing so, Ubuntu no longer connects to my Windows 7 shares in a home workgroup setting. I have not installed a firewall at this time and the Windows 7 desktop has not changed, only my installation of Natty.

I have 1 Desktop with Windows 7 Professional that a printer is connected to. I have a second Desktop that is running Ubuntu Natty. I have a Laptop that is also running Ubuntu Natty. I am able to connect both Ubuntu systems (the one desktop and the one laptop) to each other; The Ubuntu systems cannot access the Windows 7 shares and the printer connected to it.

Enclosed is my SAMBA "testparm" results. I'm looking for assistance on what settings I need to tweak/delete/add in order to connect to the Windows 7 system. Is there possibly a file(s) in the repository that was not installed by default that I may need?

Thanks in advance for taking the time to look this over and assist me.

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = FAMILY
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
    name resolve order = lmhosts host wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    valid users = steve, @steve

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = Yes

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by doas777 on 2011-05-04
well, start by setting wins support to no. setting it to yes tells it that it is the wins server.

one thing I've done in past, for clients, was to turn on:
```
client NTLMv2 auth = yes
```
but that shouldn't be needed these days.

---

### Post by stevedude on 2011-05-04
Thanks doas777 !!!

That did the trick. I can see the Windows 7 shares now. I did not need to use the "client NTLMv2 auth = yes", I only commented-out the WINS Support statement.

I do have an issue that the printer on the Windows 7 system is not viewable when I use the Print Setup program. When I choose NETWORK PRINTER > WINDOWS PRINTER via SAMBA > BROWSE, I receive an error "NO PRINT SHARES - There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration."

I'll open up a new thread for that one.

Your time/assistance is greatly appreciated.

---

