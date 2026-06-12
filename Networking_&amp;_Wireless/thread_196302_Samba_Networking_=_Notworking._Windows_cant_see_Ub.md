---
title: "Samba Networking = Notworking. Windows cant see Ubuntu..."
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by Onos on 2006-06-14
Greetings all.

After several hours of weeding through various threads on Samba... I am nearly ready to throw in the towel.

Well, almost.

I have a small network as follows:

(1) Win 2000 machine. Very cranky old crotchety machine. Very little drive space, and being a cheap @#%$!! I am not likely going to pump anymore money into it for the remaining year or so it has left to it.

(2) Ubuntu machine, running Dapper. (6.06 LTS) Not so old and cranky. Ubuntu is the reason it still lives, after some malware tore it up about 6 months ago.

(3) Slick new Win XP laptop, my guv'mint issued work computer. Networking it isn't really that critical.



SO: Setting up the directory on the Win 2000 machine (1) was a breeze; machines (2) and (3) are happy, and I was able to offload my massive font collections off to them.

Samba on the other hand, is not playing along very nicely. My **smb.conf** file is quite possibly butchered beyond all recognition, but here it is:

```

[global]
netbios name = server
server string = %h server (Samba, Ubuntu)
workgroup = Mshome
security = share
log file = /var/log/samba.log
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
wins support = no

allow hosts = 192.168.1. 127.0.0.1

########## Printing ##########
# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes
# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap
# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups
# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin
#======================= Share Definitions =======================


[homes]
   comment = Home Directories
   browseable = no
   writable = no

[homes]
  path = /home/myaccount/shared
  available = yes
  browseable = yes
  public = yes
  writable = yes


[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin



```


Running **testparm** on it turns up this:

```

myaccount@[COLOR="Green"]mycomputer[/COLOR]:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        netbios name = SERVER
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        log file = /var/log/samba.log
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        hosts allow = 192.168.1., 127.0.0.1

[homes]
        comment = Home Directories
        path = /home/myaccount/shared
        read only = No
        guest ok = Yes

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```


And for fun and giggles, (because on one of the other threads I was reading mentioned the host file as a possibly glitching point) here is my /etc/hosts file:

```

127.0.0.1	localhost.localdomain	localhost	[COLOR="Green"]mycomputer[/COLOR]

# Adding hostname for local IP from router per ubuntu forums...
192.168.0.102	[COLOR="Green"]mycomputer[/COLOR]

```

---

### Post by DarthMandeep on 2006-06-14
Are you running a firewall on the server? If so, are the Samba ports blocked? If the ports are open as they should be and you are using Firestarter, uncheck the "Block broadcasts from externel networks" option in the advanced config menu to fix the problem with Firestarter blocking Samba.

If you're not using a firewall, I'd try manually adding the client IPs to your smb.conf and running the nmap port scanner on the clients to see if the servers Samba ports are open.

---

### Post by Iowan on 2006-06-14
Is there a reason you have [homes] defined twice - with different parameters?

---

### Post by Slim Odds on 2006-06-14
[quote=Iowan]Is there a reason you have [homes] defined twice - with different parameters?[/quote]

writable=yes and writable=no would seem to conflict :( :confused:

---

### Post by Iowan on 2006-06-14
**Writable** and **browseable** both change, but **testparm** seems to go *last vote wins*. Maybe not the issue, but curious.  Perhaps more clarification of what you mean by:
> Samba on the other hand, is not playing along very nicely.

---

### Post by Onos on 2006-06-15
[QUOTE=Iowan]Is there a reason you have [homes] defined twice - with different parameters?[/QUOTE]

To be honest, I wondered about this as well. This was a rendition based upon a user with a similar issue with Samba... and supposedly he edited his smb.conf to include his share as being part of his [homes] configuration.

I am not sure, but I would guess (if it actually works) that it inherits the writeable trait, but not down to the rest of my stuff in [homes]...?

The following quote (next post if I can't edit this) will reference where I got this from....

---

### Post by agiledata on 2006-08-02
> **DarthMandeep said:**
> Are you running a firewall on the server? If so, are the Samba ports blocked? If the ports are open as they should be and you are using Firestarter, uncheck the "Block broadcasts from externel networks" option in the advanced config menu to fix the problem with Firestarter blocking Samba.


Thanks, DarthMandeep. I kept having to disable Firestarter to get Windows access. Turning off the "block brodcasts" fixed it for me.

---

