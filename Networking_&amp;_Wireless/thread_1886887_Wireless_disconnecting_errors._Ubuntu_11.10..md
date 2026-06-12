---
title: "Wireless disconnecting errors. Ubuntu 11.10."
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by MeguhNad on 2011-11-25
Hey guys, I would post this in Absolute Beginners talk but it's a Wireless issue, so here goes.

I've recently installed Ubuntu 11.10 and am using a wireless USB adapter (This one [http://www.amazon.co.uk/Belkin-F7D1101ED-Wireless-Adapter-802-11a/dp/B003GALT7O](http://www.amazon.co.uk/Belkin-F7D1101ED-Wireless-Adapter-802-11a/dp/B003GALT7O)) and it's all up and running. However, for the past day, it's been disconnecting from my network from time to time. The disconnects are often for 30 seconds or so, and I can re-connect fine, but as you can imagine, it's really annoying. Does anybody know why this could be? Any help is much appreciated.

---

### Post by praseodym on 2011-11-25
Hi,

do you use mixed WPA/WPA2 encryption? The NetworkManager often has some problems with that. I recommend WPA2-AES, ist safer and more stable. If it doesnt help, please post the terminal (CTRL+ALT+T) outputs of these command lines:
```
lsusb
lsmod
iwconfig
ifconfig -a
```

---

### Post by MeguhNad on 2011-11-25
[praseodym]("http://ubuntuforums.org/member.php?u=1411497"), I think I use WPA/WPA2, yes. How could I change to  WPA2-AES?

Here are my results from the Terminal;

lsusb: 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 006: ID 046d:c30f Logitech, Inc. Logicool HID-Compliant Keyboard (106 key)
Bus 001 Device 004: ID 046d:c041 Logitech, Inc. G5 Laser Mouse
Bus 002 Device 004: ID 050d:945a Belkin Components 
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader

lsmod: Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  7 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_intel          28358  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
r8712u                163310  0 
snd_seq_midi           13132  0 
wmi                    18744  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                63474  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505143  3 
drm_kms_helper         32889  1 i915
drm                   196322  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36466  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25761  1 ahci
r8169                  47200  0 
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


iwconfig:

 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"*********"  Nickname:"*****"
          Mode:Managed  Frequency:2.462 GHz  Access Point: ************* 
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=81/100  Signal level=43/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig -a: 

eth0      Link encap:Ethernet  HWaddr ************
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:******  Mask:***********
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41616 (41.6 KB)  TX bytes:41616 (41.6 KB)

wlan0     Link encap:Ethernet  HWaddr *************
          inet addr:************  Bcast:*************  Mask:***********
          inet6 addr: **********/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69918 errors:0 dropped:6752 overruns:0 frame:0
          TX packets:53661 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99720647 (99.7 MB)  TX bytes:5702037 (5.7 MB)

---

### Post by praseodym on 2011-11-25
You need a firewall? If not (its not neccessary) remove it via:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```
To change the encryption connect via cable (because you are changing sth.) to the router, type the router IP address in your browser and change the encryption mode. IMHO the driver firmware needs to be copied to the "right" place:
```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
sudo service network-manager restart
```
Copy/paste the commands. Check:
```
iwconfig
ifconfig wlan0
sudo iwlist scan #which is your Cell???
dmesg | grep 8712
```

---

### Post by MeguhNad on 2011-11-25
Looks like I do not have  WPA2-AES encryption? 

What did you mean about the firewall?

---

### Post by praseodym on 2011-11-25
If you dont need it you can install it. In Ubuntu 11.10 it is installed by default, but per default all ports are closed in Ubuntu. Please show the terminal outputs (maybe after a reboot).

---

### Post by MeguhNad on 2011-11-25
Sorry, I don't know what you mean about the Terminal? What do you want me to show you? And, if I don't have WPA/EAS encryption, what do I do?

---

### Post by praseodym on 2011-11-25
Copy the firmware
```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  

```
Reboot and show
```
iwconfig
ifconfig wlan0
sudo iwlist scan 
dmesg | grep 8712
```

---

### Post by MeguhNad on 2011-11-25
Okay, what do those commands do?

---

### Post by praseodym on 2011-11-26
The first 2 create a new folder and copy the firmware into it. The others show the configuration

---

