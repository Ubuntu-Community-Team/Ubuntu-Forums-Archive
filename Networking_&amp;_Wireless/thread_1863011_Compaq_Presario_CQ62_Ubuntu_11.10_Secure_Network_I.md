---
title: "Compaq Presario CQ62 Ubuntu 11.10 Secure Network Issues"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by TehNublet on 2011-10-17
I'm using a Compaq Presario CQ62, and I believe my wireless card is Realtek RTL8191SE 802.11 b/g/n Wifi Adapter. 

The issue i'm encountering is I can't seem to connect a secure wifi network. When I first installed Ubuntu I was at home, and instantly connected to my unsecure home wifi netowrk perfectly, without any problems with stability. Now I'm at a university, where i'm having nonstop Internet issues. There are two networks available here. One is unsecured and for use by guests on campus. I can connect to this one, but it frequently drops the connection. There is also a network to be used by students which is much faster, and I'd like to use it, but I can't connect. 

It shows up in my list of avaiable networks, but when it try to connect it fails after trying to connect for a while. I know for sure that i'm using the right password, because it worked fine in windows. Is there any way i can either make my connection to the open network stable, or connect to the secure wifi network?



sudo lshw -C network 
```
-network               
       description: Wireless interface 
       product: RTL8191SEvA Wireless LAN Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 10 
       serial: 68:a3:c4:74:65:65 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rtl8192se driverversion=3.0.0-12-generic firmware=N/A ip=10.219.54.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:16 ioport:3000(size=256) memory:d3500000-d3503fff 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 2c:27:d7:eb:fd:88 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff 

``` 
 
 
lspci -nnk | grep -iA2 net 
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10) 
    Subsystem: Hewlett-Packard Company Device [103c:1467] 
    Kernel driver in use: rtl8192se 
-- 
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) 
    Subsystem: Hewlett-Packard Company Device [103c:1484] 
    Kernel driver in use: r8169 

```jwconfig 
```
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bgn  ESSID:"csuguest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:30:E5:C1:A1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:1776   Missed beacon:0 

``` 
 
rfkill list all[ 
```
0: hp-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 

``` 
lsmod 
```
 
Module                  Size  Used by 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep 
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp 
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13668  1 snd_hda_codec 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec 
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event 
rtl8192se              99931  0 
rtlwifi               110972  1 rtl8192se 
snd_timer              29991  2 snd_pcm,snd_seq 
mac80211              310872  2 rtl8192se,rtlwifi 
psmouse                73882  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
serio_raw              13166  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
cfg80211              199587  2 rtlwifi,mac80211 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
i915                  566711  3 
drm_kms_helper         42558  1 i915 
drm                   236330  4 i915,drm_kms_helper 
wmi                    19256  1 hp_wmi 
i2c_algo_bit           13423  1 i915 
video                  19412  1 i915 
usbhid                 47198  0 
hid                    95463  1 usbhid 
ahci                   26002  1 
libahci                26861  1 ahci 
r8169                  52788  0 
 

``` 
sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35 
```
 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> (wlan0): supplicant interface state: authenticating -> associating 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> (wlan0): supplicant interface state: associating -> completed 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'csuguest'. 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0] 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds) 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> Activation (wlan0) Beginning IP6 addrconf. 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 18 13:02:48 ubuntu dhclient: Listening on LPF/wlan0/68:a3:c4:74:65:65 
Oct 18 13:02:48 ubuntu dhclient: Sending on   LPF/wlan0/68:a3:c4:74:65:65 
Oct 18 13:02:48 ubuntu dhclient: DHCPREQUEST of 10.219.54.103 on wlan0 to 255.255.255.255 port 67 
Oct 18 13:02:48 ubuntu NetworkManager[798]: <info> (wlan0): DHCPv4 state changed nbi -> preinit 
Oct 18 13:02:50 ubuntu dhclient: DHCPREQUEST of 10.219.54.103 on wlan0 to 255.255.255.255 port 67 
Oct 18 13:02:53 ubuntu dhclient: DHCPREQUEST of 10.219.54.103 on wlan0 to 255.255.255.255 port 67 
Oct 18 13:02:59 ubuntu kernel: [ 7670.448021] wlan0: no IPv6 routers present 
Oct 18 13:03:00 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
Oct 18 13:03:02 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
Oct 18 13:03:05 ubuntu dhclient: DHCPREQUEST of 10.219.54.103 on wlan0 to 255.255.255.255 port 67 
Oct 18 13:03:07 ubuntu dhclient: DHCPREQUEST of 10.219.54.103 on wlan0 to 255.255.255.255 port 67 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> (wlan0): IP6 addrconf timed out or failed. 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled... 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started... 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found) 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5] 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <warn> Activation (wlan0) failed for access point (csuguest) 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <warn> Activation (wlan0) failed. 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete. 
Oct 18 13:03:08 ubuntu NetworkManager[798]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0] 
Oct 18 13:03:09 ubuntu NetworkManager[798]: <info> (wlan0): deactivating device (reason 'none') [0] 
Oct 18 13:03:09 ubuntu NetworkManager[798]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 7434 
Oct 18 13:03:09 ubuntu kernel: [ 7680.010050] wlan0: deauthenticating from 00:0c:85:2f:00:93 by local choice (reason=3) 
Oct 18 13:03:09 ubuntu NetworkManager[798]: <info> (wlan0): supplicant interface state: completed -> disconnected 
 

```

---

### Post by TehNublet on 2011-10-18
Over 24 hours without a reply.

Bump.

---

### Post by Egregious on 2011-10-19
I had this problem too, not sure about a fix. Bumping for you.

---

### Post by TehNublet on 2011-10-19
One final bump before I have to give up and use windows.

---

