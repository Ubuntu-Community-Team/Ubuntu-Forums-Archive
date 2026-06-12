---
title: "Samba Shares Used in Windows DFS Not Accessible to Remote Users"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by dudemanbubba on 2010-02-07
We have an existing Windows 2000 network that I am trying to add an Ubuntu 8.04 server to.  I have put links into the windows domain DFS to the linux machine's samba shares.

The shares work fine for local users that are physically on the same network (192.168.0.X).  Remote users from other offices or dialing in with a vpn client can not access the these particular folders off the DFS.  However, they can map them directly from the ubuntu server.

Thanks in advance!

---

### Post by dudemanbubba on 2010-02-08
The other office locations which are connected via Cisco PIX vpn devices are all child domains of the main office.  Each office is in a different subnet (i.e. 192.168.1.X, 192.168.2.X, etc.)

They can access the main dfs with no problem.  It's only the dfs links that point to the ubuntu server that are not accessible from remote locations.

The followings is my smb.conf:

```
[global]
        security = ads
        realm = OCI.LOCAL
        password server = 192.168.0.102
        workgroup = OCI
        winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        winbind trusted domains only = no
        winbind allow trusted domains = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = no
        restrict anonymous = 2

[Archives]
        path = /mnt/raid/Archives
        writeable = yes
        create mask = 0777
        directory mask = 0777
        NT ACL Support = Yes

[Downloads]
        path = /mnt/raid/Downloads
        writeable = yes
        create mask = 0777
        directory mask = 0777


```For now while I am learning I have only moved our older files to this server in the Archives directory.  The Archives share is being referenced from the domain dfs.

Thanks again for any info!

---

### Post by dudemanbubba on 2010-02-10
I managed to get it working by using the actual ip address for the ubuntu box in the windows DFS setting in lieu of the hostname.  Not sure if this was the "proper" fix but it is working.

I am not a wiz kid at DNS setup, but I imagine it has something to do with name resolution between our main domain and the 4 child domains.

---

### Post by superprash2003 on 2010-02-10
if they are static ips , you can add them in the HOSTS file and then use hostnames

---

### Post by dudemanbubba on 2010-02-10
Is that something I do at the DNS server level?  It would be a pain to change the host files at all of our remote workstations.

---

### Post by superprash2003 on 2010-02-17
well , you could setup a Local DNS server for that.. yes server level

---

