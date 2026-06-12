---
title: "Upgraded from 10.10 to 11.04 and BCM4312 stopped working"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by nickfank on 2011-09-23
I just did an **upgrade from 10.10 32 bit to 11.04, 64 bit**. Before the upgrade, my wireless worked fine. 

My computer is a Dell **Vostro 1720 laptop with a BCM4312** controller. It has a switch on the side to turn wireless on/off, and a blue light to indicate when the wirelss controller is on. During all of my attempts, the switch was on, and the "active" light was also on.

Here's the log of basic diagnostic info:

nickf@nickf-Vostro-1720:~$ **lspci -vvnn| grep 14e4**
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

nickf@nickf-Vostro-1720:~$ **ifconfig**
eth0 Link encap:Ethernet HWaddr 00:24:e8:d6:9c:fe 
inet addr:172.18.64.214 Bcast:172.18.255.255 Mask:255.255.0.0
inet6 addr: fe80::224:e8ff:fed6:9cfe/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6222 errors:0 dropped:0 overruns:0 frame:0
TX packets:4568 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:5577994 (5.5 MB) TX bytes:828915 (828.9 KB)
Interrupt:47 Base address:0x2000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

nickf@nickf-Vostro-1720:~$ **iwconfig**
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

nickf@nickf-Vostro-1720:~$ lsmod | grep sta
nickf@nickf-Vostro-1720:~$ lsmod | grep b43
nickf@nickf-Vostro-1720:~$ lsmod | grep wl
wl 2568244 0 
lib80211 14991 2 lib80211_crypt_tkip,wl


A chunk of **dmesg **that might apply:

[ 12.055726] r8169 0000:08:00.0: eth0: link down
[ 12.055735] r8169 0000:08:00.0: eth0: link down
[ 12.056697] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 12.059489] wl: module license 'MIXED/Proprietary' taints kernel.
[ 12.059493] Disabling lock debugging due to kernel taint
[ 12.100728] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 12.100742] wl 0000:0e:00.0: setting latency timer to 64
[ 12.146586] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 12.146662] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[ 12.146694] HDA Intel 0000:00:1b.0: setting latency timer to 64


nickf@nickf-Vostro-1720:~$ **sudo lshw -C network**
*-network 
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:08:00.0
logical name: eth0
version: 03
serial: 00:24:e8:d6:9c:fe
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.18.64.214 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
*-network DISABLED
description: Wireless interface
product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0e:00.0
logical name: eth1
version: 01
serial: 0c:60:76:01:7a:a4
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:18 memory:fa000000-fa003fff

**iwlst scan** reports no interfaces supporting scanning.

nickf@nickf-Vostro-1720:~$ **sudo /etc/init.d/networking restart**
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.


nickf@nickf-Vostro-1720:~$ **lspci -k**
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Dell Device 02c0
    Kernel driver in use: r8169
    Kernel modules: r8169
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card
    Kernel driver in use: wl
    Kernel modules: wl, ssb

nickf@nickf-Vostro-1720:~$ **rfkill list**
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Here's what I've already tried:

1) I read a number of suggestions in the "sticky" thread for Broadcom 43xx cards about dealing with this problem, but none seemed to work. Many suggested amounted to "get rid of the current driver & get the old (10.10) version", but I couldn't seem to get the old version removed, so...

2)I did "clean" reinstall of 11.04 on my laptop using the "replace" option. I did not opt for downloading updates or obtaining third-party drivers, hoping that this would give me a clean slate to work from.

3)I then used synaptic package manager to install "firmware-b43lpphy-installer" and rebooted. Still no wireless. Used "Additional Drivers" to active the listed STA driver and rebooted. No luck still.

4) Following advice that I should replace the current version with the older driver, I uninstalled the current version using sudo apt-get remove bcmwl-kernel-source(was told it wasn't installed, so not removed. Then downloaded bcmwl-kernel-source-5.60.48.36+bdcom-0ubuntu5_amd64.deb and installed it. Activated the driver via "Additional Drivers" and restarted. still no wireless.

5) Following the troubleshooting chart posted in the sticky thread, decided I needed the "wl" driver. Uninstalled firmware-b43-lpphy-installer and b43-fwcutter using synaptic package manager. Installed broadcom-sta-common and broadcom-sta-source via synaptic. Restarted. No Wireless. Activated in "Additional Drivers" and rebooted. Still No wireless.

6) Decided I'm shooting in the dark & need help on diagnosis, and posted this... What diagnostics should I try next to narrow down the problem?

Thanks!

---

### Post by chili555 on 2011-09-23
> Following the troubleshooting chart posted in the sticky thread, decided I needed the "wl" driver.Correct.> Decided I'm shooting in the dark & need help on diagnosisTwilight, maybe, but not dark. The answer is here:> nickf@nickf-Vostro-1720:~$ rfkill list
0: dell-wifi: Wireless LAN
Soft blocked: yes
[COLOR="Red"]Hard blocked: yes[/COLOR]Notwithstanding the color of the wireless LED, the kernel thinks the wireless is switched off. Please detach the ethernet cable and do:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```If there is any change in your wireless, we'll make a few file changes to make it permanent.

Dell + Broadcom STA + 11.04 = Chili's heartburn. This may take a couple of tries.

---

### Post by nickfank on 2011-09-24
OK, here's the report:

Rebooted without cable connected. Wireless still broken.

Did "sudo rmmod -f dell-laptop". Wireless immediately wakes up and connects. (Happy dance.)

Did "sudo rfkill unblock all". No change. (But that's good.)

So you've led me straight to the solution! How do I make this permanent? And if you have the time, what's the short version of what that first command did for me?

Thanks.
    -Nick

---

### Post by chili555 on 2011-09-24
Let's blacklist dell-laptop so it never loads on boot and stops your wireless. In a terminal, please do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Many laptops have a laptop mode or acpi or wmi driver that converts key presses into information the kernel understands; in your case, "Please turn on the wireless, Mr. Kernel."

dell-laptop is notorious for not working quite well enough. The solution is to remove it altogether. It may, or may not, bring about other anomalies, but at least your wireless works.

---

### Post by nickfank on 2011-09-26
Excellent. That worked to make the change permanent, and so far, no adverse side-effects. Just in case anyone scrolls straigt to the last post, I'll note that this fix seems to be specific to problems with the broadcom 43xx wireless controllers on a dell laptop running 11.04.

Thanks Chili!

---

### Post by mozozo4 on 2011-09-26
i have an hp dv6000 laptop and i cant get wifi on ubuntu 11.04
is there a code like the one you gave for the hard blocked but for hp?

---

### Post by chili555 on 2011-09-26
Please post:```
lspci -nn | grep 0280
lsmod | grep wl
rfkill list all
```Thanks.

---

