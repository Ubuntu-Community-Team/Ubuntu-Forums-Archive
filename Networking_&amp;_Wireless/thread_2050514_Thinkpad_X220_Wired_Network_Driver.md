---
title: "Thinkpad X220 Wired Network Driver"
date: 2012-08-31
forum: Networking &amp; Wireless
---

### Post by win310 on 2012-08-31
I am using Lenovo Thinkpad X220,then i find the Wired Network does not work,who can provide the driver?
Thank you!

---

### Post by win310 on 2012-09-02
Anyone can help me?

---

### Post by chili555 on 2012-09-02
What card is it? Please post:```
lspci -nn | grep 0200
```

---

### Post by exancillatus on 2013-04-30
[EDIT]
I didn't see this post was old. I'm having the problem since I installed Ubuntu 13.04. Wired network and sometimes wifi don't get DHCP.



I have the same problem, here it the info you asked :

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)

---

### Post by chili555 on 2013-04-30
> **exancillatus said:**
> [EDIT]
I didn't see this post was old. I'm having the problem since I installed Ubuntu 13.04. Wired network and sometimes wifi don't get DHCP.



I have the same problem, here it the info you asked :

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)I will assume you want to work on the wired first. Please run and post:```
dmesg | grep -e eth0 -e e100
cat /etc/network/interfaces
nm-tool
```Thanks.

---

### Post by exancillatus on 2013-04-30
Here is what you asked. The RJ45 cable is not plugged in at the moment. Thanks for your help, I really appreciate it.

dmesg | grep -e eth0 -e e100

> [    0.000000] ACPI: SSDT 00000000dafe1000 00A27 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.815963] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    0.815965] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    0.845568] e1000e 0000:00:19.0: setting latency timer to 64
[    0.845659] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.845695] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.043324] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:c2:64:ff
[    1.043328] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.043381] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[    8.105450] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.154180] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.257849] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.258055] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.258428] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

cat /etc/network/interfaces

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

nm-tool

> NetworkManager Tool

State: connected (global)

- Device: wlan0  [FJH] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        XX:XX:XX:XX:0E:38

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ZZZZZZ:Infra, ZZ:ZZ:ZZ:ZZ:69:94, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA
    *XXX:            Infra, XX:XX:XX:XX:9E:F3, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2

  IPv4 Settings:
    Address:         172.16.24.126
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.24.254

    DNS:             91.121.161.184
    DNS:             188.165.197.144


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        XX:XX:XX:XX:64:FF

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



---

### Post by chili555 on 2013-04-30
> The RJ45 cable is not plugged in at the moment.If we're going to troubleshoot the wired ethernet, I think the cable ought to be plugged in so we can see the ethernet fail to get an address. Please do so and re-run.

---

### Post by exancillatus on 2013-04-30
OK, my bad, here are the info with the RJ45 plugged in :

dmesg | grep -e eth0 -e e100
> [    0.000000] ACPI: SSDT 00000000dafe1000 00A27 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.815963] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    0.815965] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    0.845568] e1000e 0000:00:19.0: setting latency timer to 64
[    0.845659] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.845695] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.043324] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:c2:64:ff
[    1.043328] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.043381] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[    8.105450] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.154180] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.257849] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.258055] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.258428] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7020.093939] e1000e 0000:00:19.0: System wakeup enabled by ACPI
[ 7021.449911] e1000e 0000:00:19.0: System wakeup disabled by ACPI
[ 7021.449994] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[ 7022.311758] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[ 7022.415399] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[ 7022.415612] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7493.123862] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 7493.123917] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

cat /etc/network/interfaces
> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

nm-tool

> NetworkManager Tool

State: connected (global)

- Device: wlan0  [FJH] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        10:0B:A9:A2:0E:38

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ZZZZZ:Infra, 4E:69:84:FE:69:94, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    *FJH:            Infra, 58:98:35:A1:9E:F3, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2

  IPv4 Settings:
    Address:         172.16.24.126
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.24.254

    DNS:             91.121.161.184
    DNS:             188.165.197.144


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             disconnected
  Default:           no
  HW Address:        F0:DE:F1:C2:64:FF

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

---

