---
title: "Network boot timeout error"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2009-02-22
I followed this guide: [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

Here is my /etc/bootptab file:
```

client:\
ha="00:16:36:1F:A7:1C":\
ip=192.168.1.9:\
gw=192.168.1.1:\
sm=255.255.255.0:\
td=/var/lib/tftpboot:\
hd=/var/lib/tftpboot/pxelinux.0:\
bf=pxelinux.0:\

```

I'm positive that ha, gw, and sm are correct. Not sure if ip matters.

Here is /etc/default/tftpd-hpa 

```

RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"

```

Here is the output of "ls /var/lib/tftp"

```

netboot.tar.gz  pxelinux.0  pxelinux.cfg  ubuntu-installer

```


What else do I need to check to figure out why the client isn't booting?

---

