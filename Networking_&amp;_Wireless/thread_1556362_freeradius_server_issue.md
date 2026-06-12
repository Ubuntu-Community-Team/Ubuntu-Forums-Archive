---
title: "freeradius server issue"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by omarch on 2010-08-19
Hi, I finish the setup of a freeradius server, but I have an issue, once all steps are finish and the server is running, I tried to access to the wifi, put my user and pass, but i can't access, the window ask me again and again for user and pass (even if I wrote correctly). The freeradius server is on 148.0.0.0 ip class, and the ap in on the ip class 192.0.0.0, I tried to put the AP and server in the same ip address class, but can't still connect to the wifi. I review many times the config files, i have no mistakes (I think), I don't know why can't connect to the wifi.

help me plz.  D:

regards

```

rad_recv: Access-Request packet from host 192.168.1.1 port 1034, id=1, length=165
        Message-Authenticator = 0x5544ca909212326b825832348d7141c1
        Service-Type = Framed-User
        User-Name = "rad"
        Framed-MTU = 1488
        Called-Station-Id = "00-0F-CF-BC-2A-9A:3Com"
        Calling-Station-Id = "00-17-37-FA-B2-EB"
        NAS-Port-Type = Wireless-802.11
        Connect-Info = "CONNECT 54Mbps 802.11g"
        EAP-Message = 0x0201000801726164
        NAS-IP-Address = 192.168.1.1
        NAS-Port = 1
        NAS-Port-Id = "STA port # 1"
+- entering group authorize {...}
++[preprocess] returns ok
++[chap] returns noop
++[mschap] returns noop
[suffix] No '@' in User-Name = "rad", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] EAP packet type response id 1 length 8
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] returns updated
++[unix] returns notfound
++[files] returns noop
[sql]   expand: %{User-Name} -> rad
[sql] sql_set_user escaped user --> 'rad'
rlm_sql (sql): Reserving sql socket id: 2
[sql]   expand: SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = 'rad'           ORDER BY id
WARNING: Found User-Password == "...".
WARNING: Are you sure you don't mean Cleartext-Password?
WARNING: See "man rlm_pap" for more information.
[sql] User found in radcheck table
[sql]   expand: SELECT id, username, attribute, value, op           FROM radreply           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radreply           WHERE username = 'rad'           ORDER BY id
[sql]   expand: SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority -> SELECT groupname           FROM radusergroup           WHERE username = 'rad'           ORDER BY priority
rlm_sql (sql): Released sql socket id: 2
++[sql] returns ok
++[expiration] returns noop
++[logintime] returns noop
[pap] Found existing Auth-Type, not changing it.
++[pap] returns noop
Found Auth-Type = EAP
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!    Replacing User-Password in config items with Cleartext-Password.     !!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!! Please update your configuration so that the "known good"               !!!
!!! clear text password is in Cleartext-Password, and not in User-Password. !!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
+- entering group authenticate {...}
[eap] EAP Identity
[eap] processing type tls
[tls] Initiate
[tls] Start returned 1
++[eap] returns handled
Sending Access-Challenge of id 1 to 192.168.1.1 port 1034
        EAP-Message = 0x010200061920
        Message-Authenticator = 0x00000000000000000000000000000000
        State = 0x30fef76430fceeb2d3f2a9a159ecc310
Finished request 1.
Going to the next request
Waking up in 4.9 seconds.
rad_recv: Access-Request packet from host 192.168.1.1 port 1034, id=1, length=165
Sending duplicate reply to client FCC_104A_211 port 1034 - ID: 1
Sending Access-Challenge of id 1 to 192.168.1.1 port 1034
Waking up in 2.0 seconds.
Cleaning up request 1 ID 1 with timestamp +32
Ready to process requests.

```

---

