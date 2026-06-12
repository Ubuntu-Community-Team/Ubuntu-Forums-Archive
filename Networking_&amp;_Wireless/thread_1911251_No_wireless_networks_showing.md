---
title: "No wireless networks showing?"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by BenFlowers on 2012-01-18
Hi,
I've just made a move to ubuntu from W7. 
I cannot get my wireless card to work and i have no idea why.
Its a ralink card and the current driver is rt2800pci.

here is nm-tool output:

- Device: wlan0 ----------------------------------------…
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        C8:3A:35:C6:44:C6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


does anyone know what i need to do?
Thanks,
Ben

---

### Post by praseodym on 2012-01-18
Hi,

do you have any more info about your hardware? Please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by BenFlowers on 2012-01-19
Hi,
Thanks for the response. The output of the commands are as follows.
Cheers,
Ben

```
$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169
--
09:02.0 Network controller [0280]: Ralink corp. Device [1814:3062]
    Subsystem: Ralink corp. Device [1814:3062]
    Kernel driver in use: rt2800pci

``````

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 0b05:179c ASUSTek Computer, Inc. 


``````

$ lsmod
Module                  Size  Used by
btusb                  18600  2 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_hdmi     32040  4 
bnep                   18436  2 
rfcomm                 47946  8 
bluetooth             166112  23 btusb,bnep,rfcomm
ath3k                  13195  0 
joydev                 17693  0 
nvidia              11713772  40 
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
rt2800pci              18715  0 
binfmt_misc            17540  1 
rt2800lib              54538  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
snd_hda_intel          33390  3 
eeepc_wmi              12826  0 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
asus_wmi               20035  1 eeepc_wmi
mac80211              462092  3 rt2800lib,rt2x00pci,rt2x00lib
sparse_keymap          13890  1 asus_wmi
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              199587  2 rt2x00lib,mac80211
psmouse                73882  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13166  0 
eeprom_93cx6           12725  1 rt2800pci
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 asus_wmi
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  1 
libahci                26861  1 ahci
r8169                  52788  0 
xhci_hcd               82820  0 


``````

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
``````
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````

$ sudo iwlist scan
[sudo] password for benflowers: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

``````

$ dmesg | grep rt2
[    2.871069] rt2800pci 0000:09:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.885277] Registered led device: rt2800pci-phy0::radio
[    2.885289] Registered led device: rt2800pci-phy0::assoc
[    2.885302] Registered led device: rt2800pci-phy0::quality
[    3.289523] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

```

---

### Post by praseodym on 2012-01-19
Try this driver instead (wired needed):

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot, and check:

```
uname -a
dmesg | grep rt3
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by BenFlowers on 2012-01-22
Yeah thats got it working!
Thanks very much your my hero!
-Ben

---

### Post by dave0109 on 2012-01-27
The solution posted in #4 also worked for me on a new build, which has a rebranded "Addon PCI wireless" card, which shows up as a "Ralink corp" card and by default had loaded the "rt2800pci" driver.  This was on Xubuntu 11.10 with all latest updates having already been applied.

Firstly, thankyou for the solution.

Secondly, can someone help me understand why it's necessary to get and build some 14-month old code?  Any reason this isn't anywhere that the "additional drivers" utility couldn't find?

---

