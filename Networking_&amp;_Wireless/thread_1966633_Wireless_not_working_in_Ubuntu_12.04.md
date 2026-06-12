---
title: "Wireless not working in Ubuntu 12.04"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by lossman29 on 2012-04-27
Installed 12.04 today and tried tweaking a few things but my wireless issue is not yet resolved. Will greatly appreciate it, if anyone could help.

Machine- Lenovo Ideapad z560

Code for $lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```Code for iwconfig

```

lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:2  invalid misc:0

eth0      no wireless extensions.

```Code for lsmod

```
Module                  Size  Used by
vesafb                 13844  1 
joydev                 17693  0 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_hdmi     32474  4 
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
snd_hda_codec_conexant    62128  1 
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
video                  19596  0 
nvidia              12319264  43 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  0 
mac_hid                13253  0 
hid_logitech_dj        18593  0 
psmouse                87692  0 
snd_timer              29990  2 snd_pcm,snd_seq
serio_raw              13211  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  21 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14381  2 lib80211_crypt_tkip,wl
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
usb_storage            49198  1 
r8169                  62099  0 

```Code for 
sudo lshw -C network```

*-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:84:d8:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d9100000-d9103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 88:ae:1d:25:36:b4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=143.89.234.113 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d5110000-d5110fff memory:d5100000-d510ffff memory:d5120000-d513ffff

```Code for iwlist scan

```

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```So,I have ubuntu 12.04 64 bit installed. As I try connecting to a wireless connection, it asks for credentials and then every 2 minutes it asks for credentials again. Just doesn't connect. Please let me know, if more info. is needed. Would greatly appreciate any help.

---

### Post by lossman29 on 2012-04-27
The wired connection is working perfectly fine.

---

### Post by zdeuyo on 2012-04-27
> **lossman29 said:**
> The wired connection is working perfectly fine.

Hello,


i had a similar problem with my, 'Lenovo IdeaPad Z570-1024D9U - Laptop'.

Please let me know if this article thread solves your problem.

Link: [http://ubuntuforums.org/showthread.php?t=1959458]("http://ubuntuforums.org/showthread.php?t=1959458")

All the best.

---

### Post by bkratz on 2012-04-27
> **zdeuyo said:**
> Hello,


i had a similar problem with my, 'Lenovo IdeaPad Z570-1024D9U - Laptop'.

Please let me know if this article thread solves your problem.

Link: [http://ubuntuforums.org/showthread.php?t=1959458](http://ubuntuforums.org/showthread.php?t=1959458)

All the best.



The op has a broadcom card. He/she would be better off with what is found in post 2 and later of this thread.

[http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096)

---

### Post by nathan3624 on 2012-04-27
Ok everybody please try this if you are still having the problem, i work on computers and we had lots of Ubuntu users having this problems today, we found a program on Ubuntu Software Center called Windows Wireless Drivers, it lets you install a windows wireless driver for your wireless card. Worked on all the computers we had in. Please try it.

---

### Post by lossman29 on 2012-04-27
Tried the method mentioned in the other thread for the broadcom driver but to no avail. keeps asking me for credentials every 5 minutes. Gets stuck there.

How do you use the windows wireless driver tool? Do you need to deactivate the broadcom driver and remove all installed packages first?

Also asks for an inf file? Where do you find that?

---

### Post by wildmanne39 on 2012-04-27
Hi, you do not need ndiswrapper and it is the last option you want to use.

Did you try this link as recommended by 
bkratz? 
[http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096)
if so please post ```
lsmod
``` again so we can see what is loading now and:
```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
```
Thanks

---

### Post by lossman29 on 2012-04-28
I tried everything in the link recommended by bkratz but it keeps getting stuck at asking credentials. 

Posting the codes again.

lsmod
```

Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
ppdev                  17113  0 
vesafb                 13844  1 
joydev                 17693  0 
lib80211_crypt_tkip    17390  0 
snd_hda_codec_hdmi     32474  4 
wl                   2568210  0 
snd_hda_codec_conexant    62128  1 
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
nvidia              12319264  43 
lib80211               14381  2 lib80211_crypt_tkip,wl
snd_hda_intel          33773  6 
snd_seq_midi           13324  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
video                  19596  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
hid_logitech_dj        18593  0 
wmi                    19256  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  21 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
mac_hid                13253  0 
serio_raw              13211  0 
soundcore              15091  1 snd
lp                     17799  0 
mei                    41616  0 
parport                46562  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
usb_storage            49198  1 
r8169                  62099  0 

```

lspci -nnk | grep -iA2 net
```

06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0510]
	Kernel driver in use: wl
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Lenovo Device [17aa:392e]
	Kernel driver in use: r8169


```

iwconfig
```

lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```

rfkill list all
```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Blacklist.conf currently has the extra 2 lines added where I blacklisted bcma and brcm2011.

---

### Post by wildmanne39 on 2012-04-28
Hi please do:
```
echo "blacklist brcmwl" | sudo tee -a
```
make sure you have installed all updates then run:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then reboot.
Thanks

---

### Post by lossman29 on 2012-04-28
Thanks a lot Wildmanne. 
The wifi connects but after entering credentials for the 1st time, it gets stuck and keep asking me for credentials every 2 minutes till I hit cancel. Problem not yet solved.

Any other suggestions?

---

### Post by lossman29 on 2012-04-29
Problem seems to have been solved. I tweaked some settings for the wifi connection and created a custom connection. Seems to be working now.

Thanks everyone for all the help. Appreciate it.

---

### Post by wildmanne39 on 2012-04-29
Hi, I am glad it is working please use thread tools at the top of the page to mark the thread solved and post what actually got your connection working so people can benefit from this thread.
Thanks

---

