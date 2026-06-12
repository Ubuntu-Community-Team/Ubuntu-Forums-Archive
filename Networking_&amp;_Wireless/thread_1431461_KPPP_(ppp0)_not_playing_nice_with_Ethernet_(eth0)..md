---
title: "KPPP (ppp0) not playing nice with Ethernet (eth0)."
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by Elludium_Q-36 on 2010-03-16
Other related threads that I found are closed. I'm in a remote location with NO CABLE, NO DSL, NO landline for dial-up.  Threads I read mentioned a lack of wireline broadband due to hurricane Katrina and storms do knock down lines.  This should work even just for backup.

I've read:
[http://ubuntuforums.org/showthread.php?t=658588&highlight=kppp+ethernet](http://ubuntuforums.org/showthread.php?t=658588&highlight=kppp+ethernet)
and others...

BEFORE: I could either connect KPPP to the tethered phone-modem OR plug in an Ethernet cable to my DD-WRT or stock linksys.  The cell phone could be physically connected via usb and the Ethernet would work but connect KPPP and neither would connect to local or net resources.  To go online via KPPP, the Ethernet had to be unplugged.

I did a "smart upgrade" in synaptic and something seems to have happened to my network manager packages, especially the kde network manager packages. 

NOW:  The Ethernet can be connected at anytime but does nothing, regardless of KPPP/PPP state or if the phone/modem is disconnected from the USB line.  I go online via KPPP/tethered modem, even with the Ethernet attached but can't access the lan, whether or not KPPP is logged on.  Knetwork manager seems useless  and the taskbar widget does virtually nothing, only allowing "VPN" settings while, "wired", "wireless", "mobile broadband" and "DSL" are greyed/ghosted.

The Network Management Widget uses the same graphic and layout as that found in the application launcher menu: System Settings -> under "Network & Connectivity" Network Settings -> Network Management.
It's in the same state as the widget and here is the info on the widget:
 
Network Management
Version 0.1
Using KDE 4.2.4 (KDE 4.2.4)
Will Stephenson
[email]wstephenson@kde.org[/email]

I tried the gnome network package and got some functionality from the tray applet.  It showed KPPP as active, with a phone graphic but plasma crashed and it reloaded with old-school graphics and doesn't recognize KPPP.

nm-connection-editor (gnome)
NetworkManager Applet 0.7.0.100
Notification area applet for managing your network devices and connections.
Copyright © 2004-2008 Red Hat, Inc.
Copyright © 2005-2008 Novell, Inc.
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)


Ideally, I'd like to be able to share the Internet connection over the lan but being able to access the lan and the net simultaneously would be nice.  Before a troll jumps in, I am aware of Cradlepoint with their CBA250 (Cellular Broadband Adapter), CTR350 Mobile Broadband Travel Router, CTR500 Cellular Travel Router, thier MBR1xxx (Mobile Broadband Router) series that provides failover/failback but they are not in the budget.  Besides, I'm leaning towards Tomato in the short term and OpenWRT with an AJAX gui as they are open source, have a better support community and can do more with the proper apps.  Even if I had a cradlepoint device, the Ethernet is not working.

If KPPP is closed, why would the "default route" option still be in effect?

I thank whomever released the latest KPPP as I usually no longer have to reboot after KPPP dies or is disconnected unexpectedly.  However, it's kind of a pain with this physical layout to have to unplug and replug.  I'd like to work with the WiFi settings incase I can get something or find someone with a local network or WiFiDX (Long Range WiFi).

I figured out that if I issued:  ```
 nm-connection-editor 
``` at a command prompt, I
get what appears to be the closest I've ever seen to an integrated network manager but it's never really worked on my system.

I included the contents of a few files and hope that sheds some light.  Thanks for reading!


file:///etc/NetworkManager/nm-system-settings.conf
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```


file:///etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
#iface eth0 inet dhcp

```

file:///etc/network-config/settings.txt
```

---begin user config---

name=new_config
description=<<<your description here>>>
icon=/usr/share/network-config/default-icon.png
default_net=eth0
dns_auto=TRUE
dns1=
dns2=
dns3=
run_script=

device=ppp0
active=FALSE
nat=FALSE
wifi=FALSE
w_ssid=
w_rate=auto
w_wep=
w_wpa=
dhcp=TRUE
ip=
netmask=
gateway=
-------------------

device=eth0
active=FALSE
nat=FALSE
wifi=FALSE
w_ssid=
w_rate=auto
w_wep=
w_wpa=
dhcp=TRUE
ip=
netmask=
gateway=
-------------------
______________

---end user config---

---begin internal config---

test_for_Internet=FALSE
Internet_site_for_ping=
wpa_configuration_file=/etc/wpa_supplicant/wpa_psk.conf
wpa_driver=ndiswrapper
dhcp_client=dhclient
run_script_at_the_end=
window_size_x=224
window_size_y=300

---end internal config---

```

ONE THING, because of people passing malicious code, please explain any commands, flags/switches you post.
Thanks!!!

---

### Post by Elludium_Q-36 on 2010-03-18
No one?

I got package network-config:

