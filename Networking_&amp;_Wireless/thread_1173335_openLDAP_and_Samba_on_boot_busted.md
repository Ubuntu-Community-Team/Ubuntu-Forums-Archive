---
title: "openLDAP and Samba on boot busted"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2009-05-29
I have a server running openLDAP and Samba that's been configured.  It was all working well when I went ahead and did a reboot.  The first time I try to access Samba, I get 

```
Error connecting to 192.168.10.100 (Connection refused)
Connection to BGCFC failed (Error NT_STATUS_CONNECTION_REFUSED)
```

If I run

```
sudo /etc/init.d/slapd restart
```

then rerun smbclient I get in.  Is there a specific order that these have to come up?

Thanks,

---

