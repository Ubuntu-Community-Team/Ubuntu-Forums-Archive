---
title: "NX connection error"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by _nikolaos on 2011-04-17
I have installed *freenx *in my Ubuntu desktop computer, and tried a couple of times to remotely connect to its GNOME through my Windows 7 netbook, where is NoMachine's NX client.

Whenever a GNOME session was locally open, the nx client from the netbook could open another graphical GNOME session. In most cases the netbook was in my home LAN, but I managed a couple times to enter from outside my home LAN. I supposed that everything is going  to be fine.

But now that I am really far from there, with my netbook only, connection through nx client fails. I can control my Ubuntu desktop only through putty (ssh).

This is the result (changed my personal info) of "detail" button after the error:
```
NX> 203 NXSSH running with pid: 3164
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 87.XXX.XXX.XXX on port: YYYYY
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: username
NX> 102 Password: 
NX> 103 Welcome to: fileserver user: username
NX> 105 listsession --user="username" --status="suspended,running" --geometry="1024x600x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'username' for reconnect:

Display Type Session ID Options Depth Screen Status Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: username
NX> 105 startsession --link="isdn" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Ubuntu%20remote" --type="unix-gnome" --geometry="1018x572" --client="winnt" --keyboard="pc105/en_US" --screeninfo="1018x572x32+render" 

Could not find ':' in DISPLAY: 
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 700 Session id: abcd-2017-EB0E055A58FDBE06780D9E7571220162
NX> 705 Session display: 2017
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 631c79d83d0a7c05b8deaa0e9ca9fdb3
NX> 702 Proxy IP: 192.168.1.W
NX> 706 Agent cookie: 631c79d83d0a7c05b8deaa0e9ca9fdb3
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 NX> 596 Session startup failed.
/usr/bin/nxserver: line 1590: 11723 Terminated sleep $AGENT_STARTUP_TIMEOUT
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/username/.nx/F-C-abcd-2017-EB0E055A58FDBE06780D9E7571220162/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
Can't open /var/lib/nxserver/db/running/sessionId{EB0E055A58FDBE06780D9E7571220162}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{EB0E055A58FDBE06780D9E7571220162}': No such file or directory
NX> 1006 Session status: closed
NX> 280 Exiting on signal: 15
```

I entered my remote computer with putty/ssh to investigate the file as suggested:

```
username@abcd:~$ /usr/lib/nx/nxserver --agent
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 716 Starting NX Agent ...
Error: Aborting session with 'Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again'.
Session: Aborting session at 'Sun Apr 17 17:17:29 2011'.
Session: Session aborted at 'Sun Apr 17 17:17:29 2011'.
NX> 716 NX Agent exited with status: 1
NX> 1001 Bye.

```

I suppose it has something to do with the DISPLAY variable, but what is that I should do?

Thanks.

---

### Post by _nikolaos on 2011-04-22
What worked was a (remotely driven) reboot to the computer, and the connections through NX are now accepted. Strange fix, however it's all right now.

---

### Post by cblanquer on 2011-04-27
Geia sou;

Kan you paste the exact command you used for remotely connecting? "ssh..." with something?  (of course do not copy your private data)
I have the same problem but are short of time to learn the ssh syntax after 1 year with NX working.
S'evxharistw'

---

