---
title: "ubuntu 11.10 - RT 2860 CHIP- Wlan no connection HELP PLS"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by quangvinh on 2011-10-20
hello everyone, 
can someone pls help me with my wlan. i have tried to solve the problem for 3 days, but no solution.
it´s my first ubuntu, ubuntu 11.10, so i am pretty new in this field.
i have an Edimax EW 7728 ln Card, which have a RT2860 Chip. the driver is rt2800 i think.
i can connect to my router, but i still dont have connection in firefox. i have to use ubuntu for study, pls help.

Here are some outputs of comandos, which i saw from other posts:



root@ubuntu:/home/quangvinh#** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"VLT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: F0:7D:68:4E:C6:68   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:19  Invalid misc:26   Missed beacon:0

---------------------------------------------------


root@ubuntu:/home/quangvinh#** rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---------------------------------------------------

root@ubuntu:/home/quangvinh# sudo dhclient wlan0
RTNETLINK answers: File exists


---------------------------------------------------


root@ubuntu:/home/quangvinh#** lspci -nnk | grep -iA2 net**
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Edimax Computer Co. Device [1432:7728]
    Kernel driver in use: rt2800pci



---------------------------------------------------


root@ubuntu:/home/quangvinh# **sudo lshw -c network**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:6e:b7:27
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:d800(size=256) memory:d3dff000-d3dfffff memory:d3df8000-d3dfbfff
  *-network
       **description: Wireless interface**
       product: RT2800 802.11n PCI
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:aa:9f:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-12-generic firmware=0.34 ip=192.168.0.105 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:21 memory:f7ff0000-f7ffffff



---------------------------------------------------


root@ubuntu:/home/quangvinh# **lsmod**
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  4 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i7core_edac            27942  0 
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
edac_core              53746  3 i7core_edac
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
psmouse                73882  0 
serio_raw              13166  0 
nouveau               728662  2 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
drm                   236330  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19412  1 nouveau
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech           17677  0 
ff_memless             13097  1 hid_logitech
usbhid                 47198  1 hid_logitech
hid                    95463  2 hid_logitech,usbhid
r8169                  52788  0 
ahci                   26002  0 
libahci                26861  1 ahci
pata_jmicron           12747  0 
xhci_hcd               78641  0 



---------------------------------------------------


root@ubuntu:/home/quangvinh# **cat /var/log/syslog | grep -e wl -e firmware -e wlan0 | tail -n35**
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct 20 21:06:20 ubuntu avahi-daemon[876]: Withdrawing address record for fe80::21f:1fff:feaa:9f8d on wlan0.
Oct 20 21:06:20 ubuntu avahi-daemon[876]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::21f:1fff:feaa:9f8d.
Oct 20 21:06:20 ubuntu avahi-daemon[876]: Interface wlan0.IPv6 no longer relevant for mDNS.
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 20 21:06:20 ubuntu dhclient: Listening on LPF/wlan0/00:1f:1f:aa:9f:8d
Oct 20 21:06:20 ubuntu dhclient: Sending on   LPF/wlan0/00:1f:1f:aa:9f:8d
Oct 20 21:06:20 ubuntu dhclient: DHCPREQUEST of 192.168.0.105 on wlan0 to 255.255.255.255 port 67
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 20 21:06:20 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 20 21:06:20 ubuntu avahi-daemon[876]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.105.
Oct 20 21:06:20 ubuntu avahi-daemon[876]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 21:06:20 ubuntu avahi-daemon[876]: Registering new address record for 192.168.0.105 on wlan0.IPv4.
Oct 20 21:06:21 ubuntu NetworkManager[898]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 20 21:06:21 ubuntu NetworkManager[898]: <info> Policy set 'VLT' (wlan0) as default for IPv4 routing and DNS.
Oct 20 21:06:21 ubuntu NetworkManager[898]: <info> Activation (wlan0) successful, device activated.
Oct 20 21:06:21 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 20 21:06:21 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 20 21:06:21 ubuntu avahi-daemon[876]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21f:1fff:feaa:9f8d.
Oct 20 21:06:21 ubuntu avahi-daemon[876]: New relevant interface wlan0.IPv6 for mDNS.
Oct 20 21:06:21 ubuntu avahi-daemon[876]: Registering new address record for fe80::21f:1fff:feaa:9f8d on wlan0.*.
Oct 20 21:06:30 ubuntu kernel: [ 4865.440003] wlan0: no IPv6 routers present
Oct 20 21:06:40 ubuntu NetworkManager[898]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct 20 21:06:40 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Oct 20 21:06:40 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Oct 20 21:06:40 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 20 21:06:40 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 20 21:06:40 ubuntu NetworkManager[898]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.

---

### Post by quangvinh on 2011-10-21
nobody can help me? alternativ i have a fritz wlan usb stick, but i dont know how to use it in linux

---

### Post by Frank Sullivan on 2011-10-21
I too have lost my Mobile Broadband connectivity after upgrading of Ubuntu 11.10
I had been using Sakis3g successfully for months but it seems to have "broken" under
the new release.  I also note that in the Network Manager, the Wireless Networks entry
now states "Wireless is disabled by hardware switch", while under Ubuntu 11.04  the
Vodafone  K3806-z key appeared (disabled)  in the Network Manager Menu.

The seemingly most relevant line of   lsusb   gives 

Bus 002 Device 003: ID 19d2:1013 ONDA Communication S.p.A. 

At present Sakis3g now succeeds in "switching" the modem but not in setting it up
or "preparing" it.  Before my upgrade to Ubuntu 11.10  this Sakis3g  worked more or 
less transparently  (i.e. all I had to do was say I wanted to
use the modem in 3G model, and tell Sakis3g via my configuration file
what the APN was, etc.

Here is the Sakis3g    message on requesting compilation of usb-modeswitch:

Header file usb.h missing from your system. This usually indicates libusb (or libusb-compat) development kit missing. 

Perhaps I should do a re-install of Sakis3g  ?     I have been following this thread with great interest (and gratitude to those helping to solve this problem).

---

### Post by Kisil on 2011-11-29
I have the same chip, and I had the same problem you describe - I'm connected, assigned an IP by my router, and have no connectivity. Booting with a 2.6.38-11 kernel instead of 3.0.0.12/13 fixed this for me.

If anyone who reads this knows how I can help debug this regression, please let me know.

---

