---
title: "Cannot connect from remote systems"
date: 2016-01-14
forum: Mythbuntu
---

### Post by tlvranas on 2016-01-14
I have performed a clean install of Mythbuntu (twice) and I am not able to get it working correctly. I have run an install with both the front and backends (I tried doing backend only and the system will not boot). I can play live TV on the local front end. On the Myth box I can see the system information if I browse to 127.0.0.1:6544, however, if I try that with the IP address of the system I do not get a response. During the install I did check MythTV Service to allow other systems to connect to it.

---

### Post by aelfric55 on 2016-01-15
In addition to checking the Mythtv service for the master backend, you must configure this master backend (in the general settings page in the backend setup) to run on its actual IP address, not 127.0.0.1 or localhost. All local and remote frontends should be configured from their respective frontend setups to look for the database on that master backend ip address, not 127.0.0.1 nor localhost, nor, for remote frontends, on their own remote ip addresses. Finally, slave backends (if any) that you intend to have on your network will also be configured on the general settings page of their backend setups to look for the database on the ip address of the master backend rather than on their own ip addresses or localhost.

A properly configured and running master backend on an IP address should also automatically be visible on your network as a UPnP media server. Newly set-up remote frontends will frequently (but not always) find the master-backend-as-UPnP-server even without any particular frontend configuration. And any normal UPnP client, including bare-naked Windows machines and so-called "Smart TVs" can access and stream all prerecorded MythTV content via the UPnP master backend directly, without any frontend software whatever.

---

### Post by tlvranas on 2016-01-21
Thanks. That did the trick. Setting the IP address to the actual IP address of the system and not 127.0.0.1/

---

