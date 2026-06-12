---
title: "Cannot configure network at boot time"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by humcasma on 2011-11-17
Hi,

I have created a VM with Ubuntu 9.10 that I run with Opennebula. Opennebula provides a script[1] that takes a MAC address and generates a /etc/network/interfaces file with a proper static IP address. My intention is to run that script at boot time, so that the network interface is configured as I want. I edited /etc/init/networking.conf and /etc/init/network-interface.conf see below) to invoke the vmcontext.sh provided by Opennebula, but it does not work. Any help to solve my problem is really appreciated.

Cheers,
Humberto

/etc/init/networking.conf
```

start on (local-filesystems
          and stopped udevtrigger)

task

pre-start script
        /etc/init.d/vmcontext.sh
        mkdir -p /var/run/network
end script

exec ifup -a

```

/etc/init/network-interface.conf
```

start on net-device-added
stop on net-device-removed INTERFACE=$INTERFACE

instance $INTERFACE

pre-start script
        /etc/init.d/vmcontext.sh
        mkdir -p /var/run/network
        exec ifup --allow auto $INTERFACE
end script

post-stop exec ifdown --allow auto $INTERFACE

```

[1] [http://dev.opennebula.org/projects/opennebula/repository/revisions/master/raw/share/scripts/ubuntu/net-vmcontext/vmcontext](http://dev.opennebula.org/projects/opennebula/repository/revisions/master/raw/share/scripts/ubuntu/net-vmcontext/vmcontext)

---

### Post by praseodym on 2011-11-17
Hi,

you can set the network permanently in the /etc/network/interfaces if you change "false" to "true" in the file: /etc/NetworkManager/nm-system-settings.conf, otherwise the NM ignores the manual config.

---

### Post by humcasma on 2011-11-17
> **praseodym said:**
> 
you can set the network permanently in the /etc/network/interfaces if you change "false" to "true" in the file: /etc/NetworkManager/nm-system-settings.conf, otherwise the NM ignores the manual config.

Thanks praseodym. I tried what you said, but for some reason it did not work. Anyway, i ended up completely removing the Network Manager and invoking the vmcontext.sh script at run level 2. Now it seems to work. Thanks a lot for the quick reply!

Cheers,
Humberto

---

