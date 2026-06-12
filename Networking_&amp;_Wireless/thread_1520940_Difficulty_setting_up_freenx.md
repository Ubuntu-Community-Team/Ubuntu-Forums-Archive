---
title: "Difficulty setting up freenx"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by Folcon on 2010-06-30
I've been trying to setup nx on lucid with the instructions here([https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)) and I've gotten stuck trying to connect to the machine, googling error messages have gotten me not far. I stopped using freenx when I found that nomachine provide a free version of the server for personal use.

I've setup the client/node/server deb files, but when I connect up with my client I get this error.

NX> 203 NXSSH running with pid: 3488
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.2.13 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.4.0-12 - LFE
NX> 105 Hello NXCLIENT - Version 3.4.0
NX> 134 Accepted protocol: 3.4.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: folcon
NX> 102 Password: *********************************
NX> 103 Welcome to: SYSTEM user: folcon
NX> 105 Listsession --user="folcon" --status="suspended\054running" --geometry="1440x900x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: folcon
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="home" --type="unix-gnome" --geometry="1434x832" --client="winnt" --keyboard="pc105\057gb" --screeninfo="1434x832x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: CEF797E7. To get detailed information about
NX> 595 ERROR: the error search for the string CEF797E7 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15


There relavant /var/log/messages I found are reproduced below:
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 ERROR: NXNODE Ver. 3.4.0-13  (Error id eA731F4)
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 ERROR: create session: run commands
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 ERROR: execution of last command failed
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 last command: /usr/bin/xauth -v -f /home/folcon/.nx/C-SYSTEM-1002-0EDC52578BA055D04114BBA5931CCC62/authority source /home/folcon/.nx/C-SYSTEM-1002-0EDC52578BA055D04114BBA5931CCC62/scripts/authority
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 exit value: 1
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 stdout: Using authority file /home/folcon/.nx/C-SYSTEM-1002-0EDC52578BA055D04114BBA5931CCC62/authority
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 Writing authority file /home/folcon/.nx/C-SYSTEM-1002-0EDC52578BA055D04114BBA5931CCC62/authority
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 stderr: /usr/bin/xauth:  creating new authority file /home/folcon/.nx/C-SYSTEM-1002-0EDC52578BA055D04114BBA5931CCC62/authority
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 /usr/bin/xauth: /home/folcon/.nx/C-SYSTEM-1002-0EDC52578BA055D04114BBA5931CCC62/scripts/authority:3:  bad display name "SYSTEM:1002" in "add" command
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NX> 596 init: stdin arguments: user=folcon,userip=192%2e168%2e2%2e2,uniqueid=0EDC52578BA055D04114BBA5931CCC62,display=1002,node_number=0,server_name=SYSTEM,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e2%2e13,encryption_mode=3,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=home,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1434x832x32%2brender,keyboard=pc105%2fgb,geometry=1434x832,link=adsl
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NXNodeExec::exec('startsession', 'user=folcon&userip=192%2e168%2e2%2e2&uniqueid=0EDC52578BA055D041...', 'localhost', 22) called at handlers/nxserver.pl line 3576
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NXShell::handler_session_start('--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 373
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NXShell::handle_command('startsession', '--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 145
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) NXShell::run() called at nxserver.pl line 4493
Jun 30 16:48:34 SYSTEM NXSERVER-3.4.0-12[9321]: ERROR: (exception id CEF797E7) eval {...} called at nxserver.pl line 4452


Help would be appreciated!

---

### Post by TorrentialStorm on 2010-07-13
sudo chown nx:root /var/lib/nxserver/db/* Run that. It fixed it for me.

---

