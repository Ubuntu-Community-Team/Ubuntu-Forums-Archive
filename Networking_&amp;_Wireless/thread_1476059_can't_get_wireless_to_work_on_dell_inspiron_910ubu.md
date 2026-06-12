---
title: "can't get wireless to work on dell inspiron 910/ubuntu 8.04/broadcom bcm4312"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by quitequieter on 2010-05-07
this machine used to connect to a wireless network at another location automatically and without fuss, and by entering the essid and password manually with "network" under administration i was able to get it to connect briefly to a network at a different location. edit: the issue right now is that i can connect to nonsecured networks but not the network i want to (which has a wep passphrase). i just don't know where to go to set it up right.

from the howto sticky:

1. model: dell inspiron 910

2. lspci: broadcom corporation bcm4312 802.11b/g (rev 01)

the lsusb output doesn't seem useful but here it is:

bus device 005: ID 0000:0000
bus device 004: ID 0000:0000
bus device 003: ID 0000:0000
bus device 002: ID 0000:0000
bus device 001: ID 0000:0000

3. ifconfig output is enormous and i have no way of copy/pasting it. if it's necessary i will input it manually and post it. the short of it is eth0 says Link encap: Ethernet, eth1 says Link encap: Ethernet, and lo says Link encap: Local Loopback. i don't know what any of this means.

iwconfig output:

lo         no wireless extensions
eth0     no wireless extensions
eth1     IEEE 802.11 Nickname: " "
           Access Point: Not-Associated
           Link Quality:1  Signal level:175  Noise level:167
           Rx invalid nwid:0  invalid crypt:508  invalid misc:0

4. lsmod output is also enormous. the only stuff that i can think might be relevant (and really i have no clue) is 

wl (size is 1487188, used by "0")
ieee80211_crypt_tkip (size is 11520, used by "0")
ieee80211_crypt (size is 6912, used by "2 wl, ieee80211_crypt_tkip)

5. dmesg output is terrifyingly long and i don't know what is relevant or what any of it means. the relevant looking stuff says things like

wl: module license 'MIXED/Proprietary" taints kernel.
eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.79.10
eth1: no IPv6 routers present
r8169:eth0:link down
ADDRCONF (NETDEV_UP): eth0: link is not ready

and a lot of that repeats quite a bit.

6. sudo lshw -C network output:

sudo: lshw: command not found.

7. iwlist scan output:

lo       Interface doesn't support scanning.

eth0:  Interface doesn't support scanning.

eth1:  Interface doesn't support scanning.

8. lsb_release -d output:

Ubuntu 8.04.1

9. uname -mr output:

2.6.24-22-lpia i686

10. i did the network restart but i don't know what it did. there was no output. i still can't connect.

---

