---
title: "Intel Corporation PRO/Wireless 3945ABG not working."
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by 1885 on 2012-05-03
I've got a Compaq tc4400 with an Intell 3954ABG wireless that does work.  See the lspci -vv below.
The button on the side does not turn on the wiresless on light. So I don't know if that is bad or not.
Anyway I do have a few of these units working with XUbbunu but this one doesn't  not sure if its:
Hardware, bios or drivers.  Ethernet works.

lspci -vv

10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company Device 135b
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0300c  Data: 4199
    Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [140 v1] Device Serial Number 00-19-d2-ff-ff-47-1b-5e
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

---

### Post by wildmanne39 on 2012-05-03
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by 1885 on 2012-05-04
thanks
```

root@bulldog20:~# cat /etc/lsb-release; uname -a; lspci -nnk | grep -iA2 net ;lsusb ;iwconfig; rfkill list all;lsmod 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux bulldog20 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express [14e4:16fd] (rev 21)
    Subsystem: Hewlett-Packard Company Device [103c:30b1]
    Kernel driver in use: tg3
--
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135b]
    Kernel driver in use: iwl3945
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 003: ID 0566:4002 Monterey International Corp. 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_si3054    12864  1 
snd_hda_codec_analog    75090  1 
snd_atiixp_modem       18604  0 
tpm_infineon           13200  0 
snd_via82xx_modem      18377  0 
snd_intel8x0m          18498  0 
snd_ac97_codec        106082  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
joydev                 17393  0 
ppdev                  12849  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
pcmcia                 39822  0 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tifm_7xx1              12937  0 
tifm_core              15040  1 tifm_7xx1
snd_pcm                80468  7 snd_hda_codec_si3054,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
irda                  185428  0 
crc_ccitt              12595  1 irda
i915                  505108  2 
snd_seq_midi           13132  0 
tpm_tis                14002  0 
snd_rawmidi            25241  1 snd_seq_midi
parport_pc             32114  1 
arc4                   12473  2 
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
snd_seq_midi_event     14475  1 snd_seq_midi
iwl3945                73329  0 
wmi                    18744  1 hp_wmi
iwl_legacy             71499  1 iwl3945
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
mac80211              272785  2 iwl3945,iwl_legacy
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  20 snd_hda_codec_si3054,snd_hda_codec_analog,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
video                  18908  1 i915
snd_page_alloc         14115  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
tg3                   132972  0 
ahci                   21634  2 
libahci                25727  1 ahci

```

---

### Post by wildmanne39 on 2012-05-04
Hi, pleae try:
```
sudo ifconfig wlan0 down
rfkill unblock all
sudo ifconfig wlan0 up
```
then run:
```
rfkill list all
```
and see if the hard black says no instead of yes.
Thanks

---

### Post by 1885 on 2012-05-05
no luck thanks
#ifconfig wlan0 up 
STOCKSIFFLAGS: Operation not possible due to RF-kill

---

### Post by wildmanne39 on 2012-05-05
Hi, please do:
```
gksudo gedit /etc/rc.local
```
Add these three lines above exit 0:
```
rmmod -r iwl3945
rfkill unblock all
modprobe iwl3945
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working now.
Thank you

---

