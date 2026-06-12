---
title: "rtl8188ce wifi adapter is not detected after installing newest realtek driver"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by MeiSign on 2013-02-25
I have the following problem. Since I installed a kernel update yesterday on my ubuntu 12.10 I thought I might check if there is a new realtek driver too for my wifi(8188ce chip is still very unstable in ubuntu).

What i found was a driver released on the 7th of February this year. I downloaded and installed the driver with the result that my wireless adapter ist not recognized by the system anymore. ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722))

After untaring it I installed it like that:
```
sudo make
sudo make install
sudo reboot
```

So to resolve that issue I deinstalled it again with:
```
sudo make uninstall
```

But unfortunately my wireless adapter is still unrecognized. I even tried to install the older driver again in the same way but nothing changed.

Any ideas on that problem? I hope I didnt wrecked my wifi adapter.
```
lspci | grep wifi
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

---

### Post by ahallubuntu on 2013-02-25
~

---

### Post by MeiSign on 2013-02-25
Sudo make
```
meisign@stefan-TPad:~/Downloads$ cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
meisign@stefan-TPad:~/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ sudo make
[sudo] password for meisign: 
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
meisign@stefan-TPad:~/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$
```

Sudo make install
```
meisign@stefan-TPad:~/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ sudo make install
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
make[1]: Entering directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
make -C /lib/modules/3.5.0-25-generic/build M=/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Leaving directory `/home/meisign/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
find /lib/modules/3.5.0-25-generic -name "r8192se_*.ko" -exec rm {} \;
find /lib/modules/3.5.0-25-generic -name "r8192ce_*.ko" -exec rm {} \;
find /lib/modules/3.5.0-25-generic -name "r8723e_*.ko" -exec rm {} \;
find /lib/modules/3.5.0-25-generic -name "r8188ee_*.ko" -exec rm {} \;

```

Interesting is maybe this one, I just tried that:
```
sudo modprobe rtl8192ce 
FATAL: Error inserting rtl8192ce (/lib/modules/3.5.0-25-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko): Invalid argument
```

sudo lshw -C network
```
 *-network UNCLAIMED     
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:39:d4:cd
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=172.16.0.152 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:41 ioport:3000(size=256) memory:f0804000-f0804fff memory:f0800000-f0803fff memory:f0820000-f083ffff
```

lsmod
```
Module                  Size  Used by
compat                 14950  0 
pci_stub               12623  1 
vboxpci                23195  0 
vboxnetadp             25671  0 
vboxnetflt             23480  0 
vboxdrv               287190  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               23012  1 
btusb                  22475  0 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
uvcvideo               76750  0 
snd_hda_codec_hdmi     32049  1 
videobuf2_core         32852  1 uvcvideo
snd_hda_codec_conexant    57802  1 
thinkpad_acpi          81199  0 
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
microcode              22804  0 
snd_seq_midi           13325  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_rawmidi            30513  1 snd_seq_midi
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_seq_midi_event     14900  1 snd_seq_midi
rfcomm                 46620  0 
joydev                 17458  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
bnep                   18141  2 
snd_hwdep              17699  1 snd_hda_codec
rtlwifi               123325  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             209249  11 btusb,rfcomm,bnep
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
parport_pc             32689  0 
mac80211              540032  1 rtlwifi
ppdev                  17074  0 
psmouse                95595  0 
serio_raw              13216  0 
cfg80211              206797  2 rtlwifi,mac80211
snd_timer              29426  2 snd_seq,snd_pcm
lpc_ich                17062  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
intel_ips              18244  0 
mei                    40691  0 
snd                    78921  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_seq,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
binfmt_misc            17501  1 
soundcore              15048  1 snd
nvram                  14363  1 thinkpad_acpi
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
vesafb                 13798  0 
hid_generic            12541  0 
i915                  520615  8 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
drm_kms_helper         49113  1 i915
r8169                  61651  0 
ums_realtek            17950  0 
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
video                  19391  1 i915
usb_storage            48839  1 ums_realtek

```

---

### Post by ahallubuntu on 2013-02-25
~

---

### Post by MeiSign on 2013-02-25
Edit:
I finally found the problem. Thank you for your help ahallubuntu. You had the right idea. The file iwlwifi.conf still had an entry in it which disabled the powersavingmode for the chip. Probably this option is no longer valid.

But what i dont understand is why I couldnt install the old driver again...

---

No that file does not exist:
```
meisign@stefan-TPad:~/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ cd /etc/modprobe.d/
meisign@stefan-TPad:/etc/modprobe.d$ ls -la
total 60
drwxr-xr-x   2 root root  4096 Feb 26 11:18 .
drwxr-xr-x 158 root root 12288 Feb 26 10:42 ..
-rw-r--r--   1 root root  2507 Oct  8 09:34 alsa-base.conf
-rw-r--r--   1 root root   325 Mar 19  2011 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Mar 19  2011 blacklist.conf
-rw-r--r--   1 root root   210 Mar 19  2011 blacklist-firewire.conf
-rw-r--r--   1 root root   677 Oct  1 21:26 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Oct  8 09:34 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Jan 15 22:38 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Mar 19  2011 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Mar 19  2011 blacklist-watchdog.conf
-rw-r--r--   1 root root   127 Jul 26  2012 dkms.conf
-rw-r--r--   1 root root   347 Oct  1 21:26 iwlwifi.conf
-rw-r--r--   1 root root    30 Aug  2  2012 vmwgfx-fbdev.conf
meisign@stefan-TPad:/etc/modprobe.d$ 

```

---

