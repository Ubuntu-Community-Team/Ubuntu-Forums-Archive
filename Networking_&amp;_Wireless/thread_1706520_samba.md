---
title: "samba"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by intranick on 2011-03-14
So ive been trying to set up samba so i could have a windows networking like feel across mine and my roommates network for all windows and linux machines.

we have 5 computers
king - my desktop (linux ubuntu 10.10 desktop)
tyr - my server (linux ubuntu 10.10 server)
travel - win7 netbook
cody-pc - roommates desktop (linux ubuntu 10.10 desktop)
cody-laptop - roommates laptop (linux ubuntu 10.10 desktop)

so we set up samba running on tyr and codypc to share files that are located on those two machines.

hoping to do as much of this from within the GUI as we can so we can just drag and drop etc and easy to leave and come back to whatever..

so, simply sharing the home directory of tyr and doing smbpasswd I can read, write, list, etc files on tyr using travel but not king -- (do i need to log in specifically, and how do i automatically have it done in the ubuntu gui) 

thats problem 1.

problem 2. codypc can not list smb computers on the network inside gnome, all other computers can.  why?

problem 3. when I type in findsmb -- king and tyr show up on every machine, and sometimes one random other computer will show up and sometimes not, appears to be random, and can be any one machine. 

example output: 
```

nick@King:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.7     KING          +[WORKGROUP] [Unix] [Samba 3.5.4]
192.168.1.23    TYR            [    WORKGROUP     ]

```(on a side note, whats LMB?)
output of testparm incase that helps:
```

nick@tyr:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

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

[homes]
    comment = Home Directories
    read only = No

[profiles]
    comment = Users profiles
    path = /home/samba/profiles
    create mask = 0600
    directory mask = 0700
    guest ok = Yes
    browseable = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```
problem 4.  ive been asking on some specific IRC channels all night and everybody just replies "ughh just use sftp" "just use scp"  -- or demands a detailed explanation of why i want it to be SMB -- and the truth is -- i just do.  please only give your input if it can help with samba and not telling me to switch protocols 

problem 5. im almost out of beer :(

---

### Post by bk60544 on 2011-03-15
don't mean to distract, but have you though about using VNC? Might be easier.

---

### Post by Morbius1 on 2011-03-15
> so, simply sharing the home directory of tyr and doing smbpasswd I can  read, write, list, etc files on tyr using travel but not king -- (do i  need to log in specifically, and how do i automatically have it done in  the ubuntu gui) You're actually sharing the [homes] meta share:
> [homes]
    comment = Home Directories
    read only = NoThat is not a browseable share and can only be accessed directly. Here's where is gets confusing:

_On Linux:_
You have to specifically ask for that users home directory. For example:
```
nautilus smb://192.168.0.100/morbius
```Will get me access to morbius' home directory on 192.168.0.100

_On Windows:_
Windows passes the local login users username and password automatically without being asked. If I'm logged into Windows as user morbius, my username and login password is automatically sent to the samba server when I click on the server so I'm automatically connected to morbius' home directory on the server if it exists.

*Note: I believe this is the origin of the often repeated and basically wrong advice that all the user names have to match on all systems for samba to work.*

---

### Post by BHEJU on 2011-03-15
I have somewhat similar set-up. This was unbelievably easy to set-up. I just installed "samba config tool" tool from pkg manager. it's as simple as it gets. just select the directories to share. It also let's you configure password requirements if needed. 
You might want to try it.

Cheers,

---

### Post by intranick on 2011-03-15
actually thank you guys for responding.

I solved the issue last night... once I established tyr as the local master browser and domain master...

told tyr to run netbios and all other computers to point to tyr as a netbios server ... everything fell together

I guess it works better for linux to linux if you set up netbios and have the pecking order established 


also got a laser printer working off tyr for the whole network to use and it rocks.

---

### Post by ant2ne on 2011-03-15
welcome to networking.

If you aren't completely phobic of the command line, you can easily set up very reliable and stable samba shares.

---

