---
title: "Getting gigabit networking working with 12.04.1 on a Dell PowerEdge SC1425"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by icelander on 2012-10-13
The specs:
 - OS: 12.04.1 Server
 - Kernel: 3.2.0-29-generic
 - NIC model: Intel 82541GI

So the OS installs just fine, and the network comes up but never goes over 10Mbps. So I went to Intel and downloaded the new driver. Here's the output from compiling it.

```
# make install
make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/home/paul/e1000e-2.1.4/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
# remove all old versions of the driver
find /lib/modules/3.2.0-29-generic -name e1000e.ko -exec rm -f {} \; || true
find /lib/modules/3.2.0-29-generic -name e1000e.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000e.ko /lib/modules/3.2.0-29-generic/kernel/drivers/net/e1000e/e1000e.ko
/sbin/depmod -a || true
install -D -m 644 e1000e.7.gz /usr/share/man/man7/e1000e.7.gz
man -c -P'cat > /dev/null' e1000e || true
e1000e.
```

So then I used modprobe to remove the old driver and install the new one.

```
# modprobe -rv e1000
rmmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/ethernet/intel/e1000/e1000.ko
# modprobe -v e1000e
rmmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/e1000e/e1000e.ko

```
However, when I re-run the script Intel provides to show which driver version it shows me this:

```
# ./netdriverinfo.sh
eth0 : 02:04.0
    Make/Model = Dell PRO/1000 MT Network Connection
    Ethernet controller = Intel Corporation 82541GI Gigabit Ethernet Controller 
    VenID:DevID = 8086:1076
    Driver name = No driver loaded
    Driver version = No driver loaded
eth1 : 04:03.0
    Make/Model = Dell PRO/1000 MT Network Connection
    Ethernet controller = Intel Corporation 82541GI Gigabit Ethernet Controller 
    VenID:DevID = 8086:1076
    Driver name = e1000
    Driver version = 7.3.21-k8-NAPI

```

Running lsmod shows that the new driver is loaded but isn't being used

```
# lsmod | grep e1000
e1000e 		195811 	0
```

ifup yields this:

```
# ifup eth0
Cannot find device "eth0"
Failed to bring up eth0.
```

I've also tried blacklisting e1000 but it loads anyway on reboot.

I know there's a step missing but I'm not sure what. Any ideas?

---

### Post by chili555 on 2012-10-13
e1000 is correct for your devices and not e1000e; that's why it isn't being used. I'd remove the blacklist and reboot and check again:```
./netdriverinfo.sh
```There are a number of driver parameters you might try:```
modinfo e1000
```> parm:           TxDescriptors:Number of transmit descriptors (array of int)
parm:           RxDescriptors:Number of receive descriptors (array of int)
parm:           Speed:Speed setting (array of int)
parm:           Duplex:Duplex setting (array of int)
parm:           AutoNeg:Advertised auto-negotiation setting (array of int)
parm:           FlowControl:Flow Control setting (array of int)
parm:           XsumRX:Disable or enable Receive Checksum offload (array of int)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           debug:Debug level (0=none,...,16=all) (int)
I suggest:```
sudo modprobe -r e1000
sudo modprobe e1000 Speed=1000
```If it works, you can write a /etc/modprobe.d/e1000.conf file:```
options e1000 Speed=1000
```

---

### Post by icelander on 2012-10-14
So here's what I ran:

```
# modprobe -r e1000
# modprobe e1000 Speed=1000
# ping 192.168.1.1
Network is unreachable
```

ethtool doesn't work either.

Also, the indicator light on my switch still says 10Mbit.

As a test I created that modprobe.d config file and it didn't change anything, either.

---

### Post by icelander on 2012-10-16
Any more ideas or am I stuck with installing Windows to get gigabit networking?

---

### Post by icelander on 2012-10-16
Also, the utility provided by Intel says the driver version is 7.3.21, while [Intel's SourceForge site]("http://sourceforge.net/projects/e1000/files/e1000%20stable/8.0.35/") says that the latest version is 8.0.35. Should I try upgrading to that version of the driver?

---

### Post by chili555 on 2012-10-16
> **icelander said:**
> Also, the utility provided by Intel says the driver version is 7.3.21, while [Intel's SourceForge site]("http://sourceforge.net/projects/e1000/files/e1000%20stable/8.0.35/") says that the latest version is 8.0.35. Should I try upgrading to that version of the driver?I would.

---

### Post by icelander on 2012-10-18
Unfortunately the latest version of the driver won't compile on 3.2 without patching. Argh.

---

### Post by icelander on 2012-10-21
Still no joy, but I tried installing 12.10 (in the hopes that the compilation problem would be gone - it wasn't), and created this config file:

```
options e1000 debug=16
```

So that I could at least see what the heck was going on. However, I can't find *any* logs mentioning the e1000 driver past the boot logs talking about how it was set up. Where are kernel logs kept?

---

### Post by icelander on 2012-10-21
> **icelander said:**
> Still no joy, but I tried installing 12.10 (in the hopes that the compilation problem would be gone - it wasn't), and created this config file:

```
options e1000 debug=16
```

So that I could at least see what the heck was going on. However, I can't find *any* logs mentioning the e1000 driver past the boot logs talking about how it was set up. Where are kernel logs kept?

Okay, so I found a script that will show me the module options and the only one that's enabled is copybreak, which is set to 256.

---

### Post by chili555 on 2012-10-21
> **icelander said:**
> Still no joy, but I tried installing 12.10 (in the hopes that the compilation problem would be gone - it wasn't), and created this config file:

```
options e1000 debug=16
```

So that I could at least see what the heck was going on. However, I can't find *any* logs mentioning the e1000 driver past the boot logs talking about how it was set up. Where are kernel logs kept?I suggest:```
sudo cat /var/log/syslog | grep -e e1000 -e eth0
```

---

### Post by icelander on 2012-10-21
Running that command gave me records from each boot that are identical. Here's the latest:

```