### Post by jastone54 on 2012-04-29
I have tried everything I can find to get my Dell Inspirion N4010 with a Broadcom BCM4313. If I boot with the wired network cable attached to my router then the wireless works fine, but I don't want o have to run upstairs to the router every time I use my computer.  I have followed all the different instructions but nothing is working.  Now I can't even activate the Broadcom-STA proprietary driver in the additional drivers.  I love Linux and really want to leave Windows behind.  Please help!

---

### Post by bkratz on 2012-04-29
> **jastone54 said:**
> I have tried everything I can find to get my Dell Inspirion N4010 with a Broadcom BCM4313. If I boot with the wired network cable attached to my router then the wireless works fine, but I don't want o have to run upstairs to the router every time I use my computer.  I have followed all the different instructions but nothing is working.  Now I can't even activate the Broadcom-STA proprietary driver in the additional drivers.  I love Linux and really want to leave Windows behind.  Please help!



Have you tried posts 3 and 7 here?

[http://ubuntuforums.org/showthread.php?t=1928241](http://ubuntuforums.org/showthread.php?t=1928241)

---

### Post by rohanp on 2012-06-18
Hey , i am too facing the similar problem . Then i fixed it and when i used my system for the next time , wifi again went off . Now its not working at all and also the hardware key is not working fine . It is always orange whether key is on or off . Please help .

---

### Post by wildmanne39 on 2012-06-18
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

### Post by loh on 2012-07-03
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:


Just upgraded to Ubuntu 12.04, and the wireless doesn't work anymore. The result of your commands is below. Any suggestions? Thanks!!

```

> cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux l0149020 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

> lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

> lsusbBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 005: ID 04f2:b217 Chicony Electronics Co., Ltd 


> /sbin/iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"PBS-5F7BCD"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D4:D1:84:5F:7B:D2   
          Bit Rate=6.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:96   Missed beacon:0

eth0      no wireless extensions.

> /usr/sbin/rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

> lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62311  1 
joydev                 17693  0 
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rpcsec_gss_krb5        36346  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               332672  0 
mac80211              506816  1 iwlwifi
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
thinkpad_acpi          81819  0 
nvram                  14413  1 thinkpad_acpi
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
soundcore              15091  1 snd
psmouse                87692  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  2 iwlwifi,mac80211
wmi                    19256  0 
tpm_tis                18804  0 
serio_raw              13211  0 
mac_hid                13253  0 
nfsd                  277809  0 
i915                  468737  3 
drm_kms_helper         46978  1 i915
nfs                   356315  0 
drm                   242038  4 i915,drm_kms_helper
lockd                  86161  2 nfsd,nfs
fscache                61529  1 nfs
auth_rpcgss            53380  3 rpcsec_gss_krb5,nfsd,nfs
nfs_acl                12883  2 nfsd,nfs
sunrpc                245464  7 rpcsec_gss_krb5,nfsd,nfs,lockd,auth_rpcgss,nfs_acl
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 


```

---

### Post by wildmanne39 on 2012-07-03
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Then:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.
Thanks

---

### Post by loh on 2012-07-03
> **wildmanne39 said:**
> Hi, please do:


Great, it worked! Thanks a lot!!

---

### Post by wildmanne39 on 2012-07-03
Hi, your welcome!

---

### Post by acsoaring on 2012-08-12
Ok, so here is my odessy...  I have a Cisco AM10 that works fine if the machine is also connected by a hard wired connection, and not at all if the wireless is the only network connection.

By working fine, I mean it shows up on the desktop and connects to my wireless network (can tell it was successful from the router).

I took no special steps to get the adapter working.  The attached are the previously requested commands from the PC when it is booted without the hard link (so non-working).  My guess is that some change in the start-up process will solve this problem.
```

cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu-64-FX6800 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
    Subsystem: Acer Incorporated [ALI] Device [1025:0198]
    Kernel driver in use: e1000e

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1307:0169 Transcend Information, Inc. 
Bus 004 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 001 Device 004: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 005: ID 13b1:0031 Linksys AM10 v1 802.11n [Ralink RT3072]
Bus 002 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
vesafb                 13844  1 
nvidia              12319264  58 
arc4                   12529  2 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              51144  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd_hda_codec_realtek   223962  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mxm_wmi                12979  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
wmi                    19256  1 mxm_wmi
i7core_edac            28102  0 
edac_core              53746  3 i7core_edac
mac_hid                13253  0 
lp                     17799  0 
soundcore              15091  1 snd
parport                46562  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
usbhid                 47199  0 
e1000e                156693  0 
hid                    99559  1 usbhid
pata_jmicron           12747  0 
usb_storage            49198  1 

```

---

### Post by AC_Soaring on 2012-08-12
And here is what the same commands give me when I boot with a hard wire plugged in:  (Note I have to do a "sudo ifdown eth0" to avoid confusing the network)

```

cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu-64-FX6800 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

 lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
	Subsystem: Acer Incorporated [ALI] Device [1025:0198]
	Kernel driver in use: e1000e


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1307:0169 Transcend Information, Inc. 
Bus 001 Device 004: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 005: ID 13b1:0031 Linksys AM10 v1 802.11n [Ralink RT3072]
Bus 004 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:xx:xx:xx:xx:81   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:51   Missed beacon:0

eth0      no wireless extensions.

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lsmod
Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
vesafb                 13844  1 
nvidia              12319264  58 
arc4                   12529  2 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              51144  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd_hda_codec_realtek   223962  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
mxm_wmi                12979  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 mxm_wmi
psmouse                87692  0 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
mac_hid                13253  0 
lp                     17799  0 
i7core_edac            28102  0 
parport                46562  3 parport_pc,ppdev,lp
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  3 i7core_edac
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
usbhid                 47199  0 
crc_itu_t              12707  1 firewire_core
hid                    99559  1 usbhid
e1000e                156693  0 
pata_jmicron           12747  0 
usb_storage            49198  0 


```

---

### Post by wildmanne39 on 2012-08-14
Hi, please do:
```
echo "options rt2800usb  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb
```
Then:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.

If wireless still does not connect  copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by AC_Soaring on 2012-08-15
Thank you.  No luck after the modprobe and power changes.  I'm getting a 404 error from dropbox while trying to download the script.

- Alan

---

### Post by wildmanne39 on 2012-08-15
Hi,try it this way I changed the name last night sorry! Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by AC_Soaring on 2012-08-15
Ok, so here is the upload with a working wireless adapter (booted with the hard wire plugged in and did a sudo ifdown eth0).

I'll send along the non-working version in a minute.

- Alan

---

### Post by AC_Soaring on 2012-08-15
Here is what I get from the same script after booting without the hard line installed (wireless will not come up).

Thank you,

Alan

---

### Post by wildmanne39 on 2012-08-16
Hi, did you delete the old text info before you ran the script because I think you posted the old netinfo.text file, power management is still on is the reason I think this and if you did not delete the old file then the new one should have a 1 in the name.
Thanks

---

### Post by AC_Soaring on 2012-08-16
Both the files I posted were new.  I renamed the file between runs.  The contents of etc/pm/power.d/wireless follow (though they seem to have been ignored...):

```

alan@ubuntu-64-FX6800:/etc/pm/power.d$ cat wireless
#!/bin/sh
/sbin/iwconfig wlan0 power off

```

---

### Post by wildmanne39 on 2012-08-18
> **AC_Soaring said:**
> Both the files I posted were new.  I renamed the file between runs.  The contents of etc/pm/power.d/wireless follow (though they seem to have been ignored...):

```

alan@ubuntu-64-FX6800:/etc/pm/power.d$ cat wireless
#!/bin/sh
/sbin/iwconfig wlan0 power off

```
Hi go into this file and add [COLOR="Red"]exit 0 [/COLOR]to the very bottom the save, close and reboot.
Thanks

---

### Post by AC_Soaring on 2012-08-18
No effect. An iwconfig still reports "Power Management: on" for wlan0 after the reboot.

Thank you,

Alan

---

### Post by AC_Soaring on 2012-08-18
Ok, the problem with the power was that I had forgotten to make the file named "wireless" executable (sudo chmod a+x wireless).

Now the power management is off, as expected.  No change in device behavior.

New versions of the netinfo.txt are attached.  'Good' produced by leaving the hard wire plugged in during boot and doing a "sudo ifdown eth0" afterwards (using this now).  'Bad' produced by booting without the hard wire.

Thank you,

Alan

---

### Post by wildmanne39 on 2012-08-18
Hi, try this please:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb
```
Thanks

---

### Post by AC_Soaring on 2012-08-18
No change in behavior.  New good and bad network-info files are attached.

Thank you,

Alan

---

### Post by wildmanne39 on 2012-08-19
Hi, paste the contents of this file please:
```
gksudo gedit /etc/modprobe.d/rt2800usb.conf
```
Thanks

---

### Post by AC_Soaring on 2012-08-19
The contents are:

```

cat /etc/modprobe.d/rt2800usb.conf
options rt2800usb nohwcrypt=y

```

Thank you,

Alan

---

### Post by wildmanne39 on 2012-08-19
Hi, I have been researching your issue and I am out of idea's. I am sorry I have not been able to resolve the issue.

---

### Post by AC_Soaring on 2012-08-20
I wonder if we have been looking in the right place.  We know the wireless adapter works fine if the machine boots with the hard cable in place.  So the drivers and set-up are all (at least somewhat) correct.  But if the hard cable is not in place networking does not start.  Is there a way to debug the start-up process?

- Alan

---

### Post by wildmanne39 on 2012-08-20
Hi, you could look here:
```
sudo tail -n100 /var/log/syslog
```
```
tail -n100 /var/log/kern.log
```
I would unplug the wired connection then reboot and run the commands immediately.
Thanks

---

### Post by AC_Soaring on 2012-08-21
Copies of syslog and kern.log are attached after booting with only the wireless, and only the hard wire (good versions).

Thank you,

Alan

---

### Post by wildmanne39 on 2012-08-21
Hi, please try:
```
sudo rmmod -f mxm_wmi
```
Thanks

---

### Post by AC_Soaring on 2012-08-21
No change in behavior.  New syslog and kern.log files are attached.

Some notes on other odd behavior:
- When I boot with just the wireless, ifconfig displays wlan0, but ifup and ifdown don't work
```

sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 68:xx:xx:xx:xx:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

alan@ubuntu-64-FX6800:/etc/dhcp$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
alan@ubuntu-64-FX6800:/etc/dhcp$ sudo ifdown wlan0
ifdown: interface wlan0 not configured

```

Odd...

- Alan

---

### Post by wildmanne39 on 2012-08-22
Hi, the command is ```
sudo ifconfig wlan0 up
```
Thanks

---

### Post by erfan6 on 2012-08-22
Hello,
I just installed Ubuntu 12.04 for the first time, but although I enabled Wireless Networks, no networks was shown under "Wireless Networks." I tried to do what dear Wild Man said, but after rebooting, now there is even no "Enable Wireless Network." So like before I can only access Internet just with Ethernet.
Please help me

> **Wild Man said:**
> Hi please do:
```
echo "blacklist brcmwl" | sudo tee -a
```make sure you have installed all updates then run:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```Then reboot.
Thanks

---

### Post by wildmanne39 on 2012-08-22
Hi erfan6, please start your own thread and do what post 25 says.
Thanks

---

### Post by AC_Soaring on 2012-08-22
Well "sudo ifconfig wlan0 up" had no effect.  I bought a different wireless USB stick and have the same results.  This one has an indicator light that does not come on when booting without the hard wire, but is present when the hard wire is installed.

It feels like the failure to find a hard wired eth0 is bypassing a whole section of the network startup process, but I don't know how to drill down and watch that process execute.

- Alan

---

### Post by AC_Soaring on 2012-08-25
Interesting turn of events.  I purchased a D-Link DWA-130 and saw the same initial results:
- boots fine and wireless works if hard wire also installed;
- no wireless access if hard wire not available at boot.

Today I found a major difference; "sudo ifconfig wlan1 up" works beautufully on the D-Link adapter.  

So, I am guessing I actually had 2 problems with the Cisco device: the one that is happening with both USB wireless adapters at boot; and some sort of driver issue that was blocking the ifconfig.

Back on problem 1, how do I debug the boot process so that the device is found and installed automatically?

Thank you,

Alan

---

### Post by AC_Soaring on 2012-08-25
And the winning answer is...

- sudo gedit /etc/network/interfaces
- remove all the lines after iface lo loopback

The auto-start of eth0 is failing because there was no hard wire plugged in.  This prevented network-manager from starting and so the wlan could not work.

Thank you for assisting in this journey.

- Alan

---

### Post by wildmanne39 on 2012-09-01
Hi, I am glad you got it fixed.
Enjoy

---

### Post by Bobaseth on 2012-09-26
Hey what's up peoples! I now have this issue but my wired works fine though. It happen last week after I did a "Ubuntu System Update!" I read fourms saying that it maybe the latest "Network Manager Update Package" and was told to downgrade it. I did but to no avail! I'm using "Wubi" and I'm a "Noob!" I've only been using "Ubuntu" for a month now and this is my second post! On a side note...,it seems the more I "Update Ubuntu The More Features I Lose...," like bluetooth, fn key etc. Anyway thanks for any help?

---

### Post by nmushkin on 2013-02-16
EDIT :SOLVED IT
JUST USED SUDO APT-GET UPDATE THEN WAS ABLE TO FIND PROPRIETARY  drivers

I need some help setting up wireless for ubuntu 12.04.  I have the 2012 macbookpro, bluetooth and ethernet work fine but wireless doesn't see any networks, how do I install the wireless drivers?

---

### Post by SLarson07 on 2013-04-01
Hello! My wireless is not working either. I am new to the forums and Linux/Ubuntu, so be gentle haha :) I believe there are some terminal commands you would like me to run to know what is happening with my system?

