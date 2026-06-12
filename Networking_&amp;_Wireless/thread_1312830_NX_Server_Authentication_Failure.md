---
title: "NX Server Authentication Failure"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Aimjiel on 2009-11-03
Hey All,

I just installed nomachine NX on my ubuntu server, and unfortunately it fails to authenticate.

The problem is, these lines from the syslog:

```
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: ERROR: Failed authentication. NXSsh exit status is:255 'NXNssUserManager::auth'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: Failed SSHd authentication for user 'benny', to '127.0.0.1', port '22': ' ssh_exchange_identification: read: Transport endpoint is not connected^M\n' 'NXNssUserManager::auth'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: ERROR: Error while trying to authenticate user:benny. NXNssUserManager::auth returned 255 'NXShell::handler_login'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: ERROR: failed 'sshd authentication' for user 'benny' from 'x.xx.xx.xx'. NXShell::handler_login NXShell 373

```

There is no sshd running on port 22, I use a different port, I indicated that in the server and node configs.

Note, all I did was install, edit configs, and then try to connect.

I did try nxserver --daemon restart after editing the configs.

I tried once with a system user, which failed, same error, then added benny as a test, failed, then stumbled upon that in the syslog...

How can I get it to absolutely stop trying at port 22 and use the real port?

If anyone could help, that'd be awesome!

Jason

---

### Post by aleblanc on 2009-11-19
I had some problems connecting to nxserver aswell. 
Here are the problems I encountered and how I (eventually) fixed them:

Problem: I kept getting errors when adding users 
         (with: sudo /usr/NX/bin/nxserver --useradd username)

Solution: discovered that ssh connections from the server machine to
          itself were being blocked since I had denyhosts installed, 
          and it had detected unsuccessful logins from localhost. 
          I removed all references to 127.0.0.1, 127.0.1.1 and my 
          LAN IP address from /etc/hosts.deny, and then uninstalled 
          hostsdeny (which was then reinstalled once I got nx working).


Problem: can't authenticate when connecting with nxclient

Solution: make sure that "PasswordAuthentication" is set to "yes" in
          /etc/ssh/sshd_config


Problem: I was not able to login to user accounts that did not have
         administrator priviledges on the server machine. This was a 
         security problem since it meant that clients would 
         require the system password of a user with administrator 
         priviledges.

Solution: Change from ssh authentication to nx authentication, and use
         different password to system password: 
         set EnableUserDB & EnablePasswordDB to "1" in 
         /usr/NX/etc/server.cfg
         Add required non-administrator users to nxserver, 
         and one system administrator user 
         (with "/usr/NX/bin/nxserver --useradd" command)

         Then use the system administrator user as the user for
         logging in with nxclient, but choose the desktop of the
         required non-administrator (can make sure the system 
         administrator is not logged in on the server so that their 
         desktop is not listed when nxclient connects).
         The non-administrator users need to have corresponding nx user
         accounts in order to be able to access their desktops (even 
         though you don't use them for loggin in with nxclient).
         

Not sure if this will fix your problem but it will hopefully save others the hours of frustration I went through.

---

### Post by taorn on 2011-01-24
> **Aimjiel said:**
> Hey All,

I just installed nomachine NX on my ubuntu server, and unfortunately it fails to authenticate.

The problem is, these lines from the syslog:

```
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: ERROR: Failed authentication. NXSsh exit status is:255 'NXNssUserManager::auth'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: Failed SSHd authentication for user 'benny', to '127.0.0.1', port '22': ' ssh_exchange_identification: read: Transport endpoint is not connected^M\n' 'NXNssUserManager::auth'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: ERROR: Error while trying to authenticate user:benny. NXNssUserManager::auth returned 255 'NXShell::handler_login'
Nov  3 09:26:53 ubuntu NXSERVER-3.4.0-8[7270]: ERROR: failed 'sshd authentication' for user 'benny' from 'x.xx.xx.xx'. NXShell::handler_login NXShell 373

```There is no sshd running on port 22, I use a different port, I indicated that in the server and node configs.

Note, all I did was install, edit configs, and then try to connect.

I did try nxserver --daemon restart after editing the configs.

I tried once with a system user, which failed, same error, then added benny as a test, failed, then stumbled upon that in the syslog...

How can I get it to absolutely stop trying at port 22 and use the real port?

If anyone could help, that'd be awesome!

Jason

I guess that you had found the key of the issue, your post is quite old, but just in case, I got the how fix it.

I had the same problem an I'd managed to fix it taking a look on nx config files and setting up on files ***node.cfg*** and ***sever.cfg*** file the real ssh port. Both files are on ***/usr/NX/etc/***

Hope that helps ;)

---