### Post by chili555 on 2013-04-30
Looks pretty solid to me. It appears that if the wireless were disconnected,it would connect easily. > [ 7493.123862] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 7493.123917] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
<snip>
Capabilities:
Carrier Detect: yes
Speed: 1000 Mb/s

Wired Properties
Carrier: on Can you please turn off the wireless switch and see if it connects? If not, please post:```
dmesg | grep -e eth0 -e e100
```We'll look for entries later than those timestamped above:> [ [COLOR="#FF0000"]7493.123917[/COLOR]] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready We're looking for some reason or fault preventing connection to be noted in the message log.

---

### Post by exancillatus on 2013-04-30
I turned off wifi from the switch on the left side of the x220 and plugged the RJ45 in, no dhcp acquired.

Here is the resut of the command :

dmesg | grep -e eth0 -e e100
> [    0.000000] ACPI: SSDT 00000000dafe1000 00A27 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.815963] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    0.815965] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    0.845568] e1000e 0000:00:19.0: setting latency timer to 64
[    0.845659] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.845695] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.043324] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:c2:64:ff
[    1.043328] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.043381] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[    8.105450] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.154180] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.257849] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.258055] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.258428] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7020.093939] e1000e 0000:00:19.0: System wakeup enabled by ACPI
[ 7021.449911] e1000e 0000:00:19.0: System wakeup disabled by ACPI
[ 7021.449994] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[ 7022.311758] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[ 7022.415399] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[ 7022.415612] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7493.123862] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 7493.123917] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 7724.871982] e1000e: eth0 NIC Link is Down
[ 8826.983457] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

Again, thanks for your help.

---

### Post by bonsty on 2013-04-30
Hi, I am having the precise same problem - please let me know if there is anything that I can do to help solve it!

---

### Post by bonsty on 2013-05-01
> **bonsty said:**
> Hi, I am having the precise same problem - please let me know if there is anything that I can do to help solve it!

Doing ```
dmesg | grep -e eth0 -e e100
```

I get the following:

```
[    0.000000] ACPI: SSDT 00000000dafe1000 00A69 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)[    2.053853] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    2.053856] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    2.053904] e1000e 0000:00:19.0: setting latency timer to 64
[    2.053973] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.054009] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    2.239729] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:72:77:ed
[    2.239733] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.239788] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[   20.551837] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.114496] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   22.218352] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   22.218550] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.218874] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1093.727974] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 1093.843511] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1094.694003] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 1094.795352] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 1094.796159] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1094.796934] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2795.460188] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 2801.513275] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-NAPI
[ 2801.513281] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[ 2801.513343] e1000e 0000:00:19.0: setting latency timer to 64
[ 2801.513472] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[ 2801.513525] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 2801.693587] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:72:77:ed
[ 2801.693592] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[ 2801.693653] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[ 2801.839672] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 2801.941274] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 2801.941615] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2801.942431] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready



```

Thank you for any help that you may be able to provide!

---

### Post by chili555 on 2013-05-01
In both cases, the message logs look pretty solid. Let's try to find out what Network Manager is or isn't doing at this time. With any wireless switched off and the ethernet cable attached, try to connect and then run and post:```
cat /var/log/syslog | grep etwork | tail -n20
```Thanks.

---

