---
title: "Kubuntu 4.10 - Installing PCI Wireless Mymax MWA/PCI-150N (Chip RT3060F)???"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by rafaelpasinato on 2011-08-19
Good afternoon, I have a PC with Kubuntu 10.04 and a PCI Wireless Mymax MWA/PCI-150N RT3060F chip, I am not able to install, configure the system, I downloaded the driver on the site [http://www.ralinktech.com/support](http://www.ralinktech.com/support). php? s = 2, RT3062PCI/mPCI/CB/PCIe (RT3060/RT3062/RT3562/RT3592) and follow the procedures but it still fails, the card comes up in the connections but no signal scans.

 Can anyone help me?

 Rafael Passinato

---

### Post by ajgreeny on 2011-08-19
**Kubuntu 4.10???**

Really 4.10, or did you mean 10.04?

If it's really 4.10, I doubt there is much you can do any more, as that version lost its support a long time ago (April 2006).  Try using a later version of (*)ubuntu which may have the wireless driver in the kernel.

---

### Post by rafaelpasinato on 2011-08-20
> **ajgreeny said:**
> **Kubuntu 4.10???**

Really 4.10, or did you mean 10.04?

If it's really 4.10, I doubt there is much you can do any more, as that version lost its support a long time ago (April 2006).  Try using a later version of (*)ubuntu which may have the wireless driver in the kernel.

**Sorry, the version is 10.04.**

---

### Post by praseodym on 2011-08-21
If

```
lspci -nnk | grep -iA2 net
```

shows the product and vendor IDs: 1814:3062 you may install the driver according to [this]("http://forum.ubuntuusers.de/topic/doppelseitiges-problem-wlan-kabel/#post-2739482") guide. The module rt2800pci has to be blacklisted. The drivers from the Realtek-Homepage lack the support for network-manager and wpa_supplicant. The driver in the linked thread was modified in that way (**~/RT2860STA.dat** and **~/os/linux/config.mk** inside of the unpacked folder). You may change the file **~/RT2860STA.dat** to your country code settings (it is modified for Germany there)

---

### Post by rafaelpasinato on 2011-08-22
> **praseodym said:**
> If

```
lspci -nnk | grep -iA2 net
```shows the product and vendor IDs: 1814:3062 you may install the driver according to [this]("http://forum.ubuntuusers.de/topic/doppelseitiges-problem-wlan-kabel/#post-2739482") guide. The module rt2800pci has to be blacklisted. The drivers from the Realtek-Homepage lack the support for network-manager and wpa_supplicant. The driver in the linked thread was modified in that way (**~/RT2860STA.dat** and **~/os/linux/config.mk** inside of the unpacked folder). You may change the file **~/RT2860STA.dat** to your country code settings (it is modified for Germany there)

result:

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Ralink corp. Device [1814:3060]
Subsystem: Ralink corp. Device [1814:3060]
Kernel driver in use: rt2800pci

---

### Post by praseodym on 2011-08-22
Did you install the new driver from that link? Just copy/paste the commands into the terminal:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make uninstall
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
and reboot. If you get a kernel update you have to compile again.
Control:

```
lspci -nnk | grep -iA2 Ralink
lsmod
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by rafaelpasinato on 2011-08-23
> **praseodym said:**
> Did you install the new driver from that link? Just copy/paste the commands into the terminal:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make uninstall
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```and reboot. If you get a kernel update you have to compile again.
Control:

```
lspci -nnk | grep -iA2 Ralink
lsmod
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
rfkill list
```

Good morning, I did the following steps, which do not understand is that the card appears as installed, but no sign scans, by chipset has to change "F" at the end, being "RT3060F" may be the reason for not work properly?
 If you need to get another PCI card, what would it be compatible 150Mbps?

 Thank you.

---

### Post by praseodym on 2011-08-23
Did some errors (not warnings) occur during "sudo make" or "sudo make install". You may try the "classic" debian-way as "root":

```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean
sudo make
sudo make uninstall
sudo make clean
sudo su
make
make install
exit
```and reboot. Controls:

```
lspci -nnk | grep -iA2 Ralink
lsmod
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
```
I dont think the "F" has something to do with it, its all about the Chipset [1814:3060]

---

### Post by rafaelpasinato on 2011-08-23
> **praseodym said:**
> Did some errors (not warnings) occur during "sudo make" or "sudo make install". You may try the "classic" debian-way as "root":

```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean
sudo make
sudo make uninstall
sudo make clean
sudo su
make
make install
exit
```and reboot. Controls:

```
lspci -nnk | grep -iA2 Ralink
lsmod
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
```
I dont think the "F" has something to do with it, its all about the Chipset [1814:3060]

**Warning in sudo make install:**
WARNING: modpost: missing MODULE_LICENSE() in /home/professor/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared/os/linux/rt3562sta.o

```
lspci -nnk | grep -iA2 Ralink
lsmod
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
```

**Result:**
professor@professor-System-Product-Name:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$ lspci -nnk | grep -iA2 Ralink
04:00.0 Network controller [0280]: Ralink corp. Device [1814:3060]
        Subsystem: Ralink corp. Device [1814:3060]
        Kernel driver in use: rt2860
        Kernel modules: rt3562sta, rt2800pci
professor@professor-System-Product-Name:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$ lsmod
Module                  Size  Used by
dm_crypt               22463  0 
snd_hda_codec_via      56765  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
asus_atk0110           17664  0 
parport_pc             32111  1 
snd                    55295  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt3562sta             874110  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
i915                  451068  3 
drm_kms_helper         40745  1 i915
drm                   184164  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
floppy                 60032  0 
video                  18951  1 i915
r8169                  46630  0 
professor@professor-System-Product-Name:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$ dmesg | egrep 'rt2|rt3'                                                                 
[    6.003122] rt3562sta: module license 'unspecified' taints kernel.
[    6.008355] ===> rt2860_probe
[    6.008367] rt2860 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.010096] @rt2860_probe MAC address: 00:06:4f:8e:9a:62
[    6.010097] <=== rt2860_probe
[    7.026635] <==== rt28xx_init, Status=0
[   28.849898] rt28xx_get_wireless_stats --->
[   28.849901] <--- rt28xx_get_wireless_stats
professor@professor-System-Product-Name:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

