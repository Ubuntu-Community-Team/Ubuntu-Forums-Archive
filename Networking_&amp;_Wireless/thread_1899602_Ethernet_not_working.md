---
title: "Ethernet not working"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by olwe on 2011-12-23
I'm on a Thinkpad T400 with 11.04 and Gnome classic. The icon for Internet allows me to edit connection. The Network Connections dialog box has a tab for Wired and lists "Auto eth1". Doing "ifconfig eth1" gives me the driver and the MAC address. These seem correct. I have no probs with wireless, but can't get the wired to work. I would be on a standard Auto DHCP. How can I get wired to work?

---

### Post by praseodym on 2011-12-24
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/network/interfaces
```

---

### Post by collisionystm on 2011-12-24
also post the full output of

lspci

just in case.

---

### Post by olwe on 2011-12-24
>lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
        Subsystem: Lenovo Device [17aa:20ee]
        Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
        Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
        Kernel driver in use: iwlagn

> lsmod
Module                  Size  Used by
snd_hrtimer            12744  1 
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
x_tables               29846  2 iptable_filter,ip_tables
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_conexant    62197  1 
joydev                 17693  0 
binfmt_misc            17540  1 
arc4                   12529  2 
pcmcia                 49378  0 
psmouse                73882  0 
serio_raw              13166  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
thinkpad_acpi          81819  0 
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
nvram                  14413  1 thinkpad_acpi
iwlagn                314213  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
i915                  566827  2                                                                                                                          
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq                                                                                              
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq                                                                                         
tpm_tis                18546  0                                                                                                                          
mac80211              462092  1 iwlagn
wmi                    19256  0 
cfg80211              199587  2 iwlagn,mac80211
snd                    68266  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
mei                    41480  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
ahci                   26002  2 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
libahci                26861  1 ahci
e1000e                160582  0 

> ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:24:7e:6c:66:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1973 (1.9 KB)  TX bytes:1973 (1.9 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1e:65:30:cc:12  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe30:cc12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2869204 (2.8 MB)  TX bytes:3077971 (3.0 MB)


> cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:37:82:38:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:bf:55:da:f0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x10f5 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:7e:6c:66:d9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x4237 (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:65:30:cc:12", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


> cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:37:82:38:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:bf:55:da:f0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x10f5 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:7e:6c:66:d9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x4237 (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:65:30:cc:12", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
olwe> cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by praseodym on 2011-12-24
For the driver e1000e see here:

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

You can also/additionally try to remove the firewall/iptables:

```
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by olwe on 2011-12-24
Sorry these steps did not work. Any other ideas?

---

### Post by praseodym on 2011-12-25
Checkbox all user rights in "USERS&GROUPS", login again, checkbox  "available to all users" and "connect automatically", remove the wired profile, and reboot.

---

