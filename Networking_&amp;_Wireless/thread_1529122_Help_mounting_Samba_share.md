---
title: "Help mounting Samba share"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by asenine on 2010-07-11
Hi,

I have been trying to mount a samba share using the following (followed by the pass for the share), but it doesn't seem to work:

```
smbclient //192.168.1.4/it -U it
```

It fails with the error "Server not using user level security and no password supplied". I do supply a password when asked for one.

I also tried through pyNeighborhood, it sees the shares on 192.168.1.4, but when I try to mount any of them it just says "Failed to mount".

Any ideas? It's not feasible for me to do it through places for a variety of reasons, pyNeighborhood or smbclient (or any other command line tool) would be great.

Thanks. :)

---

### Post by asenine on 2010-07-12
Bump, relatively urgent :(

---

### Post by Morbius1 on 2010-07-12
> "Server not using user level security and no password supplied"What's the next sentence of the error message?

If it's :
> Server requested LANMAN password (share-level security) but 'client  lanman auth' is disabledThen add the following lines to the [global] section of the clients smb.conf:
```
client lanman auth = Yes 
lanman auth = Yes 
```And restart samba:
```
sudo service smbd restart
```

---

### Post by asenine on 2010-07-13
Thanks a lot, I got it fixed by doing some changes serverside to the samba config.

Thanks though! :)

---

