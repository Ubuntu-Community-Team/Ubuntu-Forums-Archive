---
title: "Pro Wireless 2200BG Network DISABLE"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by palonso53 on 2011-03-10
Hi, every one !
I'm pretty new using Linux - Ubuntu, but I like it, and I'm trying to see how powerful it is.
I got a non function wireless network card. Here the information that I be able to collect:

 - Tabletop HP Compaq tc4200.
 - OS Ubuntu 10.04 LTS - the Lucid Linux.
 - Wireless interface: Pro/Wireless 2200BG [Calexico2] Network Connection. Vendor: Intel Corporation.
 - network DISABLED
 - Configuration:  - broadcast=       yes
                            - driver=              ipw2200 
                            - driverversion= 1.2.2kmprq
                            - firmware=         ABG:9.0.5.27 (Dec 12 2007)
                            - latency=           64
                            - link=                 no
                            - maxlatency=    24
                            - mingnt=            3
                            - multicast=         yes
                            - wireless=          radio off
 - Resources:     - irq:           21
                           - memory:  d0400000-d0400fff
Please, How I enable this wireless network card?

Thank you ! . . .

---

### Post by chili555 on 2011-03-10
> wireless= radio offWhat, if anything, does this tell us?```
rfkill list all

```> Tabletop HP Compaq tc4200Tabletop? I thought it was a tablet. Is there a wireless switch on the left side that's off? Can you move it to On?

---

### Post by palonso53 on 2011-03-11
Hi, Ubuntu forum.
 
Thanks, so much, for the quick answer, specially to "chili555".
 
When the code that was sent, is introduced, the return is:
 
 9: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
 
When the bottom that you asked is pushed, blue light in left side of front panel goes off and bluetooth icon in the task bar at top of screen, vanish. (see the attached pictures).
 
I tested the bluetooth device, it is working.
 
Regards.

---

### Post by chili555 on 2011-03-11
Is the module hp-wmi loaded?```
lsmod | grep hp
```> 9: hci0: Bluetooth
Soft blocked: no
Hard blocked: noIt ought to return data about wireless, as well. Here is mine:> 0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: [COLOR="Red"]Wireless LAN[/COLOR]
	Soft blocked: no
	Hard blocked: noThanks.

---

### Post by palonso53 on 2011-03-12
Hi, chili555 & Ubuntuforum. Every thing OK ?

After used the code that you provide me "lsmod | grep hp", this code did not return any answer.

Looks the hp-wmi module is not loaded. Some help with this ?

Thanks you, very much.

We are here so sorry about what is happening with people in Japan. God bless they !

---

### Post by chili555 on 2011-03-12
I'm OK here in the USA but feeling sorrow for our forum friends in Japan.

Let's load the module and see what happens:```
sudo modprobe hp-wmi
rfkill list all
```Now is there an entry for wireless?

If it works, we can load it on boot automatically.

---

### Post by palonso53 on 2011-03-14
Hi, chili555 & Ubuntuforum.
 
After use the code provided, the tablet returned enabling the wireless device and let me to establish connection with the wireless modem and it can do it automatic every time that the tablet is turn on.
Now, I be able to connect to Internet wireless, good.
Good job for "chili555", he fixed the problem and teach me some codes.
 
Thanks, thank you, so much, you saved this tablet.
 
Have a great one ! . . . .

---

### Post by palonso53 on 2012-03-28
Hi, Ubuntuforum.
Hope every one is well.
After a year working well, and after update ubuntu to Ubuntu 11.10, I got same situation wireless card is disable and after try the same codes that you provide me the situation still.
Please, could you help me ?

---

### Post by chili555 on 2012-03-28
Please let me see:> rfkill list all
iwconfig
dmesg | grep ipwThanks.

---

### Post by praseodym on 2012-03-28
Hi,

try to update the driver:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic linux-firmware
```
and reboot.

---

### Post by palonso53 on 2012-03-28
Good afternoon, Chili555, thank you for answer me.

To code "rfkill list all" asnwer was:

 0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

To code "iwconfig" answer was:

lo        no wireless extensions.

eth2      no wireless extensions.

rename3   IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

To code "dmesg | grep ipw" asnwer was:

[   37.577637] libipw: 802.11 data/management/control stack, git-1.1.13
[   37.577642] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   37.600359] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   37.600365] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   37.600593] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   37.600640] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   38.157272] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

