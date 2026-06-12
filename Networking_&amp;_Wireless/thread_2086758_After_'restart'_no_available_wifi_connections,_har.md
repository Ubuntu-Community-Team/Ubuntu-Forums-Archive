---
title: "After 'restart' no available wifi connections, hard boot works fine?"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by mate85 on 2012-11-21
I am running 12.10 and the infamous rtl8723e - how ever I believe this is not driver related, once it's working it works fine with network-manager. 

If I shut down with the rtl8723e (working or not) in ubuntu, there is no issue once I boot back up. If I shut down or restart in windows (working or not), it works fine upon next boot.

If the card is working and I 'restart' in ubuntu, the card loses functionality. Even if after 'restarting' if I choose Windows from grub, the problem persists in windows. The OS can see the card, but no networks are available, cannot force a connection or a scan.

I did a lot of trouble shooting and searching, but I need some help.

> 'cat /etc/lsb-release; uname -a'

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux ubuntu 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux> 'lspci -nnk | grep -iA2 net'

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:7102]
    Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723e> 'lsusb'

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1532:0013 Razer USA, Ltd 
Bus 002 Device 003: ID 147e:1002 Upek> 'ifconfig'

eth0      Link encap:Ethernet  HWaddr 00:90:f5:d0:f2:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6672 (6.6 KB)  TX bytes:6672 (6.6 KB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:52:b9:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)> 'rfkill list all'

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no> 'lsmod'

Module                  Size  Used by
nls_iso8859_1          12713  1 
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               287189  3 vboxpci,vboxnetadp,vboxnetflt
bbswitch               13396  0 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
bnep                   18140  2 
rfcomm                 46619  12 
parport_pc             32688  0 
ppdev                  17073  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
binfmt_misc            17500  1 
arc4                   12529  2 
mxm_wmi                12979  0 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
microcode              22803  0 
joydev                 17457  0 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
btusb                  18334  0 
bluetooth             209199  22 bnep,rfcomm,btusb
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtl8723e              175666  0 
mac_hid                13205  0 
wmi                    19070  1 mxm_wmi
rtlwifi               118726  1 rtl8723e
i915                  520629  3 
psmouse                95552  0 
mac80211              539908  2 rtl8723e,rtlwifi
drm_kms_helper         46784  1 i915
serio_raw              13215  0 
rts_bpp               369611  1 
lpc_ich                17061  0 
drm                   275528  4 i915,drm_kms_helper
cfg80211              206566  2 rtlwifi,mac80211
i2c_algo_bit           13413  1 i915
video                  19335  1 i915
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
firewire_ohci          40401  0 
r8169                  61650  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core> 'nm-tool'

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723e
  State:             disconnected
  Default:           no
  HW Address:        44:6D:57:52:B9:47

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:90:F5:D0:F2:55

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
Please let me know what else you may need to see, the above outputs are when the wifi is unavailable.

When the wifi is working lsmod is slightly different
> 
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19070  1 mxm_wmi
i915                  520629  3 
mac_hid                13205  0 
rtl8723e              175666  0 
rtlwifi               118726  1 rtl8723e
mac80211              539908  2 rtl8723e,rtlwifi
drm_kms_helper         46784  1 i915
rts_bpp               369611  1 
drm                   275528  4 i915,drm_kms_helper
lpc_ich                17061  0 
i2c_algo_bit           13413  1 i915
cfg80211              206566  2 rtlwifi,mac80211

---

### Post by mate85 on 2012-11-23
I have tried both drivers that are available, I have also tried removing and adding the driver also restarting the service when the card is non-operational.

Nothing I do seems to get a response from the card.

Any idea guys? Is there a different script that runs when when you reboot vs shutdown?

---

### Post by mate85 on 2012-11-24
Like other issues with network-manager, Wicd seems to be the solution.

Any idea how I can get Wicd to connect to a network on startup like nm can?

It starts and auto connects when I log in, but I noticed there is no longer a remote login option, nor is the tray icon available.

---

### Post by mate85 on 2012-11-25
Looks like the 12.10 Remote Desktop @ login screen feature depends on network-manager, so it is installed again.

Went back and set up wpa_supplicant and used wpa-roam in /etc/network/interfaces, no biggie there. This seems to prevent my 'restart' issue, as I am usually connecting to a known network.

Wicd is nice, but I have no use for it I guess. If I need to scan and join a new network I can just use nm, then add it to wpa_supplicant with wpa_gui.

---

