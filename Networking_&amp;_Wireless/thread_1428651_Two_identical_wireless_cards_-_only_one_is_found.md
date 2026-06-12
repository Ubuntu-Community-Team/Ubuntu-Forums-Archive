---
title: "Two identical wireless cards - only one is found"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by LinuxFan9 on 2010-03-13
Hi there,

there are two idenitical wireless DLink-Cards (Atheros Chipset) in my computer.
Using Linux Mint 8 KDE - Networking-manager-applet only shows one of both cards (using this one without any problems for WLan with WPA) as wlan0 (- XP does show both cards)
How can I use my second card (perhaps as wlan1?? for another wlan??)?

Sincerely,
LinuxFan9

lspci shows:
02:0b.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
02:0d.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

dmesg shows:
ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43) 
[ 30.329893] ath5k phy0: RF2112B 2GHz radio found (0x46) 
[ 30.329927] alloc irq_desc for 21 on node -1 
[ 30.329933] alloc kstat_irqs on node -1 
[ 30.329946] ath5k 0000:02:0d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[ 30.330012] ath5k 0000:02:0d.0: registered as 'phy1' 
[ 30.332365] ath5k phy1: Couldn't identify radio revision. 
[ 30.332393] ath5k 0000:02:0d.0: PCI INT A disabled 

iwconfig shows:
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:"x1e539"
Mode:Managed Frequency:2.457 GHz Access Point: 00:15:0C:7A:8C:BB
Bit Rate=54 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=36/70 Signal level=-74 dBm Noise level=-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
vboxnet0 no wireless extensions.

---

### Post by Iowan on 2010-03-13
Does the other one show up under **ifconfig -a** or **sudo lshw -C network**? 
Historically, NM only enabled one device at a time - although my Jaunty laptop would occasionally connect to my home wired network and my neighbor's wireless concurrently.

---

### Post by LinuxFan9 on 2010-03-13
Hmm,
sudo lshw -C network does show
*-network:1
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: wmaster0
       version: 01
       serial: 00:0f:3d:aa:b9:5d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.178.40 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:f7ee0000-f7eeffff
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: d
       bus info: pci@0000:02:0d.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:f7e90000-f7e9ffff
But -what does that mean?

---

### Post by MarkC502 on 2010-03-13
Do ifconfig -a and it should list not only an wlan0 but also prob a wlan1. If so then wlan1 is just down by default when you boot. If I am right and you see wlan1 then do the following command.

sudo ifconfig wlan1 up


And you should now see wlan1 in your iwconfig output. If so then you can use any manual or GUI based network management tools to configure and use this device with no trouble.

If not then I don't know whats wrong.


Mark

---

### Post by Iowan on 2010-03-14
There's some debate/research as to whether NM still plays nicely with the */etc/network/interfaces* file. IF it does, you should be able to let NM manage the first card and you can configure the second card via */etc/network/interfaces*. I've never used **wicd**, but I've heard it works well. Another option (notice it's last on the list) is to remove NM completely (purge), and set up everything via */etc/network/interfaces*.

---

