---
title: "Intel 3945ABG [Golan] Wireless randomly disconnects"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by Jerrac on 2009-02-11
Strange problem. For the past few weeks my wireless will randomly disconnect. I've checked my router, and it is fine. My brother doesn't disconnect at the same time as I do.

To further complicate matters, I sometimes have to restart to get it working again. Sometimes I can get it work by just right clicking and disabling and enabling networking. So far /etc/init.d/networking restart has not helped at all.

I have not noticed any kind of pattern...

Network Card: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Ubuntu 8.10.

Here is the last few lines from dmesg after the last disconnect.
> [   45.536384] NET: Registered protocol family 10
[   45.537425] lo: Disabled Privacy Extensions
[   48.708918] Bluetooth: Core ver 2.13
[   48.709024] NET: Registered protocol family 31
[   48.709031] Bluetooth: HCI device and connection manager initialized
[   48.709037] Bluetooth: HCI socket layer initialized
[   48.731407] Bluetooth: L2CAP ver 2.11
[   48.731418] Bluetooth: L2CAP socket layer initialized
[   48.770828] Bluetooth: SCO (Voice Link) ver 0.6
[   48.770841] Bluetooth: SCO socket layer initialized
[   48.924514] Bluetooth: RFCOMM socket layer initialized
[   48.924868] Bluetooth: RFCOMM TTY layer initialized
[   48.924878] Bluetooth: RFCOMM ver 1.10
[   48.948573] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   48.948582] Bluetooth: BNEP filters: protocol multicast
[   49.049522] Bridge firewalling registered
[   52.374973] [drm] Initialized drm 1.1.0 20060810
[   52.418979] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   52.418996] pci 0000:00:02.0: setting latency timer to 64
[   52.421374] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   53.239039] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   53.240192] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   53.240344] iwl3945 0000:06:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   53.240615] firmware: requesting iwlwifi-3945-1.ucode
[   53.397821] Registered led device: iwl-phy0:radio
[   53.398240] Registered led device: iwl-phy0:assoc
[   53.398569] Registered led device: iwl-phy0:RX
[   53.398881] Registered led device: iwl-phy0:TX
[   53.406436] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.523026] NET: Registered protocol family 17
[   56.251788] wlan0: authenticate with AP 00:1b:11:71:85:ca
[   56.448133] wlan0: authenticate with AP 00:1b:11:71:85:ca
[   56.648053] wlan0: authenticate with AP 00:1b:11:71:85:ca
[   56.848054] wlan0: authentication with AP 00:1b:11:71:85:ca timed out
[  100.247206] CPU0 attaching NULL sched-domain.
[  100.247222] CPU1 attaching NULL sched-domain.
[  100.248741] CPU0 attaching sched-domain:
[  100.248751]  domain 0: span 0-1 level MC
[  100.248756]   groups: 0 1
[  100.248768] CPU1 attaching sched-domain:
[  100.248773]  domain 0: span 0-1 level MC
[  100.248779]   groups: 1 0
[  111.831182] wlan0: authenticate with AP 00:1b:11:71:85:ca
[  111.834395] wlan0: authenticate with AP 00:19:5b:d6:9f:e1
[  111.836829] wlan0: authenticate with AP 00:19:5b:d6:9f:e1
[  111.836849] wlan0: authenticated
[  111.836855] wlan0: associate with AP 00:19:5b:d6:9f:e1
[  111.843140] wlan0: RX AssocResp from 00:19:5b:d6:9f:e1 (capab=0x431 status=0 aid=6)
[  111.843146] wlan0: associated
[  111.843888] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  122.292016] wlan0: no IPv6 routers present
[ 1164.999581] iwl3945: Radio Frequency Kill Switch is On:
[ 1164.999586] Kill switch must be turned off for wireless networking to work.
[ 1165.761819] Registered led device: iwl-phy0:radio
[ 1165.761901] Registered led device: iwl-phy0:assoc
[ 1165.761934] Registered led device: iwl-phy0:RX
[ 1165.761966] Registered led device: iwl-phy0:TX
[ 1165.762890] wlan0: authenticate with AP 00:19:5b:d6:9f:e1
[ 1165.763939] wlan0: authenticated
[ 1165.763947] wlan0: associate with AP 00:19:5b:d6:9f:e1
[ 1165.765767] wlan0: RX ReassocResp from 00:19:5b:d6:9f:e1 (capab=0x431 status=0 aid=6)
[ 1165.765774] wlan0: associated
[ 1167.216147] iwl3945: Radio Frequency Kill Switch is On:
[ 1167.216152] Kill switch must be turned off for wireless networking to work.
[ 1170.781020] wlan0: authenticate with AP 00:19:5b:d6:9f:e1
[ 1170.804281] wlan0: disassociating by local choice (reason=3)
[ 1170.866924] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 1170.870171] iwl3945: MAC is in deep sleep!
[ 1170.916786] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 1170.920756] iwl3945: MAC is in deep sleep!
[ 1170.976612] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 1170.980607] iwl3945: MAC is in deep sleep!
[ 1171.140351] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 1171.156957] iwl3945 0000:06:00.0: PCI INT A disabled


