---
title: "Unable to access dns service"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by roylez on 2006-01-15
The system that i installed on my ibm x32 was ubuntu at the beginning. Later I just installed kubuntu-desktop and switched to kde. After using kde for several weeks, i decide not to go back to gnome and i want to remove it to make some disk space. I removed ubuntu-desktop in synaptic and then a lot of other packages with the help of debfoster. After all those, i rebooted the computer. Kubuntu started without any warning, but I found that i could not access internet any more because "dns service is unreachable"!?

Did I removed something that is still necessary for the system, or is this just a configurational mistake? Can anybody help me? Thanks a lot.:confused:

---

### Post by adwait on 2006-01-15
The DNS servers are stored in /etc/resolv.conf. Check if the files there and the entries are correct and you should be fine.

---

### Post by Mr_Grieves on 2006-01-15
DNS server may also be recieved automaticly via DHCP.

Do this:
```

dig -x 72.14.207.99

```
and paste the result here.

---

### Post by roylez on 2006-01-16
Sorry for my late response.

My /ect/resolv.conf has only single one sentence:
```
nameserver 127.0.0.1
```

I tried the "dig" command, but it said "command not found". Maybe it was uninstalled.:(

---

### Post by roylez on 2006-01-17
when i tried "sudo ifup -a", the network connection became good again--but just for a few seconds, then the connection to dns was lost again. How strange!

---

### Post by roylez on 2006-01-17
I think I have found out what is wrong. 

The problem seems to have something to do with the command "dhclient" 's permission. After I execute the following sentences, the connection comes back to normal again. And It is still all right till now. 
```
sudo dhclient
```
I don't want to type this command after every login, any suggestions?

---

### Post by roylez on 2006-01-17
the connection is lost again. Running that command does not help any more.

---

### Post by roylez on 2006-01-17
The problem is fixed.

My solution is of ms windows style: I uninstalled all dhcp related packages together with configuration files, and then reinstalled them.

---

