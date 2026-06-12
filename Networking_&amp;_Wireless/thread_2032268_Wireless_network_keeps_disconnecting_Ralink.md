---
title: "Wireless network keeps disconnecting Ralink"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by Avoidencez on 2012-07-23
My wireless connection keeps disconnecting it connects on startup and disconnects again after a short while. and to get it to reconnect agian i have to press the disconnect button on my laptop and push it back on again i have a hp pro book 4330s.

i'm a newbie so i need some help please :)

Information:

**1) Computer brand and model: **
Hp probook 4330s

**2)Wireless Brand, Model and Wireless Chipset:**
24:00.0 Network controller: Ralink corp. Device 3592

**3)Check Interface**
wlan0     Link encap:Ethernet  HWaddr d0:df:9a:1d:3e:29  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d2df:9aff:fe1d:3e29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7464 (7.4 KB)  TX bytes:31988 (31.9 KB

wlan0     IEEE 802.11abgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:93:01:2A   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:47   Missed beacon:0


**4) Check for modules**
Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
arc4                   12473  2 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48805  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
i915                  414703  3 
jmb38x_ms              17406  0 
drm_kms_helper         45466  1 i915
mac_hid                13077  0 
drm                   197692  4 i915,drm_kms_helper
psmouse                72919  0 
i2c_algo_bit           13199  1 i915
serio_raw              13027  0 
video                  19068  1 i915
mei                    36570  0 
memstick               15857  1 jmb38x_ms
cfg80211              178679  2 rt2x00lib,mac80211
soundcore              14635  1 snd
eeprom_93cx6           12653  1 rt2800pci
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci


**5) Kernel boot messages**
[ 3353.172012] cfg80211: World regulatory domain updated:
[ 3353.172016] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3353.172022] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3353.172028] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3353.172033] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3353.172039] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3353.172045] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3355.992410] wlan0: authenticate with 00:1b:11:93:01:2a (try 1)
[ 3356.190994] wlan0: authenticate with 00:1b:11:93:01:2a (try 2)
[ 3356.390698] wlan0: authenticate with 00:1b:11:93:01:2a (try 3)
[ 3356.590294] wlan0: authentication with 00:1b:11:93:01:2a timed out
[ 3368.800541] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**6) Network configuration**
  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: wlan0
       version: 00
       serial: d0:df:9a:1d:3e:29
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-27-generic-pae firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:d4700000-d470ffff


**7) Scan for Networks**
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.


**8) Ubuntu Version**
Description:    Ubuntu 12.04 LTS


**9)Kernel/architecture (including 32 vs. 64 bit): **
3.2.0-27-generic-pae i686

**10) Restarting the Network**
 Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  

**If you need more information please let me know**

---

### Post by praseodym on 2012-07-23
Please check the chipset and the messages:

```
lspci -nnk | grep -iA2 net
rfkill list
dmesg | grep rt2
```

---

### Post by Avoidencez on 2012-07-23
vegard@vegard-HP-ProBook-4330s-LW793ES-UUW:~$ lspci -nnk | grep -iA2 net
24:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]
    Subsystem: Hewlett-Packard Company Device [103c:1638]
    Kernel driver in use: rt2800pci
--
25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:167e]
    Kernel driver in use: r8169
vegard@vegard-HP-ProBook-4330s-LW793ES-UUW:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
vegard@vegard-HP-ProBook-4330s-LW793ES-UUW:~$ dmesg | grep rt2
[   15.582253] rt2800pci 0000:24:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.582267] rt2800pci 0000:24:00.0: setting latency timer to 64
[   15.590747] Registered led device: rt2800pci-phy0::radio
[   15.590781] Registered led device: rt2800pci-phy0::assoc
[   15.590810] Registered led device: rt2800pci-phy0::quality

---

### Post by Avoidencez on 2012-07-24
any suggestions ?

---

### Post by praseodym on 2012-07-24
Try to deactivate the N-mode in your router. Encryption mode to WPA2-AES (CCMP) if possible.

---

### Post by Avoidencez on 2012-07-24
Still having the same problem. did what you said in the post above in the router settings.

---

### Post by NikTh on 2012-07-24
Hi , 
try this 
```
echo 'blacklist hp_wmi' | sudo tee -a /etc/modprobe.d/blacklist.conf 
echo 'rt2800pci nohwcrypt' | sudo tee -a /etc/modules
``` 

Reboot your pc and tell me if works now.. 
If not , we can revert the changes we did , later. 

Thanks

---

### Post by Avoidencez on 2012-07-24
Okey i tried it Nikth but unfortunately for me it did not solve the problem :(

---

### Post by wildmanne39 on 2012-07-24
Hi, please do:
```
sudo rm /etc/modules
```
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci

```
does that help?
Thanks

---

### Post by NikTh on 2012-07-25
Hi , 
indeed i missed this. 
Its nohwcrypt=1 , not only nohwcrypt . Sorry.

Thanks

---

### Post by Avoidencez on 2012-07-25
Okey i did what [[COLOR=#DD4814]**wildmanne39**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533") said and rebooted my computer but the Internet connection still keep on disconnecting

---

### Post by NikTh on 2012-07-25
Hi , 
sometimes its not the wireless or driver that causes the problem , but the channel router transmits. 
Can you go to your router's configuration page and change the channel ? 
I don't know what number (what channel) will be best for you , but you can try some. 

Thanks

---

### Post by wildmanne39 on 2012-07-25
Hi, please post the output of:
```
nm-tool
ndiswrapper -l
lsmod | grep rt2
```
When you cannot connect post:
```
rfkill list all
```
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

