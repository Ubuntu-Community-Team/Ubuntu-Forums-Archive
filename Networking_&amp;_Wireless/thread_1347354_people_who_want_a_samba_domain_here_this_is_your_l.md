---
title: "people who want a samba domain here this is your lucky day"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by headvampyre@hotmail.co.uk on 2009-12-06
hi,
   i no how tough configuring samba can be but i am posting my smb.conf here to help all who need it i will aso post some commands that will be needed for machine adding


make sure you have samba installed if you dont go to terminal and type
 **sudo apt-get install samba smbclient smbfs swat **

now it is installed 

the samba configuration files are stored in /etc/samba

make sure these files are here

smb.conf
smbpasswd
smbusers
gdbcommands

now edit the smb.conf and wipe it then paste my configuration in
and save it
____________________smb.conf______________________________________________

[global]
      workgroup = what you want the domain to be called
      netbios name = what you want your server to appear as in the domain
      server string = Samba Domain Controller
      local master = yes
      domain master = yes
      preferred master = yes
      logon drive = S:
      logon home = \\put your netbios name here\%U\winprofile
      logon path = \\%N\profiles\%U
      logon script = logon.cmd
      domain logons = yes
      security = domain
      os level = 255
      passdb backend = smbpasswd
      smb passwd file = /etc/samba/smbpasswd
      encrypt passwords = yes
      domain admin group = root
      host msdfs = yes
      nt acl support = no
      printcap name = cups
      printing = cups
      load printers = yes

[netlogon]
      path = /srv/samba/netlogon
      read only = yes
      comment = Network Logon Service
      guest ok = yes
      browseable = yes

[profiles]
      path = /home/samba/samba-ntprof
      read only = no
      create mask = 0600
      directory mask = 0700

[dfs]
      comment = dfs root (share)
      path = /dfs
      msdfs root = Yes

[homes]
      comment = My Documents
      path = /home
      read only = No
      browseable = No

[printers]
      path = /var/spool/samba/printers
      comment = Network (Domain And Workgroup "ARTHUR"'s)printers
      browseable = no
      printable = yes
      writeable = no
      public = yes
      guest ok = yes


now go to terminal again and we are going to add the users

**smbpasswd -a username(e.g root)make sure you added root**

now create a machine trust account for the pc that is going to connect to the domain

[B][B]/usr/sbin/useradd -g machines -d /var/lib/nobody \
   -c *"machine nickname"* \
   -s /bin/false *machine_name*$ [/B]

**passwd -l *machine_name*$**[/B]

**smbpasswd -a -m *machine_name***

where machine name is the cients name but always add the $ to show its a machine

if u need more help feel free to ask me
thanks for reading

---

