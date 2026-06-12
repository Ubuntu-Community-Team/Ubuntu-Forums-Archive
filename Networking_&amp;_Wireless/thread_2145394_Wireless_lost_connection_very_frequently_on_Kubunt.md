---
title: "Wireless lost connection very frequently on Kubuntu 13.04 on Lenovo E49"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by coolcolgeboy on 2013-05-15
I just bought a new lenovo laptop E49 and wireless is working excellent on Windows 7. 

But as soon as i switch to Kubuntu 13.04. Wireless connection starts fluctuating and as the distance is increased by 5m, it is completely lost but works fine on Windows then also 

OS details :-

Linux mohit-lappy 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Network Hardware Details :-

mohit@mohit-lappy:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:dc500000-dc503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 07
       serial: 3c:97:0e:68:c3:11
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.22.13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:44 ioport:2000(size=256) memory:dbc04000-dbc04fff memory:dbc00000-dbc03fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 08:3e:8e:a5:43:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-19-generic firmware=N/A ip=192.168.23.83 link=yes multicast=yes wireless=IEEE 802.11bgn

It seems to me that it is not using the default network card and instead using some inbuilt wireless interface. But, i am not sure how to resolve it. Please suggest

---

### Post by praseodym on 2013-05-15
Install the missing firmware for the driver:
```

wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Shutdown, remove any current for 10 minutes and reboot.

---

### Post by coolcolgeboy on 2013-05-15
updated firmware version, still experiencing same problem.

---

### Post by praseodym on 2013-05-16
Check:
```

lsmod
iwconfig
rfkill list
route -n
cat /etc/resolv.conf
dmesg | egrep 'bcma|brcm|wlan0|reason'
```

---

### Post by coolcolgeboy on 2013-05-28
i dont' get what i am supposed to do. 

Anyways output of each of the command is as follows 

mohit@mohit-myntra:~$ lsmod
Module                  Size  Used by
btusb                  22474  0 
nls_iso8859_1          12713  0 
usb_storage            57204  0 
ppp_deflate            12950  0 
zlib_deflate           26885  1 ppp_deflate
bsd_comp               12921  0 
ppp_async              17413  1 
crc_ccitt              12707  1 ppp_async
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
bluetooth             228619  22 bnep,btusb,rfcomm
binfmt_misc            17500  1 
joydev                 17377  0 
arc4                   12615  2 
snd_hda_codec_hdmi     36913  1 
coretemp               13355  0 
snd_hda_codec_realtek    78399  1 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
brcmsmac              550698  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_midi           13324  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         40513  1 uvcvideo
snd_rawmidi            30180  1 snd_seq_midi
videodev              129260  2 uvcvideo,videobuf2_core
thinkpad_acpi          81222  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
nvram                  14362  1 thinkpad_acpi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
b43                   378642  0 
bcma                   41051  2 b43,brcmsmac
mac80211              606457  2 b43,brcmsmac
mac_hid                13205  0 
cfg80211              510937  3 b43,brcmsmac,mac80211
psmouse                95870  0 
snd                    68876  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
serio_raw              13215  0 
ssb                    56748  1 b43
mei                    41158  0 
lpc_ich                17061  0 
rtsx_pci_ms            13011  0 
microcode              22881  0 
soundcore              12680  1 snd
memstick               16554  1 rtsx_pci_ms
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         17475  0 
nouveau               939088  1 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
i915                  600351  3 
r8169                  67446  0 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
ttm                    83187  1 nouveau
ahci                   25731  4 
libahci                31364  1 ahci
video                  19390  2 i915,nouveau
i2c_algo_bit           13413  2 i915,nouveau
drm_kms_helper         49394  2 i915,nouveau
drm                   286313  7 ttm,i915,drm_kms_helper,nouveau

mohit@mohit-myntra:~$ iwconfig
ppp0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"FireInTheHole"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 94:D7:23:66:CF:E4   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/70  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:138  Invalid misc:608   Missed beacon:0

mohit@mohit-myntra:~$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

mohit@mohit-myntra:~$ cat /etc/resolv.conf
nameserver      192.168.20.4
nameserver      4.2.2.2
nameserver      192.168.20.4
nameserver      4.2.2.2
nameserver      192.168.20.4
nameserver      4.2.2.2
nameserver      192.168.20.4
nameserver      4.2.2.2
nameserver      192.168.20.4
nameserver      4.2.2.2
nameserver      192.168.20.4
nameserver      4.2.2.2
domain mynt.myntra.com
search mynt.myntra.com
nameserver 192.168.20.4
nameserver 4.2.2.2

dmesg | egrep 'bcma|brcm|wlan0|reason command gives this repeated all the  time

[78403.229469] wlan0: authenticate with 94:d7:23:66:cf:e4
[78403.231097] wlan0: send auth to 94:d7:23:66:cf:e4 (try 1/3)
[78403.232508] wlan0: authenticated
[78403.232705] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[78403.232707] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[78403.236673] wlan0: associate with 94:d7:23:66:cf:e4 (try 1/3)
[78403.239051] wlan0: RX AssocResp from 94:d7:23:66:cf:e4 (capab=0x411 status=0 aid=7)
[78403.239848] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[78403.239854] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[78403.239857] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[78403.239870] wlan0: associated
[78407.614841] wlan0: deauthenticated from 94:d7:23:66:cf:e4 (Reason: 1)
[78407.619060] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[78407.619073] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[78407.619077] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)

Please suggest

---

### Post by praseodym on 2013-05-28
There is a wrong driver loaded:
```

echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by coolcolgeboy on 2013-06-06
Hi praseodym,

Thanks for your help so far. I think i might have found the problem but not the solution. So here is the output of lshw -C network

  *-network               
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:dc500000-dc503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 07
       serial: 3c:97:0e:68:c3:11
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:dbc04000-dbc04fff memory:dbc00000-dbc03fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 08:3e:8e:a5:43:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-23-generic firmware=N/A ip=192.168.1.10 link=yes multicast=yes wireless=IEEE 802.11bgn

as you can see we are having three network instead of two. So, when i tried to remove brcmsmac module using command 

sudo modprobe -r brcmsmac

it was successfully removed. Then, when i tried to activate module for broadcomm hardware i.e. bcma-pci-bridge, it gave following error,

sudo modprobe bcma-pci-bridge
FATAL: Module bcma-pci-bridge not found.

Any ideas on how to activate this module or use some alternative module for broadcomm wireless hardware

---

### Post by coolcolgeboy on 2013-06-06
Finally, i was able to resolve it. I followed following steps for BCM4313 wireless

1. Run  lsmod | grep "b43\|ssb\|bcma\|wl" check the output whether it contains wl and / or bcma, ssb, b43

2. If it does not contain wl install it using following steps

sudo apt-get install --reinstall bcmwl-kernel-source
sudo apt-get install wl

3. If it contains bcma, b43 or ssb, disable these using 

sudo modprobe -r brcmsmac
sudo modprobe -r bcma
sudo modprobe -r b43

4. Enable wl using

sudo modprobe wl

5. Blacklist others so that they won't be loaded at startup using command given by praseodym

echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf

Once again, thanks a lot for help praseodym.

---