Thank you, for help me.

Best regards.

---

### Post by chili555 on 2012-03-28
> [COLOR="Red"]eth2[/COLOR] no wireless extensions.

[COLOR="Red"]rename3[/COLOR] IEEE 802.11bg ESSIDff/any
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power=20 dBm Sensitivity=8/0 Ugly! I doubt it's the driver. Let's look a little deeper at:```
cat /etc/udev/rules.d/70-persistent-net.rules
sudo lshw -C network
```Your *dmesg* looks pretty solid. Thanks.

---

### Post by palonso53 on 2012-03-28
Hi, praseodym.
I glad to see you helping in this situation.

To code "sudo apt-get install linux-backports-modules-wireless-lucid-generic linux-firmware" asnwer was:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-wireless-lucid-generic

Thank you, for your help.

---

### Post by palonso53 on 2012-03-28
Hi, chili555.

Here there were asnwer to the codes:

To "cat /etc/udev/rules.d/70-persistent-net.rules":

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x109a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:b7:b3:02:67", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:d2:86:8d:f9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:d2:b9:7d:f6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x8086:0x109a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:b7:51:e7:66", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:f0:a0:4d:65", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:b0:76:fe:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

To "sudo lshw -C network":

*-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth2
       version: 11
       serial: 00:0f:b0:76:fe:22
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=5751m-v3.29a ip=192.168.1.37 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:d0000000-d000ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: rename3
       version: 05
       serial: 00:12:f0:a0:4d:65
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:d0400000-d0400fff

Wow, looks a little complicated than other time.

Thank you, best regards.

---

### Post by chili555 on 2012-03-28
Wow! That's a pile of former network devices! Did you previously have this harddrive in another computer? That's perfectly fine; I've done that myself in the past 48 hours! However, we often need to clean up 70-persistent-net.rules to remoe the old stuff.