Here are the lines from after I right clicked on the icon and disabled networking, and then enabled it.
> [ 1288.678169] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1288.682113] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1288.682285] iwl3945 0000:06:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 1288.725889] Registered led device: iwl-phy0:radio
[ 1288.726345] Registered led device: iwl-phy0:assoc
[ 1288.726707] Registered led device: iwl-phy0:RX
[ 1288.727019] Registered led device: iwl-phy0:TX
[ 1288.727688] wlan0: authenticate with AP 00:1b:11:71:85:ca
[ 1288.734265] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1288.739154] wlan0: authenticate with AP 00:1b:11:71:85:ca
[ 1288.936054] wlan0: authenticate with AP 00:1b:11:71:85:ca
[ 1289.136055] wlan0: authenticate with AP 00:1b:11:71:85:ca
[ 1289.336052] wlan0: authentication with AP 00:1b:11:71:85:ca timed out
[ 1301.505686] wlan0: authenticate with AP 00:19:5b:d6:9f:e1
[ 1301.508369] wlan0: authenticated
[ 1301.508379] wlan0: associate with AP 00:19:5b:d6:9f:e1
[ 1301.511817] wlan0: RX AssocResp from 00:19:5b:d6:9f:e1 (capab=0x431 status=0 aid=11)
[ 1301.511826] wlan0: associated
[ 1301.512917] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1312.284029] wlan0: no IPv6 routers present


---

### Post by pdtpatrick on 2009-02-11
<quote>Kill switch must be turned off for wireless networking to work.</quote>

hmmm -- wonder whats the deal with this.

---

### Post by pdtpatrick on 2009-02-11
> [ 1167.216152] Kill switch must be turned off for wireless networking to work.
[ 1170.781020] wlan0: authenticate with AP 00:19:5b:d6:9f:e1
[ 1170.804281] wlan0: disassociating by local choice (reason=3)
[ 1170.866924] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[ 1170.870171] iwl3945: MAC is in deep sleep!

strange that it disassociated .. lol maybe your brother deauths you from the AP? :) 

but anyway check the router and see if its accepting your mac.. do you have mac filtering on? Im guessing now  since you were allowed in before. 

btw what version of network manager do you have? 

sudo apt-cache show network-manager

---

### Post by Jerrac on 2009-02-11
The router does accept my MAC since I am on it right now...

apt-cache show:
> Package: network-manager
Priority: optional
Section: net
Installed-Size: 1940
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Riccardo Setti <giskard@debian.org>
Architecture: i386
Version: 0.7~~svn20081018t105859-0ubuntu1.8.10.1
Replaces: network-manager-pptp (<< 0.7~~)
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.74), libglib2.0-0 (>= 2.16.0), libhal1 (>= 0.5.8.1), libnl1, libnm-glib0 (>= 0.7~~svn20080908), libnm-util0 (>= 0.7~~svn20080908), libnspr4-0d (>= 1.8.0.10), libnss3-1d (>= 3.12.0~1.9b1), libpolkit-dbus2 (>= 0.7), libpolkit2 (>= 0.7), libuuid1 (>= 1.05), iproute, iputils-arping, lsb-base (>= 2.0-6), wpasupplicant (>= 0.6.1~), dbus (>= 0.60), hal (>= 0.5.7.1), update-notifier-common
Recommends: network-manager-gnome | network-manager-kde
Conflicts: network-manager-pptp (<< 0.7~~)
Filename: pool/main/n/network-manager/network-manager_0.7~~svn20081018t105859-0ubuntu1.8.10.1_i386.deb
Size: 267018
MD5sum: 8e4cf7afe6b120e6f2abf0e8bf7e493d
SHA1: 6ec56e7d47be96f759e18c90702acf09e8b98738
SHA256: 87bbd45904915e7c5d3bdbbfffe91e4958a6a10a9b58e05f571e9db7e48afbc1
Description: network management framework daemon
 NetworkManager attempts to keep an active network connection available at all
 times. It is intended only for the desktop use-case, and is not intended for
 usage on servers. The point of NetworkManager is to make networking
 configuration and setup as painless and automatic as possible.  If using DHCP,
 NetworkManager is _intended_ to replace default routes, obtain IP addresses
 from a DHCP server, and change nameservers whenever it sees fit.
 .
 This package provides the userspace daemons.
 .
  Homepage: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, edubuntu-desktop-kde, xubuntu-desktop, mobile-mid, mobile-mobile

