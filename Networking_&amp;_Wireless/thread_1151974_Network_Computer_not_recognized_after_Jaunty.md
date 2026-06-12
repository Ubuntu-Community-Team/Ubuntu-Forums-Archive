---
title: "Network Computer not recognized after Jaunty"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by mattgyver83 on 2009-05-07
After installing 9.04 on my laptop it cannot be seen on my local network until I restart the samba daemon.  My network connection works correctly because I can see the other machines on my network and access them from my laptop without having to restarting samba, but the network computers cannot see the laptop or shares on it.  This was not an issue with 8.10 and previous versions, as well my 9.04 Desktop is not experiencing this issue and networking works correctly. 

After restarting the samba server the laptop is now recognized on the network and its shares may be accessed.  This works, however it only works until you logout, or reboot.  

After boot, when i restart the samba daemon initially i recieve this error;

> matt@eugene:~$ sudo /etc/init.d/samba restart
[sudo] password for matt:
 * Stopping Samba daemonsstart-stop-daemon: warning: failed to kill 2213: No such process
                                                                                  [ OK ]
 * Starting Samba daemons                                                         [ OK ]After this point, samba can be restarted if necessary without issue, or 'failed to kill' response.
Here is the output of my log.smbd

> [2009/05/07 09:48:12,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/05/07 09:48:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
[2009/05/07 09:48:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
[2009/05/07 09:48:12,  0] lib/interface.c:load_interfaces(523)
  ERROR: Could not determine network interfaces, you must use a interfaces config line
[2009/05/07 09:48:12,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/05/07 09:48:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
[2009/05/07 09:48:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
[2009/05/07 09:48:12,  0] lib/interface.c:load_interfaces(523)
  ERROR: Could not determine network interfaces, you must use a interfaces config linehere is the Networking section of my smb.conf as well.  Note* This is the same as my 9.04 desktop reads which is working correctly, i did not make any edits to this section.

> #### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yesThe laptop is primarily a wireless device, however I have tested this with it on a wired connection and it produces the same results.  Has anyone else had this problem or know how to resolve this?

---

### Post by mattgyver83 on 2009-05-08
bump.

---

### Post by mattgyver83 on 2009-05-09
bump.  anyone?

---

### Post by mattgyver83 on 2009-05-12
One last bump.  Could anyone second this might be a bug I should file?  Should it be filed w/ ubuntu or samba?

---

