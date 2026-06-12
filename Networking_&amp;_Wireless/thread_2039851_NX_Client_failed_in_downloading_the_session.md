---
title: "NX Client failed in downloading the session"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by khiat on 2012-08-09
Hi all
I am new to Ubuntu and NX server
I installed Gnome and nx server on my headless ubuntu 10.10 
and tried to connect with no machine nx client for windows and the authintication passed but failed in downloading the session information , and below is the error log, i dont know what to do?
Thanks in advance


NX> 203 NXSSH running with pid: 5296
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 176.34.124.170 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
Linux ip-10-54-210-26 2.6.35-30-virtual #61-Ubuntu SMP Tue Oct 11 18:26:36 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Thu Aug  9 22:19:55 UTC 2012

  System load:  0.0               Processes:           98
  Usage of /:   78.1% of 7.87GB   Users logged in:     1
  Memory usage: 4%                IP address for eth0: 10.54.210.26
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
---------------------------------------------------------------------
At the moment, only the core of the system is installed. To tune the 
system to your needs, you can choose to install one or more          
predefined collections of software by running the following          
command:                                                             
                                                                     
   sudo tasksel --section server                                     
---------------------------------------------------------------------

3 packages can be updated.
3 updates are security updates.

New release 'natty' available.
Run 'do-release-upgrade' to upgrade to it.

A newer build of the Ubuntu maverick server image is available.
It is named 'release' and has build serial '20120410'.
Get cloud support with Ubuntu Advantage Cloud Guest
  [http://www.ubuntu.com/business/services/cloud](http://www.ubuntu.com/business/services/cloud)
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: khiat
NX> 102 Password: 
NX> 103 Welcome to: ip-10-54-210-26 user: khiat
NX> 105 listsession --user="khiat" --status="suspended,running" --geometry="1366x768x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'khiat' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: khiat
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="ximoxiiiii" --type="unix-gnome" --geometry="1024x768" --client="winnt" --keyboard="pc105/en_US" --screeninfo="1024x768x32+render" 

NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 700 Session id: ip-10-54-210-26-2000-4D88D7D48594A907090637913F1D1E77
NX> 705 Session display: 2000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: b557866ab3cca0c419d064c1d90fc27c
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: b557866ab3cca0c419d064c1d90fc27c
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/khiat/.nx/F-C-ip-10-54-210-26-2000-4D88D7D48594A907090637913F1D1E77/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 1006 Session status: closed
NX> 1009 Session status: starting
Can't open /var/lib/nxserver/db/running/sessionId{4D88D7D48594A907090637913F1D1E77}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{4D88D7D48594A907090637913F1D1E77}': No such file or directory
NX> 280 Exiting on signal: 15

---