---

### Post by wildmanne39 on 2013-04-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by SLarson07 on 2013-04-01
Per your request

---

### Post by wildmanne39 on 2013-04-01
Please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe b43
```
Then if it does not come on try:
```
sudo rfkill unblock all
```
The wl driver will work with your device but I believe that the b43 driver works better IMO.
Thanks

---

### Post by SLarson07 on 2013-04-01
I am getting this message for the first two commands:
      ```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

and this for the third:
      ```
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'Ic3man07'
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'sudo'
```

---

### Post by wildmanne39 on 2013-04-01
This > E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?usually means you have like the terminal and software center open at the same time if that is not the case then reboot and it should clear it so you can install the packages.
Thanks

---

### Post by SLarson07 on 2013-04-01
That was my guess. So I restarted and tried again before posting those messages.

---

### Post by wildmanne39 on 2013-04-01
Please start another thread for that issue then come back here and do the commands I posted and you should have wifi.
Thanks

---

### Post by SaintT on 2013-04-20
okay, I'm a new user so forgive me.  I've tried everything that has been used in the forums and everywhere else, but I just can't seem to figure out why the internet isn't working properly.  Ubuntu wont work, but my windows7 will.  This is refering to wireless of course... so I typed in iw config and this is what comes up:  Usage:	iw [options] commandOptions: 
	--debug		enable netlink debugging 
	--version	show version (3.2) 
