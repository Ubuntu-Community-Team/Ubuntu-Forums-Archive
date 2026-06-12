---
title: "Wireless Not Detected after suspend mode"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by Healinghands on 2012-06-27
My wireless is not detected after I resume from being in 
suspend mode.   I have to reboot for Ubuntu 12.04 to see 
my wireless card.
  Any suggestions on how to fix this issue?

---

### Post by wildmanne39 on 2012-06-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Healinghands on 2012-06-28
Linux james-Satellite-Pro-A200 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Subsystem: Toshiba America Info Systems Device [1179:ff10]
    Kernel driver in use: sky2
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1040]
    Kernel driver in use: iwl3945




Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




Module                  Size  Used by
xt_limit               12541  0 
xt_tcpudp              12531  0 
ipt_LOG                12783  0 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  0 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  0 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
iptable_nat            13016  0 
nf_nat                 24959  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           73847  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  0 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21974  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
pcmcia                 39791  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
tifm_7xx1              12937  0 
tifm_core              15040  1 tifm_7xx1
binfmt_misc            17292  1 
arc4                   12473  2 
iwl3945                73152  0 
iwl_legacy             71134  1 iwl3945
psmouse                72919  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13027  0 
mac80211              436455  2 iwl3945,iwl_legacy
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414663  3 
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  1 toshiba_acpi
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
sky2                   53628  0

---

### Post by wildmanne39 on 2012-06-28
Hi, please do:
```
gksudo gedit /etc/pm/config.d/config
```
Add one line:
```
SUSPEND_MODULES="iwl3945"
```
Proofread, save, then close gedit.
Reboot
Thanks

---

### Post by Healinghands on 2012-06-28
Thank I will try that tonite 
  I will report back with the results.
  Thank you for your help and time.

---

### Post by Healinghands on 2012-06-28
I just got home added the code in the file rebooted and I 
am sorry to inform you that the problem has not been resolved.

---

### Post by wildmanne39 on 2012-06-28
Hi, please post the contents of:
```
gksudo gedit /etc/pm/config.d/config
```
Thanks

---

### Post by Healinghands on 2012-06-28
SUSPEND_MODULES="iwl3945"

---

### Post by wildmanne39 on 2012-06-28
Hi, after you suspend your computer and before you connect the wireless again please post the output of:
```
rfkill list all
lsmod | grep iwl
dmesg | egrep 'iwl|firm|etork|wlan0'
```
Thanks

---

### Post by Healinghands on 2012-06-28
rfkill list all 
IT did nothing when I hit enter..

lsmod | grep iwl
iwl3945                73152  0 
iwl_legacy             71134  1 iwl3945
mac80211              436455  2 iwl3945,iwl_legacy
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211


dmesg | egrep 'iwl|firm|etork|wlan0'


iwl3945                73152  0 
iwl_legacy             71134  1 iwl3945
mac80211              436455  2 iwl3945,iwl_legacy
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
james@james-Satellite-Pro-A200:~$ ^C
james@james-Satellite-Pro-A200:~$ ^C
james@james-Satellite-Pro-A200:~$ dmesg | egrep 'iwl|firm|etork|wlan0'
[   25.679038] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   25.679041] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   25.679114] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.679130] iwl3945 0000:03:00.0: setting latency timer to 64
[   25.735618] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   25.735622] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   25.735779] iwl3945 0000:03:00.0: irq 47 for MSI/MSI-X
[   25.767007] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   26.584536] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   26.655104] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.655638] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.053142] iwl3945 0000:03:00.0: PCI INT A disabled
[  150.959934] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  150.959938] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  150.960028] iwl3945 0000:03:00.0: enabling device (0000 -> 0002)
[  150.960042] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  150.960063] iwl3945 0000:03:00.0: setting latency timer to 64
[  150.964015] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  150.989075] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  151.010811] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  151.032499] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  151.054216] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  151.075911] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  151.093624] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
[  151.093627] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[  151.093660] iwl3945 0000:03:00.0: Unable to init EEPROM
[  151.096088] iwl3945 0000:03:00.0: PCI INT A disabled
[  151.096104] iwl3945: probe of 0000:03:00.0 failed with error -2
[  208.835229] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  208.835233] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  208.835309] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  208.835331] iwl3945 0000:03:00.0: setting latency timer to 64
[  208.836011] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  208.861105] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  208.882854] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  208.904545] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  208.926230] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  208.947931] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  208.965648] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
[  208.965652] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[  208.965686] iwl3945 0000:03:00.0: Unable to init EEPROM
[  208.965737] iwl3945 0000:03:00.0: PCI INT A disabled
[  208.965753] iwl3945: probe of 0000:03:00.0 failed with error -2
[  456.970086] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  456.970089] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  456.970160] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  456.970181] iwl3945 0000:03:00.0: setting latency timer to 64
[  456.972009] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  456.996007] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  457.017699] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  457.039375] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  457.061047] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  457.082733] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  457.100432] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
[  457.100436] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[  457.100469] iwl3945 0000:03:00.0: Unable to init EEPROM
[  457.105625] iwl3945 0000:03:00.0: PCI INT A disabled
[  457.105642] iwl3945: probe of 0000:03:00.0 failed with error -2
[  607.118943] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  607.118947] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  607.119018] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  607.119039] iwl3945 0000:03:00.0: setting latency timer to 64
[  607.120012] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  607.144811] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  607.166585] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  607.188309] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  607.210017] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  607.231729] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  607.249450] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
[  607.249454] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[  607.249488] iwl3945 0000:03:00.0: Unable to init EEPROM
[  607.249529] iwl3945 0000:03:00.0: PCI INT A disabled
[  607.249547] iwl3945: probe of 0000:03:00.0 failed with error -2
[  759.396324] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  759.396328] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  759.396996] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  759.397017] iwl3945 0000:03:00.0: setting latency timer to 64
[  759.400011] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  759.422795] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  759.444556] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  759.466267] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  759.487965] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  759.509667] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[  759.527402] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
[  759.527406] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[  759.527439] iwl3945 0000:03:00.0: Unable to init EEPROM
[  759.528064] iwl3945 0000:03:00.0: PCI INT A disabled
[  759.528079] iwl3945: probe of 0000:03:00.0 failed with error -2

---

### Post by wildmanne39 on 2012-06-28
Hi, please do:
```
gksudo gedit /etc/modprobe.d/50-iwl3945.conf
```
add one line:
```
options iwl3945 debug=10 disable_hw_scan=0 swcrypto=1
```
save and close gedit then reboot.
Thanks

---

### Post by Healinghands on 2012-06-29
No Luck

  I added in the code.....
   Reboot, then the wireless was disabled.. 
  Then I connected Thru LAN   went to the   
50-iwl3945.conf 
  Then I deleted the line you told me to add.

  Rebooted then wireless works now.

  Thank you for your help..

---

