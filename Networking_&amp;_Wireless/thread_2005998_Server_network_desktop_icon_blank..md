---
title: "Server network desktop icon blank."
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by area1509 on 2012-06-18
Hi guys I installed the server edition of Ubuntu 12.04 and then installed the desktop with (sudo apt-get ubuntu-desktop).
Everything works, I can browse the internet with firefox, I have gotten the updates through update manager on the desktop so the network card is working fine.

My question is between the mail and sound icon there is an icon for the network manager and when I click in it and select connection information it displays an error saying
(error displaying connection information:)
(No valid connections found!)

when I open edit connections on the wired tab it is blank? is there a way to get this utility to read the network state and display it so I can edit it using this tool instead of the command line?

Thanks for your help and yes I am a noob but learning.

---

### Post by matt_symes on 2012-06-18
Hi

> **area1509 said:**
> Hi guys I installed the server edition of Ubuntu 12.04 and then installed the desktop with (sudo apt-get ubuntu-desktop).
Everything works, I can browse the internet with firefox, I have gotten the updates through update manager on the desktop so the network card is working fine.

My question is between the mail and sound icon there is an icon for the network manager and when I click in it and select connection information it displays an error saying
(error displaying connection information:)
(No valid connections found!)

when I open edit connections on the wired tab it is blank? is there a way to get this utility to read the network state and display it so I can edit it using this tool instead of the command line?

Thanks for your help and yes I am a noob but learning.

Why didn't you install the Ubuntu desktop edition ? Was it giving you problems when you tried to install it ?

From the terminal, please post the output of these commands..

```
ps aux | grep -iE "network-manager|networkmanager"
```

The E after -iE need to be a captial E. Case is important.

```
cat /etc/network/interfaces
```

Kind regards

---

### Post by area1509 on 2012-06-18
I wanted a file server that would also server videos to my xbox.

[HTML]area@File-Server:~$ ps aux | grep -iE "network-manager|networkmanager"
root       827  0.0  0.1 158668  5848 ?        Ssl  15:54   0:00 NetworkManager
area      2901  0.0  0.0   9380   920 pts/0    S+   17:43   0:00 grep --color=auto -iE network-manager|networkmanager

area@File-Server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.90.1.2
gateway 10.90.1.1
netmask 255.255.255.0
network 10.90.1.0
broadcast 10.90.1.255[/HTML]

---

