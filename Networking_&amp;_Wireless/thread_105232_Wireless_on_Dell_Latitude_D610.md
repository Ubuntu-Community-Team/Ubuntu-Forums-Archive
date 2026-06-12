---
title: "Wireless on Dell Latitude D610"
date: 2005-12-17
forum: Networking &amp; Wireless
---

### Post by Delphinus on 2005-12-17
Hello,

I'm looking for some help getting my onboard wireless going on my Dell Latitude D610 Laptop... But not sure what I should be doing.

Have just installed Kubuntu 5.10 and everything else appears to be working well.

Many Thanks,
Delph

---

### Post by gerbman on 2005-12-18
[QUOTE=Delphinus]Hello,

I'm looking for some help getting my onboard wireless going on my Dell Latitude D610 Laptop... But not sure what I should be doing.

Have just installed Kubuntu 5.10 and everything else appears to be working well.

Many Thanks,
Delph[/QUOTE]

Hi,
I have the D810 and Kubuntu 5.10 (with wireless working), so I might be able to help. Can you list the contents of "/etc/network/interfaces", as well as any error messages you might be getting?

---

### Post by Delphinus on 2005-12-18
Thankyou for your help :)

Is this what you wanted?
```
jack@kubuntu-lappy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
jack@kubuntu-lappy:~$

```

And as for error messages.. well i haven't actually tried much apart from check in the network settings and can only see my LAN connection.

---

### Post by gerbman on 2005-12-18
[QUOTE=Delphinus]Thankyou for your help :)

Is this what you wanted?
```
jack@kubuntu-lappy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
jack@kubuntu-lappy:~$

```

And as for error messages.. well i haven't actually tried much apart from check in the network settings and can only see my LAN connection.[/QUOTE]

I am assuming that eth0 is your wired card. It looks like your wireless card (eth1) is missing from the interfaces file you listed. If you can't see your wireless interface in "Network Settings" then you might try editing the interfaces file directly. Try putting the following lines in there ```
iface eth1 inet dhcp
wireless-essid <your router name>
```Save the file and do ```
sudo ifup eth1
```from the command line. If "ifup" works, but you still can't connect, try doing ```
sudo dhclient
```Let me know where this gets you.

---

### Post by Delphinus on 2005-12-18
```
root@kubuntu-lappy:/home/jack# ifup eth1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.
root@kubuntu-lappy:/home/jack#

```

---

### Post by gerbman on 2005-12-18
[QUOTE=Delphinus]```
root@kubuntu-lappy:/home/jack# ifup eth1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.
root@kubuntu-lappy:/home/jack#

```[/QUOTE]

Try ```
sudo modprobe ipw2200
``` to load the wireless module. Then run the ifup command followed (if needed) by the dhclient command.

Hope that works.

---

### Post by Delphinus on 2005-12-18
```
root@kubuntu-lappy:/home/jack# modprobe ipw2200
root@kubuntu-lappy:/home/jack# ifup eth1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.
root@kubuntu-lappy:/home/jack#  
```

Do I not need to install any drivers or anything for it?

---

### Post by gerbman on 2005-12-18
[QUOTE=Delphinus]```
root@kubuntu-lappy:/home/jack# modprobe ipw2200
root@kubuntu-lappy:/home/jack# ifup eth1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.
root@kubuntu-lappy:/home/jack#  
```

Do I not need to install any drivers or anything for it?[/QUOTE]

I didn't have to on mine. What wireless card have you got? And what does ```
lsmod | grep ipw
``` output?

---

### Post by Delphinus on 2005-12-18
```
root@kubuntu-lappy:/home/jack# lsmod | grep ipw
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
root@kubuntu-lappy:/home/jack#  
```

Not sure what is in there actually... how can i find out?
Does this help at all?
```
jack@kubuntu-lappy:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:03:01.0 CardBus bridge: Texas Instruments: Unknown device 8036
0000:03:01.5 Communication controller: Texas Instruments: Unknown device 8038
0000:03:03.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)
jack@kubuntu-lappy:~$   
```

---

### Post by gerbman on 2005-12-18
Hmmm...that all looks the same as mine. Maybe it's called something other than eth1 on your system. I'll do some looking around for other possibilities. Kinda running out of ideas, I'm no expert.

---

### Post by Delphinus on 2005-12-18
Appreciate your help, you are more of an expert than me and it all helps!

---

### Post by gerbman on 2005-12-18
I've also seen "wlan0" in some posts. Might replace "eth1" with that in the interfaces file and then run "ifup wlan0".

---

### Post by Delphinus on 2005-12-18
Unfortunately same error :(

---

### Post by jpkotta on 2006-01-03
```
ifconfig -a
``` will list all available interfaces.  From what I remember of mucking with wireless on Gentoo, as soon as I modprobed the driver, the interface was available.  Fortunately for me, Ubuntu autoconfigured all of the networking for me.  Unfortunately, I'm not sure how to do this stuff manually in Ubuntu.  I just use the GUI, because I can't figure out which commands to run.

Here's my /etc/networking/interfaces:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid ACTIONTEC

auto eth1

But it is changed according to the network profile I have loaded.

---

