---
title: "Realtek 8111C LAN ports not communicating"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by Azothyran on 2011-12-18
Hello, I have Ubuntu 11.04 and Windows 7 Professional dual-booted on my  system (I'm currently posting from Windows). The problem I am having is  that neither of my LAN/Ethernet ports are communicating while in Ubuntu,  however the connections manager recognizes eth0 and/or eth1 as viable  connections options (though it claims an Ethernet cable is not  connected...) I assumed the  issues were related to a lack of drivers/modules to make the ports work  as intended, but after installing the modules in Realtek's repository  the ports still do not communicate.

I have dabbled with the terminal, and I understand basic  commands and how to execute them.

My system has a Gigabyte Technologies motherboard, model number EP45T-UD3R revision 1.0. The LAN/Ethernet ports are listed in Windows Device Manager as "Realtek RTL8168C(P)/8111C(P) PCI-E Gigabit Ethernet NIC" and this board has two (identical) LAN ports. I'm not sure if you need any more technical information about my hardware, but if you do I have all of the components in my system on Overclock.net here (the hardware list is near the bottom of the page).

[link --> Azothyran's rig on Overclock.net]("http://www.overclock.net/lists/display/view/id/3847565")

I HAVE tried NDISwrapper, I extracted the proper INF and SYS files from the sfxexe that Gigabyte provided, installed NDISwrapper using Terminal from the Ubuntu install USB stick I made, and told NDISwrapper to install and load the INF, but that didn't seem to make a difference to the connection manager (maybe I'm missing something?) but the wrapper did not spit out any errors. However, I have a sinking feeling NDISwrapper might only look for wlan, which won't do me a damn bit of good since they're ethernet ports (correct me if I'm wrong).

If anyone can assist me in this endeavor I would greatly appreciate it. If we can't figure out how to get Ubuntu to use my Realtek Ethernet ports, I wouldn't mind someone suggesting a cheap PCI LAN/Ethernet card to stuff in my system (I would prefer PCI over PCI-e, but either way) that has FULL compatibility with both Windows and Ubuntu.

---

### Post by Azothyran on 2011-12-19
Nobody has an idea or suggestions to help me with this issue? Not even a snotty 'search Google' comment?

---

### Post by praseodym on 2011-12-19
Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands:

```
uname -a
lspci -nnk
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /var/lib/NetworkManager/NetworkManager.state
```
You can c/p the outputs to a .txt file and upload it.

---

### Post by Azothyran on 2011-12-19
I uploaded the results of those terminal commands as you requested. Thanks.

---

### Post by praseodym on 2011-12-19
The interface name is called "eth1" instead of "eth0", and there is only one card shown:

```
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8168
	Kernel modules: r8168
```
Please show:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
after removing the wired profile in the networkmanager and rebooting.

---

### Post by Azothyran on 2011-12-19
After removing the profile in NetworkManager, rebooting, and inputting the command, I get:

```
# PCI device 0x10ec:0x8168 (r8169)

SUBSYSTEM=="net",
ACTION=="add",
DRIVERS=="?*",
ATTR{address}=="00:1f:d0:8f:9c:ca",
ATTR{dev_id}=="0x0",
ATTR{type}=="1",
KERNEL=="eth*",
NAME="eth0"

```

I'm not positive, but shouldn't there be something listed under the Device ID attribute?

---

### Post by praseodym on 2011-12-19
Now "ifconfig -a" should show eth0. Try also: Checkbox all user rights in "USERS&GROUPS", login again, checkbox "available to all users" and "connect automatically" in the wired profile of the network-manager, remove the profile and reboot.

---

### Post by Azothyran on 2011-12-19
Unfortunately, running "ifconfig -a" again shows 'eth1' and 'lo.'

```
azothyran@Chernobyl:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:1f:d0:80:a3:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0x6000 


```

I also checked the connection manager, and it did not have any profiles  in it. Upon clicking "New..." it shows "Available to all users" and  "Connect automatically" as checked by default.
 
 I'm sorry, but I'm not sure what you mean by Users&Groups, I only  saw User Accounts in system settings, and I found nothing related to  user permissions. I might need more information on how to do that.

---

### Post by praseodym on 2011-12-20
Try:

```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
```

---

### Post by Azothyran on 2011-12-20
Alright, eth0 is now listed under "ifconfig -a" and the ConnectionsManager. Tried rebooting and creating a network profile on eth0 but no luck still. Getting closer I think.

```
azothyran@Chernobyl:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:80:a3:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0x8000 

```

---

### Post by praseodym on 2011-12-20
Remove the profile again and take _anything_ off the current for about 10 minutes, then boot again.

---

### Post by Azothyran on 2011-12-20
> **praseodym said:**
> Remove the profile again and take _anything_ off the current for about 10 minutes, then boot again.

That didn't seem to have any effect, however I connected the Ethernet cable to the other LAN port on the mobo and it started showing activity on the port's LEDs, but on investigation in Ubuntu, no packets have been transferred...

---

