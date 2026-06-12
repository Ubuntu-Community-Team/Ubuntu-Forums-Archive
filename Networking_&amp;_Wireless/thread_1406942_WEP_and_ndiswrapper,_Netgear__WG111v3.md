---
title: "WEP and ndiswrapper, Netgear  WG111v3"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by damitch on 2010-02-14
Karmic, 32 bit; trying to get a Netgear WG111v3 usb stick running with ndiswrapper.  It works on a local unsecured site, but I'd really prefer to have it connect to the site from the cable modem, with WEP security.  That last seems to be the problem.

It tries to connect, seemingly, then keeps asking for the 128-bit pass key, and never succeeds with connection.  I've gotten other connections working with the same site and pass key, so I don't think the problem is the site or pass key value.

I had it working with the rtl8187 linux driver, but that seemed to cause random system freezes - which matches with what I've seen reported before (I think).  So, based on other people's posts, I removed the initially-installed ndiswrapper, downloaded and compiled the latest version of ndiswrapper, 1.55, and installed the other associated apps for it.  I blacklisted rtl8187.  That all seems to work.

Diagnostics:
```
david@goodwill-desktop:~$ sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:40:2b:27:f7:5b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:17 ioport:2000(size=256) memory:e8101000-e81010ff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:3f:de:66:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg111v3 driverversion=1.55+NETGEAR Inc.,05/11/2007,5.1 link=yes multicast=yes wireless=IEEE 802.11g

david@goodwill-desktop:~$ ndiswrapper -l
wg111v3 : driver installed
	device (0846:4260) present (alternate driver: rtl8187)

david@goodwill-desktop:~$ sudo dmesg | grep rtl8187
// (returned nothing)

david@goodwill-desktop:~$ sudo dmesg | grep ndiswrapper
[   23.913566] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   25.150559] ndiswrapper: driver wg111v3 (NETGEAR Inc.,05/11/2007,5.1084.0511.2007) loaded
[   32.877569] usbcore: registered new interface driver ndiswrapper
[   93.460954] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  162.187011] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  267.261367] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1075.519748] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1151.561483] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1461.888126] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1734.582316] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1813.452727] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1964.742548] ndiswrapper (iw_set_auth:1602): invalid cmd 12

david@goodwill-desktop:~$ 

```
Why does ndiswrapper say that rtl8187 is an 'alternate driver' -?  Near as I can tell, that driver shouldn't be anywhere.  Is it causing any kind of interference, do you suppose?  If so, how to get rid of it?

Do those listings for 'invalid cmd 12' mean anything much?

Any other ideas for how to get WEP working?  Many thanks.

---

### Post by chili555 on 2010-02-15
> Is it causing any kind of interference, do you suppose?I *do* suppose. Let's see if it is loaded with:```
lsmod | grep rtl81
```If it is loaded, and you believe you properly blacklisted it, let's check with:```
cat /etc/modprobe.d/blacklist.conf
```If it is loading, despite being blacklisted, then let's try to explicitly unload it and see if the behavior improves.```
sudo gedit /etc/rc.local
```Add a line:```
rmmod -f rtl8187
```Proofread, save and close gedit. Now reboot and run:```
ndiswrapper -l
lsmod | grep rtl81
dmesg | grep ndis

```Any improvement?

---

### Post by damitch on 2010-02-17
**chili555**, thanks for your response.  Might be a few more days before I have time to check this out.

---

### Post by damitch on 2010-02-20
Well, that was simple:

```
david@goodwill-desktop:~$ lsmod | grep rtl81
david@goodwill-desktop:~$
```

That is, the lsmod call returned nothing.  No such module is loaded.

As above, though, ndiswrapper -l still shows rtl8187 as an alternate driver.

---

### Post by chili555 on 2010-02-20
That's good, actually. Let's look at another possibility. Is the WEP key a 10 or 26 character key? Is it going in the drop-down for '40/128-bit HEX?'

You might also check in lsmod to see if any rtl8187 dependencies are loading:> $ modinfo rtl8187 | grep depends
depends:        mac80211,eeprom_93cx6,led-class,cfg80211I don't think any of these are required for ndiswrapper to run correctly, but it's easy to remove any of them temporarily and see the effect...better, worse or same.```
sudo rmmod -f <module name>
```

---

### Post by damitch on 2010-02-21
The WEP code is 10 characters long.  I've been typing in the straight characters into the dialog with the '40/128-bit HEX' option you said, no formatting or anything - otherwise, I've seen that the 'connect' button stays disabled.

As for the other:
```
david@goodwill-desktop:~$ modinfo rtl8187 | grep depends
depends:        mac80211,eeprom_93cx6,led-class,cfg80211
david@goodwill-desktop:~$ lsmod | grep mac80211
david@goodwill-desktop:~$ lsmod | grep mac
david@goodwill-desktop:~$ lsmod | grep eeprom
david@goodwill-desktop:~$ lsmod | grep led
david@goodwill-desktop:~$ lsmod | grep cfg
david@goodwill-desktop:~$
```
That is, all of these have returned nothing.

---