Oct 21 13:13:40 nimbus kernel: [    0.884990] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
Oct 21 13:13:40 nimbus kernel: [    0.885013] e1000: Copyright (c) 1999-2006 Intel Corporation.
Oct 21 13:13:40 nimbus kernel: [    0.885086] e1000 0000:02:04.0: >PCI IRQ 32 -> rerouted to legacy IRQ 16
Oct 21 13:13:40 nimbus kernel: [    1.122223] e1000 0000:02:04.0: >eth0: (PCI:66MHz:32-bit) 00:12:3f:20:d7:04
Oct 21 13:13:40 nimbus kernel: [    1.122245] e1000 0000:02:04.0: >eth0: Intel(R) PRO/1000 Network Connection
Oct 21 13:13:40 nimbus kernel: [    1.566228] e1000 0000:04:03.0: >eth1: (PCI:33MHz:32-bit) 00:12:3f:20:d7:05
Oct 21 13:13:40 nimbus kernel: [    1.566247] e1000 0000:04:03.0: >eth1: Intel(R) PRO/1000 Network Connection
Oct 21 13:13:40 nimbus kernel: [    4.201623] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 21 13:13:40 nimbus kernel: [    9.235916] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 21 13:13:43 nimbus dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 21 13:13:46 nimbus dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 21 13:13:50 nimbus kernel: [   19.256712] e1000: eth0 NIC Link is Up 10 Mbps Full Duplex, Flow Control: RX/TX
Oct 21 13:13:50 nimbus kernel: [   19.256914] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 21 13:13:53 nimbus dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 21 13:13:53 nimbus dhclient: DHCPREQUEST of 192.168.1.125 on eth0 to 255.255.255.255 port 67

```

---

### Post by chili555 on 2012-10-21
> eth0 NIC Link is Up [COLOR="Red"]10 Mbps Full Duplex[/COLOR], Flow Control: RX/TXDoes the Speed parameter change this?```
options e1000 Speed=100 [COLOR="Red"]<--or 1000[/COLOR]
```Also, what does this tell us?```
cat /sys/module/e1000/parameters/AutoNeg
```

---

### Post by icelander on 2012-10-21
I tried the speed setting at both 100 and 1000 and it didn't change anything other than taking down the network connectivity until I rebooted. There's no AutoNeg file in that directory, either. Here's what I see:

```

$ ls /sys/module/e1000/parameters/
copybreak

```

---

### Post by icelander on 2012-10-30
Any more ideas? It's basically just a paperweight now...

---

