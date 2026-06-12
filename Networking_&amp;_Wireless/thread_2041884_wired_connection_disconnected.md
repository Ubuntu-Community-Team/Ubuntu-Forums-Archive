---
title: "wired connection disconnected"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by wrknight on 2012-08-13
My network connection periodically comes and goes on my dual boot ubuntu 12.04 / Windows 7 64 bit system.  This only happens with ubuntu.  It doesn't happen with Windows 7 loaded.  Also, I have 5 other computers on the network, four of which are also dual boot Windows 7/Ubuntu 12.04.  This problem is not observed on any other machine.

I upgraded to 12.04 this morning with a fresh installation after deleting the old partition and formatting a new one.  Initially, the network connection was established and everything worked fine.  While reloading files from my backup the network went down.  After poking at it several times with ifconfig, ifup, ifdown dhclient and nm-tool, it came back up and continued to work for about 15 minutes then went down again.

sudo ifdown eth0 returns "interface eth0 not configured"

sudo ifup eth0 returns "ignoring unknown interface eth0"

ifconfig shows the hardware with correct mac address but no ip address

nm-tool shows the device is wired with driver r8169, correct mac address, carrier detected and on, speed 100 Mb/s, state="connecting (getting IP configuration) 

dmesg says nothing about the network going down but repeated reports no ipv6 router present.

I have deleted, added, and reconfigured the network connections parameters at least a dozen times using the small no-name applet in the notifications panel.

When I ping the router it returns "Network is unreachable".

At this point, I cannot get the network back up at all.  Can anyone help?

---

### Post by praseodym on 2012-08-13
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
```
Checked the BIOS ("last state", "on")?

---

### Post by wildpulse on 2012-08-16
I had the same problem with a Sony Vaio laptop. Reviewed system logs and noted 'interface not ready' messages. Forcing a kill on NetworkManager worked for me.

```
sudo pkill -9 NetworkManager
```

---

### Post by wrknight on 2012-09-01
Problem solved.  I use a powerline network adapter (ethernet over powerlines) because my house isn't wired for ethernet and wireless routers won't reach to through the entire house.  One of the powerline adapters was creating excessive noise that reduced the S/N to the computer in question.  When I replaced the noisy powerline network adapter, the problem went away.

---

