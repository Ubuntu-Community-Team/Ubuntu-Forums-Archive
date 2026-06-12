---
title: "Samba not working on Lucid Lynx 10.04"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by ElQanah on 2010-05-20
samba issues

I had Samba shares (a public folder and a printer) running fine on Jaunty 9.10, when upgraded to 10.04 it stopped working.

I've tried several tips and following different threads to no avail.

when I run   smbclient -L localhost  or else smbclient -L 127.0.0.1 I get:
```

session setup failed: NT_STATUS_NO_SUCH_DOMAIN

```when I run   smbclient -L TKA I get:
```

Connection to TKA failed (Error NT_STATUS_CONNECTION_REFUSED)

```Here is my current smb.conf:
```

[global]
    workgroup = tkanet
    server string = %h server (Samba, Ubuntu)

#   wins support = no
;   wins server = w.x.y.z

    dns proxy = no
    name resolve order = lmhosts host wins bcast

#### Networking ####

    interfaces = lo eth0
    bind interfaces only = true


#### Debugging/Accounting ####

    log file = /var/log/samba/log.%m
    max log size = 1000
#   syslog only = no
    syslog = 0
    panic action = /usr/share/samba/panic-action %d

####### Authentication #######
    security = share
;    encrypt passwords = yes

;    passdb backend = tdbsam
    obey pam restrictions = yes
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
#   logon path = \\%N\%U\profile
;   logon drive = H:
#   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

#   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;    printing = cups
;   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
#   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;    usershare max shares = 100

    usershare allow guests = yes
    guest ok = yes
    guest account = nobody
    username map = /etc/samba/smbusers

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
    comment = All Printers
    browseable = yes
    path = /tmp
    printable = yes
    public = yes
    ;; error in samba??  ready only = yes
    create mask = 0700
    use client driver = yes

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
    writeable = yes
    guest ok = yes
    use client driver = Yes
;   write list = root, @lpadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Public]
    comment = TKA Publico
    path = /mnt/public
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755
    available = yes

```Now, when I browse the network, I see the TKANET group and my TKA box shows up. 

In ubuntu client with 10.04 I get a message stating the place can not be mounted and that it failed to obtain the sharing list from the server.  (something like that, my client computer is in spanish).  In winxp I got:

> 
\\TKA is not accessible.  You might not have permissions to use this network resource.  Contact the administrator of this server to find out if you have access permissions.

The network path was not found.
I installed samba4 but did't do any difference, so I uninstalled that.  Reinstalled SAMBA and the config tool for samba several times.  No  difference.

**  any ideas to win this battle?  :confused:

---

### Post by pajaritoman on 2010-05-21
I get the same response when I run smbclient -L localhost with Kubuntu 10.14.  This worked fine in Kubuntu 8.04.
.

---

### Post by ElQanah on 2010-05-22
Just in case someone else is looking for this same issue...  I completely uninstalled the whole samba and samba config tool from Synaptic and deleted the /etc/samba/smb.conf file (renamed it actually).  Then reinstalled.  Did nothing for me.

Also tried using the backup, default smb.conf copy located at /usr/share/samba/smb.conf copying that to /etc/samba location.  After restart, tried to use the samba tool to set up the shares.  Nothing!.  :confused:

[SOLUTION]

Got to one _**[tutorial here]("http://www.badgerbait.net/linux/ubuntu-10-04-server-lucid-print-and-file-server-for-home-network")**_ and just used the authors suggested smb.conf   Worked great.  Just twaked it a little bit, as I am sharing a printer with samba too.

Here is the final smb.conf (obviously with my setting when it comes to ip mask and shared folders names, but it might help someone else:

```

[global]
    workgroup = tkanet
;    netbios name = tka
    server string = TKA
    security = share
    encrypt passwords = no
    guest ok = yes
;    guest account = nobody
    load printers = yes
    hosts allow = 192.168.7. 127.
    interfaces = lo eth0

[printers]
    browseable = yes
    path = /tmp
    printable = yes
    public = yes
    ready only = yes
    create mask = 0700
    use client driver = yes
    guest ok = yes

[public]
    path = /mnt/public
    guest ok = yes
    comment = TKA's Public
;    available = yes
    writable = yes
;    browsable = yes
    create mask = 0666

```only problem I have now is the cups starting after smbd issue already reported as a bug, so i need to restart the smbd service after every reboot otherwise my public shared folder shows up but my printer don't.

```

restart smbd

```

---

### Post by AlexDudko on 2010-05-22
I created a new share and it started working (the old share name became also visible).

---

