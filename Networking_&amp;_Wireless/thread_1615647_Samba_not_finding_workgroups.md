---
title: "Samba not finding workgroups"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by roobinatube on 2010-11-07
Hi all,

On my desktop PC I use Kubuntu, and on my laptop i use mint XFCE. I dont, however, seem to be able to get them to see each other via samba. In XFCE I am using Gigolo to browse shares, and dolphin in kde. Both are the amd64 versions.

Using gigolo in xfce i am able to mount shares from kubuntu by manually entering the ip and connecting, but no workgroups show up when it searches the network.

When I look in pyneighbourhood the workgroup is found but the mounting fails every time.

In Kde i see nothing at all in any of my network folders.

I have the following samba packages installed on both machines
samba
samba-common
samba-common-bin
libwbclient0
python-smbc
winbind
smbfs
smbclient
libsmbclient

I also have my firewall turned on, but allowed the service samba and nfs in gufw
I have apparmor enforcing, with the base apparmor profiles installed, however when i turn off the firewall and apparmor, there is no change in the result.

I have set the permissions of the folders in my smb.conf to allow my samba username read/write access, my smb.conf is below:

```
[global]
   workgroup = WORKGROUP
   netbios name = SHARK
   server string = %h server (Samba, KUbuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   usershare allow guests = yes
   preferred master = no
   local master = no 
   wins support = yes

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

[shark-home]
   path = /home/roo
   valid users = smbshark
   read only = no
   create mask = 0777
   directory mask = 0777


```What on earth am i doing wrong?! About 8 months ago i had samba working seamlessly with fedora 13 on my desktop, to share music with my housemates at university, when i moved away i didnt use samba for a long time, but now i was given a laptop from work and want to share my files between computers again, I cant do it at all!

I have looked this up, but all i can find is things about the problem being with gnome... Seeing as im not using gnome, and definitely not nautilus, i dont think this applies to me.

When I run "smbclient -L ROO-DESKTOP" from my laptop I can see all the shares, and other windows computers on the workgroup.

Thanks for any help!
Roob

---

### Post by roobinatube on 2010-11-09
bump

---

### Post by roobinatube on 2010-11-13
noone? I still havent managed to get this working!

---

### Post by 00_MACKIE_00 on 2010-11-13
Same problem

---

### Post by roobinatube on 2010-11-14
actually, I have solved my problem.

If I actually stop ufw
```
sudo service ufw stop
```

rather than turning it off in gufw, there are no problems browsing samba. Not a clue why gufw doesnt actually turn off ufw.

The problem now is that when the firewall is started, the samba browsing stops working again.

The ports I had open were the preset ones in gufw. What that preset forgets is [according to the samba team]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports"), more are often needed (1024-65535).

I have uninstalled gufw and use ufw from the command line... maybe one day i will actually learn iptables...

```

sudo ufw allow proto tcp to any port 135 from 192.168.0.1/24
sudo ufw allow proto udp to any port 137 from 192.168.0.1/24
sudo ufw allow proto udp to any port 138 from 192.168.0.1/24
sudo ufw allow proto tcp to any port 139 from 192.168.0.1/24
sudo ufw allow proto udp to any port 1024:65535 from 192.168.0.1/24

```

Now everything works. Im not sure how secure it is to have so many ports open, If someone can lean me in the direction of if this is a problem, or how i can control it that would be helpful.

Cheers
Roob

---

