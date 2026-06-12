---
title: "wireless disabled"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by Joust on 2010-08-28
i installed ubuntu on a laptop and wireless worked.
after a reboot, it no longer works.
since it worked at first, I assume all the drivers and everything required is there but for the life of me I cannot make it go active again.
please help.

---

### Post by yesterfox on 2010-08-28
i have the same problem...
can you paste the results of the "lspci" here ?

---

### Post by xircon on 2010-08-28
Did either of you force a reboot after a failed attempt to suspend?

Check the output of:

```
cat /var/lib/NetworkManager/NetworkManager.state
```

It should read sort of like:

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

If it says false edit, change and reboot:

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by Iowan on 2010-08-28
Just in case you haven't checked...
Right-click Network Manager icon and verify Networking (and wireless?) is enabled.

---

### Post by Joust on 2010-08-28
Dude, you're a genius. that was it.
its all working now.
Its odd that the network managers could not change this 
i changed WirelessEnabled=true and its all good now.

> **xircon said:**
> Did either of you force a reboot after a failed attempt to suspend?

Check the output of:

```
cat /var/lib/NetworkManager/NetworkManager.state
```It should read sort of like:

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```If it says false edit, change and reboot:

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by xircon on 2010-08-28
Happened to me, 23:30 at night, bog-eyed, took me till 2:30 to sort it.  Still can't suspend the damned laptop yet :(

---

### Post by Joust on 2010-08-28
mine seems to suspend fine.
thanks again for the help. that was the trick for sure.
now to figure out what xwindows gui will make this change.

---

