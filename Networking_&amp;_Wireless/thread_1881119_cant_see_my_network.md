---
title: "cant see my network"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by WinterMadness on 2011-11-14
Asus u46. **Wireless does work**, but I cant seem to see **my** network(no, its not hidden). I tried connecting manually but its not working. I also "scanned" and it does not see my network.

I am using the latest version of Kubuntu, which im not familiar with, im used to an older version so if anyone has tips please help me.

Needless to say, it does connect to the network if I use the ethernet.

---

### Post by northd_tech on 2011-11-15
We will need a little more information about your networking hardware.  Can you copy/paste the output of these terminal commands here:

```
lspci
sudo lshw -C network
lsmod
lsusb
ifconfig
iwconfig
uname -a
cat /etc/lsb-release

```

---

### Post by WinterMadness on 2011-11-15
Some details: Im on the live cd trying to make sure everything works before installing, also I turned off (f6-first option) aspci(?) 

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:51:ad:24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:4f:4f:a0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:dd400000-dd43ffff ioport:a000(size=128)
ubuntu@ubun

```

```

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
arc4                   12529  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bnep                   18436  2 
rfcomm                 47946  0 
snd_seq_midi           13324  0 
bluetooth             166112  10 bnep,rfcomm
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
snd_seq_midi_event     14899  1 snd_seq_midi
iwlagn                314213  0 
videodev               93004  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  1 iwlagn
joydev                 17693  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
squashfs               36799  1 
overlayfs              28267  1 
nls_utf8               12557  1 
isofs                  40253  1 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
i915                  566711  2 
xhci_hcd               78641  0 
atl1c                  41643  0 
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
ahci                   26002  1 
libahci                26861  1 ahci
ubuntu@ubuntu:~$ 
----------------------

ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 
ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 14:da:e9:4f:4f:a0  
          inet6 addr: fe80::16da:e9ff:fe4f:4fa0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1792 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1904929 (1.9 MB)  TX bytes:257998 (257.9 KB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)

wlan0     Link encap:Ethernet  HWaddr 40:25:c2:51:ad:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 14:da:e9:4f:4f:a0  
          inet6 addr: fe80::16da:e9ff:fe4f:4fa0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1792 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1904929 (1.9 MB)  TX bytes:257998 (257.9 KB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)

wlan0     Link encap:Ethernet  HWaddr 40:25:c2:51:ad:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

```
ubuntu@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
```

---

### Post by WinterMadness on 2011-11-15
also, my router is: netgear n600 wireless dual band router, model wndr3400

---

### Post by WinterMadness on 2011-11-15
Also, using te iwlagn driver apparently. Keep in mind that I CAN connect to wireless networks, I just cant see MY wireless network.

---

### Post by northd_tech on 2011-11-15
> **WinterMadness said:**
> also, my router is: netgear n600 wireless dual band router, model wndr3400

Have you gone into your router settings to see if you are actually broadcasting?  (I recently had my ISP recofigure our router remotely somehow, or else a power spike/'bump' reset some of the router settings).

Check your SSID, channel, etc.  in the router settings first.  I tried searching the Netgear site for instructions, manual(s), etc. but I found at least 5 differnet "N600 wireless Dual Band" routers:

