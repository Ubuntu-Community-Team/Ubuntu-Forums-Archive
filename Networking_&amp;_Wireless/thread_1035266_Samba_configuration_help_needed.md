---
title: "Samba configuration help needed"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by xterm on 2009-01-09
Hello all. 

I have fiddled about with samba for some time now but I can't get this to work like I want to. And of course I don't want it to work like anyone else... like, why keep it simple stupid? :D

**OK here's the scenario:** 
I have a server running a Linux dist. and samba. In my home network I have both a windows XP client (my dear girlfriends, that I still hasn't been able "to turn to the right side of the force", i.e Ubuntu) and of course my own PC running Ubuntu desktop. 

**This is what I want to accomplish threw samba:**
[LIST]
[*]A public share that is available from any computer on our LAN (including, but limited to, the two computers specified above) and that doesn't require the user to login.
[*]A private share tied to our login name on our PC (specified above)
[*]A public printer share
[/LIST]

**Here are my current samba config:**
```

[global]
workgroup = mshome
netbios name = Andromeda
encrypt passwords = yes
server string = Fileserver
log file = /var/log/samba/%m.log
#socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
#socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_SNDBUF=8192

#test
log level = 1                      # Default is 0 
socket options = TCP_NODELAY IPTOS_LOWDELAY 
read raw = yes                     # Default 
write raw = yes                    # Default 
oplocks = yes                      # Default 
max xmit = 65535                   # Default 
dead time = 15                     # Default is 0
getwd cache = yes
lpq cache = 30

hostname lookups = No
dns proxy = no

printcap name = cups  
printing = cups   
security = share 

[homes]
read only = no
browsable = no
public = no

[public]
path = /storage/pub
public = yes
browsable = yes
read only = yes
write list = @users

[printers]   
browseable = yes   
printable = yes   
public = yes   
create mode = 0700   
guest only = yes   
use client driver = yes
guest account = smbprint   
path = /home/smbprint

```

**And here comes the problem:**
[LIST]
[*]My girlfriends computer (running windows XP) has no trouble mounting neither the public share or her private share. Her computer also finds the printer share and she can print flawlessly threw the share. 
[*]My own computer (running Ubuntu) can't find any shares on the server (though it finds the server when browsing network).
[*]My old laptop (also running Windows XP at the moment can't find any shares (not even public share). 
[*]My friends laptop (running Windows Vista) finds the public share but not the printer.
[/LIST]

Seems to me as my config is a bit buggy. Can anyone see any problems with my config or something I can improve to make this work better. Maybe there is another better way to define both public and private shares in samba?

Any help is appreciated

---

