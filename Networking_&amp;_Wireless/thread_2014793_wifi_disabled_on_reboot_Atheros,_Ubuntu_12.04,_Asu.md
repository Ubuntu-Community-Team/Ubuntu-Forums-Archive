---
title: "wifi disabled on reboot: Atheros, Ubuntu 12.04, Asus netbook Eee Pc 1000HE"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by OOHHOO on 2012-07-02
hi everyone, :cry:

hopefully someone can help. today i unchecked "enable wireless" from the panel so i could use a wired lan cable. the "enable wireless" option disappeared. i can now only see "enable networking". 

so i go into the bios and wireless networking is now disabled. so i manually enable wireless, save and exit out of bios. when xubuntu starts, i log in and still no "enable wireless" in the panel. so i reboot into bios and again wireless networking is disabled. it seems when xubuntu starts it disables my wifi in my netbook.

i searched and found an old thread with someone saying to go to
/etc/init.d/eeepc-restore 
  
and disable
EEEPC_PATH/eeepc-wifi-toggle.sh poweroff || true

but i dont have the "eeepc-restore" file in my init.d folder. 

any help is greatly appreciated.


```

$ lspci

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at ec00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ATL1E
	Kernel modules: atl1e

```

```

$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:8c:73:5f:bb  
          inet addr:24.115.221.88  Bcast:24.115.223.255  Mask:255.255.240.0
          inet6 addr: fe80::224:8cff:fe73:5fbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7638 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:7802774 (7.8 MB)  TX bytes:969951 (969.9 KB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99146 (99.1 KB)  TX bytes:99146 (99.1 KB)

```

```

$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

```

```

$ rfkill list all

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```

$ sudo /etc/init.d/networking restart

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                [ OK ]

```

```

$ sudo lshw -class network

  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:73:5f:bb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=24.115.221.88 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fbfc0000-fbffffff ioport:ec00(size=128)

```

thanks for any help.

---

### Post by OOHHOO on 2012-07-02
okay, now my wifi works  0_o

i rebooted numerous times after manually enabling wifi networking in bios just to have it disabled when logging into xubuntu.

the only thing i did differently this time is run in terminal

```
sudo /etc/init.d/networking restart
``` 

and i got the following output

```
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 
```

that seemed to reset my wifi  :confused:

well, all i know after reboot, i now have the "enable wireless" option so i can check it to activate wifi. 

hopefully this will help someone else.

---

### Post by snapsta on 2012-08-07
Thanks for the tips as I am facing exactly the same problem.  Unfortunately restarting the network didn't work for me though :confused:. 

Anyone have any other suggestions? Where would I find such a setting (given that I don't seem to have a 'eeepc-restore' in my /etc directory)?

---

### Post by snapsta on 2012-08-07
Okay, so kept going and found out what the problem was. As per [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/182251]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/182251"), when I typed 

```

$ rfkill list all

0: eeepc-wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

so then I typed

```

$ rfkill list all

0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

and "enable wireless" showed up in network manager, and it works fine.

I am not sure if this was the original problem or something I introduced trying to solve the same problem as the OP but hey it's working now!

Cheers

---

