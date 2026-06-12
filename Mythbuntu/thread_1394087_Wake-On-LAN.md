---
title: "Wake-On-LAN"
date: 2010-01-30
forum: Mythbuntu
---

### Post by Crowie on 2010-01-30
Hi all

In an attempt to reduce carbon footprint and electric bill Ive setup ACPI wake up on fe/be box which works fine.  On a remote frontend ive configured it to wake the combined fe/be box when its powered on by simply putting 

```
wakeonlan <Mythtv BE/FE mac address> 
```

in /etc/rc.local which works and wakes the FE/BE however, as the frontend has nearly booted, it thinks there is no backend and asks to configure one eachtime.

Im not running mythbuntu-diskless just a mythbuntu frontend install on a hd

Does anyone have another way to either send wakeonlan magic packet earlier in the boot process or still have mythfronted autostart, but not default to configuring connection to backend.

thanks

---

### Post by Neon Dusk on 2010-01-30
Instead of putting the wakeonlan command in /etc/rc.local you should configure 'Enable Database Server Wakeup (Utilities / Setup -> Setup -> General -> Database Configuration 2/2) on the remote frontend.

Edit: There seems to a bug that stops mythfrontend starting once the backend is online - [Launchpad](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/514727)

---

### Post by Crowie on 2010-01-30
Thanks that works fine, 

Well it wakes the backend up but as you mentioned the frontend doesnt auto start at present due to that bug.

Thanks again

---

### Post by SiHa on 2010-02-01
On my old 8.04 install (and before I realised there was 'Enable Database Server Wakeup' built-in), I had a script that sent the WOL packet regardless, then pinged the backend once a second until it got a response before continuing. I can't remember the exact syntax, but it was something like:```
#!/bin/bash 
wakeonlan <backend mac address>
until [ ping <backend ip address> ]; do
     sleep 1
done

```

I added it to the start of the mythfrontend script, but I suppose there's no reason it couldn't go in /etc/rc.local.

---

