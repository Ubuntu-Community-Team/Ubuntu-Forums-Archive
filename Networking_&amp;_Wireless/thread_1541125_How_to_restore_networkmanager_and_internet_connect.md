---
title: "How to restore networkmanager and internet connection after ubuntu update"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by andrew nz on 2010-07-28
Hi guys, i'm realatively new to linux am just getting my head around the command line, any way my problem today is, my network connection and networkmanger program have been deleted/uninstalled after i did a system update. im running ubuntu 10.04 32 bit. I have run of some commands which should be able to tell you whats going on. at the moment i'm using a live ubuntu cd to gain net access.

so the question is How do i restore my network connection and get my networkmanager program back without a internet connection. (i can download stuff to a memory stick and do manual install)

Hope someone can shed some light on this, i know this topic has been covered before although each case seems slightly different to mine.

andrew@andrew-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:95:27:f4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:327464 (327.4 KB)  TX bytes:327464 (327.4 KB)

andrew@andrew-desktop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e6:95:27:f4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:cc00(size=256) memory:e3010000-e30100ff
andrew@andrew-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

andrew@andrew-desktop:~$ ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
andrew@andrew-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
andrew@andrew-desktop:~$ sudo service network-manager start
start: Job failed to start
andrew@andrew-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e6:95:27:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:22 ioport:cc00(size=256) memory:e3010000-e30100ff
andrew@andrew-desktop:~$ /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
                                                                         [fail]
andrew@andrew-desktop:~$

---

### Post by Iowan on 2010-07-28
You've tried re-adding a "Notification Area" to the top panel to see if Network Manger returns? Have you checked (from a terminal) **ps -ef |grep nm** to see if nm-applet is running?

---

### Post by andrew nz on 2010-07-28
andrew@andrew-desktop:~$ ps -ef |grep nm 
andrew    1691  1597  0 11:45 pts/0    00:00:00 grep --color=auto nm 
andrew@andrew-desktop:~$

---

### Post by andrew nz on 2010-07-28
I tried "add to panel", but its not their in the list of options. also when i go into ubuntu software centre it shows up as been not installed( because you can click the install button) not that simple tho because you need a connection to install from the software centre

---

### Post by Iowan on 2010-07-28
> **andrew nz said:**
> I tried "add to panel", but its not their in the list of options. You are looking for "Notification Area" - not Network Manager?

[Here]("http://ubuntuforums.org/showpost.php?p=9648261&postcount=2") is another option.

---

### Post by andrew nz on 2010-07-29
i tried the alt+f2 trick to run nm-applet , didn't work because their is no networkmanager installed.

also tried to add "notification area" click install but nothing happens either.

this is odd that an update would uninstall or disable networkmanager and maybe eth0,
all that :
andrew@andrew-desktop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface 

and

andrew@andrew-desktop:~$ ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: Permission  denied
andrew@andrew-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
andrew@andrew-desktop:~$ sudo service network-manager start
start: Job failed to start
andrew@andrew-desktop:~$ lshw -C network



how can i reinstall this program off a memory stick?

---

### Post by bkratz on 2010-07-29
Here is a similar thread--it is referencing 9.10 specifically; but hopefully it will help lead you to the right answer.

[http://ubuntuforums.org/showthread.php?t=1319244](http://ubuntuforums.org/showthread.php?t=1319244)


See post 5 and on

---

### Post by cavalier911 on 2010-07-29
I disable Network Manager on my desktop computers.
I use Jaunty,the shortcut menu names to Startup Programs may be different on Lucid. 
Open synaptic and search for network-manager and network-manager-gnome
Have they been removed, or are they installed but broken?
If they're not installed you can skip Step 1.
 
Step 1. Turn off NM from starting when I log into gnome.
System/Preferences/Startup Applications/Startup Programs tab/NetworkManager uncheck
Step 2. Edit /etc/network/interfaces
```
gksudo gedit /etc/network/interfaces
```Add what's in **bold** for DHCP:
```
# The loopback network interface
auto lo
iface lo inet loopback


[B]# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp[/B]

```Save,Reboot

To enable network manager  you can put # marks in front of your edits to /etc/network/interfaces and recheck network manager in Startup Programs

---

### Post by andrew nz on 2010-07-30
I ended up solving the problem the hard way. clean re-install.
i've been staying away from the update manager.
have got ushare and apache setup (can access webpage on my computer from web now)
and i want to do a update but without risking losing my network and networkmanager.

---

