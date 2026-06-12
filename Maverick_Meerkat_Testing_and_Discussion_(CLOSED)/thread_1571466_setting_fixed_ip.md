---
title: "setting fixed ip"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by devoncatt on 2010-09-09
It looks like the location to set a fixed IP  is not in /etc/network/interfaces. Where does network manager store a fixed ip not a dhcp address?
When I edit the file below the networking doesnot work

cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by cariboo on 2010-09-09
You now have to use Network-Manager to set static ip addresses:

[list=1]
[*] Right click The NM icon in the top panel and choose edit connections
[*] Highlight your device and click edit
[*] Click the IPv4 settings tab
[*] From the Method drop-down select Manual
[*] Enter your ip address, netmask and gateway, pressing enter after entering each address
[*] Enter your dns ip addresses
[*] Click Apply, and enter your password
[/list]

After entering your password, you see a notification of dis-connecting and connecting again.

---

### Post by seeker5528 on 2010-09-09
> **cariboo907 said:**
> You now have to use Network-Manager to set static ip addresses

I didn't see that in the list of changes, don't always read them all that carefully though. 

On all my systems network manager ignores interfaces that are defined in /etc/network/interfaces. The [bug with resolvconf](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/448095) isn't fixed yet and doesn't seem like the Ubuntu devs really seem to care about fixing it so if you want to specify dns servers in the interfaces file you either have to use the solution in the follow up to the bug report so the right things are done during boot up for resolvconf or you have to use some other mechanism later in the boot to do an ifdown/ifup of the desired interface.

The relevant text in the network-manager README.Debian file, if you want to make sure network manager is set up to ignore interfaces specified in /etc/network/interfaces, would be :

> Managed vs. Unmanaged mode and /etc/network/interfaces
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Devices listed in /etc/network/interfaces _will_ be managed by NetworkManager
unless the ifupdown system-config-setting is enabled and is setup to run
in "Unmanaged mode".

The config to select unmanaged/managed mode is in
/etc/NetworkManager/NetworkManager.conf:

[ifupdown]
managed=true/false

Unmanaged mode will make NetworkManager not touch any wired/wireless device
matching an interface name configured in /etc/network/interfaces.

Managed mode will make NetworkManager manage all devices and will make
NetworkManager honour all dhcp and static configurations for wired and
wireless devices.


After modifying /etc/NetworkManager/NetworkManager.conf _or_
/etc/network/interfaces you may want to tell NetworkManager about the changes
by running "service network-manager restart".

Later, Seeker

---

### Post by cariboo on 2010-09-09
I didn't read the changelog, this is just from personal experience. NM has been this way since at least karmic, if not earlier.

---

### Post by RTrev on 2010-09-24
I've got a problem in that network manager shows two connections.  One is called "ifupdown (eth0)" and the other, which I added, is called just "eth0".

I can't delete the first one, or edit it.  The second one I can edit, but control defaults to the first one on boot.

How can I get rid of the "ifupdown (eth0)" and have it use just "eth0"?

TIA,
Bob

---

