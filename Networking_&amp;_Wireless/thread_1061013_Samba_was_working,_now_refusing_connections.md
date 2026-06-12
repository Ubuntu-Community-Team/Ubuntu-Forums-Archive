---
title: "Samba was working, now refusing connections"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by sipickles on 2009-02-05
Hi,

I have set up an Ubuntu intrepid server as a file server at my work, thru Samba.

Clients have been successfully connecting for several months. They are Mac OSX, WinXP, Vista, and Ubuntu users.

Yesterday the Vista computer couldn't connect, and today no-one can connect. :(

The server is available on the network - I can ssh into it from other machines and smbd is running:
```
simon@sciproj-server:~$ ps -ef | grep smb
root      4539     1  0 16:19 ?        00:00:00 /usr/sbin/smbd -D
root      4572  4539  0 16:19 ?        00:00:00 /usr/sbin/smbd -D

```

Here's the log:
```
[2009/02/05 16:19:45,  0] smbd/server.c:main(1213)
  smbd version 3.2.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2009/02/05 16:19:45,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/02/05 16:19:45,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/02/05 16:21:04,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
[2009/02/05 16:24:06,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/02/05 16:24:06,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/02/05 16:24:53,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected

```

getpeername failed appears everytime a client attempts to access the samba shares. The clients sees a password rejection, or nothing

Thanks for any advice

Simon

---

### Post by sipickles on 2009-02-06
bump 

Sorry about that - my colleagues are getting unimpressed!

---

### Post by superprash2003 on 2009-02-06
hmm.. post outpt of cat /etc/samba/smbusers and try restarting samba sudo /etc/init.d/samba restart

---

### Post by sipickles on 2009-02-09
Hi, thanks for the reply

I dont have a file on the system called /etc/samba/smbusers.

I've tried restarting samba a few times.  Here's the last bit of the log of my winXP user:

```
[2009/02/05 09:23:59,  0] lib/util_sock.c:write_data(1059)
[2009/02/05 09:23:59,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2009/02/05 09:23:59,  0] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2009/02/05 13:02:05,  0] lib/util_sock.c:write_data(1059)
[2009/02/05 13:02:05,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2009/02/05 13:02:05,  0] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)

```


Thanks

EDIT - I still have the same authentication problem even if I set 'security = none' in smb.conf

EDIT - Here's the net view output from the XP machine, showing the connection is good:
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.
C:\Documents and Settings\Simon Pickles>net view \\SCIPROJ-SERVER
Shared resources at \\SCIPROJ-SERVER

sciproj-server (Ubuntu Intrepid)

Share name  Type  Used as  Comment

-------------------------------------------------------------------------------
BACKUP      Disk           Backup
The command completed successfully.

```

EDIT:

log.nmbd has some more info:
```
[2009/02/09 08:25:20,  0] nmbd/nmbd.c:main(849)
  nmbd version 3.2.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2009/02/09 08:25:49,  0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(395)
  *****

  Samba name server SCIPROJ-SERVER is now a local master browser for workgroup MSHOME on subnet 192.168.1.100

  *****
[2009/02/09 08:25:49,  0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(350)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME.
  Unable to sync browse lists in this workgroup.
[2009/02/09 08:41:07,  0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(350)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME.
  Unable to sync browse lists in this workgroup.

```

Here is an attempt to log in with smbclient on the samba server:
```
simon@sciproj-server:~$ smbclient -L sciproj-server -U sciproj
Enter sciproj's password:
session setup failed: NT_STATUS_LOGON_FAILURE

```

---

### Post by sipickles on 2009-02-09
Well, it seems to be working for now. 

I had to reset the samba user:

```
sudo smbpasswd -a sciproj
```

God knows why! Samba is clever but very tetchy! :)

---

### Post by sipickles on 2009-02-11
After several days, Samba has forgotten my password again!

I have had to do smbpasswd again to manually reset it... any way I can avoid this?

:confused:

---

### Post by superprash2003 on 2009-02-11
follow step 3,4,5,6 [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by bhold on 2009-02-13
I have had samba and cups printing both fail when my XP system receives a patch, automatically reboots, and then gets a new dynamic ip address. 

I'm not enough of a network expert to provide a robust fix. You might be able to fix it with a static ip on the XP system, but I have tried that and introduced other more serious problems. 

Anyway, all I do whenever this happens is update /etc/hosts on my Ubuntu system, modifying the ip address of the XP system. That usually gets the XP shares and printer working again.

I have no idea whether or not this is your situation, but symptoms sound like the ones I have seen so might be worth a try.

---

### Post by FishRCynic on 2009-02-14
[http://ubuntuforums.org/showthread.php?t=388337](http://ubuntuforums.org/showthread.php?t=388337)

this summarizes the samba name resolving solutions
it fixes the ubuntu samba side (various solutions)

---

