---
title: "Adding networking via USB 3G modem"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2013-07-31
I have a USB 3G modem that Kubuntu finds automatically but Lubuntu does not.  

How do I use nm-connection-editor (or other tools) to set up the modem?
Can it be done with the existing Lubuntu 13.10a system?

        $ lsusb
        Bus 001 Device 008: ID 12d1:1f01 Huawei Technologies Co., Ltd.

        $ lsb_release -rd
        Description:    Ubuntu Saucy Salamander (development branch)
        Release:        13.10

---

### Post by praseodym on 2013-07-31
Hi,

normally Lubuntu lacks the package "modemmanager", so just install it.

---

### Post by Lars Noodén on 2013-07-31
It seems to be there already in 13.10a

```

$ sudo apt-get install modemmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
modemmanager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by Lars Noodén on 2013-08-01
It looks like modem-manager is running but cannot find or recognize the modem:

```

$ pgrep -lf modem-manager
741 /usr/sbin/modem-manager

```

Strange that the modem is recognized and used by Kubuntu and not Lubuntu.   Does it have to be passed certain parameters?

---

