---
title: "samba woes: guest access option grayed out. Cannot employ passwordless sharing"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2009-05-05
Hi all.
I'm running Jaunty Jackalope on a 32 bit machine.
I'd like to share a hard drive on this machine, allowing passwordless access.

I've opened the netbios ports on the local machine to the local network.

When I use nautilus to navigate to a folder to check "sharing options", the option to share without enforce passwords is grayed out, and cannot be enabled.

I've tried to get around this by editing my smb.conf file to allow guest passwordless access. But so far, the option is still grayed out and my windows machine is still being asked for a password.

How do I fix this problem ?

Below is my smb.conf:
```

[global]
    ; General server settings                                                   
    netbios name = SKYNET_server
    server string =
    workgroup = SKYNET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_\
SNDBUF=8192

    passdb backend = tdbsam
    security = share
    guest account = nobody
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

  printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[Share]
    comment = local network shared area
    path = /media/shared
    public = yes
    writable = yes
    browseable = yes
    read only = no
    guest ok = yes
    guest only = yes
    guest account = nobody
    create mask = 0644
    directory mask = 0755



```

---

