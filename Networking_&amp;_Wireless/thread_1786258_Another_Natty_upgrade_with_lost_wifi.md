---
title: "Another Natty upgrade with lost wifi"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by rickbeton on 2011-06-19
Our Acer 5820T handles Natty nicely in all respects except for the wifi not working. It was fine under 10.10.

It uses the Atheros ath9k driver ... details:

```
rick@pond:~$ uname -a
Linux pond 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
rick@pond:~$ sudo lshw -C network
[sudo] password for rick: 
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: c8:0a:a9:33:d2:24
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.135 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:d3400000-d343ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: f0:7b:cb:85:10:ed
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d240ffff

```

I tried enabling wifi using the hotkey (fn-F3) with no success. Here's syslog when I try it:
```
Jun 19 16:47:20 pond NetworkManager[890]: <info> WiFi now enabled by radio killswitch
Jun 19 16:47:20 pond NetworkManager[890]: <info> (wlan0): bringing up device.
Jun 19 16:47:20 pond kernel: [ 1809.158370] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 16:47:20 pond NetworkManager[890]: <info> (wlan0): supplicant interface state:  starting -> ready
Jun 19 16:47:20 pond NetworkManager[890]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Jun 19 16:47:20 pond NetworkManager[890]: <info> WiFi now disabled by radio killswitch
Jun 19 16:47:20 pond NetworkManager[890]: <info> (wlan0): device state change: 3 -> 2 (reason 0)
Jun 19 16:47:20 pond NetworkManager[890]: <info> (wlan0): deactivating device (reason: 0).
Jun 19 16:47:20 pond NetworkManager[890]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun 19 16:47:20 pond NetworkManager[890]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun 19 16:47:20 pond NetworkManager[890]: <info> (wlan0): taking down device.

```
Any suggestions as to what I can try or do next?

Thanks,
Rick

---

### Post by vbSteve on 2011-06-19
Same problem here/

Acer Aspire 7551
Atheros 802.11b/g/n

```


  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:bb:ee:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d030ffff

06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```


Wireless stopped working after upgrade.

FN+F3 has no effect. I've been trying to get this to work for 2 days. I've done several guides and trouble shooter.

I think I'm gonna do a rollback to Maverick...

---

### Post by silex89 on 2011-06-19
I guess you've already tried "sudo ifconfig wlan0 up" (without the quotes). If you did and the wifi didn't worked, the command should throw you some output from the error. If this is the case, please post it :)


Best luck :)

---

### Post by vbSteve on 2011-06-19
OMG!     Thanks allot; That did the trick.  :)


EDIT ***


No it didn't work.   My Wifi LED turned on, but that's it,  still not able to connect or view a list of availble networks. (The option is grayed out)

---

### Post by chili555 on 2011-06-19
> WiFi now disabled by radio killswitchTurn on the switch??

---

### Post by rickbeton on 2011-06-19
> **chili555 said:**
> Turn on the switch??

Already done that - it turns off again (see syslog output above).

Rick

---

### Post by rickbeton on 2011-06-19
[QUOTE=silex89;10957560]I guess you've already tried "sudo ifconfig wlan0 up" (without the quotes). If you did and the wifi didn't worked, the command should throw you some output from the error. If this is the case, please post it :)


Thanks for the suggestion. It didn't help though. And there was no output message, nor did anything appear in the syslog.

Rick

---

### Post by silex89 on 2011-06-19
Hmmmm.... maybe if you do "sudo modprobe ath9k" and then "sudo depmod -a"

That should reload your driver and resolve the module depedencies for it, if you have no output everything went fine, so you can try "sudo ifconfig wlan0 up" again

Post the results! :D


Best luck :)

---

### Post by rickbeton on 2011-06-19
Thanks.

Unfortunately, there wasn't any output from either of those.

Rick

---

### Post by vbSteve on 2011-06-19
No output.  Option is still grayed out, Wifi LED is lit.

I can do this though: sudo iwlist scan
So the wireless is working, I don't understand why gnome would lock it. Is there a way to refresh it?

---

### Post by silex89 on 2011-06-19
Oh gosh..... :S....

The ath9k driver was installed from jockey right?

---

### Post by chili555 on 2011-06-19
What does this tell us?```
rfkill list all
```Thanks.

---

### Post by rickbeton on 2011-06-19
```
rick@pond:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2011-06-19
> **rickbeton said:**
> ```
rick@pond:~$ rfkill list all
0: [COLOR="Red"]acer-wireless: Wireless LAN
	Soft blocked: yes[/COLOR]
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```Please try:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Does it work now? If so, we can amputate acer-wmi.

---

### Post by rickbeton on 2011-06-19
Sweet! It's now working nicely.

Rick :-)

---

### Post by chili555 on 2011-06-19
Would you care to make it permanent? If so, please do:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit 
```Post back if you have more questions.

WARNING! silex and Steve, if you don't have this symptom, then this fix is not for you:> [COLOR="Red"]acer-wireless: Wireless LAN
	Soft blocked: yes[/COLOR]

---

### Post by silex89 on 2011-06-19
Don't worry man :) I was trying to guess a solution for the issue the guys were having. I have no issues with my laptop.

There's a ton of things I have to learn yet :D


Best Luck! :)

---

### Post by rickbeton on 2011-06-20
> **chili555 said:**
> Would you care to make it permanent? If so, please do:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit 
```

Thanks very much - it's working well now.
:P

---