professor@professor-System-Product-Name:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$ sudo iwlist scan
[sudo] password for professor: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

professor@professor-System-Product-Name:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$

---

### Post by praseodym on 2011-08-23
As you can see, the network interface name changed to "ra0". Try deleting the current wireless profile and set up a new one.

---

### Post by rafaelpasinato on 2011-08-23
> **praseodym said:**
> As you can see, the network interface name changed to "ra0". Try deleting the current wireless profile and set up a new one.

Can you help me in deleting and creating a new profile?

thanks...

---

### Post by praseodym on 2011-08-23
Right-click on the tray icon->Edit connections->wireless

You should know which profile is yours (ESSID and password), mark this connection and delete it (I am a GNOME user, dont know the exact workaround with the KDE-NM, despite in English ;-) ). Then you create a new profile adding your ESSID, password and encryption settings (WPA&WPA2 Personal).

---

### Post by rafaelpasinato on 2011-08-23
> **praseodym said:**
> Right-click on the tray icon->Edit connections->wireless

You should know which profile is yours (ESSID and password), mark this connection and delete it (I am a GNOME user, dont know the exact workaround with the KDE-NM, despite in English ;-) ). Then you create a new profile adding your ESSID, password and encryption settings (WPA&WPA2 Personal).

The process but I still can not connect, does not scan any signs.

You tell me if the DWA-525 PCI Adapter D-Link is compatible with Kubuntu 4.10? And if the compatibility is native or be installed?

thanks

---

### Post by praseodym on 2011-08-23
See here

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

