---
title: "add route mask"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by tobodestroyer on 2010-03-11
How can I add this to Ubuntu so that I can effectively use both networks connected to my machine. All I do in WinXP is run this from the command prompt:

route -p add 10.0.0.0 mask 255.0.0.0 10.15.122.9


How do I do this in Ubuntu?

---

### Post by helgman on 2010-03-12
Hello,

I'd try (might need to sudo here)
```
route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.15.222.9
```

(You need to open a terminal.)

More information: [http://linux.die.net/man/8/route](http://linux.die.net/man/8/route)

Regards,
Helgman

---

### Post by tobodestroyer on 2010-03-12
> **helgman said:**
> Hello,

I'd try (might need to sudo here)
```
route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.15.222.9
```

(You need to open a terminal.)

More information: [http://linux.die.net/man/8/route](http://linux.die.net/man/8/route)

Regards,
Helgman

I have two network cards. How do I specify which card to use?

---

### Post by helgman on 2010-03-12
> **tobodestroyer said:**
> I have two network cards. How do I specify which card to use?

[From link in previous post:](http://linux.die.net/man/8/route)
> **dev If**
[INDENT]    force the route to be associated with the specified device, as the kernel will otherwise try to determine the device on its own (by checking already existing routes and device specifications, and where the route is added to). In most normal networks you won't need this.

    If **dev If** is the last option on the command line, the word **dev** may be omitted, as it's the default. Otherwise the order of the route modifiers (metric - netmask - gw - dev) doesn't matter.[/INDENT]

Regards,
Helgman

---