Commands: 
	help 
	event [-t] [-r] [-f] 
	phy 
	list 
	phy <phyname> info 
	dev 
	dev <devname> info 
	dev <devname> del 
	dev <devname> interface add<name> type <type> [mesh_id <meshid>] [4addron|off] [flags <flag>*] 
	phy <phyname> interface add<name> type <type> [mesh_id <meshid>] [4addron|off] [flags <flag>*] 
	dev <devname> ibss join <SSID><freq in MHz> [fixed-freq] [<fixed bssid>][beacon-interval <TU>] [basic-rates <rate inMbps,rate2,...>] [mcast-rate <rate in Mbps>] [key d:0:abcde]
	dev <devname> ibss leave 
	dev <devname> station dump 
	dev <devname> station set <MACaddress> vlan <ifindex> 
	dev <devname> station set <MACaddress> plink_action <open|block> 
	dev <devname> station del <MACaddress> 
	dev <devname> station get <MACaddress> 
	dev <devname> survey dump 
	dev <devname> mesh leave 
	dev <devname> mesh join <meshID> [<param>=<value>]* 
	dev <devname> mpath dump 
	dev <devname> mpath set<destination MAC address> next_hop <next hop MAC address>
	dev <devname> mpath new<destination MAC address> next_hop <next hop MAC address>
	dev <devname> mpath del <MACaddress> 
	dev <devname> mpath get <MACaddress> 
	dev <devname> scan [-u] [freq<freq>*] [ies <hex as 00:11:..>] [ssid <ssid>*|passive]
	dev <devname> scan trigger [freq<freq>*] [ies <hex as 00:11:..>] [ssid <ssid>*|passive]
	dev <devname> scan dump [-u] 
	reg get 
	reg set <ISO/IEC 3166-1 alpha2> 
	dev <devname> connect [-w]<SSID> [<freq in MHz>] [<bssid>] [key 0:abcded:1:6162636465] 
	dev <devname> disconnect 
	dev <devname> link 
	dev <devname> offchannel <freq><duration> 
	dev <devname> cqm rssi<threshold|off> [<hysteresis>] 
	phy <phyname> wowlan show 
	phy <phyname> wowlan disable 
	phy <phyname> wowlan enable[any] [disconnect] [magic-packet] [gtk-rekey-failure][eap-identity-request] [4way-handshake] [rfkill-release] [patterns<pattern>*] 
	dev <devname> roc start <freq><time> 
	phy <phyname> set antenna<bitmap> | all | <tx bitmap> <rx bitmap> 
	dev <devname> set txpower<auto|fixed|limit> [<tx power in mBm>] 
	phy <phyname> set txpower<auto|fixed|limit> [<tx power in mBm>] 
	phy <phyname> set distance<distance> 
	phy <phyname> set coverage<coverage class> 
	phy <phyname> set netns <pid>
	phy <phyname> set rts <rtsthreshold|off> 
	phy <phyname> set frag<fragmentation threshold|off> 
	dev <devname> set channel<channel> [HT20|HT40+|HT40-] 
	phy <phyname> set channel<channel> [HT20|HT40+|HT40-] 
	dev <devname> set freq <freq>[HT20|HT40+|HT40-] 
	phy <phyname> set freq <freq>[HT20|HT40+|HT40-] 
	phy <phyname> set name <newname> 
	dev <devname> set peer <MACaddress> 
	dev <devname> set 4addr <on|off>
	dev <devname> set type <type>
	dev <devname> set meshid<meshid> 
	dev <devname> set monitor<flag>* 
	dev <devname> set mesh_param<param>=<value> [<param>=<value>]* 
	dev <devname> set power_save<on|off> 
	dev <devname> set bitrates[legacy-<2.4|5> <legacy rate in Mbps>*] 
	dev <devname> get mesh_param[<param>] 
	dev <devname> get power_save<param> 


