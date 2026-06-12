---
title: "Cannot connect to windows comnputers after Ubuntu reinstall"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by Francis4344 on 2011-08-07
After reinstalling Ubuntu, I cannot reach the windows computers (both on the MAISON workgroup). Since I have not changed a thing to these two win machines, I assume something is wrong with my Ubuntu config.

Samba is installed and running (or so it seems). Dolphin shows the Samba shares, but give this error message:

Unable to find any workgroups in your local network

this is the testparm output :

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    workgroup = MAISON
    netbios name = SAMBA24
    server string = Samba file and print server
    interfaces = 127.0.0.1/8, 192.168.0.0/24
    bind interfaces only = Yes
    update encrypted = Yes
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    guest account = smbguest
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    password level = 6
    username level = 6
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 1000
    name resolve order = wins lmhosts bcast
    client signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    machine password timeout = 120
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    delete user script = /usr/sbin/userdel '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    logon script = %G.bat
    logon path = \\%L\profiles\%u
    logon drive = m:
    logon home = \\%L\homes\%u
    os level = 33
    local master = No
    domain master = No
    dns proxy = No
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind separator = @
    winbind cache time = 360
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind nested groups = No
    winbind nss info = no
    hosts allow = 127., 192.168.0.
    cups options = raw
    follow symlinks = No

[homes]
    comment = Home Directories
    path = /home
    read only = No
    locking = No
    strict locking = No

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    read only = No
    guest ok = Yes
    printable = Yes
    locking = No
    strict locking = No

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    guest ok = Yes
    printable = Yes
    locking = No
    strict locking = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    read only = No
    guest ok = Yes
    printable = Yes
    browseable = No
    locking = No
    strict locking = No

[pdf-documents]
    comment = Converted PDF Documents
    path = /home/pdf-documents
    read only = No
    guest ok = Yes
    locking = No
    strict locking = No

[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    use client driver = Yes

Must be something simple... hopefully....

Thanks in advance

Francis

---

### Post by Francis4344 on 2011-08-08
Anybody?   :(

---

### Post by Morbius1 on 2011-08-08
Gosh,

* You posted in the "ubuntu" section but you said you are using Dolphin so I'm guessing you use KDE. I don't use KDE myself.

* That smb.conf if it were in an Ubuntu system can only come from one place and that's gadmin-samba. Only that utility would produce such an incoherent mess. There's probably only 2 people in this entire forum who knows what each one of those lines are actually doing - I'm not one of them. Fortuantley only about 5% of smb.conf has any impact on accessing someone else's shares since it's mostly used to share folders to others.

* All I can do is guess that this:
>  Unable to find any workgroups in your local networkIs the KDE or perhaps Dolphin equivalent to this in Ubuntu / Nautilus:
> Unable to mount location. Failed to retrieve share listI would try to access the windows box directly by ip address. In Nautilus it would be something like this:
```
nautilus smb://192.168.0.100
```Where 192.168.0.100 is the ip address of the windows box you are trying to access.

If that works then the problem is likely a name services problem - the network can't convert a host name to an ip address.

---

### Post by Francis4344 on 2011-08-08
You are quite the genius!

I am using Ubuntu and gadmin-samba.

I tried Dolphin to see if the error message (if any - one can hope!) would point me in th right direction. 

And yes, the Dophin message is the equivalent of 

Unable to mount location. Failed to retrieve share list.

I finally figured (dah) how to invoque the ip address from the terminal (since there is no address bar in Nautilus) and it did work!!

You score on all points!

So, the problem is DNS related. Isn't the router in charge of this? (Dlink 2640B)

In the mean time, I can work...

Thanks a Zillion! :KS:KS

Francis

---

### Post by Morbius1 on 2011-08-08
> I finally figured (dah) how to invoque the ip address from the terminal (since there is no address bar in Nautilus) and it did work!!There is an address bar in Nautilus but it's not enabled by default because ... I don't know why it's not enabled. When you have Nautilus up select "Ctrl+L" and it should switch to the address bar.

It's sort of a DNS problem and some routers can actually cause this to happen by getting in the way of things between hosts in the LAN. I actually solved this problem once by switching routers. There is one thing you can try that actually works most of the time. Change this:
>      name resolve order = wins lmhosts bcastTo this:
```
name resolve order = bcast lmhosts host wins 
```"bcast" or broadcast is the only mechanism that works by default as lmhosts is either empty or doesn't exist and wins needs to be set up. Sometimes wins will actually send the samba client outside the network to try to resolve hostnames and stalls before it gets to bcast. Placing bcast first gives you a shot before wins gets hold of the process. No guarantees but worth a shot if yo really need to browse to shares rather than access them directly. 

BTW once you get your share to open in Nautilus you can bookmark it ( Bookmarks > Add Bookmark ) so that it shows up on the left panel of nautilus just like a "mapped drive" does in windows.

---

### Post by Francis4344 on 2011-08-09
I have tried your suggestion :

name resolve order = bcast lmhosts host wins

But no success. I suspect that the Router is playing games with me.
I will have to do a bit of research on that. 

In the meantime, I will probably switch my WIN machines to fixed IP address to simplify matters.

Thanks again

---

### Post by Morbius1 on 2011-08-09
> In the meantime, I will probably switch my WIN machines to fixed IP address to simplify matters.Fixed ip addresses are your friend and fix or at least bypass a multitude of problems. You should see if your router can do this for you so you don't have to mess with each machine individually. 

Each router mfg has a different name for it but one name is  "DHCP Reservation" and what it does is it allows the client machine to remain as a dhcp client and assigns the exact same ip address to that exact same machine every time that machine boots. It is useful for laptops and such since they can have essentially fixed ip addresses when they are in your home lan and act normally when they are out and about.

---

