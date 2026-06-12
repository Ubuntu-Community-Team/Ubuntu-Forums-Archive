---
title: "Ubuntu is not online correctly?"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by MiKogz on 2011-09-24
Hi, currently, I am on Ubuntu, and I am on line, but it shows that it hasn't installed properly and it won't let me download any add-ons from Ubuntu Software Center, I have a AT&T 3800hgv-b modem, wired connection. Also, I tried installing the device firmware, and the terminal won't let me enter my password, and if I press enter, it skips a line and then I can enter things but it says sorry that was incorrect! and makes me retype my password.

Sorry about the terrible organization of the thread, but I don't know much about Ubuntu, and don't usually ask for help anyways. If someone can tell me whats wrong, it would be greatly appreciated.

---

### Post by Bucky Ball on 2011-09-24
It is letting you enter your password in the terminal. It doesn't appear. Invisible for security reasons so please carry on. Just put your password in and hit enter.

Example:
Username?: Frank
Password?: [you won't see what you type here!]

How exactly is Ubuntu indicating that it hasn't installed correctly? Are you getting a message saying 'Ubuntu hasn't installed correctly' or are surmising it hasn't? What version? As a new comer the current long-term support release, 10.04 LTS, is a good place to start. 

Don't understand what device firmware you are loading ... for the internal network card or the external modem? You don't need the firmware for the latter, that is probably already working fine. ;)

---

### Post by MiKogz on 2011-09-24
> **Bucky Ball said:**
> It is letting you enter your password in the terminal. It doesn't appear. Invisible for security reasons so please carry on. Just put your password in and hit enter.

Example:
Username?: Frank
Password?: [you won't see what you type here!]
Oh thank you that helps, and also what is the terminal codes to install new router device firmware? Sorry, again I'm a newbie.

---

### Post by Bucky Ball on 2011-09-24
You shouldn't need to install that. Why? Please read my edited last post. Routers and modems don't need to have anything installed from Ubuntu to work with Ubuntu. They should be working already and if they're not, that is an issue with them, not Ubuntu. I'd concentrate on what's happening with your Ubuntu install on your local device. ;)

Open a terminal and paste/type this:

```
sudo lshw -C network
```Post the output back here please. That will show you exactly what is happening with the network device on your local machine. Also try, separately, not at the same time:

[/code]iwconfig
ifconfig[/code]

That will give you more info about your local network setup. Also, right click the network icon and make sure you have networking enabled. A wired connection should work 'automagically' but then, if you are using 11.10 (which isn't released yet) or one of the other newer releases you might be experiencing a known problem (bug) in the release. Once you know the hardware in the machine you have a better chance of fixing.

---

### Post by MiKogz on 2011-09-24
> **Bucky Ball said:**
> You shouldn't need to install that. Why? Please read my edited last post. Routers and modems don't need to have anything installed from Ubuntu to work with Ubuntu. They should be working already and if they're not, that is an issue with them, not Ubuntu. I'd concentrate on what's happening with your Ubuntu install on your local device. ;)

Open a terminal and paste/type this:

```
sudo lshw -C network
```Post the output back here please. That will show you exactly what is happening with the network device on your local machine. Also try, separately, not at the same time:

[/code]iwconfig
ifconfig[/code]

That will give you more info about your local network setup. Also, right click the network icon and make sure you have networking enabled. A wired connection should work 'automagically' but then, if you are using 11.10 (which isn't released yet) or one of the other newer releases you might be experiencing a known problem (bug) in the release. Once you know the hardware in the machine you have a better chance of fixing.


Alright, the outcome of that was:


  *-network UNCLAIMED
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fe8fc000-fe8fffff memory:d0000000-d00fffff
  *-network
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:4f:60:8b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=half firmware=1.1-1 ip=192.168.1.76 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:44 memory:febe0000-febfffff memory:febdb000-febdbfff ioport:eca0(size=32)
  *-network
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth1
       version: 24
       serial: 00:50:da:12:8e:3f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:cc80(size=128) memory:fe5fb780-fe5fb7ff memory:fe600000-fe61ffff
michael@ubuntu:~$ clear

michael@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fe8fc000-fe8fffff memory:d0000000-d00fffff
  *-network
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:4f:60:8b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=half firmware=1.1-1 ip=192.168.1.76 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:44 memory:febe0000-febfffff memory:febdb000-febdbfff ioport:eca0(size=32)
  *-network
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth1
       version: 24
       serial: 00:50:da:12:8e:3f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:cc80(size=128) memory:fe5fb780-fe5fb7ff memory:fe600000-fe61ffff

---

### Post by Bucky Ball on 2011-09-24
Oh, okay. ***New*** router. In the manual for the router you will find an IP address for the router. Plug a cable directly from the comp to the router, open Firefox (or a web browser) and in the address bar enter the router's IP address. It is in the form 192.168.0.1 (example only, your IP is probably different). That way you can enter the new router firmware BUT the router will already have firmware installed so does that need to be updated??? That is not the issue.

If you plug the cable straight from the modem to the computer do you go online (bypassing the router for now, that is probably just a setup issue)?

---

### Post by MiKogz on 2011-09-24
> **Bucky Ball said:**
> Oh, okay. ***New*** router. In the manual for the router you will find an IP address for the router. Plug a cable directly from the comp to the router, open Firefox (or a web browser) and in the address bar enter the router's IP address. It is in the form 192.168.0.1 (example only, your IP is probably different). That way you can enter the new router firmware BUT the router will already have firmware installed so does that need to be updated??? That is not the issue.

If you plug the cable straight from the modem to the computer do you go online (bypassing the router for now, that is probably just a setup issue)?


I didn't think the problem was my network, I was just making sure of it, because I was having problems with it earlier, but that doesn't explain why when I try to install something on Ubuntu Software Center, it says Failed to Download Package Files: Check Internet Connection.  I have been trying to install some things for a while, and it isn't just one package.

---

### Post by Bucky Ball on 2011-09-25
You can browse with Firefox just can't get packages? Only software centre that's not working? Do you know the IP of the router? Can you ping the router? If you know the IP of the router open a terminal and type:

```
ping ***.***.***.***
```... where '***.***.***.***' is the IP of your router.

When you right click on the network icon go to 'Edit Connections' and have a look in there if you are having no success. As for the router, that may need to be setup specific to how your ISP has you connecting to the net.

---

### Post by Dry Lips on 2011-10-02
> **MiKogz said:**
> I didn't think the problem was my network, I was just making sure of it, because I was having problems with it earlier, but that doesn't explain why when I try to install something on Ubuntu Software Center, it says Failed to Download Package Files: Check Internet Connection.  I have been trying to install some things for a while, and it isn't just one package.

Try running these commands from the Terminal:

```
sudo -i
apt-get update
apt-get upgrade
apt-get clean
apt-get autoclean
exit
```

---

