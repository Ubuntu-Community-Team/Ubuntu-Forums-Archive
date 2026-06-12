---
title: "Nx and ubuntu 11.04: A fatal error occurred in NX Server"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2011-05-31
Hi,

I'm using with success NX server and client on Ubuntu 11.04 on both side. Yesterday the server crashed and now the client can't connect to it. The client works well because if I try to connect to an other server it works well and if I try to connect to this server with an other user it works well.
So I think that there is a problem with my user. I have tried to solve the problem as explained in the details of the error. Unfortunately there is no file /var/log/messages so I can't search the code of the exception...
What can I do?

Thank you

```

NX> 203 NXSSH running with pid: 3877
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.1.0.60 on port: 22
NX> 202 Authenticating user: nx
Ubuntu 11.04
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.5.0-4 - LFE
NX> 105 Hello NXCLIENT - Version 3.5.0
NX> 134 Accepted protocol: 3.5.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: torello
NX> 102 Password: ********
NX> 103 Welcome to: mido user: torello
NX> 105 Listsession --user="torello" --status="suspended\054running" --geometry="1280x1024x24+render" --type="unix-gnome" 
NX> 127 Available sessions: 

NX> 148 Server capacity: not reached for user: torello
NX> 105 Start session with: --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="mido" --type="unix-gnome" --geometry="1280x1024" --client="linux" --keyboard="pc105\057it" --screeninfo="1280x1024x24+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 628DE1B5. To get detailed information about
NX> 595 ERROR: the error search for the string 628DE1B5 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

```

---

### Post by cracklebar on 2011-06-30
Try removing any .Xauthority files in your home directory

rm .Xauthority*

Ian...

---

