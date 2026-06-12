---
title: "Wicd is suffocating me with its inability to connect to my home network."
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by LinuxforHumans on 2009-07-28
Hello.

I have been trying for days now to connect to my home network using Wicd. I have also tried KNetworkManager. As well as the WPA supplicant GUI. I've also tried to set it up manually via command line using both ifconfig and iwconfig. Nothing works.

Wicd detects my home network, as well as various other networks in my neighborhood. I can connect to my neighbor's unencrypted network, and browse the internet wirelessly on it. So I know my wireless card is functional and the drivers work.

I can't connect to my home WEP network. I guarantee the passphrase is correct.

I'm not really an expert with Linux. Please tell me which log files/shell outputs/file contents you need to see to help solve this issue once and for all, and for anyone else having this horrible problem.

Thank you.

---

### Post by SuperSonic4 on 2009-07-28
Which OS are you using and is your home SSID hidden?

---

### Post by LinuxforHumans on 2009-07-28
I am using BackTrack 4, a distro based on Ubuntu. I'm not sure whether my home SSID is hidden, how can this be determined? It shows up in the list of Wicd's available networks to join.

---

### Post by LinuxforHumans on 2009-07-28
Anyone?

---

### Post by LinuxforHumans on 2009-07-29
Okay pretend I'm using Ubuntu. How can I determine whether my SSID is hidden?

---

### Post by superprash2003 on 2009-07-29
when asked for the WEP key try various options like 64bit , 128bit etc

---

### Post by LinuxforHumans on 2009-07-29
superprash2003,

I've just tried each of the different WEP modes Wicd has available, and still none of them worked.

---

