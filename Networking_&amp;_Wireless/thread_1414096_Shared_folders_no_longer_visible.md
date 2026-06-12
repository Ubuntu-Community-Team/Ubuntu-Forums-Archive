---
title: "Shared folders no longer visible"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by wingrider78 on 2010-02-23
Hello, I have two computers in the house that I have shared folders and one has a shared printer.  I have a desktop running 9.04 and a laptop running 9.10.  The desktop has several shared folders and a shared HP printer.  The laptop only has one shared folder.  Everything was working fine up until a couple days ago.  I went on the laptop to access one of the desktop shared folders, and nothing shows up under "places, network" except windows network.  

It no longer shows that the printer is currently shared either, but the funny thing is that I can still print to the desktop from the laptop...

I just can't figure out how to access the shared folders....anyone have any ideas???

---

### Post by awang726 on 2010-02-23
Same like me. This is my network schema:

Server -- pc1
     |
     ------ pc 2
     |
     ------ pc 3
     |
     etc.

My server have a printer and a public folder that I shared to all client. Now all client can't see my shared folder but still can print. I used ubuntu 9.04 for server and client.

This is my smb.conf:

```

[global]
workgroup = complex-cafe
server string = kasir
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
encrypt passwords = false
passdb backend = tdbsam
obey pam restrictions = yes
interfaces = lo eth1
bind interfaces only = true
security = share
guest account = nobody
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
usershare allow guests = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[public]
   comment = public
   read only = yes
   path = /home/kasir/Public
   guest ok = yes
   share modes = yes
   browseable = yes

```

I never change my smb.conf, how can this happen? Anyone can help?

---

### Post by dehcbad25 on 2010-02-23
are you sharing using NFS or samba?
 i will guess that you already tried restarting the services or the computer. i have more knowledge on windows that linux,but if you can print it probably means that you can do direct connections and the network discovery is not working, either because something on the server or something in the client. Again, i suggest restarting both, and checking the firewall and ip table rules.
just to check you should try to mount directly the shared folders. if you can still print, you should be able to mount the folders as well.

---

### Post by awang726 on 2010-02-23
I try to restarting the service:

here is the command and output

```

#sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                              [ OK ] 
* Starting Samba daemons                                               [ OK ] 

```

but, when I click Network on Nautilus, there is an error message:

```

Unable to mount location

Failed to retrieve share list from server

```

I already rebooting the computer too, but still can't view my shared folder.

what should I do?

---

### Post by wingrider78 on 2010-02-24
Yes I have tried restarting the samba services using the

sudo /etc/init.d/samba restart
 command, I got an OK for both the stop and restart of the service, but still the problem persists.  I realized last night that I was prompted to update via the update manager, I think there was a recent kernel update for my machines...could this somehow be the issue??  I will restart the desktop using the previous kernel version and see if that fixes the issue, but on my laptop I don't see any grub boot screens to select prior kernels...is there a way to 

1. enter the boot screen to select prior kernels, memtest, etc??
2. uninstall the newest kernel and use the prior one that is installed??

---

### Post by wingrider78 on 2010-02-24
I am unsure of what happened, but the laptop and desktop both had an update request from update manager, so I let them go ahead and update.  After they finished, I tried accessing the samba shares, and they were working.  I have no idea if the updates caused the problem and then solved the problem, but it is now working.

---

### Post by awang726 on 2010-02-25
> **wingrider78 said:**
> I am unsure of what happened, but the laptop and desktop both had an update request from update manager, so I let them go ahead and update.  After they finished, I tried accessing the samba shares, and they were working.  I have no idea if the updates caused the problem and then solved the problem, but it is now working.

I have a same problem like you, and I already report this as bugs.
They give me a solution. I try and it's works. I can view my shared folder again.

```

#sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
#sudo dpkg --configure -a
#sudo /etc/init.d/samba restart

```

My problem solved.

---