[http://support.netgear.com/app/products/family/a_id/19421](http://support.netgear.com/app/products/family/a_id/19421)

[http://support.netgear.com/app/products/family/a_id/17702](http://support.netgear.com/app/products/family/a_id/17702)

Many of the routers that I've worked on/with you access the router setup by entering one of these 2 addresses in a [blank or new] browser window:

[http://192.168.0.0](http://192.168.0.0)

[http://192.168.0.1](http://192.168.0.1)

NOTE:  Your browser very likely might block those links and you will need to copy/paste one of them  directly into your browser's URL bar/window- mine did that and the 2nd link (...168.0.1) worked for my router.

```
http://192.168.0.0

http://192.168.0.1
```It is possible that you might need https:// and/or a login & password to get into that router though- the manual should tell you what is involved there (or how to reset the password to factory defaults).

I'll analyze your hardware specifics very shortly- but please check your router settings first.  It sounds like your wireless is probably working fine if you are seeing **other **wireless routers- are any of them open/unsecured?  If so, have you tried accessing those (or McDonalds' or Burger Kings' or ...).

---

### Post by northd_tech on 2011-11-15
> **WinterMadness said:**
> 
ubuntu@ubuntu:~$ **lspci**
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
04:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
ubuntu@ubuntu:~$ **sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:51:ad:24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: **broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926** latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:4f:4f:a0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:dd400000-dd43ffff ioport:a000(size=128)

ubuntu@ubuntu:~$ **lsmod**
Module                  Size  Used by
**iwlagn   **             314213  0 
mac80211              310872  1** iwlagn**
cfg80211              199587  2 **iwlagn**,mac80211

ubuntu@ubuntu:~$** lsusb**
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 

ubuntu@ubuntu:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

That's an Intel Centrino Wireless-N + WiMAX 6150 wireless interface, and as you already posted, the driver is** iwlagn**.  Your **lsmod** makes it look like those driver modules are fine to me, but I don't know much about that Intel Centrino wireless- hopefully someone else will chime in who knows that one well.

After you check that router setup/status, you might want to look for blacklisted modules with these terminal commands:

```
cat /etc/modules
egrep 'iw|entrin' /etc/modprobe.d/*
ls -l /etc/modprobe.d/
```Let's also  see what dmesg tells us:

```
dmesg | egrep 'iwl|entrin|irmware'
```

---

### Post by WinterMadness on 2011-11-15
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo modprobe iwlagn 
ubuntu@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ubuntu@ubuntu:~$ egrep 'iw|entrin' /etc/modprobe.d/*
ubuntu@ubuntu:~$ ls -l /etc/modprobe.d/
total 10
-rw-r--r-- 1 root root 2507 2011-05-05 05:26 alsa-base.conf
-rw-r--r-- 1 root root  325 2011-06-15 16:57 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2011-06-15 16:57 blacklist.conf
-rw-r--r-- 1 root root  108 2011-09-27 12:47 blacklist-cups-usblp.conf
-rw-r--r-- 1 root root  210 2011-06-15 16:57 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 2011-06-15 16:57 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2011-05-05 05:26 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2011-10-12 15:11 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 2011-06-15 16:57 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 2011-06-15 16:57 blacklist-watchdog.conf
ubuntu@ubuntu:~$ dmesg | egrep 'iwl|entrin|irmware'
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[   82.882999] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   82.883002] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   82.883068] iwlagn 0000:02:00.0: PCI->APIC IRQ transform: INT A -> IRQ 17
[   82.883077] iwlagn 0000:02:00.0: setting latency timer to 64
[   82.883104] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   82.893763] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   82.893764] iwlagn 0000:02:00.0: Device SKU: 0X9
[   82.893766] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   82.895409] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   82.895495] iwlagn 0000:02:00.0: irq 43 for MSI/MSI-X
[   83.860101] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   84.666564] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
ubuntu@ubuntu:~$ 

```

I was able to get it to see my network with the following code:
```
ubuntu@ubuntu:~$ rmmod iwlagn
ERROR: Removing 'iwlagn': Operation not permitted
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ su rmmod iwlagn
Unknown id: rmmod
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ modprobe iwlagn 11n_disable=0
ubuntu@ubuntu:~$ modprobe iwlagn 
ubuntu@ubuntu:~$ rmmod iwlagn
ERROR: Removing 'iwlagn': Operation not permitted
ubuntu@ubuntu:~$ sudo rmmod iwlagn
ubuntu@ubuntu:~$ modprobe iwlagn 11n_disable=0
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Operation not permitted
ubuntu@ubuntu:~$ sudo modprobe iwlagn 11n_disable=0
ubuntu@ubuntu:~$ sudo modprobe iwlagn 
ubuntu@ubuntu:~$ 

```

However, it gets stuck waiting for authorization. Connecting to my phones network (tethered) does not have this issue.

---

### Post by northd_tech on 2011-11-15
> **WinterMadness said:**
> ```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo modprobe iwlagn 
...
[code]ubuntu@ubuntu:~$ rmmod iwlagn
ERROR: Removing 'iwlagn': Operation not permitted
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ su rmmod iwlagn
Unknown id: rmmod
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ modprobe iwlagn 11n_disable=0
ubuntu@ubuntu:~$ modprobe iwlagn 
ubuntu@ubuntu:~$ rmmod iwlagn
ERROR: Removing 'iwlagn': Operation not permitted
ubuntu@ubuntu:~$ sudo rmmod iwlagn
ubuntu@ubuntu:~$ modprobe iwlagn 11n_disable=0
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Operation not permitted
ubuntu@ubuntu:~$ sudo modprobe iwlagn 11n_disable=0
ubuntu@ubuntu:~$ sudo modprobe iwlagn 
ubuntu@ubuntu:~$ 

```However, it gets stuck waiting for authorization. Connecting to my phones network (tethered) does not have this issue.

That's an awful LOT of **sudo rmmod** (or **modprobe -r **BTW) and **sudo modprobe** commands.

It is good to check whether you've actually done anything after a modprobe or rmmod with these terminal commands (specific to kernel module **iwlagn** in this case only):

```
lsmod | grep iwl
modinfo iwlagn

```I think I know what that would tell us though. so let's get that Centrino Wireless-N **iwlagn** module loaded at boot time with these terminal commands in the same order that I list them:

```
echo '# load kernel module iwlagn for Centrino Wireless-N' | sudo tee -a /etc/modules
echo 'iwlagn' | sudo tee -a /etc/modules
```After rebooting, your **iwlagn** module troubles should be over.  Check with these 2 again after you reboot:

```
lsmod | grep iwl
modinfo iwlagn

```Unfortunately, it also sounds like you have a wireless authentication problem too.  Let's see what this command tells us about your installed wireless packages:

```
dpkg -l wire*

```You might need to **sudo apt-get install wireless-tools** if that package isn't installed (depending upon what we learn from **dpkg **above).
BTW- are you using WPS, WPA, WPA2, WEP or some other wireless security in the router settings?

Edit:  Your time would be very well spent by disabling your wireless security in your router until AFTER you get connected wirelessly to your router at least twice (with a reboot in between them for good measure).

---

### Post by WinterMadness on 2011-11-15
its kinda weird, but I dont think the modprobe had anything to do with me seeing my network, I think it may just take a long time, or that I was connecting to my phones network and then it appeared (thouygh I dont know if either are true at ALL).

I should mention that when I boot I turn off acpi queries

---

### Post by WinterMadness on 2011-11-15
So whenever my network actually does show up, it hangs at configuring interface, it eventually gets passed that and then fails at the authentication (waiting for authorization).

---

### Post by WinterMadness on 2011-11-15
right now im connected to it, but i had to turn off my security :(

---

### Post by northd_tech on 2011-11-15
I'm not so sure- going back to what you wrote earlier, I have highlighted the commands that generated [COLOR=Red]**error messages** in red[/COLOR] below:

> **WinterMadness said:**
> 
```
ubuntu@ubuntu:~$[B] [COLOR=Red]rmmod iwlagn[/COLOR][COLOR=Red]
ERROR: Removing 'iwlagn': Operation not permitted[/COLOR][/B]
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ [COLOR=Red]**su rmmod iwlagn**[B]
Unknown id: rmmod[/B][/COLOR]
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ modprobe iwlagn 11n_disable=0
ubuntu@ubuntu:~$ modprobe iwlagn 
ubuntu@ubuntu:~$ [COLOR=Red][B]rmmod iwlagn
ERROR: Removing 'iwlagn': Operation not permitted[/B][/COLOR]
ubuntu@ubuntu:~$ **[COLOR=Blue]sudo[/COLOR]** rmmod [COLOR=DarkGreen]**iwlagn**[/COLOR]
ubuntu@ubuntu:~$ [COLOR=Red][B]modprobe iwlagn 11n_disable=0
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Operation not permitted[/B][/COLOR]
ubuntu@ubuntu:~$** [COLOR=Blue]sudo[/COLOR] modprobe [COLOR=DarkGreen]iwlagn[/COLOR] 11n_disable=0**
ubuntu@ubuntu:~$ **[COLOR=Blue]sudo[/COLOR] modprobe [COLOR=DarkGreen]iwlagn [/COLOR]**
ubuntu@ubuntu:~$ 

```However, it gets stuck waiting for authorization. Connecting to my phones network (tethered) does not have this issue.

For changing kernel modules during runtime, you should always need a "sudo" command under Ubuntu, and the only lines that should have actually made any changes are highlighted with the blue[COLOR=Blue]** sudo**[/COLOR] above.

I translate the above that you removed (**rmmod**) the [COLOR=DarkGreen]**iwlagn**[/COLOR] module once, then added it twice (with **[COLOR=Blue]sudo[/COLOR] modprobe**).

So what does **lsmod | grep iwl** tell you is your current status now?  And **modinfo iwlagn**? And **cat /etc/modules** and **dpkg -l wire***?  Those really are NOT 'trivial' questions- they probably run though and/or surround your wireless troubles.

While we're at it, it would probably help to see this too:
```
dmesg | grep iwl
```

Edit:  this is Re: post #10 above (I see we must have cross-posted).

---

### Post by WinterMadness on 2011-11-15
```


joe@joe-U46:~$ lsmod | grep iwl 
iwlagn                314213  0 
mac80211              310872  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
```

```

joe@joe-U46:~$ modinfo iwlagn
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-105-5.ucode
firmware:       iwlwifi-2030-5.ucode
firmware:       iwlwifi-2000-5.ucode
srcversion:     F1AF2D897D96C14B77FE0BA
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000266bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000066bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000226bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004466bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004266bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004066bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004464bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004264bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004064bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004466bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004066bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004426bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004226bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004026bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        mac80211,cfg80211
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (bool)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
joe@joe-U46:~$ 
```

```
joe@joe-U46:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
# load kernel module iwlagn for Centrino Wireless-N
iwlagn
```

```
joe@joe-U46:~$ dpkg -l wire*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                       Version                                    Description
+++-==========================================-==========================================-====================================================================================================
ii  wireless-crda                              1.14                                       Wireless Central Regulatory Domain Agent
ii  wireless-tools                             30~pre9-5ubuntu1                           Tools for manipulating Linux Wireless Extensions
```

```
oe@joe-U46:~$ dmesg | grep iwl
[   12.694074] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.694077] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   12.694133] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.694144] iwlagn 0000:02:00.0: setting latency timer to 64
[   12.694181] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   12.704809] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   12.704812] iwlagn 0000:02:00.0: Device SKU: 0X9
[   12.704814] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.705063] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.705161] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
[   12.870639] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.872720] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1002.866499] iwlagn 0000:02:00.0: PCI INT A disabled
[ 1015.283047] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 1015.283058] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 1015.283201] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1015.283227] iwlagn 0000:02:00.0: setting latency timer to 64
[ 1015.283305] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[ 1015.294311] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[ 1015.294319] iwlagn 0000:02:00.0: Device SKU: 0X9
[ 1015.294323] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[ 1015.294382] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[ 1015.294532] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
[ 1015.298314] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[ 1015.299154] ieee80211 phy1: Selected rate control algorithm 'iwl-agn-rs'
[ 1335.900206] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 0
[ 1949.895609] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 0
[ 1956.303432] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = e0:91:f5:fd:1f:8e tid = 0

```

---

### Post by WinterMadness on 2011-11-15
as far as I can tell, the driver for my wireless has trouble with N networks and WPA2. If you dont see anything there, I think its good info to have.

---

### Post by northd_tech on 2011-11-15
> **WinterMadness said:**
> as far as I can tell, the driver for my wireless has trouble with N networks and WPA2. If you dont see anything there, I think its good info to have.
Yes,  it actually looks pretty good as far as the **iwlagn** module (and his 2 or 3 'friends') being loaded into the Linux kernel properly, the firmware appears to have loaded without any error messages, and those 2 lines being echo'ed onto the end of** /etc/modules** should make sure that your** iwlagn** module gets loaded at each boot.  All that stuff looks good.

I was expecting that the **wireless-tools** package wasn't there but it looks like you have that one installed too.  (As I recall, that is one of the main ones that handles your WEP and WPA/WPA2 authentication.).

I did just find this likely problem in an old helpfile though: let's take a look at:

```
dpkg -l wpa*
```

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

You might need to **sudo apt-get install wpasupplicant wpagui** if they are not there and if you have a working ethernet cable connection (or your router is still "open" WITHOUT authentication and the wireless is still connected), or if all else fails- download the appropriate .DEB file(s) here from another computer and use the trusty, old "USB stick and sneakers-NET":

These are for Onieric Ocelot Ubuntu 

[http://packages.ubuntu.com/oneiric/wpagui](http://packages.ubuntu.com/oneiric/wpagui)
[http://packages.ubuntu.com/oneiric/wpasupplicant](http://packages.ubuntu.com/oneiric/wpasupplicant)

This one is something for Oneiric (and newer) Ubuntu, and I've never seen it before- but it might be something needed for newer Ubuntu wireless to connect:
[http://packages.ubuntu.com/oneiric/wpasupplicant-udeb](http://packages.ubuntu.com/oneiric/wpasupplicant-udeb)

If that isn't really needed later, it is very easy to get rid of in Synaptic Pkg Manager (or is that Ubuntu Software in the newer versions).

Right now, the goal is to get your network secured, and WPA2 is probably one of the better protocols there (although WPS is REALLY easy with its ~2 minute pushbutton authentication, but I seem to recall it not being supported very well yet in Ubuntu).  Perhaps WPS is now better supported by the newer 11.xx versions of Ubuntu.

---

### Post by northd_tech on 2011-11-15
> **WinterMadness said:**
> 
I am using the latest version of Kubuntu, which im not familiar with, im used to an older version so if anyone has tips please help me.

Needless to say, it does connect to the network if I use the ethernet.

Hey, that answers that question about your ethernet cable (but you often needed to disconnect that and reboot Ubuntu to 'jump start' the wireless in 8.xx 9.xx and possibly 10.xx Ubuntu versions- but I don't think the newer versions of Network Manager or Wicd are so much that way anymore from what I have read).

As far as the "latest version of Kubuntu" let's take a look at the output from these commands to make sure I linked you to the correct wpasupplicant .DEB files above (Edit: IF you download them that way for **future safekeeping** <<<=== HINT HINT):

```
uname -a
cat /etc/lsb-release
```

---

### Post by WinterMadness on 2011-11-15
```
joe@joe-U46:~$ uname -a
Linux joe-U46 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
joe@joe-U46:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
joe@joe-U46:~$ 




```

---

### Post by northd_tech on 2011-11-15
> **northd_tech said:**
> 
I did just find this likely problem in an old helpfile though: let's take a look at:

```
dpkg -l wpa*
```[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

You might need to **sudo apt-get install wpasupplicant wpagui** if they are not there and if you have a working ethernet cable connection (or your router is still "open" WITHOUT authentication and the wireless is still connected)

Just reading through that old WPA Howto, I noticed a couple of Kubuntu-specific tidbits:

> **Kubuntu**

 Note that  for Kubuntu users, the Wireless Assistant Wireless LAN Manager, found in  the KMenu/Internet menu, does not integrate with WPA, and should not be  used. 
Kubuntu users should install the KDE version (from Kubuntu 6.0.6): 
sudo apt-get install knetworkmanagerKubuntu  (still 6.0.6) users should also skip the section on editing of files  and the section on password nagging, and activate kwalletmanager  instead. This means you will only get WPA when logged into KDE, but hey  ... (For instructions on how to do this, see [this link]("http://en.opensuse.org/Projects/KNetworkManager#How_can_I_store_passphrases_associated_with_encrypted_wireless_networks.3F")).  Log out and back in, and start KNetworkManager from the Internet menu.  In some rare cases WPA needs special setup, perhaps for the RT2500  chipset [WifiDocs/Driver/RalinkRT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") (i have not tried this but I have seen it in an office). 
Or for earlier versions of Kubuntu: 
sudo apt-get install network-manager-kde

> **Note  to Kubuntu users: No editing of files needed. Just make sure  wpasupplicant is installed and start knetworkmanager from the Internet  menu.**

Those were the only 2 that I read, but dinner just got served, so I might be gone for a while.

Good luck (and take good notes- Kubuntu is a little bit of a 'different beast' than what most people here use- I actually preferred xubuntu of the bunch, but I don't use it because it is a little too 'obscure' and doesn't 'play nice' with some of my other Ubuntu customizations).

---

### Post by northd_tech on 2011-11-15
> $ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=**11.10**
**DISTRIB_CODENAME=oneiric**
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Yep, it looks like I guessed the correct .DEB packages (but the **sudo apt-get install wpasupplicant wpagui**) is still probably your easiest & best way to get the correct versions.

Edit:  Oh yes, you are also running a 64bit (amd64 packages needed) Linux kernel from **uname -a** output.

---

### Post by WinterMadness on 2011-11-15
okay, so I have the wpa supplicant, but it doesnt seem to be changing anything.

---

### Post by WinterMadness on 2011-11-16
im starting to think the solution is to not use wlagn, but rather iwlwifi

how do I try that out? It says my kernel should have it already

---

### Post by northd_tech on 2011-11-16
So you did already have wpasupplicant or you recently installed it?  Perhaps there is some configuration SNAFU there.  Also, I still haven't heard whether you are trying to connect using WEP, WPA, WPA2, WPS, or some other more exotic wireless authentication method that I haven't heard of yet- that might help in a search.

I still suspect this might be a Kubuntu-specific problem (but that HOWTO was ANCIENT by computer standards, so we might have to do some deep digging far & wide.  I don't know of a Kubuntu forum *per se* (I think this might be it actually).  

Looking back at your original **lsmod** output to see if there is an "asus" or other 'soft-key' module interfering, I'm wondering about the **mei** and **arc4** modules that load around when/where your [COLOR=DarkGreen]**iwlagn**[/COLOR] wireless module does- what does this command tell us:

```
modinfo mei
modinfo arc4

```You also have a **bluetooth** module with **rfcomm** and **bnep**, but I don't think that is really the problem here.

Let's also see:

```
rfkill list all
```I'm at something of a loss here as to the authentication failure(s).  Are you sure you don't have a MAC address deny/allow thing going on in your wireless router?  (I actually prefer to set things up with "Allow MAC address(es):" enabled for the known wireless devices in a network- it's theoretically "more secure" that way and it often results in faster connect times for me.)  But that's a little too complicated for your setup tonight- you're probably more tired of this than I am.  :(

You might want to search this forum for Intel Centrino wireless and authentication failure [for WEP, WPA, WPA2, etc.]  You might want to piggyback on one of those relevant threads or start a new one (now that we have your Centrino wireless 'seeing' the network, the thread title is no longer accurate to your wireless router authentication problem.

I'm fairly sure this is a problem "downstream" from your wireless module though.

Let's see what this command tells us:

[HTML]nm-tool[/HTML]Looking back at that old Howto page, I think we might need to get rid of the [GNOME] Network Manager stuff and get you some KDE-specific packages.

SHAZAM!!- the 3rd time I skimmed/read that old WPA Howto- LOOK what I found!!!:
[B]
WiFiDocs: WPA Howto: [COLOR=Red]Kubuntu[/COLOR][/B]

[LIST]
[*][Kubuntu]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu?action=fullsearch&context=180&value=linkto%3A%22WifiDocs%2FWPAHowTo%2FKubuntu%22")
[/LIST]
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

That looks MUCH better- scroll down to the "Easy Steps..." part:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu#Easy_Steps_to_get_WPA_to_Work_on_Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu#Easy_Steps_to_get_WPA_to_Work_on_Kubuntu)

You will probably still need to blast the GNOME Network Manager settings (& packages) out, but let's get those KDE packages loaded in there and see if that helps.

---

### Post by northd_tech on 2011-11-16
> **WinterMadness said:**
> im starting to think the solution is to not use wlagn, but rather iwlwifi

how do I try that out? It says my kernel should have it already

Well according to Debian (where Ubuntu derives from and consequently Kbuntu as well):

[http://wiki.debian.org/iwlwifi](http://wiki.debian.org/iwlwifi)

> For support of the Intel Wireless WiFi Link 5000, **6000** and 1000 **series** of devices, see [iwlagn]("http://wiki.debian.org/iwlagn"). Also, I don't see your Intel Centrino WiMax 6150 listed there under "supported devices."

Let's see what numbers this gives us:

```
lspci -vvnn | grep trino
```Karnak the Debnificent predicts one of:

> PCI: 8086:**0885 **Intel Corporation Centrino Wireless-N + WiMAX 6150
PCI: 8086:**0886** Intel Corporation Centrino Wireless-N + WiMAX 6150
[http://wiki.debian.org/iwlagn#Supported_Devices](http://wiki.debian.org/iwlagn#Supported_Devices)

Since you did get it to finally see the wireless router 'radio' while unsecured or "open," I'm reasonably certain this is an authentication ONLY problem NOW (I'm not sure that was always true though- the modules took a little work).

---

### Post by northd_tech on 2011-11-16
> **northd_tech said:**
> 
Looking back at your original **lsmod** output to see if there is an "asus" or other 'soft-key' module interfering, I'm wondering about the **mei** and **arc4** modules that load around when/where your [COLOR=DarkGreen]**iwlagn**[/COLOR] wireless module does- what does this command tell us:

```
modinfo mei
modinfo arc4

```

Posts #4, 5, & 6 on this other thread (as well as much experience with Dell, Toshiba, & HP laptops with "soft-keys") is why I was thinking about that possibility:

[http://ubuntuforums.org/showpost.php?p=11123017&postcount=5](http://ubuntuforums.org/showpost.php?p=11123017&postcount=5)

---

### Post by WinterMadness on 2011-11-16
Its not that I can see the network when I remove security, on the contrary, I can see it pretty consistently right now. The problem is that I cant connect to it because the driver apparently has issues with WPA2 (this is the protocol im using)

```
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
        Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
joe@joe-U46:~$ 

```

```

joe@joe-U46:~$ modinfo mei
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/staging/mei/mei.ko
version:        7.1.20.1
license:        GPL v2
description:    Intel(R) Management Engine Interface
author:         Intel Corporation
srcversion:     0A1192D3177950D60ACC4F4
alias:          pci:v00008086d00001DBAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001CBAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001E3Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001D3Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001C3Asv*sd*bc*sc*i*
alias:          pci:v00008086d00003B65sv*sd*bc*sc*i*
alias:          pci:v00008086d00003B64sv*sd*bc*sc*i*
alias:          pci:v00008086d00002E34sv*sd*bc*sc*i*
alias:          pci:v00008086d00002E24sv*sd*bc*sc*i*
alias:          pci:v00008086d00002E14sv*sd*bc*sc*i*
alias:          pci:v00008086d00002E04sv*sd*bc*sc*i*
alias:          pci:v00008086d00002A74sv*sd*bc*sc*i*
alias:          pci:v00008086d00002A64sv*sd*bc*sc*i*
alias:          pci:v00008086d00002A54sv*sd*bc*sc*i*                                                                                                                                            
alias:          pci:v00008086d00002A44sv*sd*bc*sc*i*                                                                                                                                            
alias:          pci:v00008086d000028F4sv*sd*bc*sc*i*                                                                                                                                            
alias:          pci:v00008086d000028E4sv*sd*bc*sc*i*                                                                                                                                            
alias:          pci:v00008086d000028D4sv*sd*bc*sc*i*
alias:          pci:v00008086d000028C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000028B4sv*sd*bc*sc*i*
alias:          pci:v00008086d000029F4sv*sd*bc*sc*i*
alias:          pci:v00008086d000029E4sv*sd*bc*sc*i*
alias:          pci:v00008086d000029D4sv*sd*bc*sc*i*
alias:          pci:v00008086d000029C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000029B4sv*sd*bc*sc*i*
alias:          pci:v00008086d00002A14sv*sd*bc*sc*i*
alias:          pci:v00008086d00002A04sv*sd*bc*sc*i*
alias:          pci:v00008086d000029A4sv*sd*bc*sc*i*
alias:          pci:v00008086d00002994sv*sd*bc*sc*i*
alias:          pci:v00008086d00002984sv*sd*bc*sc*i*
alias:          pci:v00008086d00002974sv*sd*bc*sc*i*
depends:        
staging:        Y
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           watchdog_timeout:Intel(R) AMT Watchdog timeout value in seconds. (default=120, disable=0) (ushort) 
```

```
joe@joe-U46:~$ modinfo arc4
filename:       /lib/modules/3.0.0-12-generic/kernel/crypto/arc4.ko
author:         Jon Oberheide <jon@oberheide.org>
description:    ARC4 Cipher Algorithm
license:        GPL
srcversion:     0E7B177AF22D87B5B21A577
depends:        
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
joe@joe-U46:~$ 

```

---

### Post by WinterMadness on 2011-11-16
ok im very confused. I dunno what happened, but right now its working with security enabled.

Im going to restart the computer and see if it continues to work.

edit: I restarted, and it worked. I really hope this stays this way. Though it should be noted that I cant always boot properly because of ACPI, sometimes I get nothing, other times a cursor. I rebooted three times, on the third time kubuntu loaded and the wireless worked.

I pretty much did everything in this thread, and I also loaded the firmware I talked about by moving the .ucode file supplied by the intel linux website to lib/firmware

---

### Post by northd_tech on 2011-11-16
> **modinfo mei**
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/staging/mei/mei.ko
version:        7.1.20.1
license:        GPL v2
description:    Intel(R) Management Engine Interface
author:         Intel Corporation
OK- so we apparently know that kernel module **mei** comes from Intel and it "manages" something... :confused:

I was reading another thread about Intel Centrino wireless, but it was for a different series number.  Back to your thought last night- let's look a little closer at that iwlagn module itself:

```
modinfo iwlagn
```Let's also take a look at the firmware files too:

```
ls -la /lib/firmware | egrep 'iwl|ucode'
```I was a little bit surprised to see that I have those same firmware files in my (much 'older' ) Ubuntu 10.04 distro that I saw listed on that Intel Centrino 6250 thread nearby:

> **ls -la /lib/firmware | egrep 'iwl|ucode'**
-rw-r--r--  1 root root  335056 2010-12-14 09:25 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  337520 2011-04-06 13:39 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root  150100 2010-12-14 09:25 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-14 09:25 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-14 09:25 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-14 09:25 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  340696 2011-03-03 09:00 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 2010-12-14 09:25 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  462280 2010-12-14 09:25 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 07:26 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 07:26 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2011-03-03 09:00 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-14 09:26 iwlwifi-6050-5.ucode
I do find it strange that I don't see unique Cetnrino/WiMAX 6150, 6230, and 6250 firmware listed there though (if the iwlwifi-**6000-4**.ucode, 6050-4, 6050-5, etc. numbers mean what I'm guessing they do).  Of course, there is no reason why 6100 or 6200 series wireless circuits could not use the 'earlier' 6000-series firmware (or 6000g2a-5 or 6000g2b-5, etc.)  I'll assume that is the case for right now and chalk that one up as one of life's unsolved mysteries.

Unfortunately, I'm going to need to hit the road and go get some work done for a couple of days, so I likely won't be frequenting this thread.  It is also unfortunate that so many people here apparently avoid Kubuntu.  My current Ubuntu install is a bit of a 'hybrid' with both KDE and GNOME-based packages installed, and 2 of my older Ubuntu hybrid installs actually had KDE desktops that could be selected at boot time (making it a "Kubuntu" in appearance, function, and fact, I believe).  I have a 'newer' Ubuntu hybrid version installed though that only has a "Kwin" window manager selectable through Compiz.  My system is still predominantly built upon and of GNOME components.

I still suspect this WPA2 authentication issue involves a GNOME **package or configuration syntax/script **not 'playing well' with the Kubuntu system.  I've been burned by the GNOME Network Manager before, and I find myself leaning towards the Wicd wireless tool time and time again (I'm just not sure it works under or has a Kubuntu version that will 'play nice' with Kubuntu 11.xx Oneiric Ocelot).

There apparently is a fairly recent KDE[4] Wicd client (but it looks like one needs to compile it from sourcecode and it depends upon Cmake- which has been 'buggy' and difficult for me in the past).  The INSTALL script looks pretty complete though.

[http://kde-apps.org/content/show.php?content=132366](http://kde-apps.org/content/show.php?content=132366)

I've had much better results with Wicd than with "Network Manager" in the past, and I fully intend to install Wicd again when I get the time to mess with it.  I'm not sure how the Kubuntu factor plays into all this though- but it's at least an option.

Speaking of options, there is also NOT using Network Manager at all and doing a Manual Network Configuration (but these aren't recommended for computers that move around from place to place and 'talk' to different wireless 'radios' for security reasons).

**      How To: Manual Network Configuration without the need for Network Manager**
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

That is kind of a 'last resort' though.

---

### Post by northd_tech on 2011-11-16
```

```> **WinterMadness said:**
> ok im very confused. I dunno what happened, but right now its working with security enabled.

Im going to restart the computer and see if it continues to work.

edit: I restarted, and it worked. I really hope this stays this way. Though it should be noted that I cant always boot properly because of ACPI, sometimes I get nothing, other times a cursor. I rebooted three times, on the third time kubuntu loaded and the wireless worked.

I pretty much did everything in this thread, and I also loaded the firmware I talked about by moving the .ucode file supplied by the intel linux website to lib/firmware

I see we cross-posted again.  Well I'm glad it worked at least twice, but I'm still scratching my head about what got changed in your setup.  I would look a lot closer at those firmware files and compare to some of those other Intel Centrino wireless setups (which will almost certainly be running Ubuntu 'proper,' not Kubuntu).

Which website did you get the firmware from?  Maybe it is a newer (or WiMAX 6150-specific) version.

Edit:  let's see what this tells us about the wireless and its firmware loading:
```
dmesg | egrep 'iwl|irmware|trino'
```

---