If that's the case, I'd change it as I've highlighted:```
sudo gedit 
```> # This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x109a (e1000e)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", [COLOR="Red"]#[/COLOR]ATTR{address}=="00:15:b7:b3:02:67", ATTR{dev_id}=="0x0", [COLOR="Red"]#[/COLOR]ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", [COLOR="Red"]#[/COLOR]ATTR{address}=="00:19:d2:86:8d:f9", ATTR{dev_id}=="0x0", [COLOR="Red"]#[/COLOR]ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x4222 (iwl3945)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", [COLOR="Red"]#[/COLOR]ATTR{address}=="00:19:d2:b9:7d:f6", ATTR{dev_id}=="0x0", [COLOR="Red"]#[/COLOR]ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x8086:0x109a (e1000e)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", [COLOR="Red"]#[/COLOR]ATTR{address}=="00:15:b7:51:e7:66", ATTR{dev_id}=="0x0", [COLOR="Red"]#[/COLOR]ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:f0:a0:4d:65", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth1[/COLOR]"

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:b0:76:fe:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth0[/COLOR]"
Proofread carefully twice, save and close gedit. Immediately reboot. Now let us see:```
iwconfig
dmesg | grep ipw
```Thanks.

---

### Post by palonso53 on 2012-03-28
Hi, chili555.
I did what you suggest.
I opened gedit and I copy and paste the quote that you sent.
When try to save it, system ask for name and named "Wireless Document 1" but also ask for save in a folder and options are: "root" and "File System", I stoped there for your suggestions.

---

### Post by chili555 on 2012-03-28
> **palonso53 said:**
> Hi, chili555.
I did what you suggest.
I opened gedit and I copy and paste the quote that you sent.
When try to save it, system ask for name and named "Wireless Document 1" but also ask for save in a folder and options are: "root" and "File System", I stoped there for your suggestions.I made a mistake; I'm sorry. Please try again:```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```Make only the changes I've highlighted. Proofread carefully twice, save and close gedit. Immediately reboot.

Sorry.

---

### Post by palonso53 on 2012-03-28
chili555:
Don't need to say sorry, you are helping to everybody and you are doing your best.

About if I had the harddrive in other pc, I don't know, but it is perfectly posible because I bought it used and it looks rebuilt.

Now, the moment of true:

answer for iwconfig:

lo        no wireless extensions.

eth1      no wireless extensions.

rename3   IEEE 802.11bg  ESSID:"35_alonso"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:3D:C7:AA:4F:B6   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/100  Signal level=-26 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:65


answer for dmesg | grep ipw:

 
[FONT=monospace][   36.989836] libipw: 802.11 data/management/control stack, git-1.1.13
[   36.989841] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   37.156699] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   37.156703] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   37.156826] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   37.156852] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   38.149338] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

Now, when I opened the network icon in the top of screen because I am wired connected to network, I can see the wired and wireless connections. it means that it is problem solve ?
[/FONT]

---

### Post by chili555 on 2012-03-29
> it means that it is problem solve ?Did you detach the ethernet and try to connect? It may. Are you close to the router?> Link Quality=[COLOR="Red"]31[/COLOR]/100

It's still not correct,though. Let's fine-tune. Please show me:```
dmesg | grep -e eth -e rename
cat /etc/udev/rules.d/70-persistent-net.rules
```Thanks.

---

### Post by palonso53 on 2012-03-29
Hi, there. I hope all is Ok. 
All before happens connected wired to router, I detached and was connected wireless and it were about 5ft from the router.
Every thing now is happenig wireless connected and about 20 ft. from the router.

Answer for "dmesg | grep -e eth -e rename":

[    0.068003] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    1.554697] tg3 0000:10:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:0f:b0:76:fe:22
[    1.554704] tg3 0000:10:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.554708] tg3 0000:10:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.554712] tg3 0000:10:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   37.821972] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.816024] eth1: no IPv6 routers present


Answer for "cat /etc/udev/rules.d/70-persistent-net.rules":

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x109a (e1000e)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", #ATTR{address}=="00:15:b7:b3:02:67", ATTR{dev_id}=="0x0", #ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", #ATTR{address}=="00:19:d2:86:8d:f9", ATTR{dev_id}=="0x0", #ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x4222 (iwl3945)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", #ATTR{address}=="00:19:d2:b9:7d:f6", ATTR{dev_id}=="0x0", #ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x8086:0x109a (e1000e)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", #ATTR{address}=="00:15:b7:51:e7:66", ATTR{dev_id}=="0x0", #ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:f0:a0:4d:65", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:b0:76:fe:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

Thank you for all.

---

### Post by palonso53 on 2012-03-29
Also here the answer for: "iwconfig" in the new location:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"35_alonso"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:3D:C7:AA:4F:B6   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/100  Signal level=-62 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:0   Missed beacon:66

Regards.

---

### Post by chili555 on 2012-03-29
I assume you mean it's now working perfectly and your wireless interface is now properly named eth1. If so, great! We can now permanently remove the extraneous entries in /etc/udev/rules.d/70-persistent-net.rules```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```Make it look just like this:```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:f0:a0:4d:65", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:b0:76:fe:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```In other words, only eth1/wireless/ipw2200 and eth0/wired ethernet/tg3 remain. Proofread carefully save and close gedit. You should be all set!

---

### Post by palonso53 on 2012-03-29
Here, what I got after rewrite "/etc/udev/rules.d/70-persistent-net.rules" and reboot system:

For "cat /etc/udev/rules.d/70-persistent-net.rules":

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:f0:a0:4d:65", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:b0:76:fe:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
owner@owner-laptop:~$ 

For "dmesg | grep -e eth -e rename":

[    0.072003] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    1.562817] tg3 0000:10:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:0f:b0:76:fe:22
[    1.562824] tg3 0000:10:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.562829] tg3 0000:10:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.562832] tg3 0000:10:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   37.993008] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.640022] eth1: no IPv6 routers present

and,

for "iwconfig":

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"35_alonso"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:3D:C7:AA:4F:B6   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/100  Signal level=-61 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:6  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:69


Well, for me it is working properly. I didn't know if all is named correctly, but one more time I know that Linux is so powerfull I need to envolve more, to learn more.

Thank you chili555 and Ubuntuforum for save me from disaster again.

I have more question but I ask in other time soon.

Best regards.

PD: chili555: waiting for your feedback if any.

---

### Post by praseodym on 2012-03-29
Hi,

to setup a new actual "70-persistent-net.rules"-file you can execute:

```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak [COLOR="Red"]#backup[/COLOR]
sudo udevadm trigger [COLOR="Red"]#setup a new file[/COLOR]
sudo service udev reload [COLOR="Red"]#restart 'udev'[/COLOR]
```

---

