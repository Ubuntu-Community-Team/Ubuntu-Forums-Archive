---
title: "Unable to mount XP share: Error NT_STATUS_UNSUCCESSFUL."
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by milkywayfarer on 2011-08-14
Hi all,
I'm failing with mounting XP share, receiving message: 
 -- ...
 -- mount error(110): Connection timed out
 -- Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

When I try to list shares with smbclient, finally I receive message: 
 -- ...
 -- Running timed event "tevent_req_timedout" 0x7f2902964ad0
 -- Error connecting to 192.168.34.140 (Success)
 -- lang_tdb_init: /usr/share/samba/en_US:en.msg: No such file or
 -- directory
 -- Connection to 192.168.34.140 failed (Error NT_STATUS_UNSUCCESSFUL)

I wasn't able to find solution, could anyone advise?

Context: 
 * I'm trying to mount share of NT-domain machine with XP which is accessed via VPN. While my ubuntu machine is still in default WORKGROUP. Is this possible at all?
 * Connection to target machine could be established, f.e. I can connect to it via RDP.
 * Command executed to mount: mount -t cifs //192.168.34.140/share_name /media/share_name -o username=XPDomainUsername,password=XPDomainPassword,workgroup=XPDomainName
 * Command executed to list shares: smbclient -L //192.168.34.140 -U XPDomainName\\XPDomainUsername --debuglevel=10

---

### Post by milkywayfarer on 2011-08-14
Unfortunately, it seems, that this is firewall issue, and file sharing ports are blocked for VPN connections. I can telnet on 445'th port of my XP machine from LAN, while I can't telnet the same via VPN, getting timeout exception: telnet: Unable to connect to remote host: Connection timed out.

---

