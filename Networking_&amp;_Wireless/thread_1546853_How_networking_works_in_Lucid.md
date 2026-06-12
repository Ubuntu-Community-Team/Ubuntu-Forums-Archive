---
title: "How networking works in Lucid"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by kaway1337 on 2010-08-06
I am a little confused with the way that networking works in Ubuntu (Lucid in particular). I switch my PC on and my network magically works (ie I dont understand what is configuring everything). I do have a DHCP server, but im not sure which process/file is configuring the interface.

There is no entry for my wired interface (eth0) in /etc/network/interfaces.

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

Does this means that Network Manager is then responsible for configuring this interface? How does Network Manager configure this interface (are there config files somewhere that specify settings such as static IP and duplex)?

---

### Post by dineshs on 2010-08-06
Lucid uses Network manager Right-click on the NM icon(two opposite arrows on top right of the panel OR system=preferences=network connections) and then click on Edit Connections. 
Select the tab, wired 
You will see eth config
The config files are in /etc/NetworkManager

---

### Post by zoya on 2010-08-06
I switch my PC on and my network magically works (ie I dont understand what is configuring everything). I do have a DHCP server, but im not sure which process/file is configuring the interface.

thanks

---

### Post by kaway1337 on 2010-08-16
> **kaway1337 said:**
> Does this means that Network Manager is then responsible for configuring this interface? 

OK so I found this bit of documentation on my local system (/usr/share/doc/network-manager/README.Debian):

> Devices listed in /etc/network/interfaces _will_ be managed by NetworkManager
unless the ifupdown system-config-setting is enabled and is setup to run
in "Unmanaged mode".

...

Unmanaged mode will make NetworkManager not touch any wired/wireless device matching
an interface name configured in /etc/network/interfaces.

Managed mode will make NetworkManager manage all devices and will make NetworkManager
honour all dhcp and static configurations for wired and wireless devices.

So this kind of answers my first question. I am running NetworkManager in unmanaged mode (ie NM will not try to configure any devices that have an interface entry in /etc/network/interfaces) which I can verify because of the entry in /etc/NetworkManager/nm-system-settings.conf

> 
[ifupdown]
managed=false


Given that I havent screwed around with my network settings, I have to conclude that NM is set to configure any interface that is not specifically defined in /etc/network/interfaces by default.



> **kaway1337 said:**
> How does Network Manager configure this interface (are there config files somewhere that specify settings such as static IP and duplex)?

As mentioned by dineshs, config files for NM seem to be in /etc/NetworkManager, specifically the one setting managed/unmanaged is /etc/NetworkManager/nm-system-settings.conf. 

Looking through that directory, there does not seem to be any config files that relate to a specific interface. There are a number of settings that can be specifed by using NetworkManager Applet or "system->preferences->Network Connections" (however, duplex settings are not one of them - which is a bugger because it is setting my duplex to half-duplex every time I restart my PC) but I do not know where these settings are stored.  

Perhaps it gets this information from DHCPclient?

If thats the case, I guess its possible that I can tell my DHCP client to override the duplex settings.

---

### Post by dineshs on 2010-08-16
There is a folder system-connections which contain files such as Autoeth0 DSLconnection etc
Does ```
gksudo nautilus /etc/NetworkManager
```
show [COLOR="RoyalBlue"]system-connections[/COLOR]

---

### Post by kaway1337 on 2010-08-16
yup it shows that folder.

but the folder is empty.

---

### Post by dineshs on 2010-08-16
Are you using NM or /etc/network/interfaces
In my case there is a text file Auto eth1 that contains
```
[connection]
id=Auto eth1
uuid=335fe4a7-426f-4d5a-83af-20627374bbcb
type=802-3-ethernet
autoconnect=true
timestamp=0

[ipv4]
method=manual
dns=4.2.2.1;8.8.8.8;
addresses1=22.2.1.182;24;22.2.1.1;
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:e0:18:c0:4d:8f
mtu=0

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false
```

---

### Post by kaway1337 on 2010-08-16
I must be using NM.

> **kaway1337 said:**
> There is no entry for my wired interface (eth0) in /etc/network/interfaces.

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


I would have expected a file somewhat like yours but there isnt one in /etc/NetworkManager (or anywhere in /etc)

```

$ sudo grep -ir eth0 /etc/ | grep -v ":#"
/etc/samba/smb.conf:;   interfaces = 127.0.0.0/8 eth0
/etc/initramfs-tools/initramfs.conf:DEVICE=eth0
grep: /etc/motd: No such file or directory
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="--MyMAC--", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
$

```

Is there anything other than NM that could be controlling my interfaces?
:confused:

This was a fresh install (ie not upgraded from a previous Ubuntu release), although it was on another PC/hardware and I have just dd'ed the old hard drive to a new drive and put the new drive into my current PC. Perhaps some files were automatically removed because the MAC changed (Ubuntu detected a new interface)?

---

### Post by kaway1337 on 2010-08-23
OK so reading up on NetworkManager documentation and there are two types of connections: system and user.

I believe you can toggle a connection's type by going into "Network Connections" -> edit and toggling the "available to all users" checkbox at the bottom left. 

I assume, enabling this checkbox changes the connection type to be system as when this is checked a file (named after the connection name in Network Connections) is created in **/etc/NetworkManager/system-connections/** and when it is unchecked it is removed.

```

# updatedb
# locate 'Wired'
/etc/NetworkManager/system-connections/Wired connection 1
#
# ls /etc/NetworkManager/system-connections/
Wired connection 1
#

```
At this point I toggled the checkbox
```

# updatedb
# locate 'Wired'
#
# ls /etc/NetworkManager/system-connections/
#

```

This explains why **dineshs** had a file in that folder called "Auto eth1" and I did not.

When I tick the checkbox, the file that is created is similar to dineshs' and contains the line duplex=full, but yet the interface still is not set to full duplex on reboot.

```

# grep duplex /etc/NetworkManager/system-connections/Wired\ connection\ 1 
duplex=full
# mii-tool eth0
eth0: no autonegotiation, 100baseTx-HD, link ok
#

```

Which raises two questions:
1) Where does the "Wired connection 1" config file go when the checkbox is unticked?
2) Does the config file "/etc/NetworkManager/system-connections/Wired\ connection\ 1" actually do anything (since it seems to be ignoring the duplex setting)?

---

### Post by COKEDUDE on 2011-01-10
> **kaway1337 said:**
> OK so reading up on NetworkManager documentation and there are two types of connections: system and user.

**I believe you can toggle a connection's type by going into "Network Connections" -> edit and toggling the "available to all users" checkbox at the bottom left. **

**I assume, enabling this checkbox changes the connection type to be system as when this is checked a file (named after the connection name in Network Connections) is created in [B]/etc/NetworkManager/system-connections/** and when it is unchecked it is removed.[/B]



This also happens to me. Whenever I uncheck available to all users it goes away. 

I also found out if you open a terminal and use this command there is more information. 

```
gconf-editor
```

It is located here: **/system/networking/connections**

---

### Post by COKEDUDE on 2011-01-10
The user settings will be stored here. 

```
/home/userdirectory/.gconf/system/networking/connections
```

[http://www.arachnoid.com/linux/NetworkManager/](http://www.arachnoid.com/linux/NetworkManager/)

The System settings will be stored here. 


```
/etc/NetworkManager
```
```
/etc/NetworkManager/system-connections
```

---

