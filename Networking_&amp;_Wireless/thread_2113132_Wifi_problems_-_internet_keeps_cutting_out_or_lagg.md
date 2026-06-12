---
title: "Wifi problems - internet keeps cutting out or laggs"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by littlealien on 2013-02-06
Hi!
I never had wifi problems on windows, but on after installing linux (12.10) on my laptop along windows I am now experiencing very serious wifi problems.

Basically, internet works, but keeps cutting off and disconnecting every 5 or 10 minutes. Sometimes its connected, but pages just take ages to load. I have fiber optics internet  and all other computers and internet enabled devices dont have any problems at all. I tried disabling firewalls and even using a different routers but nothing helps. I think it must be a driver issue.

Here is some info:

lspci output:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```lsmod output:
```
Module                  Size  Used by
snd_hda_codec_realtek    77876  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
arc4                   12529  2 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
microcode              22803  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
joydev                 17457  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
rtl8192ce              53594  0 
rtl8192c_common        48779  1 rtl8192ce
rtlwifi                74705  1 rtl8192ce
mac80211              539908  3 rtl8192ce,rtl8192c_common,rtlwifi
snd                    78734  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                95552  0 
serio_raw              13215  0 
toshiba_acpi           18726  0 
sparse_keymap          13890  1 toshiba_acpi
wmi                    19070  1 toshiba_acpi
intel_ips              18049  0 
cfg80211              206566  2 rtlwifi,mac80211
lpc_ich                17061  0 
soundcore              15047  1 snd
i915                  520519  3 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
video                  19335  1 i915
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
r8169                  61650  0 
ums_realtek            17949  0 
uas                    17844  0 
hid_logitech_dj        18604  0 
usbhid                 46947  1 hid_logitech_dj
hid                   100366  2 hid_logitech_dj,usbhid
usb_storage            48838  1 ums_realtek

```lshw -c network output:
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: dc:0e:a1:4a:f6:a4
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 9c:b7:0d:c3:ea:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-17-generic firmware=N/A ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:d1500000-d1503fff

```If anyone could help me, I would appreciate it very much because I really like linux and this is the only problem that I have.

---

### Post by kurt18947 on 2013-02-06
If you haven't done so, you could look through this thread about the RTL8188CE:

[http://ubuntuforums.org/showthread.php?t=1981968&highlight=8188CE](http://ubuntuforums.org/showthread.php?t=1981968&highlight=8188CE)

---

### Post by littlealien on 2013-02-06
I have read like 10 threads about similar issues, and tried stuff like compiling the drivers my self, using different firmware and disabling hardware  decryption, but those "solutions" either break the internet completely or don't change anything.

I am still having problems. I can see that many people are having similar issues with similar realtech drivers. Maybe I should just give up and use windows until I can buy a new laptop with linux compatible hardware. next time I buy a laptop, I will read read and read some more until I am 100% sure all hardware is compatible with linux.

This driver problem is driving me crazy.

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by littlealien on 2013-02-06
As compiling that driver on 12.10 doesnt work, I will try installing 12.04 version and compiling the drivers. Will let you know how it goes.

---

### Post by wildmanne39 on 2013-02-06
Hi, have you tried everything in post 6 of this thread?
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Thanks

---

### Post by littlealien on 2013-02-06
Unfortunately that did not solve the problem. I can use the internet for like 5 mins properly, and after that BOOM and its gone. I get either disconnected or it starts lagging really bad.

---

### Post by wildmanne39 on 2013-02-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by littlealien on 2013-02-07
I installed linux mint (based on ubuntu 12.10) and compiled the drivers. I didn't do anything else, but it seems to be working great right now. In the last 2 hours of using internet, I have no problems at all. Strange. I don't understand how it would not work on ubuntu 12.10 and would work on mint that is based on 12.10. Isn't mint basically the same as ubuntu just with different DE?
Maybe I messed something up myself on ubuntu by trying all kind of stuff.

Anyway, so far my internet problems seem to be gone, and that is what matters.

---

### Post by kurt18947 on 2013-02-08
> **littlealien said:**
> I installed linux mint (based on ubuntu 12.10) and compiled the drivers. I didn't do anything else, but it seems to be working great right now. In the last 2 hours of using internet, I have no problems at all. Strange. I don't understand how it would not work on ubuntu 12.10 and would work on mint that is based on 12.10. Isn't mint basically the same as ubuntu just with different DE?
Maybe I messed something up myself on ubuntu by trying all kind of stuff.

Anyway, so far my internet problems seem to be gone, and that is what matters.

Good to see you seem to have it sorted.  I suspect that having tried a number of different things may have complicated your life somewhat.  I run into the same thing.  I don't know that there's good documentation on how to fully 'undo' some of the things we do.  I sometimes have a 'mule' install that I can abuse without breaking the 'good' install.

---

