---
title: "Samba, mount OK, no access after some time"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by isadjuk on 2009-11-18
PROBLEM:  Mounting share OK. Access to all files/dirs OK. After some time no access to share.

Tried mounting by commands:
> mount -t cifs //serwer/Serwer\ \(i\) /mnt/serwer --verbose -o domain=WORKGROUP,user=Pawe&#322;,password=pawel,iocharset=utf8,noexec,noperm
mount -t cifs //serwer/Serwer\ \(i\) /mnt/serwer --verbose -o domain=WORKGROUP,user=Pawe&#322;,password=pawel,iocharset=utf8,noexec,noperm,file_mode=0777,dir_mode=0777,sec=ntlmv2,nounix,nobrl,nosuid,nodev,rw 
Mounting was successful with rw access to all dirs/files (as was previous in winXP)
After some time - no access to share.

**testparm-s**
>     Load smb config files from /etc/samba/smb.conf
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    smb ports = 139
    name resolve order = lmhosts host wins bcast
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    path = /home/user/Publiczny
    create mask = 0700
    guest ok = Yes

[public]
    read only = No ** dmesg | tail**
>     [108371.454088] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[108371.454100]  CIFS VFS: Send error in SessSetup = -13
[109202.842897] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[109202.842911]  CIFS VFS: Send error in SessSetup = -13
[109205.320960] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[109205.320972]  CIFS VFS: Send error in SessSetup = -13
[109205.321705] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[109205.321714]  CIFS VFS: Send error in SessSetup = -13
[109205.323011] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[109205.323023]  CIFS VFS: Send error in SessSetup = -13 **cat log.smbd | tail -2**
>     [2009/11/18 14:38:19,  0] lib/util_sock.c:get_peer_addr_internal(1676)
  getpeername failed. Error was Transport endpoint is not connected

---

### Post by dmizer on 2009-11-18
Looks like your connection to the server is getting severed. Are you connecting wirelessly, and is there any firewall that could be interfering?

---

### Post by isadjuk on 2009-11-18
It's a LAN connection in office UBUNTU 9.04--Win2k3
When there was WinXP instead of Linux, all works fine. I replaced it for Ubuntu for some reasons and now got some strange problems.

I havent direct access to Win2k3 computer. There is Windows Firewall enabled and NOD installed. Could this make these problems ?!?!

---

### Post by dmizer on 2009-11-18
Well, for obvious reasons Windows handles the vagaries of Samba much better than Linux so just because you don't perceive a problem between Windows computers doesn't mean a problem doesn't exist.

Try disabling the firewall and NOD for a while and see if your problem persists.

Otherwise, if you are not mounting these shares via /etc/fstab, you may have more luck doing so.

---

### Post by isadjuk on 2009-11-24
I haven't direct access to win2k3 computer and cannot disable NOD and firewall :/

In this weekend I perheaps found solution.
I made simple script:
[B]
cat cifs_sync[/B]
```

#!/bin/sh

cifs_sync_proc(){    
    sleep 120
    #cd /mnt/serwer
    #ls > /dev/null
    ls `mount -l -t cifs | awk -F" " '{ print $4 }' ` > /dev/null
    cifs_sync_proc
    }

cifs_sync_proc

```After mounting, every 2 minutes this is accessing to all "cifs" shares. So all these errors are happen when win2k3 detect inactivity. For me logical is that samba on linux should simply reconnect/login to these shares or do something to keep connection. Is there any option/way todo that simply by command mount?

---

### Post by dmizer on 2009-11-24
My thoughts are that you'll have better luck mounting the share in /etc/fstab rather than using the mount command.

If you mount in /etc/fstab, I don't believe you'll experience this problem any longer.

---

### Post by isadjuk on 2009-11-24
I did as you write (fstab) and the situation is the same like mounting by command. After some time of inactivity I havent access to these shares (cifs).

Temporary **working** solution for me is using script as below [B][cifs_sync]
[/B]I see that this is not commonly happened problem :/
Maybe someone know the other way to this kind of synchronizing !?!?

---- EDITED:
I've found information on M$2003 support pages that system autodisconnect inactive shares after 15min default.

How enable keeping connections by samba ?

---

### Post by dmizer on 2009-11-24
You have a very unique case. Your connection is getting terminated by the server, not by Ubuntu. So the fix isn't really on the Ubuntu side.

The only thing I can think of is to try configuring autofs for mounting your CIFS share. Here's a primer: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by isadjuk on 2009-11-27
This should work !!
With option "--timeout=600" (10min) on mounting point will override M$2003 Server inactivity timeout limit 15min.

In next week I will see how it works in office and I think this may be added to your faq.
Sometimes this issue happen when people are connecting Ubuntu(samba) to Win2003/8 Server

One question I have got about this problem:
John Shakespeare wrote: Be or not to be ? I think: Samba should keep connection or shouldnt ? :P ;)

---

### Post by dmizer on 2009-11-29
> **isadjuk said:**
> 
John Shakespeare wrote: Be or not to be ? I think: Samba should keep connection or shouldnt ? :P ;)

In most cases, the /etc/fstab mount works. In this case, you have a specific server configuration that's intentionally severing inactive connections. You appear to have found one way to solve the problem. Another way would be to make Samba act more like a Windows client by configuring autofs as I suggested earlier.

So to answer your rhetorical question:
If you think Samba should only stay connected when needed, then you'll need to configure autofs.
If you think Samba should force connectivity for usability, then your solution should be fine.

Either way, congrats for finding that solution!

---

