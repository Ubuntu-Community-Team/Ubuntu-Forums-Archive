---
title: "update 10.04 to 12.04, nfs mounts not working correctly"
date: 2012-10-23
forum: Networking &amp; Wireless
---

### Post by Hammi on 2012-10-23
Since upgrading my nfs server from 10.04 to 12.04, my nfs mounts (on a 12.04 ubuntu client) are not working ok anymore:

I can chown files on the mounted nfs shares to some users, but not to others. When the chown fails on the client (I want to chown to amavis:amavis), I get the following message/error on the server:

```

Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfsdcb: authbuf=192.168.1.0/255.255.255.0,192.168.1.102 authtype=user
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_uid_to_name: calling nsswitch->uid_to_name
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_uid_to_name: nsswitch->uid_to_name returned 0
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_uid_to_name: final return value is 0
Oct 23 17:05:04 alpha rpc.idmapd[14775]: Server : (user) id "1000" -> name "me@mydomain.org"
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfsdcb: authbuf=192.168.1.0/255.255.255.0,192.168.1.102 authtype=group
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_gid_to_name: calling nsswitch->gid_to_name
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_gid_to_name: nsswitch->gid_to_name returned 0
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_gid_to_name: final return value is 0
Oct 23 17:05:04 alpha rpc.idmapd[14775]: Server : (group) id "1000" -> name "me@mydomain.org"
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfsdcb: authbuf=192.168.1.0/255.255.255.0,192.168.1.102 authtype=user
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_name_to_uid: calling nsswitch->name_to_uid
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nss_getpwnam: name 'amavis@mydomain.org' domain 'mydomain.org': resulting localname 'amavis'
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nss_getpwnam: name 'amavis' not found in domain 'mydomain.org'
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_name_to_uid: nsswitch->name_to_uid returned -2
Oct 23 17:05:04 alpha rpc.idmapd[14775]: nfs4_name_to_uid: final return value is -2
Oct 23 17:05:04 alpha rpc.idmapd[14775]: Server : (user) name "amavis@mydomain.org" -> id "65534"
```For other users, "chown" is working. I never had this issue before, it appeared upon the upgrade from 10.04 to 12.04, and even after googling around for 4 hours, I haven't yet understood what the root cause is and how to fix it.

FWIW, user and group amavis exist in /etc/passwd and /etc/group on the client, but (of course) not on the server. idmapd.conf exists on both machines and is identical.

Please help!

---

