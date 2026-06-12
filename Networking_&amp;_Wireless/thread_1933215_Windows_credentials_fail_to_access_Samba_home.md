---
title: "Windows credentials fail to access Samba home"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by docallo on 2012-02-28
[FONT=Courier New]Hi,[/FONT]
 
[FONT=Courier New]I need some help to get Samba and Active Domain to play nicely.[/FONT]
[FONT=Courier New]The server is an Ubuntu 10.04 LTS with Kubuntu to provide GUI, running Samba 3.4.7[/FONT]
[FONT=Courier New]We have several other Linux servers that work perfectly well however this is the first 10.04LTS the others are 8.04LTS.[/FONT]
[FONT=Courier New]Authentication is done through Kerberos/AD and works great![/FONT]
[FONT=Courier New]We use NX for remote login and it is working well. [/FONT]
[FONT=Courier New]There is no “shared folder”. The users use Samba to access their home directory from their WinXp or Win7 machines. But we are always asked for our credentials and then the authentication fails.[/FONT]
 
[FONT=Courier New]The only errors that I can find is this message in the Samba log.[/FONT]
 
[FONT=Courier New]The Samba log shows:[/FONT]
 
[FONT=Courier New]2012/02/28 09:40:48, 1] libads/kerberos_verify.c:336(ads_secrets_verify_ticket)[/FONT]
[FONT=Courier New]ads_secrets_verify_ticket: failed to fetch machine password[/FONT]
[FONT=Courier New][2012/02/28 09:40:48, 1] smbd/sesssetup.c:342(reply_spnego_kerberos)[/FONT]
[FONT=Courier New]Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE![/FONT]
[FONT=Courier New][2012/02/28 09:40:48, 1] libads/kerberos_verify.c:336(ads_secrets_verify_ticket)[/FONT]
[FONT=Courier New]ads_secrets_verify_ticket: failed to fetch machine password[/FONT]
[FONT=Courier New][2012/02/28 09:40:48, 1] smbd/sesssetup.c:342(reply_spnego_kerberos)[/FONT]
[FONT=Courier New]Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE![/FONT]
[FONT=Courier New][2012/02/28 09:40:57, 1] libads/kerberos_verify.c:336(ads_secrets_verify_ticket)[/FONT]
[FONT=Courier New]ads_secrets_verify_ticket: failed to fetch machine password[/FONT]
[FONT=Courier New][2012/02/28 09:40:57, 1] smbd/sesssetup.c:342(reply_spnego_kerberos)[/FONT]
[FONT=Courier New]Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE![/FONT]
[FONT=Courier New][2012/02/28 09:41:12, 0] lib/util_sock.c:539(read_fd_with_timeout)[/FONT]
[FONT=Courier New][2012/02/28 09:41:12, 0] lib/util_sock.c:1498(get_peer_addr_internal)[/FONT]
[FONT=Courier New]getpeername failed. Error was Transport endpoint is not connected[/FONT]
[FONT=Courier New]read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.[/FONT]
 
 
 
[FONT=Courier New]Thanks![/FONT]
[FONT=Courier New]Alfredo[/FONT]
 
[FONT=Courier New]%%%%% Background info %%%%%[/FONT]
 
[FONT=Courier New]The smb.conf[/FONT]
 
[FONT=Courier New]From testparm[/FONT]
 
[FONT=Courier New]Load smb config files from /etc/samba/smb.conf[/FONT]
 
[FONT=Courier New][global][/FONT]
[FONT=Courier New]workgroup = USFN[/FONT]
[FONT=Courier New]realm = USFN.NZCORP.NET[/FONT]
[FONT=Courier New]server string = Samba Server - Rio[/FONT]
[FONT=Courier New]security = ADS[/FONT]
[FONT=Courier New]map to guest = Bad User[/FONT]
[FONT=Courier New]obey pam restrictions = Yes[/FONT]
[FONT=Courier New]password server = ##.###.##.###[/FONT]
[FONT=Courier New]pam password change = Yes[/FONT]
[FONT=Courier New]syslog = 0[/FONT]
[FONT=Courier New]log file = /var/log/samba/log.%m[/FONT]
[FONT=Courier New]max log size = 1000[/FONT]
[FONT=Courier New]name resolve order = lmhosts host wins bcast[/FONT]
[FONT=Courier New]socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192[/FONT]
[FONT=Courier New]dns proxy = No[/FONT]
[FONT=Courier New]usershare allow guests = Yes[/FONT]
[FONT=Courier New]panic action = /usr/share/samba/panic-action %d[/FONT]
[FONT=Courier New]idmap uid = 16777216-33554431[/FONT]
[FONT=Courier New]idmap gid = 16777216-33554431[/FONT]
[FONT=Courier New]invalid users = root[/FONT]
 
[FONT=Courier New][homes][/FONT]
[FONT=Courier New]comment = Home Directories[/FONT]
[FONT=Courier New]path = %H[/FONT]
[FONT=Courier New]read only = No[/FONT]
 
 
[FONT=Courier New]smbclient -L rio.usfn.nzcorp.net -U%[/FONT]
[FONT=Courier New]Domain=[USFN] OS=[Unix] Server=[Samba 3.4.7][/FONT]
 
[FONT=Courier New]Sharename Type Comment[/FONT]
[FONT=Courier New]--------- ---- -------[/FONT]
[FONT=Courier New]homes Disk Home Directories[/FONT]
[FONT=Courier New]print$ Disk Printer Drivers[/FONT]
[FONT=Courier New]IPC$ IPC IPC Service (Samba Server - Rio)[/FONT]
[FONT=Courier New]Domain=[USFN] OS=[Unix] Server=[Samba 3.4.7][/FONT]
 
[FONT=Courier New]Server Comment[/FONT]
[FONT=Courier New]--------- -------[/FONT]
[FONT=Courier New]RIO Samba Server - Rio[/FONT]
 
[FONT=Courier New]Workgroup Master[/FONT]
[FONT=Courier New]--------- -------[/FONT]
[FONT=Courier New]USFN DCUSFN200[/FONT]

---

