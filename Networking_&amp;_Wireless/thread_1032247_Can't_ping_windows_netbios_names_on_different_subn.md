---
title: "Can't ping windows netbios names on different subnet"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by john_spiral on 2009-01-06
Hi,

I've run through quite a few threads about pinging windows names from a Ubuntu/Linux box, but I'm still unable to ping Windows machines on a different subnet by their short netbios name.

I can ping Windows machines on my own subnet by their netbios name and machines on another subnet by their full domain name, i.e machine.domain.local


I've got the following in place:

running: winbind

Within /etc/nsswitch.conf :

[COLOR="DimGray"]hosts:          files mdns4_minimal wins dns mdns4[/COLOR]

Within /etc/samba/smb.conf :

[COLOR="DimGray"]#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ubuntuworkgroup
   netbios name = ubuntu

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
#wins server = 192.168.110.2

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts host wins bcast dns

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0
[/COLOR]
Not sure if I really need to be messing with the smb.conf as I'm not running as a Windows share?

Thanks in advance for any help.

John

---

### Post by Iowan on 2009-01-06
Just thinking via keyboard, and wondering if a different subnet means using a router - and maybe requiring DNS.

---

### Post by john_spiral on 2009-01-07
thanks for the response Iowan,

Looks like the nsswitch.conf file already references a DNS server? 

```
hosts: files mdns4_minimal wins dns mdns4
```

---

### Post by Iowan on 2009-01-07
Are the windows boxes "registered" in that DNS server?

---

### Post by capscrew on 2009-01-07
NetBios names are handled by a WINS server.  Do you have a WINS server on the local subnet?  

WINS is a LAN technology.  The ports (tcp135/139) may not be routable in your situation.  

The order of the listings in your nsswitch.conf file are important.  I notice that you have lmhosts and hosts (files) before the WINS and DNS servers.  I would have them after the 2 servers and a failsafe rather than the other way around.

---

### Post by john_spiral on 2009-01-08
> **Iowan said:**
> Are the windows boxes "registered" in that DNS server?

Iowan, when booted into Windows I can succesfully ping Windows short names, I think this shows they are being resolved by either the Wins or DNS servers.

Capscrew might be onto something by suggesting I change the order of resolution in my nsswitch.conf file.

I'll give this a bash and report back.

---

### Post by john_spiral on 2009-01-15
made a change to my /etc/nsswitch.conf :

hosts: wins dns mdns4 files mdns4_minimal 

rebooted , still can't ping Windows names on different subnet.

The funny thing is if I do a traceroute to the machines ip address it returns it's name on the last hop? 

If traceroute is resolving names surely ping should also?

---

### Post by jonobr on 2009-01-15
Interesting topic and just as a wag contribution,
It sounds as if the windows network, has its own wins resolution.
and from your samba config it looks as if you are turning the ubuntu box as a wins server also.
***************
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

*****************


If you could point ubuntu to your wins server on your other network and disable the ubuntu wins server.
Im thinking your nsswitch will now point to what you have defined here
*********************
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
#wins server = 192.168.110.2<-----

****************

Im thinking at some point you will need to run wireshark to see whats happening on the wires.

Last stupid question, are you pinging netbios name or host name,
from what I saw, these can be different.

 Im contributing only as the topic is interesting, so feel free to ignore this as Im no Wins expert, just interested in the question :P

---

### Post by john_spiral on 2009-01-19
Yup jonobr you were right!

To ping windows names on other subnets do the following:

(1) edit /etc/nsswitch.conf

Add "wins" to the end of the line so it looks something like this:

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

note wins before dns

(2) Install winbind

sudo aptitude install winbind

(3) Install samba:

sudo apt-get install samba

stop service:

sudo /etc/init.d/samba stop


(4) Specify your wins server in /etc/samba/smb.conf , this can be obtained from a Windows machine on the network with the **ipconfig /all** command. 

Look for the following section, take out the semi colon and replace w.x.y.z with wins server from ipconfig /all command.

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

also change name resolve order in /etc/samba/smb.conf

name resolve order = lmhosts host wins bcast 

(5) Start samba:

sudo /etc/init.d/samba start

thanks

John

EDIT: forgot to add I did a clean install of Ubuntu to get to the route of this beast problem.

---

### Post by john_spiral on 2009-01-20
resolving of windows shortnames on a different subnet even seems to work without samba running?

Looks like winbind might just need to ref the wins server setting in /etc/samba/smb.conf?

who knows :o

---

