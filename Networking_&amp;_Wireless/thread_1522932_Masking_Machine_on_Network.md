---
title: "Masking Machine on Network"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by lelantus on 2010-07-02
I've searched the forums for some time, but can't really find a consistent working answer to this issue. If there's a thread that I missed, just post a link and I'll be the happiest guy around.

I'm currently running Jaunty with a Wubi dual-boot, just in case you wanted to know.

Here's the situation: when viewing a network that the machine is connected to, you can navigate to the Workgroup and see that it's connected as 'UBUNTU'. Now, you can't go in and view any files because file-sharing has been disabled on my end, but I'm still able to connect to networked machines and transfer files to the Ubuntu computer.

I'm wondering if it's possible to "hide" the computer name of 'UBUNTU' on this network list while still maintaining the ability to print to networked printers as well as connect to networked computers and transfer files. Basically to maintain all the privileges of a networked machine while masking the existence of the machine.

---

### Post by lelantus on 2010-07-05
[Update] Upgraded to 10.04, Lucid Lynx. The question remains the same.

---

### Post by lelantus on 2010-07-10
Bump.

---

### Post by Mr_VeRiTy on 2010-07-10
I would like to know too *bump*

---

### Post by bcbc on 2010-07-11
This is just a wild stab... for wubi installs the hostname defaults to ubuntu.

I don't know how you can hide it, but you should be able to change it from UBUNTU to something less obvious. On my network the ubuntu installs have different names.

change /etc/hosts to be ```
127.0.0.1	localhost
127.0.1.1	**NotUbuntu**

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

and /etc/hostname to be ```
**NotUbuntu**
```

Reboot and see if it shows up as NotUbuntu.

---

### Post by lelantus on 2010-07-16
It's not exactly what I was looking for, but it has basically the same result.

Thanks a lot!

---

