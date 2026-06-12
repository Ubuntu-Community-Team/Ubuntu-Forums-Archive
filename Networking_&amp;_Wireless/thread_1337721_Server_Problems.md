---
title: "Server Problems"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by mike.dap on 2009-11-25
I have set up Ubuntu 910 with a shared file and in network manager I have set ipv4 to manual . I have entered the ip address and subnet and dns and set the workgroup in samba. All windows xp clients with static ip addresses can log on to the server and read and write. The laptops on the other hand can only read the file not write to it. The folder shows without having to even log on. I need to have the laptops read and write to this folder. Any ideas

---

### Post by pdc124 on 2009-11-25
post your smb.conf file 
do
 grep ^[A-Za-z\ ] /etc/samba/smb.conf 

to remove the comment lines 

whats the output of smbclient -L ip.of.server

---

### Post by mike.dap on 2009-11-25
I am very green to ubuntu, can you explain what you are asking

---

### Post by mike.dap on 2009-11-25
1

---

### Post by pdc124 on 2009-11-26
can the computers see each other on the network
the way you test this is by pinging from one to the other . A ping sends a little bit of data and waits for a reply.
get the IP address of the target machine
(windows - Start->run->cmd->ipconfig
linux terminal ->sudo ifconfig
 you are looking for 4 numbers eg 192.168.x.x

go to the other machine and
windows start->-run>cmd> ping
linux terminal ->ping 

followed by the number. You should get a response 

if the various computers are pingable then its not a networking problem.

the other line grep.....
displays the samba config file . Samba is the program that shares linux folders with windows machines

---

### Post by mike.dap on 2009-12-15
here is my smb.conf file
dap@SP:~$ grep ^[A-Za-z\ ] /etc/samba/smb.conf 
   workgroup = DUNCAN AUTO
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
dap@SP:~$

---

### Post by mike.dap on 2009-12-15
I am not having problems wiht xp only windosw home and windows 2000.

---

### Post by pdc124 on 2009-12-16
what username are the laptops using to log in ? 
does this use exist on your server ? 

isuspect its somthin to do with this in your config 

guest ok = no
read only = yes

try logging in and  and then have a look in the various  samba log file 
/var/log/samba/log name ( or IP - i cant remember ) of client

---