You can omit the 'phy' or 'dev' if theidentification is unique, 
e.g. "iw wlan0 info" or "iwphy0 info". (Don't when scripting.) 


Do NOT screenscrape this tool, we don'tconsider its output stable.  

I don't know if this helps, but I am getting super frustrated.  please help!  I have an Asus K501 and I just downloaded the Ubuntu 12.04  I tried uninstalling and reinstalling firefox as well, and now I can't reinstall it lol ugh!!! I don't know what to do!

---

### Post by wildmanne39 on 2013-04-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by mksan on 2013-05-07
hello, i  have a problem with the wireless network it simply doesn't work.
 i have a dell latitude b630 with ubuntu 12.04
but my wired network works fine
please help i don't know what to do

---

### Post by wildmanne39 on 2013-05-07
Please do what is in post 61.
Thanks

---

### Post by mksan on 2013-05-07
this is what it shows



[HR][/HR]*************** info trace ****************



**** uname -a ****


Linux mark-Latitude-D630 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:28:09 UTC 2013 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: wl


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 004: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader


**** iwconfig ****




**** rfkill ****


1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
dm_crypt               22528  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
parport_pc             32114  0 
rfcomm                 38139  12 
ppdev                  12849  0 
bnep                   17830  2 
snd_hda_codec_idt      60251  1 
pcmcia                 39826  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
binfmt_misc            17292  1 
dell_laptop            17767  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
nvidia              10286823  44 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
psmouse                96718  0 
yenta_socket           27428  0 
snd_timer              28931  2 snd_pcm,snd_seq
wl                   3032542  1 
serio_raw              13027  0 
joydev                 17393  0 
mac_hid                13077  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              178877  1 wl
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211               14040  1 wl
wmi                    18744  1 dell_wmi
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41937  0 
hid                    77428  1 usbhid
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
video                  19115  0 
tg3                   137318  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             200.44.32.12
    DNS:             200.11.248.12




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search cantv.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
#blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist brcmsmac
blacklist bcma


**** dmesg ****


[    2.561878] tg3.c:v3.121 (November 2, 2011)
[    2.561897] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.561909] tg3 0000:09:00.0: setting latency timer to 64
[    2.581502] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address <MAC address removed>
[    2.581508] tg3 0000:09:00.0: eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.581512] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.581515] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   24.058475] wmi: Mapper loaded
[   24.337393] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.337403] wl 0000:0c:00.0: setting latency timer to 64
[   24.340042] wl driver 6.20.155.1 (r326264) failed with code 21
[   24.340068] Modules linked in: snd_timer wl(P+) serio_raw joydev mac_hid pcmcia_rsrc pcmcia_core cfg80211 snd_seq_device lib80211 wmi btusb bluetooth snd soundcore snd_page_alloc lp parport vesafb usbhid hid firewire_ohci firewire_core crc_itu_t video tg3
[   24.340135] EIP is at wdev_priv.part.7+0x3/0x5 [wl]
[   24.340208]  [<fa13d924>] wl_cfg80211_detach+0xc4/0xd0 [wl]
[   24.340239]  [<fa13657f>] wl_free_if.isra.10+0x1f/0xa0 [wl]
[   24.340269]  [<fa136f48>] wl_free+0x58/0x250 [wl]
[   24.340301]  [<fa056e92>] ? wlc_attach+0xf6c/0xfda [wl]
[   24.340331]  [<fa13e409>] wl_pci_probe+0x51a/0x53a [wl]
[   24.340422]  [<f9239017>] wl_module_init+0x17/0x1000 [wl]
[   24.340494] EIP: [<fa13e496>] wdev_priv.part.7+0x3/0x5 [wl] SS:ESP 0068:ef583cec
[   25.041090] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
[   26.662428] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   26.662433] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   95.643891] tg3 0000:09:00.0: eth0: Link is down
[   98.557716] dell_wmi: Unknown key e044 pressed
[  139.275915] dell_wmi: Unknown key e043 pressed
[  139.358510] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[  139.358520] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[15793.216346] tg3 0000:09:00.0: eth0: Link is down
[15796.014536] dell_wmi: Unknown key e044 pressed
[15932.538419] dell_wmi: Unknown key e043 pressed
[15932.662116] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[15932.662127] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX


