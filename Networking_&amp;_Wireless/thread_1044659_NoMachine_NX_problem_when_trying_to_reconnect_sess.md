---
title: "NoMachine NX problem when trying to reconnect session"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by vasco_pedro on 2009-01-19
I have installed NoMachine NX Desktop on Ubuntu Hardy. The installation went fine, the server is up and I can connect perfectly. The problem is that if I disconnect a session instead of terminating, when I try to reconnect from windows, I get a connection timed out. 

I get this on var/log/messages when I try to reconnect

kernel: [446980.220088] nxserver[10598]: segfault at 0000600d eip 0000600d esp bf8ff4fc error 14

and this is the client feedabck

NX> 203 NXSSH running with pid: 7576
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 64.245.185.133 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-14 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login
NX> 101 User: bueda
NX> 102 Password: *****
NX> 103 Welcome to: bueda user: bueda
NX> 105 Listsession –user=”bueda” –status=”suspended54running” –geometry=”1280×800x32+render” –type=”unix-gnome”
NX> 127 Available sessions:

Display Type Session ID Options Depth Screen Status Session Name
——- —————- ——————————– ——– —– ————– ———– ——————————
NX> 280 Exiting on signal: 15

If I restart the NX server I can connect again, but obviously I loose all the applications that were running, which is really annoying. I couldn't find anything on this, I wonder is anyone experienced this?

Please help, this is very frustrating, since NoMachine NX does not seem to have a forum where you can post questions unless you are a paying client.

Thanks,

Vasco

---

### Post by nasenmann72 on 2009-01-22
Hi,

I 've exactly the same problem on Intrepid:

```

NX> 203 NXSSH running with pid: 14215
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.200.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-14 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: snake
NX> 102 Password: *************
NX> 103 Welcome to: snakesrv user: snake
NX> 105 Listsession --user="snake" --status="suspended\054running" --geometry="1920x1200x24+render" --type="unix-application" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
NX> 280 Exiting on signal: 15
```

Thanks for any hints solving this problem!

Snake

---

### Post by jia103 on 2009-12-19
Don't know if this will help everyone, but if you disable encryption (checkbox checked), try unchecking the checkbox to enable encryption. Worked for me using the NoMachine client with FreeNX Server.

---

### Post by Earnol on 2010-06-07
Basically the same problem. Happens after lucid upgrade.
```
NX> 203 NXSSH running with pid: 2556
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.10 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: vladik
NX> 102 Password: 
NX> 103 Welcome to: SVA1 user: vladik
NX> 105 listsession --user="vladik" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'vladik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
2001    unix-gnome       6BE6F7CE04C73D7B39BB0C39371A502F -RD--PSA    32 1024x768       Suspended   SVA1


NX> 148 Server capacity: not reached for user: vladik
NX> 105 restoresession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="SVA1" --type="unix-gnome" --geometry="1024x768" --client="winnt" --keyboard="pc102/en_US" --id="6BE6F7CE04C73D7B39BB0C39371A502F" --resize="1" 

NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 /usr/bin/nxserver: line 1584: 24644 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 280 Exiting on signal: 15
```

So it looks like attempt to restore session leads to session termination? Any ideas?

---

### Post by natnek on 2010-06-09
> **Earnol said:**
> Basically the same problem. Happens after lucid upgrade.
<snip>
So it looks like attempt to restore session leads to session termination? Any ideas?

I have the same problem, and a friend of mine is also getting the same error - attempting to resume a suspended sessions kills the session.  Afterwards I can reconnect again fine with a new session.  This all started with the lucid update.

My error message:
```
NX> 203 NXSSH running with pid: 2980
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XXX.XXX.XXX.XXX on port: XXXXX
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: XXXX
NX> 102 Password: 
NX> 103 Welcome to: XXXX user: XXXX
NX> 105 listsession --user="XXXX" --status="suspended,running" --geometry="1920x1080x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'XXXX' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
2001    unix-gnome       0F40215D8216F84040B6C35A6C349BBC -RD--PSA    32 1024x768       Suspended   XXXX


NX> 148 Server capacity: not reached for user: XXXX
NX> 105 restoresession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="XXXX" --type="unix-gnome" --geometry="1024x768" --client="winnt" --keyboard="pc102/en_US" --id="0F40215D8216F84040B6C35A6C349BBC" --resize="1" 

NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 /usr/bin/nxserver: line 1584:  6197 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 280 Exiting on signal: 15
```It looks like a couple of other guys are having the same problem here too:

[http://ohioloco.ubuntuforums.org/showthread.php?p=9341725#post9341725](http://ohioloco.ubuntuforums.org/showthread.php?p=9341725#post9341725)[URL="http://ohioloco.ubuntuforums.org/showpost.php?p=9341725&postcount=12"]
[/URL]

---

### Post by orion940 on 2010-06-18
I just updated freenx with the latest, and the resume works.  On my system, with a lot of stuff going on, it took a little time, but it works.
I am using 0.7.3.git100327.e224628-0~ppa7~lucid which is in [http://ppa.launchpad.net/freenx-team/ppa/ubuntu](http://ppa.launchpad.net/freenx-team/ppa/ubuntu) repo.

O.

---

### Post by Zarok on 2010-06-19
> **orion940 said:**
> I just updated freenx with the latest, and the resume works.  On my system, with a lot of stuff going on, it took a little time, but it works.
I am using 0.7.3.git100327.e224628-0~ppa7~lucid which is in [http://ppa.launchpad.net/freenx-team/ppa/ubuntu](http://ppa.launchpad.net/freenx-team/ppa/ubuntu) repo.

O.
I can confirm this - I couldn't resume sessions at all until I updated freenx-server minutes ago. Works like a charm now!

---

### Post by diml@otenet.gr on 2011-04-21
> **Zarok said:**
> I can confirm this - I couldn't resume sessions at all until I updated freenx-server minutes ago. Works like a charm now!


  Dear friend,
  I have the same problem and as a temporarily solution (in order to SOLVED this later with the new version of NXSERVER) I am doing this (i have ubuntu 8..:


  Connect to server with SSH
  Stop NX : /usr/NX/bin/nxserver --stop (or) shutdown
  Start NX: /usr/NX/bin/nxserver --start
   
  This will terminate the session and you can reconnect now to your server :)

---

### Post by MilleBii on 2011-06-10
Same problem 3 times in a week, although I have not changed either ubuntu 8 nore the nxclient/nxserver configuration.

```

user> /etc/init.d/nxserver restart
user> /usr/NX/nxserver --shutdown


```

failed to stop lost connections

---

### Post by HvanMidden on 2011-07-21
Hi there,

I have since a few months problems resuming sessions. Everything worked fine before and I did not make any changes except the suggested upgrades.

My system is Ubuntu 10.10 - the Maverick Meerkat 
I am using Lucid: 0.7.3.git110520.3884279-0ubuntu1ppa4 (freenx)

Since this version is higher than the vesrion mentioned above as the solution, I suspect that it was upgraded (how can I find my upgrade hiostory?) this newer version reintroduced the resume problem.

Has anyone similar problems or even better a solution, because it is very irritating to always have to restart the session.

Thanks
Herman

---

