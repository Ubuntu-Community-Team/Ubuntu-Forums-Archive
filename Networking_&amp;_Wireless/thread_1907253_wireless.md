---
title: "wireless"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by ubunewtu on 2012-01-11
running ubuntu 11.10 on a dell inspiron 6400 i cant get the wireless card to work used nds wrapper and still no luck i seem to remember alwas running a script in older ubuntu versions with the live cd that alwas seemed to work is there such a script i could run in terminal for 11.10? is there a better version of ubuntu for this laptop that will detect the wireless?

---

### Post by UltimateCat on 2012-01-11
I had the same trouble.
I found that when I installed the driver for my NIC it made the difference.
I also installed Ndiswrapper as you did.
Try google or try the website of the manufacturer that made your internal card.
Hope this helps
Best Regards

---

### Post by carl4926 on 2012-01-11
Post the result of

```
lspci -nnk
```

---

### Post by prshah on 2012-01-11
> **ubunewtu said:**
> running ubuntu 11.10 on a dell inspiron 6400 i cant get the wireless card to work

The stock Dell 6400 comes with an Intel Pro wireless card, which should be supported out of the box in Ubuntu; you shouldn't need to install any "drivers".

Please check that the wireless card is enabled in the BIOS. Please also check that the wireless is not being disabled by it's "kill switch" (Fn+F2 in most Dells).

If you are unsure about how to do these, please post back the information from the following troubleshooting commands. Run the below commands in a terminal (Applications-Accessories-Terminal) and copy/paste the output here```
lsusb
lspci | grep -E -i wireless\|network
lshw -C network
tail -f /var/log/syslog
# Press Fn+F2 on the keyboard, some output should appear
# copy and paste the new output to this thread.

```

The above information will give us more information about your specifications.

---

### Post by ubunewtu on 2012-01-12
it was indeed the kill switch

---

### Post by beyazkopek on 2012-07-10
Been using Ubuntu since 2008, first time I've needed to post a question.

The output from above:
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jeff@jeff-10dot10:~$ lspci | grep -E -i wireless\|network
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
jeff@jeff-10dot10:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:d0:4c:fd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.102 latency=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
jeff@jeff-10dot10:~$ tail -f /var/log/syslog
Jul 10 13:28:54 jeff-10dot10 kernel: [ 3670.075948] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:28:54 jeff-10dot10 kernel: [ 3670.075971] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:28:54 jeff-10dot10 kernel: [ 3670.855922] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:28:54 jeff-10dot10 kernel: [ 3670.855938] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:30:58 jeff-10dot10 kernel: [ 3794.153834] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:30:58 jeff-10dot10 kernel: [ 3794.153851] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:30:59 jeff-10dot10 NetworkManager[660]: <info> WiFi now enabled by radio killswitch
Jul 10 13:30:59 jeff-10dot10 kernel: [ 3795.064065] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:30:59 jeff-10dot10 kernel: [ 3795.064085] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:31:00 jeff-10dot10 NetworkManager[660]: <info> WiFi now disabled by radio killswitch
Jul 10 13:31:47 jeff-10dot10 kernel: [ 3843.301012] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:31:47 jeff-10dot10 kernel: [ 3843.301037] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:31:49 jeff-10dot10 NetworkManager[660]: <info> WiFi now enabled by radio killswitch
Jul 10 13:32:10 jeff-10dot10 kernel: [ 3866.723233] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:32:10 jeff-10dot10 kernel: [ 3866.723258] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:32:12 jeff-10dot10 NetworkManager[660]: <info> WiFi now disabled by radio killswitch
^C

so yes, it is the killswitch, but I can't use it?

ran all above as sudo with slightly different results.

jeff@jeff-10dot10:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:d0:4c:fd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.102 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
jeff@jeff-10dot10:~$ sudo tail -f /var/log/syslog
Jul 10 13:30:59 jeff-10dot10 kernel: [ 3795.064065] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:30:59 jeff-10dot10 kernel: [ 3795.064085] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:31:00 jeff-10dot10 NetworkManager[660]: <info> WiFi now disabled by radio killswitch
Jul 10 13:31:47 jeff-10dot10 kernel: [ 3843.301012] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:31:47 jeff-10dot10 kernel: [ 3843.301037] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:31:49 jeff-10dot10 NetworkManager[660]: <info> WiFi now enabled by radio killswitch
Jul 10 13:32:10 jeff-10dot10 kernel: [ 3866.723233] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:32:10 jeff-10dot10 kernel: [ 3866.723258] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:32:12 jeff-10dot10 NetworkManager[660]: <info> WiFi now disabled by radio killswitch
Jul 10 13:41:11 jeff-10dot10 sudo: pam_ecryptfs: pam_sm_authenticate: /home/jeff is already mounted
Jul 10 13:42:23 jeff-10dot10 kernel: [ 4479.611587] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:42:23 jeff-10dot10 kernel: [ 4479.611612] keyboard: can't emulate rawmode for keycode 240
Jul 10 13:42:25 jeff-10dot10 NetworkManager[660]: <info> WiFi now enabled by radio killswitch
^Cjeff@jeff-10dot10:~$

---

### Post by computer13137 on 2012-07-10
A fantastic tool we found at work for determining issues with these "wireless switches" is rfkill.

"rfkill list" will show you if the wireless is hard blocked or soft blocked.

We had an issue with some of our Lenovo netbooks where the wireless switch was changing a setting that the Linux drivers didn't know how to change back (it only worked correctly under Windows). Disabling the wireless resulted in us having to pull the CMOS battery.  Our somewhat crude fix was to open all 300 of the netbooks and insert a toothpick into the switches so they couldn't be flipped off. (since we're a school, the kids figured out that they could flip off the switch and waste class time, we needed an immediate fix.)

---

### Post by beyazkopek on 2012-07-10
thanks,
reports no to both soft or hard blocked?

---

### Post by beyazkopek on 2012-07-10
broke the battery holder while trying to force a reset, time to recycle it.

---