**************** done ********************







if you can help me i would be very gratefull if not i'll still gratefull you tried

---

### Post by mksan on 2013-05-07
[ATTACH]242310[/ATTACH]

---

### Post by wildmanne39 on 2013-05-07
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe b43
```
Thanks

---

### Post by skroth on 2013-07-16
Please help 



```
*************** info trace ***************

***** uname -a *****

Linux swaroop-laptop 3.2.0-49-generic-pae #75-Ubuntu SMP Tue Jun 18 18:00:21 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: wl
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Lenovo Device [17aa:392e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0489:e00d Foxconn / Hon Hai 
Bus 002 Device 003: ID 04f2:b1c1 Chicony Electronics Co., Ltd 

***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:"BITS"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   342801  0 
bcma                   25651  1 b43
ssb                    50691  1 b43
iwlwifi               366509  0 
mac80211              436493  2 b43,iwlwifi
wl                   2906597  0 
cfg80211              178877  4 b43,iwlwifi,mac80211,wl
lib80211               14040  2 lib80211_crypt_tkip,wl

***** nm-tool *****

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1  [BITS] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Alekhya:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    GANNUK-PC_Network: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Zephyr:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    redBus Ruckus1  :Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA
    VPS:             Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 22
    Muse:            Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 50 WPA2
    COMPACT WIFI:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WEP
    redBus1:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA
    SWAROOP-PC_Network: Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 2 WPA
    COMPACT WIFI:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WEP
    BITS:            Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption keyn
                    ESSID:"BITS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000442495453
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100098FC11C9AB1D102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304C3530333338301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption keyff
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 320130
                    IE: Unknown: DD0A0002BC01001E2A3D3160
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"GANNUK-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 001147414E4E554B2D50435F4E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545720010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010004
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8809094E4F079D3103C000101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000032127A
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Alekhya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0007416C656B687961
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Indhu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0005496E646875
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051600000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"redBus Ruckus1  "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0010726564427573205275636B7573312020
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030102
                    IE: Unknown: 050400020100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C338C011BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: 2D1A8C011BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: DD1A00904C3402000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602000000000000000000000000000000000000000000
                    IE: Unknown: DD080013920100018500
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Muse"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00044D757365
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Zephyr"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00065A6570687972
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081100000000000000000000000000000000000000
          Cell 09 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"VPS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** dmesg *****

[   33.971493] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   91.862818] eth1: no IPv6 routers present
[  701.788807] eth1: no IPv6 routers present
[  850.979697] eth1: no IPv6 routers present
[  900.082269] eth1: no IPv6 routers present
[ 1023.437514] eth1: no IPv6 routers present
[ 1075.966918] eth1: no IPv6 routers present
[ 1124.175688] eth1: no IPv6 routers present
[ 1174.202503] eth1: no IPv6 routers present
[ 1365.185113] eth1: no IPv6 routers present
[ 1711.771182] eth1: no IPv6 routers present
[ 1760.151729] eth1: no IPv6 routers present
[ 1810.976056] eth1: no IPv6 routers present
[ 1858.821524] eth1: no IPv6 routers present
[ 1961.484460] eth1: no IPv6 routers present
[ 2009.311346] ERROR @wl_dev_intvar_get : error (-1)
[ 2009.311355] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2103.847770] eth1: no IPv6 routers present
[ 2111.832381] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2111.832390] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2111.832399] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2111.832403] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2111.832411] ERROR @wl_dev_intvar_get : error (-1)
[ 2111.832415] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************
```

---

### Post by wildmanne39 on 2013-07-16
Hi, you have three drivers loaded, we need to remove two of them, please do:
```
sudo apt-get purge --remove b43-fwcutter firmware-b43-installer
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then:
```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
Thanks

---

### Post by eoin_fanning on 2013-08-02
Please help me if you can i have tried all suggestions i can find. Wireless was working fine. then started to come and go then i deleted connection and tried to reenter but have nothing now. its like the wireless is disabled or something. using a wireless usb pen connected to a desktop. Thank you


```
jester@jester-server:~$ cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux jester-server 3.2.0-51-generic-pae #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 i686 i686 i386 GNU/Linux
jester@jester-server:~$ 



```
```
jester@jester-server:~$ lspci -nnk | grep -iA2 net00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
    Subsystem: Packard Bell B.V. Device [1631:e028]
    Kernel driver in use: via-rhine
jester@jester-server:~$ 



```
```
jester@jester-server:~$ lsusbBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 004: ID 1044:8008 Chu Yuen Enterprise Co., Ltd GN-WB01GS
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 002 Device 002: ID 1631:0121 Good Way Technology 
Bus 001 Device 006: ID 040b:650a Weltrend Semiconductor 
Bus 002 Device 003: ID 1631:0601 Good Way Technology 
Bus 002 Device 004: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600



