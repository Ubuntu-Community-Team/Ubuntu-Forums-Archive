---
title: "Not showing proper hostname on local network"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by jleg94 on 2011-03-08
Hello everyone, so lately I've been trying to get my computer's hostnames to work within my LAN. I found that I needed to connect them to the same workgroup, which I now have and for the most part it works. However, for one of the computers I do not want to use a .local domain, rather I need to use a .org. But no matter what I do, other computers on the network think it is a .local hostname. Currently the /etc/hostname on the computer file is as follows:
```

myhost.org
```The /etc/hosts file is as follows:
```

192.168.1.104    myhost.org    myhost    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
```And the /etc/samba/smb.conf global settings are as follows:

```
#======================= Global Settings =======================

[global]
   workgroup = WORKGROUP
   netbios name = myhost.org
   server string = %h server (Samba, Ubuntu)
   wins support = yes
;  wins server = w.x.y.z
   dns proxy = no
;  name resolve order = lmhosts host wins bcast
```By the way, running a DNS server is not an option for me. The other  computers are configured to use the DNS provided by the router, and I  cannot change them. I've been working on this for days, so any help would be greatly appreciated, thanks!

P.S., Here is a screenshot of an ipscan done from another computer on the  local area network so you can see what I'm talking about.

---

### Post by koszta on 2011-03-08
/etc/hostname is supposed to be only MYHOST, there is no domain there dude :) It is a VERY common mistake that even some of really good networking people make... 

/etc/hosts will have both myhost.mydomain, myhost

---

### Post by jleg94 on 2011-03-08
Thanks for the tip, I think I did hear that somewhere else too. Anyway I changed it, but still it doesn't fix the problem. Other computers on the network still see myhost.org myhost.local.

---

