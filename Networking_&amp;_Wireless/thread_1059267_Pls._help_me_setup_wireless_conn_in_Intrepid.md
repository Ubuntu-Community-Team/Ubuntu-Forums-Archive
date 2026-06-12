---
title: "Pls. help me setup wireless conn in Intrepid"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by iClouseau88 on 2009-02-03
Hi,

XP Pro SP3-Ubuntu 8.10 dual-booted Toshiba Satellite Pro4600 laptop.  The laptop  has a DLink WNA-2330 PCMCIA wireless adapter card to connect wirelessly to a DLink DI-624 router, i.e. gets DHCP address from the router.  Wireless connection works fine in Windows.

I installed linux-backports-modules-intrepid, located /etc/modprobe.d then put a comment (#) in front of "blacklist ath5k".  Synaptic Package Manager shows wpasupplicant already installed.

Went to Network Manager -> Edit wireless connection -> Entered data and WPA passphrase.  Rebooted.  Still no wireless connection (cf. wired connection is fine).  It's strange that in Network Manager window, even wired (eth1) connection has the word "never" next to it, as is the case for wireless connection.  Here is what the terminal shows:

hoe1@hoe1-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

ath0      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

hoe1@hoe1-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

ath0      No scan results

eth1      No scan results

pan0      Interface doesn't support scanning.

hoe1@hoe1-laptop:~$ 

Can you help me sort this out?  Thanks a lot for your help!

---

### Post by Metaljaz on 2009-02-03
Try typing lspci in the terminal window and look for
network controller. What is the output?

---

### Post by iClouseau88 on 2009-02-03
Hi, the terminal output is as follows:

hoe1@hoe1-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0c.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
0b:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

---

### Post by Metaljaz on 2009-02-04
Since your wireless adapter is atheros based following the below link for how to install the ath5k module. If you still have trouble post back.

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by iClouseau88 on 2009-02-05
Hi,

Been there,done that.

I typed: sudo gedit /etc/network/interfaces and got the following:

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

I checked and saw that ath5k is active, but somehow don't get ip address, netmask and default gateway under ath0.  What should I do now to get wireless connection?  Pls. note that wired connection is fine under Ubuntu Intrepid.

Thanks a lot for your help.

---

### Post by iClouseau88 on 2009-02-05
Hi again,

Here's the terminal output for "lshw -C network":

 lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:8d:b4:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.101 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:e9:d9:d1:f0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:26:70:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.14 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:61:1c:7f:8d:16
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
hoe1@hoe1-laptop:~$ 


Any suggestions?

---

### Post by iClouseau88 on 2009-02-05
Greetings to all,

PROBLEM SOLVED! (How do I show PROBLEM SOLVED?) 

Here are what I did to get wireless connection:

1) Enable  wireless broadcast in router, otherwise wireless clients cannot pickup radio signal.

2) Turn on wireless switch on the side of the laptop (Duh!)

3) Accessories > Terminal > sudo gedit /etc/network/interfaces

4) These next 2 steps are from debadmin web site (search wpa). Put a comment # sign in front of every line except the first 2 lines of "lo" entry,then hit "Save".

5) sudo gedit /etc/default/wpasupplicant.  In the blank file that will appear, type ENABLED=0 and Save the file.

6) Reboot

7) unplug the CAT5e cable. When you click on the Network Manager icon (mine is a mouse icon!), you will see a menu of wired and wireless connections. Now instead of a mouse icon you will see a stairstep icon (indicating wireless signal strength).

Note that previously,I had done all the preliminary steps such as installing network manager, wpasupplicant, and madwifi (ath5k driver) for wireless to work.

I hope this is helpful.

---