```

```
jester@jester-server:~$ lsusbBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 004: ID 1044:8008 Chu Yuen Enterprise Co., Ltd GN-WB01GS
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 002 Device 002: ID 1631:0121 Good Way Technology 
Bus 001 Device 006: ID 040b:650a Weltrend Semiconductor 
Bus 002 Device 003: ID 1631:0601 Good Way Technology 
Bus 002 Device 004: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600
jester@jester-server:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
[CODE]jester@jester-server:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jester@jester-server:~$ 
[CODE]jester@jester-server:~$ lsmod
Module                  Size  Used by
vesafb                 13516  1 
arc4                   12473  2 
rt73usb                27029  0 
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
rt2x00usb              20099  1 rt73usb
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rt2x00lib              48875  2 rt73usb,rt2x00usb
mac80211              436493  2 rt2x00usb,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
snd_hda_codec_realtek   174313  1 
usbhid                 41937  0 
hid                    77428  1 usbhid
snd_hda_codec_hdmi     31775  1 
snd_hda_intel          32719  5 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nvidia              10286823  30 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                86520  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
serio_raw              13027  0 
i2c_viapro             12969  0 
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13077  0 
binfmt_misc            17292  1 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  0 
firewire_ohci          40172  0 
via_rhine              27413  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  2 rt73usb,firewire_core
pata_via               13428  0 
sata_via               13495  2 
jester@jester-server:~$ 



```

[/CODE]

[/CODE]

---

### Post by Joleen on 2013-08-11
Dear WildManne
My wireless had all the problems reported, notedly could not authenticate and reask me for the password, (the only place where it did not, was my house wifi, where it disconnected every two minutes, and now, when I removed my laptop, it can't even see any wireless around. I've been reading the forum and tried many different things, and the first was to uninstall and reinstall bcm, with no result. (actually it can see SOME of the wireless and after reboot its dying again.)
I regret to say that I use ubuntu the last 5 years, but recently it is becoming harder and harder and harder for non-professionals to handle them. I am now using ubuntu 12.04, its not a new release, and it should be better tested...:(
Below I paste the output of my wireless info script....I would appreciate any help...I need it for work...


*************** info trace ***************


***** uname -a *****


Linux petit 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:21:10 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise


***** lspci *****


01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: AzureWave Device [1a3b:2047]
	Kernel driver in use: wl


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 005 Device 002: ID 13d3:3315 IMC Networks Bluetooth module


***** PCMCIA Card Info *****




***** iwconfig *****


eth2      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


b43                   342801  0 
mac80211              436493  1 b43
bcma                   25651  1 b43
ssb                    50691  1 b43
wl                   2906597  0 
cfg80211              178877  3 b43,mac80211,wl
lib80211               14040  2 lib80211_crypt_tkip,wl


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254




- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=false


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


eth2      No scan results




***** resolv.conf *****


nameserver 127.0.0.1
search lan


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist bcma
blacklist brcm80211


***** modinfo *****


filename:       /lib/modules/3.2.0-51-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     86DC7EAD5064E99821DBACC
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.2.0-51-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)


filename:       /lib/modules/3.2.0-51-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-51-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-51-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-51-generic SMP mod_unload modversions 686 






***** udev rules *****


# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0a5c:0x6300 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


***** dmesg *****


[   20.251048] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.403954] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.403977] wl 0000:02:00.0: setting latency timer to 64
[   20.461621] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   20.693881] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   21.101788] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140100)
[   21.198707] udevd[366]: renamed network interface eth1 to eth2
[  129.796606] wl 0000:02:00.0: PCI INT A disabled
[  130.598937] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  130.598956] wl 0000:02:00.0: setting latency timer to 64
[  826.932507] ERROR @wl_dev_intvar_get : error (-1)
[  826.932541] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1114.071416] ERROR @wl_dev_intvar_get : error (-1)
[ 1114.071428] ERROR @wl_cfg80211_get_tx_power : error (-1)


****************** done ******************

---

### Post by wildmanne39 on 2013-08-11
Please do:
```
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Reboot
Thanks

---

### Post by Joleen on 2013-08-11
if it better helps you, here is the script attached.
thanks Wildmanne..

