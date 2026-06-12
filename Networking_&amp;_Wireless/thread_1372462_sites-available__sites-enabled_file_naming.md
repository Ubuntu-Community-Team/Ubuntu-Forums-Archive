---
title: "sites-available / sites-enabled file naming ?"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2010-01-04
So I've got dyndns pointing to my machine and all of that works fine.  I've since added in my /etc/hosts file:
```

127.0.0.2    localhost.localdomain    testsite.com
```

Added this to /etc/resolv.conf
```

search localhost.localdomain
```

FF will go where I want when I enter in [color="blue"]http://testsite.com/[/color]  Now, does the testsite.com file have to end in .conf in either or both of those directories?  I want to be consistent.  If my dyndns assigned name doesn't end in .conf in the .../sites-enabled dir. then apache says it can't find it.

TIA,

---

### Post by Charlietje on 2010-01-04
sites available or enabled is a configuration for apache2.

Unless you have your own dns SERVER running you put in your resolv.conf your default gateway, so the router will take care of the dns queries.

dyndns is only to make your dynamic IP address available on the internet.
No need to do additional interface configurations.


Regards

---

