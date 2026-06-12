---
title: "Windows share folder on Ubuntu"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by 0xCAFEFACE on 2010-04-27
I'm trying to set up a windows share folder on Ubuntu.

**What I want to do:**
I want users to be able to use sdb2 as a windows share folder. (Meaning, I need 
to get smbpasswd to sync with my Active Directory accounts, so they log in with DOMAIN\user, rather than UBUNTU\user)

**What I have done so far:**
I've got a separate hard drive (sdb2) mounted with NTFS on it.
I have added the machine to the Windows Domain (kerberos) and the windows machines on the network identify the box as part of the domain.

However, after searching across threads and google, including [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) I'm still having a hard time figuring this one out.

**Problems encountered:**
While the box is part of the domain, I cannot authenticate into it. 

I don't believe I know how to successfuly create the share folder, but the authentication part is preventing me from even doing "smbclient -L name" (which results in NT_STATUS_LOGON_FAILURE)

Maybe there is something I am doing wrong in the conf file?

Edit:

I was able to make "smbclient -L name" work after doing smbpasswd 'username' on my account...
```
Domain=[T] OS=[Unix] Server=[Samba 3.4.0]

        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (devubuntu server (Samba, Ubuntu))
        bg              Disk      Home Directories
Domain=[T] OS=[Unix] Server=[Samba 3.4.0]

        Server               Comment
        ---------            -------
        DEVUBUNTU            devubuntu server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        T

```

However, my Domain users from windows account are still unable to get into the folder from windows explorer. I believe there is something wrong with my samba passwords being in-sync with this?
Note-- The folder should be open to an AD group, not just the specific users.

edit2: my conf file.

```

[global]
        workgroup = T
        realm = T.COM
        server string = %h server (Samba, Ubuntu)
        security = ADS
        map to guest = Bad User
        obey pam restrictions = Yes
        password server = mainserver.t.com
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        restrict anonymous = 2
        client NTLMv2 auth = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        domain logons = Yes
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        template shell = /bin/bash
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes

[homes]
        comment = Home Directories
        read only = No
        create mask = 0775

```

edit3:
And the output from one of the log items...
```

[2010/04/26 15:55:39,  1] smbd/service.c:676(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

[2010/04/26 15:55:39,  1] smbd/service.c:676(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

[2010/04/26 15:55:39,  1] libads/kerberos_verify.c:335(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: failed to fetch machine password

[2010/04/26 15:55:39,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!

[2010/04/26 15:55:39,  1] libads/kerberos_verify.c:335(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: **failed to fetch machine password**

[2010/04/26 15:55:39,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!

```

edit 4:
I'm thinking I need to find a process to sync my samba passwords and my nix users...

edit 5:
Looks like I can log via windows in with DEVUBUNTU\bg, but not T\bg.

edit 6:[B]
Real question:
How do I get smbpasswd to sync with my Active Directory stuff?[/B]

---

### Post by 0xCAFEFACE on 2010-04-28
Bump.

I've added more detail to my problem and narrowed down what I need to do: get smbpasswd to sync with my Active Directory accounts.

---