I have tried that  before, and retried after your suggestion. No result. :(

---

### Post by wildmanne39 on 2013-08-11
> **Wild Man said:**
> Please do:
```
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Reboot
ThanksYou just ran both of these commands and rebooted?
Also please run:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Reboot, if it does not connect run the script again and post the new file here so we can see if the changes took effect.
Thanks

---

### Post by Joleen on 2013-08-12
dear Wildmanne, yes I just ran the two commands, then rebooted.
after I did the same for the third. It still cannot see the wireless (it is a thomson rooter) around.
here is the new script...



*************** info trace ***************


***** uname -a *****


Linux petit 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:21:10 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise


***** lspci *****


01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: AzureWave Device [1a3b:2047]
	Kernel driver in use: brcmsmac


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 005 Device 002: ID 13d3:3315 IMC Networks Bluetooth module


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


brcmsmac              540923  0 
mac80211              436493  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178877  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12518  1 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=false


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     No scan results




***** resolv.conf *****


nameserver 127.0.0.1
search lan


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist bcma
blacklist brcm80211
blacklist b43
blacklist ssb
blacklist bcma


***** modinfo *****


filename:       /lib/modules/3.2.0-51-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-51-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-51-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-51-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0a5c:0x6300 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


***** dmesg *****


[   19.426539] brcmsmac 0000:02:00.0: bus 2 slot 0 func 0 irq 10
[   19.426574] brcmsmac 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.426594] brcmsmac 0000:02:00.0: setting latency timer to 64
[   20.034808] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140100)
[   22.742564] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   22.742576] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   22.743147] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.743708] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.745760] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  220.028036] atl1c 0000:01:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.


****************** done ******************

firmware bug??????

---

### Post by varunendra on 2013-08-12
> **Joleen said:**
> firmware bug??????
...not related to your wireless interface. It is regarding the ethernet driver (atl1c) and even that is just a notification, not necessarily a problem.

The brcmsmac driver definitely works better for your card in Ubuntu 13.04, but in 12.04, it is often a matter of hit or miss (in my personal experience).

Sometimes, in 12.04, an older version of the wl driver (version 5.100.82.38) works better than the brcmsmac ([reference post]("http://ubuntuforums.org/showthread.php?t=2140263&p=12625996#post12625996")). To see what versions are available for you, please show us the output of -
```
apt-cache show bcmwl-kernel-source | grep -i version
```
Although I'd go with whatever Wild Man suggests.

**PS:**
@ Joleen,

Please post the outputs within 'Code' tags. It puts the code in a nice box (like above) and preserves the formatting. Follow the "Code Tags example" link in my signature to see an elaborated example.

---

### Post by joeymac2011 on 2013-08-12
Hi Joleen,

Try

sudo modprobe -r brcmsmac && sudo modprobe brcm80211

---

### Post by Joleen on 2013-08-12
Dear all, 
thank you very much for your help. I keep trying. I will let you know if anything.
x

---

### Post by wildmanne39 on 2013-08-12
To use the brcmsmac driver you need to do:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` 
Then remove bcma from the list, save, close gedit and reboot.

From the time I last posted you changed drivers that makes it hard to get your wireless working when you try things on your own.

I was setting things up to try just the wl driver and now we are using the brcmsmac driver it may work it is hit  and miss.

Let us know if the brcmsmac driver connects after removing bcma from the blacklist file.
Thanks

---

### Post by Joleen on 2013-08-21
Dear all,
here is what was happening:
the wireless started working since the first instructions of Wildmanne.
The problem was with a particular rooter. The particular rooter I was trying to connect to (which was the ONLY one in the desert I was in), was set to canal 13. My wireless could not even see it. When I got in the rooter and changed to canal 6, it detected the network and connected to it. 
 This maybe is a problem worth looking into. I am really curious about it and looking forward for your responses. I do not know if this is a general problem of Ubuntu 12.04? I am back in the desert and can test the other canals if you tell me.
Thank you all.

---

### Post by wildmanne39 on 2013-08-21
Hi, your wireless card may not be able to connect to channels above 11, run this command to see:
```
iwlist chan
```
Thanks

---

### Post by Joleen on 2013-08-22
True! so this is a hardware thing!

---

### Post by wildmanne39 on 2013-08-22
If you post the output of the command in my last post we can look and see.
Thanks

---

### Post by Joleen on 2013-08-23
here is the output 
```
lo        no frequency information.


wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.437 GHz (Channel 6)


eth0      no frequency information.



```
 
:)

---

### Post by wildmanne39 on 2013-08-23
That is what I figured your wireless device is only capable of working on channels 1 thru 11 there is nothing wrong with it, it is just made that way.
Thanks

---

### Post by lamont2 on 2013-09-02
**Re: Wireless not working in Ubuntu 12.04**

                                                                                  [INDENT]                     Please do:
     Code:
     sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source 
     Code:
     sudo apt-get install linux-firmware-nonfree 
     Code:
     sudo modprobe b43 
Then if it does not come on try:
     Code:
     sudo rfkill unblock all 
The wl driver will work with your device but I believe that the b43 driver works better IMO.
Thanks                 [/INDENT]
            
                         
                                                                         [URL="https://help.ubuntu.com/community/CompositeManager"]this turns my wifi on,but if i shut laptop off it wount work unless i do this again
[/URL]

---

### Post by wildmanne39 on 2013-09-02
lamont2 who's device are you saying can use the b43 driver?, also with the last person that posted it will not make any difference because their device still is not capable of working on channels above 11.

---

### Post by UOS0013 on 2013-09-13
Ok, my results are below. Any help?

```
turtlebot@turtlebot:~$ cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
Linux turtlebot 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
turtlebot@turtlebot:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: AzureWave Device [1a3b:2110]
    Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
turtlebot@turtlebot:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 13d3:3393 IMC Networks 
Bus 001 Device 004: ID 13d3:5188 IMC Networks 


turtlebot@turtlebot:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

turtlebot@turtlebot:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


turtlebot@turtlebot:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
bnep                   18281  2 
ppdev                  17113  0 
rfcomm                 47604  12 
binfmt_misc            17540  1 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath3k                  12961  0 
arc4                   12529  2 
joydev                 17693  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
ath9k                 132428  0 
mac80211              506862  1 ath9k
btusb                  18332  2 
ath9k_common           14053  1 ath9k
snd_timer              29990  2 snd_pcm,snd_seq
ath9k_hw              411239  2 ath9k,ath9k_common
bluetooth             180113  24 bnep,rfcomm,ath3k,btusb
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
asus_nb_wmi            12710  0 
asus_wmi               24456  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                97519  0 
serio_raw              13211  0 
soundcore              15091  1 snd
cfg80211              205774  3 ath9k,mac80211,ath
mac_hid                13253  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
i915                  478239  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
wmi                    19256  1 asus_wmi
i2c_algo_bit           13423  1 i915
video                  19651  1 i915





```

---

### Post by varunendra on 2013-09-13
> **UOS0013 said:**
> ```

turtlebot@turtlebot:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter **[168c:0034]** (rev 01)
    Subsystem: AzureWave Device [1a3b:2110]
    Kernel driver in use: **ath9k**

```

Your wireless card is using ath9k driver, which seems to be problematic currently. Please follow [post=12785322]this post[/post] to try a few things, and if they don't work, then compile and install a newer version as suggested in the same post.

---

### Post by Elfy on 2013-09-13
Thread closed.

This thread was started last year by someone requesting support.

Anyone else needing support should post their own thread here.

---

