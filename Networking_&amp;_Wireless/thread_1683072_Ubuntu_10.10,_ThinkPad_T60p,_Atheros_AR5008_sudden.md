---
title: "Ubuntu 10.10, ThinkPad T60p, Atheros AR5008 suddenly stopped working"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by rulfzid on 2011-02-07
[SIZE="4"][COLOR="Red"]**[SOLVED]: see post #3**[/COLOR][/SIZE]

Hi,

I've been running Ubuntu 10.10 on this ThinkPad for a couple of months now, with absolutely no problems at all.

The wireless was working fine earlier today out at a coffee shop. When I got home and turned the computer on, the network applet just showed a "Wireless is disabled" message.

I poked around for a while, mucking with whatever I could (limited, unfortunately, I don't have great linux-fu) and doing the ritual reboot to see if that would get things going.

I then spent some time reading through forum threads here, but didn't find any answers.

Below are the results of the various commands as described in [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681") sticky thread - thanks in advance for all your help.


**Machine brand and model**

```
Lenovo ThinkPad T60p
```

**lspci -nn | grep Atheros**

```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR5008 Wireless Network Adapter [168c:0024] (rev 01)
```

**ifconfig**

```
eth0      Link encap:Ethernet  HWaddr 00:16:41:e7:24:e9  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fee7:24e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3506365 (3.5 MB)  TX bytes:555789 (555.7 KB)
          Interrupt:16 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41448 (41.4 KB)  TX bytes:41448 (41.4 KB)
```

**iwconfig**

```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```     

**lsmod | grep ath**

```
ath9k                  88756  0 
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
mac80211              231959  2 ath9k,ath9k_common
cfg80211              144694  4 ath9k,ath9k_common,ath,mac80211
led_class               2633  2 thinkpad_acpi,ath9k
```

**dmesg | grep ath**

```
[    0.464027] device-mapper: multipath: version 1.1.1 loaded
[    0.464033] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.225671] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.225687] ath9k 0000:03:00.0: setting latency timer to 64
[   22.424679] ath: EEPROM regdomain: 0x62
[   22.424682] ath: EEPROM indicates we should expect a direct regpair map
[   22.424686] ath: Country alpha2 being used: 00
[   22.424688] ath: Regpair used: 0x62
[   22.467321] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   22.468061] Registered led device: ath9k-phy0::radio
[   22.468086] Registered led device: ath9k-phy0::assoc
[   22.468110] Registered led device: ath9k-phy0::tx
[   22.468129] Registered led device: ath9k-phy0::rx
```

**sudo lshw -C network**

```
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:e7:24:e9
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.5-1 ip=192.168.1.79 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:ee000000-ee01ffff ioport:3000(size=32)
  *-network DISABLED
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:2f:62:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-25-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:edf00000-edf0ffff
```

**iwlist scan**

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
```

**lsb_release -d**

```
Description:	Ubuntu 10.10
```

**uname -mr**

```
2.6.35-25-generic i686
```

**sudo /etc/init.d/networking restar**t

```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
```

---

### Post by tgalati4 on 2011-02-07
Pull the battery.  Let it sit for 10 min.  Boot.

---

### Post by rulfzid on 2011-02-07
> **tgalati4 said:**
> Pull the battery.  Let it sit for 10 min.  Boot.

That was actually the first thing I tried, as mentioned above - "ritual reboot" is my phrase for it.

However, this is solved. It turns out I'm just an idiot who doesn't know some basic things about his computer.

After reading through some other forum thread, I tried:

```
sudo ifconfig wlan0 up
```

which resulted in:

```
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

Googling that, I discovered what rfkill is and discovered my wireless had a "hard block", meaning a physical wireless on/off switch on my computer was in the off position. :redface:

I didn't even know I had a wireless on/off switch.

Apologies to those of you who took the time to read my ticket.

---

