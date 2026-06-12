---
title: "connection's lost, system didn't recognize"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by m-tarek on 2009-09-05
[FONT="Tahoma"]I have a problem with my LAN and Wireless connection.
When I'm connected to the internet, suddenly nothing open although the network icon in the tray indicates that I'm still connected.:confused::confused:
When it happens (and it's happening alot) I have to unplug the wire (or turn off the wireless) and reconnet again. (smoetimes I  lose important data):(
I have HP laptop and my friend have another computer and also have the same problem.
Forgive my bad english, regards[/FONT]

---

### Post by uylug on 2009-09-05
> **m-tarek said:**
> [FONT=Tahoma]I have a problem with my LAN and Wireless connection.
When I'm connected to the internet, suddenly nothing open although the network icon in the tray indicates that I'm still connected.:confused::confused:
When it happens (and it's happening alot) I have to unplug the wire (or turn off the wireless) and reconnet again. (smoetimes I  lose important data):(
I have HP laptop and my friend have another computer and also have the same problem.
Forgive my bad english, regards[/FONT]
Are you sure you're still connected?

What is the output of this command when you think it is not working:

```
ping -c 4 google.com

```Does this problem happen to both wired and wireless connections?

---

### Post by m-tarek on 2009-09-05
[FONT="Tahoma"]I'm sure that it isn't connected.
Nothing responde, update manager, synaptic, firefox, miro
or any app i run. but the icon still like i tell you.
note: the network activity in the system monitor is at 0 or something like 4-40 b\sec[/FONT]

---

### Post by uylug on 2009-09-05
Are you connecting wirelessly or wired?

---

### Post by m-tarek on 2009-09-05
[FONT="Tahoma"]well, my connection is wired, but my friend's is wireless. he has the same problem.[/FONT]

---

### Post by uylug on 2009-09-06
> **m-tarek said:**
> [FONT=Tahoma]well, my connection is wired, but my friend's is wireless. he has the same problem.[/FONT]

Two computers connecting using different methods and still getting the same results? Do you have a router? Don't you think that may be the cause of it?

You probably have no internet for a while, which is because of your router disconnecting. You will not be notified if you lose internet connection

---

### Post by m-tarek on 2009-09-06
[FONT="Tahoma"]Sometimes that problem happens when I'm in internet-cafe, and nobody in the cafe suffer form this pronlem>
I'm in Damascus, Syria and my friend in London and we using diffrent connections so, I'm sure the router is not the problem.[/FONT]

---

### Post by hal10000 on 2009-09-06
> well, my connection is wired, but my friend's is wireless. he has the same problem.
Does he have the same problem on the same network?
How are you connected to the internet (router or what else)?

---

### Post by m-tarek on 2009-09-06
I told you. Sometimes that problem happens when I'm in internet-cafe, so I'm connected to a router. and my friend is connected to a wireless network.
And no, we aren't at the same network. I know him from another forum.

---

### Post by hal10000 on 2009-09-06
Instead of unplugging try the following command (in a terminal window):
[COLOR="Red"]sudo /etc/init.d/networking restart[/COLOR]
Does this work?
You may post the outputs of  the comands [COLOR="Red"]lspci[/COLOR] and [COLOR="Red"]lsusb[/COLOR] to verify which network card you have.
Maybe there are better drivers, i had the same problem with my intel wireless card and could fix it with the iwlagn drivers from the linux-backports-modules.

---

### Post by m-tarek on 2009-09-06
lspci:
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
lsusb:
Bus 002 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 09da:90a0 A4 Tech Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 138a:0001  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
My friend, the problem is not about reconnect, the problem is why is about disconnecting!!:confused:

---

### Post by hal10000 on 2009-09-06
I understand your problem, and the command i told you to try was only to verify wether the driver module is still loaded after disconnecting.
I forgot to tell you to shoot up this command he next time you get disconnected

---

### Post by m-tarek on 2009-09-06
OK, but in the mean time what can I do.

---

### Post by hal10000 on 2009-09-06
I found a possible olution here[http://www.linuxforen.de/forums/showpost.php?p=1572463&postcount=10]("http://www.linuxforen.de/forums/showpost.php?p=1572463&postcount=10"). Unfortunately it's in german, but i'll try to translate.
It might only help if you have windows installed on your computer.
The reason for the problem is the **Wake-On-Lan after Shutdown** Option in Windows, which has to be **enabled**. A criterion for this problem is the followig error message in your /var/log/syslog file (the next time you get disconnected):
> r8169: eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by hal10000 on 2009-09-06
I just found that this bug is already known here:[https://bugs.launchpad.net/linux/+bug/347711]("https://bugs.launchpad.net/linux/+bug/347711").

In post #13 it is stated, that compiling the latest kernel source might be a solution, but i don' know how familiar you are in compiling a new kernel.

---

