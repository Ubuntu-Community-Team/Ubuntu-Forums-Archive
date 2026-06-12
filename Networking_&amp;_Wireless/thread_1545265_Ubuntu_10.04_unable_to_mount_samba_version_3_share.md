---
title: "Ubuntu 10.04 unable to mount samba version 3 share"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by bajhn on 2010-08-03
I've just loaded a laptop with Ubuntu 10.04, and I am unable to mount a samba share from an older Red Hat server. The problem first occurred when I tried using "Places -> Network" or "Places -> Connect to server", and the server's log gives me something like this

[I][2010/08/03 15:40:38, 1] auth/auth_server.c:check_smbserver_security(363)
  password server 10.100.1.2 rejected the password: NT_STATUS_LOGON_FAILURE
[2010/08/03 15:40:38, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [bjohnson] -> [bjohnson] FAILED with error NT_STATUS_LOGON_FAILURE[/I]

I tried smbmount, and the result is this:
[I][bjohnson@brn-601 ~]% sudo mount //lnbgdev01/bjohnson /mnt/lnbgdev01 -t cifs -o username=bjohnson
[sudo] password for bjohnson: 
mount: wrong fs type, bad option, bad superblock on //lnbgdev01/bjohnson,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/I]
Dmesg tells me this:
[I]20062.382309] Slow work thread pool: Starting up
[20062.382370] Slow work thread pool: Ready
[20062.382555]  CIFS VFS: cifs_mount failed w/return code = -22
[20166.982164]  CIFS VFS: cifs_mount failed w/return code = -22
[20403.005992]  CIFS VFS: cifs_mount failed w/return code = -22
[21627.362755]  CIFS VFS: cifs_mount failed w/return code = -22
[/I]
It works fine from a Debian Lenny box:
[I]jed:~#  sudo mount //lnbgdev01/bjohnson /mnt/lnbgdev01 -t smb -o username=bjohnson
Password: 
jed:~# 
[/I]
I also tried this:
*[bjohnson@brn-601 ~]% sudo mount //lnbgdev01/bjohnson /mnt/lnbgdev01 -t cifs -o username=bjohnson,sec=ntlmv2i*

and this:
[I][bjohnson@brn-601 ~]% sudo mount -t cifs -o username=bjohnson //lnbgdev01/bjohnson /mnt/lnbgdev01
[/I]
The samba version on the Red Hat server is 3.0.33-0.19.el4_8.1.

The successful mount from the Debian box produced this log on the server:
[I][2010/08/03 15:23:10, 2] smbd/reply.c:reply_special(324)
  netbios connect: name1=10.100.1.211    name2=JED            
[2010/08/03 15:23:10, 2] smbd/reply.c:reply_special(331)
  netbios connect: local=10.100.1.211 remote=jed, name type = 0
[2010/08/03 15:49:17, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [bjohnson] -> [bjohnson] -> [bjohnson] succeeded
[2010/08/03 15:49:17, 1] smbd/service.c:make_connection_snum(1042)
  10.100.1.213 (10.100.1.213) connect to service bjohnson initially as user bjohnson (uid=504, gid=100) (pid 14562)
[2010/08/03 15:50:07, 1] smbd/service.c:close_cnum(1239)
  10.100.1.213 (10.100.1.213) closed connection to service bjohnson
[/I]
while the unsuccessful mount attempts produced this:
[I][2010/08/03 15:22:39, 1] auth/auth_server.c:check_smbserver_security(363)
  password server 10.100.1.2 rejected the password: NT_STATUS_LOGON_FAILURE
[2010/08/03 15:22:39, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [bjohnson] -> [bjohnson] FAILED with error NT_STATUS_LOGON_FAILURE
[2010/08/03 15:40:38, 1] auth/auth_server.c:check_smbserver_security(363)
  password server 10.100.1.2 rejected the password: NT_STATUS_LOGON_FAILURE
[2010/08/03 15:40:38, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [bjohnson] -> [bjohnson] FAILED with error NT_STATUS_LOGON_FAILURE
[2010/08/03 15:41:33, 1] auth/auth_server.c:check_smbserver_security(363)
  password server 10.100.1.2 rejected the password: NT_STATUS_LOGON_FAILURE
[2010/08/03 15:41:33, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [ABORT] -> [ABORT] FAILED with error NT_STATUS_LOGON_FAILURE
[/I]
I don't know what version of Windows the server at 10.100.1.2 is running, but it's old enough that I can rule out Windows 7 or Vista.

Thanks in advance for any insights!

---

### Post by bilkay on 2010-08-04
I'm having a similar problem. The server is RedHat fc8, the laptop Ubuntu 10.04. I get the error message "Failed to retrieve share list from server," but when running Windows 7 on the same laptop, there's no problem accessing the shares. I didn't check the RedHat  message log.

---

### Post by jonathansfl on 2011-01-03
try replacing your //server_name (*sudo mount //lnbgdev01/bjohnson) *with //*10.100.1.211 *(*sudo mount //source_IP_address/bjohnson) *
 
*mounting with hostnames seems to be problematic*

---

