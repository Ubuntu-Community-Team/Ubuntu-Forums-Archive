---
title: "samba sharing - filtering problems"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by fx69 on 2013-01-14
Hello!

I'm trying to set 2 computers with ubuntu 12.04 to work with samba and network sharing. 
Both connect router. One by wifi (ubuntu2) and the other (ubuntu1) has standard wire connection. After great struggles I found that on ubuntu1 there are closed ports which samba uses (tcp: 139 and 445) so opened them in ubuntu firewall (gufw). I can successfully ping ubuntu2 from ubuntu1 and vice versa:

```
sudo nmap -sS -p 138-446 192.168.0.103

Starting Nmap 5.21 ( http://nmap.org ) at 2013-01-14 19:25 CET
Nmap scan report for 192.168.0.103
Host is up (0.059s latency).
Not shown: 307 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
MAC Address: 90:F6:52:16:1B:3C (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 0.44 seconds
```I cant get to workgroup on network - it gives me error. However I can access it after calling:

```
nautilus smb://192.168.0.103
```Now I see the shared folders on another system, but cant browse them. It brings the password prompt but nothing suits...  ](*,) This happens on either ubuntu1 and ubuntu2.
I created the accounts on both systems and added them in samba.

Please, I beg you, help me! I've been working on it for 3 days with no results...

Here's my smb.conf from ubuntu1

```
sudo testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[root]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = ubuntu-parter
    interfaces = 127.0.0.0/8, eth0
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

[root]
    comment = root-parter
    path = /root
    valid users = fx69, ubuntu-pietro
    read only = No

```

sorry for the confusion:
ubuntu-parter = ubuntu1
ubuntu-pietro = ubuntu2

---