Package: network-manager
Priority: optional
Section: net
Installed-Size: 1936
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Riccardo Setti <giskard@debian.org>
Architecture: i386
Version: 0.7~~svn20081018t105859-0ubuntu1
Replaces: network-manager-pptp (<< 0.7~~)
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.74), libglib2.0-0 (>= 2.16.0), libhal1 (>= 0.5.8.1), libnl1, libnm-glib0 (>= 0.7~~svn20080908), libnm-util0 (>= 0.7~~svn20080908), libnspr4-0d (>= 1.8.0.10), libnss3-1d (>= 3.12.0~1.9b1), libpolkit-dbus2 (>= 0.7), libpolkit2 (>= 0.7), libuuid1 (>= 1.05), iproute, iputils-arping, lsb-base (>= 2.0-6), wpasupplicant (>= 0.6.1~), dbus (>= 0.60), hal (>= 0.5.7.1), update-notifier-common
Recommends: network-manager-gnome | network-manager-kde
Conflicts: network-manager-pptp (<< 0.7~~)
Filename: pool/main/n/network-manager/network-manager_0.7~~svn20081018t105859-0ubuntu1_i386.deb
Size: 266464
MD5sum: a579146280af86233788fab84bc27dd9
SHA1: 40b294347bf2e1d416cea9aaf540ae57c3bf2d4d
SHA256: 857c2f3a00db1e22b067a9a2411d9cf95272f641f36f0a97513462e999b1dae0
Description: network management framework daemon
 NetworkManager attempts to keep an active network connection available at all
 times. It is intended only for the desktop use-case, and is not intended for
 usage on servers. The point of NetworkManager is to make networking
 configuration and setup as painless and automatic as possible.  If using DHCP,
 NetworkManager is _intended_ to replace default routes, obtain IP addresses
 from a DHCP server, and change nameservers whenever it sees fit.
 .
 This package provides the userspace daemons.
 .
  Homepage: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, edubuntu-desktop-kde, xubuntu-desktop, mobile-mid, mobile-mobile


Another reason I know it isn't my router is that when it disconnects, it won't even show the other networks around me. I can usually see 5 or more networks.

---

### Post by mykrob on 2009-02-11
I had that same card in my laptop and it would disconnect randomly as well. Nothing i did made it work right.. I ended up buying on of these for $23 USD

[http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless-802.11b/g---54Mbps/c42_73/p149/GIGABYTE-GN-WS50G--802.11-b/g-Atheros-AR5007-chipset-minicard-mPCI-express-card/product_info.html](http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless-802.11b/g---54Mbps/c42_73/p149/GIGABYTE-GN-WS50G--802.11-b/g-Atheros-AR5007-chipset-minicard-mPCI-express-card/product_info.html)

And never looked back. Using it right now, matter of fact.

---

### Post by MarkAfterDark on 2009-02-16
This is something new.  My 3945 has been working fine (more like awesome) for a month (after figuring how to remedy the WEP problem).

I'm in a different hotel almost every day (LOTS of travel with my job).  Just about all hotels run open access routers.  I haven't had a problem until a couple of days ago.
Here's my dmesg output> [ 5099.644824] wlan0: associate with AP 00:11:21:e5:a1:10
[ 5099.646406] wlan0: RX ReassocResp from 00:11:21:e5:a1:10 (capab=0x421 status=0 aid=176)
[ 5099.646416] wlan0: associated
[ 5103.271616] wlan0: deauthenticated
[ 5104.268039] wlan0: authenticate with AP 00:11:21:e5:a1:10
[ 5104.269481] wlan0: authenticated
[ 5104.269493] wlan0: associate with AP 00:11:21:e5:a1:10
[ 5104.271728] wlan0: RX ReassocResp from 00:11:21:e5:a1:10 (capab=0x421 status=0 aid=177)
[ 5104.271739] wlan0: associated
[ 5107.904074] wlan0: deauthenticated
[ 5108.904044] wlan0: authenticate with AP 00:11:21:e5:a1:10
[ 5108.905452] wlan0: authenticated
[ 5108.905465] wlan0: associate with AP 00:11:21:e5:a1:10
[ 5108.907102] wlan0: RX ReassocResp from 00:11:21:e5:a1:10 (capab=0x421 status=0 aid=178)
[ 5108.907114] wlan0: associated
[ 5112.520165] wlan0: deauthenticated
[ 5113.524063] wlan0: authenticate with AP 00:11:21:e5:a1:10
[ 5113.525505] wlan0: authenticated
[ 5113.525512] wlan0: associate with AP 00:11:21:e5:a1:10
[ 5113.527099] wlan0: RX ReassocResp from 00:11:21:e5:a1:10 (capab=0x421 status=0 aid=179)
[ 5113.527105] wlan0: associated
[ 5117.162442] wlan0: deauthenticated
[ 5118.160092] wlan0: authenticate with AP 00:11:21:e5:a1:10
[ 5118.161449] wlan0: authenticated
[ 5118.161453] wlan0: associate with AP 00:11:21:e5:a1:10
[ 5118.163031] wlan0: RX ReassocResp from 00:11:21:e5:a1:10 (capab=0x421 status=0 aid=180)
[ 5118.163037] wlan0: associated


This is how it is after only being connected for a few seconds.  I reconnect and it'll work for a few seconds and then it happens again.  I don't think I updated anything in the past few days.  

Why it doing this?  Anybody?  I gots cookies for whoever finds the solution!!!

---

### Post by MarkAfterDark on 2009-02-17
Bump.

---

