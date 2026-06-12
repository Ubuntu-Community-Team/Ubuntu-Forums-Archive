---
title: "xubuntu, no wired or wireless"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by cbatty on 2011-11-13
hi, was on ubuntu 10.10 before and now im at uni i wanted a windows system with ubuntu, i backed up all my important files and done a clean install of windows 7, then installed xubuntu on duel boot so both operating systems are brand new. 

in halls we use an ethernet cable and wireless in the library, i tried both and neither worked (on windows and xubuntu) 

i assume its something pretty basic i have done wrong, or not done, but i am completely lost. 

the message i keep getting is the port has timed out. 

one thing i should add is to access the internet here we are directed to a login page, i managed to reach this page once using wireless on the windows system but never on xubuntu. 

i know it is very vague but if anyone can point me in the right direction you will be my friend forever :P

chris

---

### Post by Jose Catre-Vandis on 2011-11-13
So sounds like your wireless/wired is working (under W7)

Does the login page require Internet Explorer? (I found this to be a problem in some hotels with wireless access, maybe the same at your Uni ?

Do you have a hardware switch for your wireless? Is it on?

On Xubuntu have you got all the wireless tools installed?
```
sudo apt-get install wireless-tools
```

report back on the following commands in Xubuntu in a terminal:
```
ifconfig
iwconfig
sudo lshw -c network
```

---

### Post by cbatty on 2011-11-14
it told me everything was installed for wireless...

ifconfig i got:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a3:72:9f  
          inet addr:10.191.0.97  Bcast:10.191.7.255  Mask:255.255.248.0
          inet6 addr: fe80::21e:68ff:fea3:729f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:206628 (206.6 KB)  TX bytes:31102 (31.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

sudo ishw -c network:

```
 *-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:68:91:33:7e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:68:a3:72:9f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=10.191.0.97 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f0400000-f0403fff ioport:a000(size=256)

```

thankyou for your help.

---

### Post by deltacomp on 2011-11-14
Hello, are you able to plug-in and connect to the interenet? It looks like that is working?

If your wireless hardware switch is one, have you tried to enable wireless through the desktop? In the top right corner, where the internet connections are, click on it and "enable wireless" if that option is available. If it is not, I am going to go with a drivers problem. 

lspci -nn in the terminal and post results. This will tell us what kind of wireless card you have, then we can lookup drivers.

---

### Post by cbatty on 2011-11-14
I cannot connect to the Internet at all not through wire or wireless. It's more the wired I need as that is what I have in my room. All wireless switches are on. 

It is telling me that I am connected but I have no Internet, yet everyone in my flat has it working. That's the confusing bit...

---

### Post by mathia on 2011-11-14
Hi,
Please install the following driver for your wired LOM as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices    Linux 2.6 - Fedora

$ sudo tar xvfj ./install_v10.91.2.3.tar.bz2
$ sudo cd ./DriverInstall
 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---

### Post by cbatty on 2011-11-15
Unfortunately it did not work.... any other ideas? I didn't install anything special when I had ubuntu 10.10...

edit: wireless now works, so im on xubuntu in the library. :D but unfortunately wired internet is more important

---

### Post by deltacomp on 2011-11-16
[QUOTE=cbatty;11458751]Unfortunately it did not work.... any other ideas? I didn't install anything special when I had ubuntu 10.10...

To clarify, the install didn't work? Or the install went fine, and the internet connection still doesn't work?

If the install of the drivers failed, let us know and we will try another solution. 

If the driver install worked, and you are still not getting internet, I would attempt this, it has worked for me in the past. 

Must have internet.

Open this [link]("http://pastebin.com/raw.php?i=RHSv9w8y"), save the file as wifix, open a terminal and cd to the folder where you save the file. Type "sudo bash wifix" (no quotes) hit enter and let it work. It will take some time, but it will try to install a lot of different internet drivers to your computer.

---

### Post by mathia on 2011-11-22
> **cbatty said:**
> Unfortunately it did not work.... any other ideas? I didn't install anything special when I had ubuntu 10.10...

edit: wireless now works, so im on xubuntu in the library. :D but unfortunately wired internet is more important
 
Hi,

Please post the install.log file to check the error.

Thanks,

---