### Post by netman3d on 2013-05-01
on my Thinkpad X230 i had the same problem... after the release update from 12.10 to 13.04
Small solution is to use the driver for the e1000e Version 2.3.2 from [http://sourceforge.net/projects/e1000/files/?source=navbar](http://sourceforge.net/projects/e1000/files/?source=navbar)

---

### Post by bonsty on 2013-05-01
When doing
```

cat /var/log/syslog | grep etwork | tail -n20

```

I get:

```
May  1 17:04:48 mert2760 NetworkManager[4479]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May  1 17:04:48 mert2760 NetworkManager[4479]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  1 17:04:48 mert2760 NetworkManager[4479]: <info> Policy set 'eduroam' (wlan0) as default for IPv4 routing and DNS.
May  1 17:04:48 mert2760 NetworkManager[4479]: <info> Writing DNS information to /sbin/resolvconf
May  1 17:04:48 mert2760 avahi: Avahi disabled itself. If you want to use Avahi in this network, please
May  1 17:04:48 mert2760 NetworkManager[4479]: <info> (wlan0): roamed from BSSID 3C:E5:A6:A0:41:12 (eduroam) to 3C:E5:A6:A0:5F:12 (eduroam)
May  1 17:04:48 mert2760 NetworkManager[4479]: <info> Activation (wlan0) successful, device activated.
May  1 17:05:05 mert2760 NetworkManager[4479]: <info> (wlan0): IP6 addrconf timed out or failed.
May  1 17:05:05 mert2760 NetworkManager[4479]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  1 17:05:05 mert2760 NetworkManager[4479]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  1 17:05:05 mert2760 NetworkManager[4479]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  1 17:06:50 mert2760 NetworkManager[4479]: <info> WiFi now disabled by radio killswitch
May  1 17:06:50 mert2760 NetworkManager[4479]: <info> (wlan0): device state change: activated -> unavailable (reason 'none') [100 20 0]
May  1 17:06:50 mert2760 NetworkManager[4479]: <info> (wlan0): deactivating device (reason 'none') [0]
May  1 17:06:50 mert2760 acvpnagent[1615]: A network interface has gone down.
May  1 17:06:50 mert2760 NetworkManager[4479]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 8879
May  1 17:06:50 mert2760 NetworkManager[4479]: <warn> DNS: plugin dnsmasq update failed
May  1 17:06:50 mert2760 NetworkManager[4479]: <info> Removing DNS information from /sbin/resolvconf
May  1 17:06:50 mert2760 avahi-daemon[9173]: Network interface enumeration completed.
May  1 17:06:50 mert2760 NetworkManager[4479]: <warn> error monitoring device for netlink events: No buffer space available

```

With regards to using the new drivers for the hardware, I tried that a few hours ago and it didn't do anything...

Oh, and thank you for your help chili!

I should probably add that the ethernet lights flash in the usual way as if there were a working connection.

---

### Post by adharris on 2013-05-01
I'm having what looks to be the same issue since upgrading to 13.04, and my outputs to all commands so far match bonsty's.  One thing i'll note that is if I reboot with the cable attached then LAN works.  However, detaching and reattaching the cable no longer will connect to LAN.

---

### Post by chili555 on 2013-05-01
> NetworkManager[4479]: <warn> error monitoring device for netlink events: No buffer space availableWell, this is a new development! Do all of you also have this? It may not be a driver problem, but an NM problem.

Googling....> With regards to using the new drivers for the hardware, I tried that a few hours ago and it didn't do anything...
Did it compile correctly? No errors or scary warnings?

Edit: I see this: [https://bbs.archlinux.org/viewtopic.php?id=146261](https://bbs.archlinux.org/viewtopic.php?id=146261)> It works if you set IPv6 to "link local" (after a few seconds).While it seems unlikely to me, bontsy, would you please try it and report back? Also try IPv6 as Ignore. In both cases, you'll need to restart NM:```
sudo service network-manager restart
```

---

### Post by bonsty on 2013-05-01
No, no errors, it all went according to plan - I'm not particularly versed in linux so I followed the instructions from intel on how to do this...

---

### Post by chili555 on 2013-05-01
> **bonsty said:**
> No, no errors, it all went according to plan - I'm not particularly versed in linux so I followed the instructions from intel on how to do this...And now you have a different version number here?```
modinfo e1000e
```My un-modified version in 13.04 is:> $ modinfo e1000e
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
[COLOR="#FF0000"]version:        2.1.4-k[/COLOR]
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     2631BAE58994F6AA09DC82F
Any changes from the link-local or ignore changes in Network Manager?

---

### Post by netman3d on 2013-05-01
```
$ modinfo e1000e
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/e1000e.ko
version:        2.3.2-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     281F7CB2F8EDEC01E32F57F
```

---

### Post by chili555 on 2013-05-01
> **netman3d said:**
> ```
$ modinfo e1000e
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/e1000e.ko
version:        2.3.2-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     281F7CB2F8EDEC01E32F57F
```Exactly. I was very interested in bontsy's result since he asserts, "... I'm not particularly versed in linux..." If he gets 2.3.2-NAPI, then we're confident he succeeded.

My meager money is bet on Network Mangler as the issue.

---

### Post by bonsty on 2013-05-02
That's what I get:

```


filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        2.3.2-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     281F7CB2F8EDEC01E32F57F

```

I haven't had any network manager crash reports or errors come up on screen.

Thanks for your help!

---

### Post by chili555 on 2013-05-02
> version:        2.3.2-NAPIExcellent.

@bontsy--

Would you please right-click the Network Manager icon, select Edit Connections, select Wired, and Edit Coonnections. Select the IPv6 tab and select Link Local. Save and close. Can you connect?

If not, set IPv6 to Ignore. Save and close. Can you connect now? 

Please see attached.

---

### Post by bonsty on 2013-05-03
Just tried it (both ignore and link local), still no luck... I also installed some ubuntu system updates which also did not correct the problem...

Please advise.

---

### Post by chili555 on 2013-05-03
Greater love for the forum hath no other than he disconnect his wireless, compile e1000e as above (no errors, yay!!) and walk over to the router, hook up the ethernet cable and try every method in his meager bag of tricks to coax his e1000e device to connect, including *REMOVING* Network Manager and reverting to manual methods.

I couldn't.

I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652)  Please run:```
lspci -nn | grep 0200
```Find the bus number for your ethernet device. Here is an example from my machine:> [COLOR="#FF0000"]00:19.0[/COLOR] Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea]Now check:```
cat /sys/devices/pci0000:00/0000:[COLOR="#FF0000"]00:19.0[/COLOR]/power/control
```Substitute your bus number here. If it returns 'auto' when your ethernet is connected, force it to 'on':```
sudo su
echo on > /sys/devices/pci0000:00/0000:00:19.0/power/control
exit
```And check:```
cat /sys/devices/pci0000:00/0000:00:19.0/power/control
```In every case, of course, substitute your PCI bus numer for mine 00:19.0.

Now does it connect?

---

### Post by bonsty on 2013-05-04
SUCCESS! chili555 you are an absolute hero! Thank you so much for your help, as soon as I changed the power setting to 'on' as oppose to 'auto' the whole thing just worked, hopefully the setting will be persistent when I reboot, if not then I should be able to work something out!

Thanks again!

---

### Post by chili555 on 2013-05-04
> hopefully the setting will be persistent when I rebootMaybe it will be, but I suspect not. If not, please do:```
gksudo gedit /etc/rc.local
```Add your declaration right above exit 0:```
echo on > /sys/devices/pci0000:00/0000:[COLOR="#FF0000"]00:19.0[/COLOR]/power/control
```Of course, substitute your bus number here. Reboot and please report your success.

---

### Post by bonsty on 2013-05-04
Had already added that to rc.local! And yes, it works which is good news.

Thanks again for all of your help!

---

### Post by chili555 on 2013-05-04
> **bonsty said:**
> Had already added that to rc.local! And yes, it works which is good news.

Thanks again for all of your help!Great news. I am sure it will help some searchers, too.

---

### Post by rsahadevan on 2013-05-12
HI 

Thanks for the help. I have the same issue and below solution helped me to resolve the issue

echo on > /sys/devices/pci0000:00/0000:[COLOR=#FF0000]00:19.0[/COLOR]/power/control

But Every time I need to manually do after resuming from susped. I tried by adding in  But doesnt work
 	Code:

 	
gksudo gedit /etc/rc.local
echo on > /sys/devices/pci0000:00/0000:[COLOR=#FF0000]00:19.0[/COLOR]/power/control 
Add your declaration right above exit 0: 	Code:
 	
Please help

---

### Post by chili555 on 2013-05-12
> **rsahadevan said:**
> HI 

Thanks for the help. I have the same issue and below solution helped me to resolve the issue

echo on > /sys/devices/pci0000:00/0000:[COLOR=#FF0000]00:19.0[/COLOR]/power/control

But Every time I need to manually do after resuming from susped. I tried by adding in  But doesnt work
 	Code:

 	
gksudo gedit /etc/rc.local
echo on > /sys/devices/pci0000:00/0000:[COLOR=#FF0000]00:19.0[/COLOR]/power/control 
Add your declaration right above exit 0: 	Code:
 	
Please helpLet's see:```
lspci -nn | grep 0200
cat /etc/rc.local
```Thanks.

---

### Post by shrijith1 on 2013-05-25
Thanks a lot chilli555 for the help. I also ran into this issue and on extensive googling got this thread :) Thanks again. Looks like the fix will be out soon in an updated kernel...

---

### Post by grepcat on 2013-06-23
This solution works for me as well - ThinkPad X220, 13.04 and  Intel 82579LM Gigabit Network Connection [8086:1502] (rev 04).

Thank you - this was driving me crazy.

---

### Post by Diwakar_Suvvari on 2013-08-01
Hi,
I am new to this forum and to ubuntu. I have a similar issue and need a solution if anyone can provide one.

I have installed Ubuntu 11.10 (dual boot with win 7 on different partition) and when i login to ubuntu, my ethernet port is not detected. (I am able to use wired connection on win 7).

My network adapters:

Atheros AR8162/8166/8168 PCIE-E Fast Ethernet Controller (NDIS 6.20)
Atheros AR9285 wireless Network Adapter

I have run some commands (note: ethernet cable is not connected):

**administrator@administrator-Lenovo-G580:~$ ifconfig**
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7584 (7.5 KB)  TX bytes:7584 (7.5 KB)

wlan0     Link encap:Ethernet  HWaddr 2c:d0:5a:14:1a:15 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**administrator@administrator-Lenovo-G580:~$ sudo lshw -C network**
[sudo] password for administrator:
  *-network              
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 2c:d0:5a:14:1a:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

**administrator@administrator-Lenovo-G580:~$ lspci -nn | grep 0200**
03:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1090] (rev 10)
[B]administrator@administrator-Lenovo-G580:~$ dmesg | grep -e eth0 -e e100
administrator@administrator-Lenovo-G580:~$ cat /etc/network/interfaces[/B]
auto lo
iface lo inet loopback

**administrator@administrator-Lenovo-G580:~$ nm-tool**

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        2C:D0:5A:14:1A:15

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by chili555 on 2013-08-01
> **Diwakar_Suvvari said:**
> Hi,
I am new to this forum and to ubuntu. I have a similar issue and need a solution if anyone can provide one.

I have installed Ubuntu 11.10 (dual boot with win 7 on different partition) and when i login to ubuntu, my ethernet port is not detected. (I am able to use wired connection on win 7).

My network adapters:

Atheros AR8162/8166/8168 PCIE-E Fast Ethernet Controller (NDIS 6.20)
Atheros AR9285 wireless Network Adapter

Let's have a look at:```
lspci -nn | grep 0200
```Thanks.

---

### Post by Diwakar_Suvvari on 2013-08-01
Hi chilli555,

I have already posted the result of that command:

[B]administrator@administrator-Lenovo-G580:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1090] (rev 10)


[/B]

---

### Post by chili555 on 2013-08-01
> **Diwakar_Suvvari said:**
> Hi chilli555,

I have already posted the result of that command:

[B]administrator@administrator-Lenovo-G580:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1090] (rev 10)


[/B]That device is covered by the driver *alx*. We could download and compile the driver for the two year old 11.10 or you could install 13.04 and it will work by default. Which do you prefer?

---

### Post by Diwakar_Suvvari on 2013-08-01
Since i have already installed 11.10, i would prefer installing the other drivers.

Actually i am have gone through your post "[http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126)".

It actually talks about the same issue.

[COLOR=#000000]build-essential depends on dpkg-dev, g++, gcc, libc6-dev or libc-dev
[/COLOR]
Is there anyway i can download all the dependent packages together. I am downloading them on different machine and transferring through USB.

Thanks
Diwakar

---

### Post by chili555 on 2013-08-01
Is your wireless not working? If you can get a temporary wireless connection, it will take just a few moments:```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by Diwakar_Suvvari on 2013-08-01
I have tried to install the package mentioned in the above thread, but am getting this error:

dpkg-deb: error: 'build-essential_11.5ubuntu2_i386.deb' is not a debian format archive

---

### Post by Diwakar_Suvvari on 2013-08-01
I don't have a wifi connection at home. I have to work with a wired connection and 2 machines and USB.

---

### Post by chili555 on 2013-08-01
> **Diwakar_Suvvari said:**
> I have tried to install the package mentioned in the above thread, but am getting this error:

dpkg-deb: error: 'build-essential_11.5ubuntu2_i386.deb' is not a debian format archiveWhere did you download it? In the Ubuntu package search? For 11.10? For 32- or 64-bit as appropriate?

[https://launchpad.net/ubuntu/maverick/+package/build-essential](https://launchpad.net/ubuntu/maverick/+package/build-essential)

Do you still have the install CD?

---

### Post by Diwakar_Suvvari on 2013-08-01
I have downloaded from "[http://packages.ubuntu.com/precise/build-essential](http://packages.ubuntu.com/precise/build-essential)"

Mine is 32 bit, 11.10 Ubuntu.

uname -a
Linux administrator-Lenovo-G580 3.0.0-12-generic#20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/LINUX

Sorry, but I don't have the install CD now.

---

### Post by chili555 on 2013-08-01
However, Ubuntu 11.10 is not Precise, it is Maverick. I suggest you try the package I linked above.

---

### Post by Diwakar_Suvvari on 2013-08-01
Oh, Ok.

Can you point me to the website from where i can download other packages from Maverick.

[COLOR=#000000]The red dots indicate that the package build-essential depends on dpkg-dev, g++, gcc, libc6-dev or libc-dev and make. Download those packages also.[/COLOR]

[COLOR=#000000]Now for linux-headers: [/COLOR][http://packages.ubuntu.com/search?ke...se&section=all]("http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all")[COLOR=#000000] As you can see, you can download linux-headers-generic or linux-headers-generic-pae. Find out which you need with:[/COLOR][COLOR=#000000]Code:
uname -r[/COLOR]
[COLOR=#000000]This package depends on the headers matching your running kernel. That means that, in addition to the 'generic' or generic-pae' package, you'll also need linux-headers for your kernel. For example, if the uname -r command shows that you are running [/COLOR]*3.2.0-23-generic, you will need linux-headers-[I]3.2.0-23-generic. *[/I]

---

### Post by chili555 on 2013-08-01
[https://launchpad.net/ubuntu/maverick/+search?text=dpkg-dev](https://launchpad.net/ubuntu/maverick/+search?text=dpkg-dev)

Try plugging in each package name in the search box and download them.

Do you see what's going on here? You could have downloaded and installed 13.04 an hour ago! If you insist on 11.10, then please proceed.

---

### Post by Diwakar_Suvvari on 2013-08-01
Thanks for the pointers. I still want to go to the end with 11.10.
I will update you when i am done.

Thanks again for the help.

---

### Post by chili555 on 2013-08-01
I will be away for lunch for awhile. Good luck and I'll check in a bit later.

---

### Post by Diwakar_Suvvari on 2013-08-06
Sorry for the late reply.

I have tried to install the packages and the links keep on increasing, so i had paused there and uninstalled 11.10 & installed 13.04.

It has the said alx driver and my ethernet port was detected and connection got through.

Thanks for the help.

---

### Post by chili555 on 2013-08-06
Glad it's working.

---

### Post by chris30 on 2013-08-08
I have the same issue with a fresh install desktop connecting though I suspect there maybe a different underlying cause. the pci bus for my Ethernet Controller is listed as 06:00.0 with no corresponding file structure under /sys/devices/pci0000:00/**[COLOR=#ff0000]0000:00:06.0[/COLOR]**/power/control

lspci -nn |grep 0200 = 06:00.0 Ethernet Controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
uname -u = 3.8.0-19-generic

I get a continuous kernel entry in syslog r8169 0000:06:00.0 link 

Just comparing, I have a lenovo x200 notebook with the same install build which connects without issue 
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300

---

### Post by chili555 on 2013-08-08
> **chris30 said:**
> I have the same issue with a fresh install desktop connecting though I suspect there maybe a different underlying cause. the pci bus for my Ethernet Controller is listed as 06:00.0 with no corresponding file structure under /sys/devices/pci0000:00/**[COLOR=#ff0000]0000:00:06.0[/COLOR]**/power/control

lspci -nn |grep 0200 = 06:00.0 Ethernet Controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
uname -u = 3.8.0-19-generic

I get a continuous kernel entry in syslog r8169 0000:06:00.0 link 

Just comparing, I have a lenovo x200 notebook with the same install build which connects without issue 
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300You and I *both* suspect another underlying cause. Please start your own new thread and fully describe your symptoms. Include:```
nm-tool
ifconfig
lspci -nn | grep 0200
```

---

