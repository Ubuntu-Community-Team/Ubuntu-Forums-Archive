---
title: "Invalid MAC address detected"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by arcull on 2010-11-26
Hi there everyone. I've just installed a fresh copy of Maverick Meerkat 64bit and I wanted to setup static ip, but unfortunately I can't because of invalid mac address detection during each startup. The message looks like this```
dmesg |grep Mac
[    5.988576] forcedeth 0000:00:07.0: Invalid Mac address detected: 0b:68:66:ea:0f:00
[    5.988590] forcedeth 0000:00:07.0: Please complain to your hardware vendor. Switching to a random MAC
```. I remember having the same problem on suse distro and the solution I found at that time, was to change the /etc/udev/rules.d/70-persistent-net.rules and edit it to look like this```
#SUBSYSTEM=="net",ACTION=="add",DRIVERS=="?*",ATTR{address}#=="00:00:6c:ea:75:3e",ATTR{type}=="1",#KERNEL=="eth*",NAME="eth0"
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ID=="0000:00:07.0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
``` So I checked this file on my ubuntu distro, but the file is empty, it contain only some comments on how to use rules. I tried to add the line```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ID=="0000:00:07.0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
``` and rebooted pc, but still no change. So the question is, which file should I edit and how to make the MAC address and therefore also IP permanent. Thanks for any help you can provide.

---

### Post by wet-willy on 2010-11-26
I noticed in the dmsg quote that it switched to a random mac. Myself, I don't like to leave tracks, so I have macchanger installed and put these lines in /etc/rc.local:
```
macchanger -r eth0
macchanger -r eth1
```
Every time I reboot, a random mac is asigned to my ethernet and wireless interfaces.
You can also have it use a specific mac:
```
macchanger -m 11:22:33:44:55:66
```
Whatever mac address network manager likes.

SOMETHING TO THINK ABOUT:
Many people whom had network issues in Debian based systems solved their problems by installing wicd, then un-install network-manager, reboot and smile.

---

### Post by endotherm on 2010-11-26
the first 6 digits of the mac address are supposed to identify the manufacturer of the card, but several databases I've checked have no licensed vendor for "0b:68:66". per [RFC 1700]("http://www.iana.org/assignments/ethernet-numbers"), "0b" should be associated with a multicast protocol address rather than a station address. 

so thats probably why some drivers across vendors complain about the mac on that card. just out of curiosity, does if have any brand markings?

anyway, i would use mac changer to set a new valid mac, masquarading as a popular nic manufacturer like intel or realtek.

---

### Post by arcull on 2010-11-26
Thanks for answers guys. It is an onborad nvidia NIC```
lspci -nn |grep Eth
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
``` Does macchanger change MAC permanently or do I have to run it at every startup? Thanks again for your help.

---

