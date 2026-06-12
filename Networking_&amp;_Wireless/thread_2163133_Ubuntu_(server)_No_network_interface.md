---
title: "Ubuntu (server): No network interface"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by hammereditor on 2013-07-17
I got a VPS from weloveservers.net yesterday, and it cannot ping any IP address, and I cannot use the apt-get and wget commands. After trying to figure out the problem for a while, I found that the network interfaces eth0 and eth1 are not configured. To make matters worse, bash cannot find the 'auto' command. I looked online and found that you mey need to edit /etc/network/interfaces or something, but there is an error saying that "Permission is denied" when I try entering '/etc/network/interfaces' into the remote console. I have full root access. It seems that the VPS provider installed something other than default Ubuntu 12.04 64-bit. For all I know, I may have Ubuntu Server installed, or some crazy, unheard-of OS. So is there a way to configure the eth0/eth1 network interface properly? If you're wondering how I can access the remote console, I think that the control panel program directly communicates with the server.

**EDIT: **The precise version of the OS is Ubuntu 12.04.1 LTS.

---

### Post by praseodym on 2013-07-17
As root open the file with nano:
```

nano /etc/network/interfaces
```
Close with CTRL+X. Check your system via:
```

uname -a
lsb_release -a
cat /etc/network/interfaces
cat /etc/resolv.conf
lspci -nnk | grep -iA2 net
```

---

### Post by hammereditor on 2013-07-17
Strangely, bash says the 'nano' command is unavailable. And, of course, there is no GUI installed.
Also, the OS is Ubuntu 12.04.1 LTS.

---

### Post by praseodym on 2013-07-17
Reboot and press the SHIFT button until you reach the grub2 bootloader. Choose the "recovery mode" then, and there "network configuration" and "root console". Install the tool:
```

apt-get install nano
exit
```

---

### Post by hammereditor on 2013-07-17
[LIST=1]
[*]Since there is no network interface, I cannot use the 'apt-get install' command.
[*]For some strange reason, there isn't a GUI and a desktop manager isn't installed.
[*]This is a virtual private server from a company, and there is no way I can access the boot loader.
[/LIST]

---

