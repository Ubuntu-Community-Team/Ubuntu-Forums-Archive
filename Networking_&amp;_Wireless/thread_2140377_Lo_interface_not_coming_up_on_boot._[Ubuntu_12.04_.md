---
title: "Lo interface not coming up on boot. [Ubuntu 12.04 LTS Server]"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by mboeschen on 2013-04-29
Lo interface is not coming up on boot.  Below is my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
#       address 127.0.0.1
#       netmask 255.0.0.0
#       broadcast 127.255.255.255
#       up ip route replace 127.0.0.0/8 dev lo


# Auto generated venet0 interfaces
auto venet0
iface venet0 inet static
        address 127.0.0.1
        netmask 255.255.255.255
        broadcast 0.0.0.0


        up route add default dev venet0


auto venet0:0
iface venet0:0 inet static
        address 74.208.104.xxx
        netmask 255.255.255.255



```
The other two interfaces come up fine.  I can get out to the internet, but I cannot get to localhost (127.0.0.1), and there is one in my hosts file.  Once the machine comes up, I can run a IFUP Lo command, and then it will work just fine.

---

### Post by mboeschen on 2013-04-29
EDIT: If I do an IFUP lo, it says "interface already configured".  I have to do an ifdown lo, then ifup lo.

---

### Post by Cheesehead on 2013-04-29
Is 127.0.0.1 defined in /etc/hosts?
Is there a relevant message in /var/log/syslog?
Is there a relevant message in /var/log/dmesg?

---

### Post by mboeschen on 2013-04-29
Hosts:
127.0.0.1 localhost.localdomain localhost
Syslog:
I have nothing in there since Apr 25 (I upgraded from 10.04 lts to 12.04 lts)
Dmesg:
Empty

---

### Post by Cheesehead on 2013-05-02
> **mboeschen said:**
> 
Syslog:
I have nothing in there since Apr 25 (I upgraded from 10.04 lts to 12.04 lts)
Dmesg:
Empty

You should probably reboot the system. Nothing getting logged is a different (and potentially big) problem.

---

### Post by mboeschen on 2013-05-02
I have already rebooted.  I think what the overall problem is the different startup scripts between 10.04 and 12.04.  I think it is not logging because the logging service is not starting at boot.  And neither my Apache or Mysql are starting automatically.  I have to start them manually.  My guess is something similar with the networking piece.  Any ideas?

---