```

kubuntu@kubuntu:~$ network-config --help
Network-config version 0.2
Alexandru Ionut Munteanu
io_fx AT yahoo.fr

USAGE:  network-config [OPTIONS]

OPTIONS:
  -tl                   lists all the configurations
  -ts CONFIG            shows CONFIG configuration
  -tc CONFIG "FORMAT"   changes the CONFIG configuration
      FORMAT example : name=test,eth0[dhcp=TRUE ip=192.168. netmask=255.]
      formats : name,icon,description,dns_auto,dns1,dns2,run_script,dns3,default_net
      devices formats : active,ip,netmask,gateway,nat,dhcp,w_wep,
                        w_wpa,w_ssid,w_rate
  -ta CONFIG            applies the CONFIG configuration

kubuntu@kubuntu:~$

```
I was able to pull up the homepage of my DD-WRT Linksys router at 192.168.1.1 but in doing so, disabled the route to KPPP, though, ppp0 was selected as the default gateway in the GUI/frontend for network-config.  I had to disconnect KPPP and re-connect which allowed the route to KPPP but does not allow the route through eth0.

When I pulled network-config back up, I see a profile for avahi-autoipd which is a package and daemon.
```

Avahi IPv4LL network address configuration daemon

Avahi is a fully LGPL framework for Multicast DNS Service Discovery.
It allows programs to publish and discover services and hosts
running on a local network with no specific configuration.  For
example you can plug into a network and instantly find printers to
print to, files to look at and people to talk to.

This tool implements IPv4LL, "Dynamic Configuration of IPv4 Link-Local
Addresses" (IETF RFC3927), a protocol for automatic IP address
configuration from the link-local 169.254.0.0/16 range without the
need for a central server. It is primarily intended to be used in
ad-hoc networks which lack a DHCP server.

Canonical provides critical updates for avahi-autoipd until October 2010.

```

Seems like I'm pretty close but I could use and would really appreciate some guidance before I disable my route to KPPP.

---

### Post by dcstar on 2010-03-19
Issues with multiple network connections can be caused by incorrect routing - or using the same IP ranges for the disparate networks.

You need to look at the following things for all the various combinations of networks (one, the other, both):
```
route -n
ifconfig
iwconfig
```
You also need to check the /etc/resolv.conf file to see what DNS settings are in use.

Sometimes scripts that run after connection/disconnection of network devices to not get things right - especially since the newer way of doing things with the network-manager package in recent times.

I actually remove network-manager and use the "traditional" gnome-network-admin packages to set things up, because I like my Ethernet connection to work at boot-up **before** I log into a GUI.......

---

### Post by Elludium_Q-36 on 2010-03-19
Thanks for having a look.

I installed package gnome-network-admin and remember that from my first Fiesty Fawn box.  I left package network-manager in place for now.

ifconfig:
```

kubuntu@kubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr ****EDIT****  
          inet6 addr: ****EDIT****** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                             
          RX bytes:49220 (49.2 KB)  TX bytes:14799873 (14.7 MB)    
          Interrupt:23 Base address:0xe000                         

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:199710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                                
          RX bytes:11499163 (11.4 MB)  TX bytes:11499163 (11.4 MB) 

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.23.6.2  P-t-P:10.23.6.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1452  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0       
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0     
          collisions:0 txqueuelen:3                                 
          RX bytes:19459 (19.4 KB)  TX bytes:4783 (4.7 KB)       

```

iwconfig:
```

kubuntu@kubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

```

I ran route -n:
```

kubuntu@kubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.23.6.1       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
kubuntu@kubuntu:~$

```

I tried a few things an ran route -n again.
```

kubuntu@kubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.23.6.1       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
kubuntu@kubuntu:~$

```

I also ran ifconfig again:
```

kubuntu@kubuntu:~$ ifconfig
eth0      Link encap:Ethernet  ****EDIT******
          inet6 addr: *****EDIT****** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:49220 (49.2 KB)  TX bytes:14983515 (14.9 MB)
          Interrupt:23 Base address:0xe000

eth0:avahi Link encap:Ethernet  HWaddr ****EDIT*****
          inet addr:169.254.10.255  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11566590 (11.5 MB)  TX bytes:11566590 (11.5 MB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.23.6.2  P-t-P:10.23.6.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1452  Metric:1
          RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1160894 (1.1 MB)  TX bytes:236036 (236.0 KB)

```


I'm picking away at it but don't want to be cut off from the slow connection, which is better than nothing.

---

### Post by dcstar on 2010-03-20
> **Elludium_Q-36 said:**
> Thanks for having a look.
.........
I tried a few things an ran route -n again.
```

kubuntu@kubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.23.6.1       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
kubuntu@kubuntu:~$

```
........

There is no Default Gateway, for example:

```
dc@dc-master:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
172.16.142.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.158.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0        ** UG  **  100    0        0 eth1
```

Your primary network connection should have an entry to route all packets that do not have overriding routing entries, you do not have one.

It is a wonder anything works at all (this is supposed to be done by the if-up scripts):

```
route add default gw your-gateway-ip
```

---

### Post by Elludium_Q-36 on 2010-03-21
Thanks David,

Do you recall in which files that resides?
I'd rather edit the files and if things go wrong I can undo the editing.

I think for destination 0.0.0.0 my gateway should be either 10.23.6.1 or 10.23.6.2 and for destination 192.168.0.0 my gateway should be 192.168.1.1

The GUI frontends are a bit nondescript and could have better tooltip/doccumentation.

I wish I had stayed with 8.04 and would revert to 8.04.4 if it were supported longer.  I'm hoping 10.04 comes out with few unresolved bugs.

---

### Post by darab on 2010-10-12
Hi! I had the same problem, and here is the answer:

edit the /etc/NetworkManager/system-connections/Auto eth0 file:

[ipv4]
method=auto
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

change the "never-default" value to "true", and problem solved (for me, hopefully for you too).

---

