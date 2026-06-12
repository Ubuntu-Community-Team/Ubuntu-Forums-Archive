---
title: "Wireless detected only when plugged in the LAN cable"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by ping128 on 2012-05-21
Hey, I have been tried fixing this problem for 4 days, but I still have the problem. My laptop is Dell 14R with Ubuntu 12.04. I install all the update hardware, but the wireless works only after I plug in the LAN cable and reboot it. How can I solve it?

---

### Post by ping128 on 2012-05-21
ping128@admin:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"thehousejew"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:01:58:B4   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:49   Missed beacon:0

eth0      no wireless extensions.

ping128@admin:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ping128@admin:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  12 
bnep                   17830  2 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31775  1 
btusb                  17912  2 
bluetooth             158438  23 rfcomm,bnep,btusb
bcma                   25651  0 
arc4                   12473  2 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_realtek   174055  1 
dcdbas                 14098  0 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72919  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
intel_ips              17753  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
wmi                    18744  1 dell_wmi
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19068  0 
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
radeon                733693  3 
brcmutil               14675  1 brcmsmac
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
cfg80211              178679  2 brcmsmac,mac80211
drm                   197692  5 radeon,ttm,drm_kms_helper
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
mei                    36570  0 
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
atl1c                  36718  0 
ping128@admin:~$

---

### Post by ping128 on 2012-05-21
You see it's working because I plugged in LAN cable first. It's like LAN cable can activate it.

---

### Post by kevdog on 2012-05-21
ifconfig
lshw -C network

---

### Post by wildmanne39 on 2012-05-21
Hi, when you have the wired connection plugged in it overrides the wirless so I doubt that it is actually connecting through the wireless.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ping128 on 2012-05-21
```

ping128@admin:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ping128-Inspiron-N4010 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux
ping128@admin:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
--
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0456]
    Kernel driver in use: atl1c
ping128@admin:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 004: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
ping128@admin:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:202  Noise level:160
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

eth0      no wireless extensions.

ping128@admin:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ping128@admin:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31775  1 
lib80211_crypt_tkip    17275  0 
btusb                  17912  2 
bluetooth             158438  23 rfcomm,bnep,btusb
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_hda_codec_realtek   174055  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32765  7 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
video                  19068  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
wmi                    18744  1 dell_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
radeon                733693  3 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  0 
snd                    62064  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
uvcvideo               67203  0 
psmouse                72919  0 
serio_raw              13027  0 
intel_ips              17753  0 
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
videodev               86588  1 uvcvideo
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
uas                    17699  0 
usb_storage            39646  1 ums_realtek
atl1c                  36718  0 

```

---

### Post by ping128 on 2012-05-21
another thing
```
ping128@admin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:6e:34:7f  
          inet addr:128.208.117.21  Bcast:128.208.117.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe6e:347f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59085 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:151035957 (151.0 MB)  TX bytes:5542086 (5.5 MB)
          Interrupt:46 

eth1      Link encap:Ethernet  HWaddr 70:f1:a1:ba:b4:40  
          inet addr:128.208.117.178  Bcast:128.208.117.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:feba:b440/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22567 errors:0 dropped:0 overruns:0 frame:220774
          TX packets:57 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3177819 (3.1 MB)  TX bytes:11555 (11.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16502 (16.5 KB)  TX bytes:16502 (16.5 KB)

ping128@admin:~$ 
ping128@admin:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 70:f1:a1:ba:b4:40
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=128.208.117.178 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:6e:34:7f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=128.208.117.21 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f0200000-f023ffff ioport:3000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by ping128 on 2012-05-21
Now everything is working. The wireless doesn't work when I restart my laptop without plugging in the wired connection.

---

### Post by kevdog on 2012-05-21
I'm a little confused what you want?

Do you want to use the wired connection?

Let's say you get your wireless to work by plugging in your wired connection, if you
sudo ifconfig eth0 down

does the wireless still work?

I'm not very experienced with the wl module that his current chipset uses.  It seems its loading at boot based on the lsmod statement, however something isn't right.  If after you boot, have you taken a look at dmesg or tail -50 /var/log/syslog.  Does anything in these log files give a clue?

---

### Post by ping128 on 2012-05-21
> **kevdog said:**
> I'm a little confused what you want?

Do you want to use the wired connection?

Let's say you get your wireless to work by plugging in your wired connection, if you
sudo ifconfig eth0 down

does the wireless still work?

I'm not very experienced with the wl module that his current chipset uses.  It seems its loading at boot based on the lsmod statement, however something isn't right.  If after you boot, have you taken a look at dmesg or tail -50 /var/log/syslog.  Does anything in these log files give a clue?

I just want to use Wireless connection. But my laptop doesn't detect any wireless unless I plug in the wire connection first and reboot it. How to make the wireless enable without plugging in the wired connection?

And after I "sudo ifconfig eth0 down", the wireless is working fine. The problem is how I can make the wireless working without plug in the wired connection at the first place.

---

### Post by wildmanne39 on 2012-05-21
The lsmod information that you posted the first time is completely different concerning the wireless driver loaded from the second one did you uninstall one driver and install another?
Thanks

---

### Post by ping128 on 2012-05-22
Yes, I think I installed Broadcom STA wireless driver, but it still didn't work.

---

### Post by wildmanne39 on 2012-05-22
Hi, disconnect your wired connection so you do not have a wireless or wired connection then run these commands and post the output here please:
```
nm-tool
sudo iwlist scan
lsmod | grep wl
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware - wpa -e eth1 -e etork | tail -n55
```
Thanks

---

### Post by ping128 on 2012-05-22
Hi, this is what I get

> nm-tool
sudo iwlist scan
lsmod | grep wl```

ping128@admin:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        B8:AC:6F:6E:34:7F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        70:F1:A1:BA:B4:40

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


ping128@admin:~$ sudo iwlist scan
[sudo] password for ping128: 
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

ping128@admin:~$ lsmod | grep wl
ping128@admin:~$ 
ping128@admin:~$ 


```> sudo cat /var/log/syslog | grep -e wl -e firmware - wpa -e eth1 -e etork | tail -n55```
ping128@admin:~$ sudo cat /var/log/syslog | grep -e wl -e fireware - wpa -e eth1 -e etrok | tail -n5
grep: wpa: No such file or directory
(standard input):May 22 12:46:27 ping128-Inspiron-N4010 kernel: [  214.969006] ieee80211 phy0: wl0: fatal error, reinitializing
(standard input):May 22 12:46:28 ping128-Inspiron-N4010 kernel: [  215.967249] ieee80211 phy0: wl0: fifo 0: descriptor error
(standard input):May 22 12:46:28 ping128-Inspiron-N4010 kernel: [  215.967258] ieee80211 phy0: wl0: fatal error, reinitializing
(standard input):May 22 12:46:29 ping128-Inspiron-N4010 kernel: [  216.965532] ieee80211 phy0: wl0: fifo 0: descriptor error
(standard input):May 22 12:46:29 ping128-Inspiron-N4010 kernel: [  216.965539] ieee80211 phy0: wl0: fatal error, reinitializing
ping128@admin:~$ 

```I think I messed up my laptop. I won't do anything more, and follow your step.

This morning, I opened my laptop without wired connection. My wireless just works fine. Surprise! Then I restarted it. It didn't work again.

---

### Post by wildmanne39 on 2012-05-22
Hi, please do the following with the wired connection plugged in and just copy and paste for accuracy:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
``` 
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Watch for errors when it is done reboot.
Thanks

---

### Post by ping128 on 2012-05-22
Now I get this.
```

ping128@admin:~$ echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist bcma
ping128@admin:~$ echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist brcmsmac

```I'm doing the third quote.

```

ping128@admin:~$ sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  firefox-locale-zh-hans
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  diffstat module-assistant quilt
Suggested packages:
  procmail graphviz default-mta mail-transport-agent
The following NEW packages will be installed:
  broadcom-sta-common broadcom-sta-source diffstat module-assistant quilt
0 upgraded, 5 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 2,385 kB/3,588 kB of archives.
After this operation, 3,525 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse broadcom-sta-common all 5.100.82.112-4 [9,556 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main diffstat i386 1.54-1 [21.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main quilt all 0.50-2 [287 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse broadcom-sta-source all 5.100.82.112-4 [1,966 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/universe module-assistant all 0.11.4 [101 kB]
Fetched 2,385 kB in 2s (1,019 kB/s)       
(Reading database ... 188805 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Selecting previously unselected package broadcom-sta-common.
Unpacking broadcom-sta-common (from .../broadcom-sta-common_5.100.82.112-4_all.deb) ...
Selecting previously unselected package diffstat.
Unpacking diffstat (from .../diffstat_1.54-1_i386.deb) ...
Selecting previously unselected package quilt.
Unpacking quilt (from .../archives/quilt_0.50-2_all.deb) ...
Selecting previously unselected package broadcom-sta-source.
Unpacking broadcom-sta-source (from .../broadcom-sta-source_5.100.82.112-4_all.deb) ...
Selecting previously unselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.11.4_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.2.0-24-generic-pae
Building for architecture i686
Building initial module for 3.2.0-24-generic-pae
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up broadcom-sta-common (5.100.82.112-4) ...
update-initramfs: deferring update (trigger activated)
Setting up diffstat (1.54-1) ...
Setting up quilt (0.50-2) ...
Setting up broadcom-sta-source (5.100.82.112-4) ...
Setting up module-assistant (0.11.4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
ping128@admin:~$ 


```

---

### Post by ping128 on 2012-05-22
After I reboot it, there was no any errors.

Then, I run.

```

ping128@admin:~$ sudo cat /var/log/syslog | grep -e wl -e firmware - wpa -e eth1 -e etork | tail -n55 
[sudo] password for ping128: 
grep: wpa: No such file or directory
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): bringing up device.
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 kernel: [   14.896794] ADDRCONF(NETDEV_UP): wlan0: link is not ready
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): preparing device.
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): deactivating device (reason 'managed') [2]
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 kernel: [   14.897589] ADDRCONF(NETDEV_UP): wlan0: link is not ready
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: starting -> ready
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
(standard input):May 22 13:06:48 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: ready -> inactive
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) starting connection 'thehousejew'
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0/wireless): connection 'thehousejew' has security, and secrets exist.  No new secrets needed.
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
(standard input):May 22 13:06:49 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: inactive -> scanning
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 kernel: [   17.057189] wlan0: authenticate with 58:6d:8f:01:58:b4 (try 1)
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: scanning -> authenticating
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 kernel: [   17.066511] wlan0: authenticated
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: authenticating -> associating
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 kernel: [   17.070167] wlan0: associate with 58:6d:8f:01:58:b4 (try 1)
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 kernel: [   17.090007] wlan0: RX AssocResp from 58:6d:8f:01:58:b4 (capab=0x411 status=0 aid=2)
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 kernel: [   17.090014] wlan0: associated
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 kernel: [   17.090739] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: associating -> associated
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'thehousejew'.
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 dhclient: Listening on LPF/wlan0/70:f1:a1:ba:b4:40
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 dhclient: Sending on   LPF/wlan0/70:f1:a1:ba:b4:40
(standard input):May 22 13:06:50 ping128-Inspiron-N4010 dhclient: DHCPREQUEST of 128.208.117.178 on wlan0 to 255.255.255.255 port 67
(standard input):May 22 13:06:52 ping128-Inspiron-N4010 avahi-daemon[954]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:feba:b440.
(standard input):May 22 13:06:52 ping128-Inspiron-N4010 avahi-daemon[954]: New relevant interface wlan0.IPv6 for mDNS.
(standard input):May 22 13:06:52 ping128-Inspiron-N4010 avahi-daemon[954]: Registering new address record for fe80::72f1:a1ff:feba:b440 on wlan0.*.
(standard input):May 22 13:06:53 ping128-Inspiron-N4010 dhclient: DHCPREQUEST of 128.208.117.178 on wlan0 to 255.255.255.255 port 67
(standard input):May 22 13:06:53 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
(standard input):May 22 13:06:53 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
(standard input):May 22 13:06:53 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
(standard input):May 22 13:06:53 ping128-Inspiron-N4010 avahi-daemon[954]: Joining mDNS multicast group on interface wlan0.IPv4 with address 128.208.117.178.
(standard input):May 22 13:06:53 ping128-Inspiron-N4010 avahi-daemon[954]: New relevant interface wlan0.IPv4 for mDNS.
(standard input):May 22 13:06:53 ping128-Inspiron-N4010 avahi-daemon[954]: Registering new address record for 128.208.117.178 on wlan0.IPv4.
(standard input):May 22 13:06:54 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
(standard input):May 22 13:06:55 ping128-Inspiron-N4010 NetworkManager[913]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
(standard input):May 22 13:06:55 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) successful, device activated.
(standard input):May 22 13:06:55 ping128-Inspiron-N4010 NetworkManager[913]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
(standard input):May 22 13:07:01 ping128-Inspiron-N4010 kernel: [   28.026661] wlan0: no IPv6 routers present
ping128@admin:~$ 

```

---

### Post by wildmanne39 on 2012-05-22
Hi, does your wireless work now? did it come on? you have to enter you long password.
Thanks

---

### Post by ping128 on 2012-05-22
The wireless is working, because It's plugged in the wired connection. Do you want me to unplug it and reboot?

---

### Post by wildmanne39 on 2012-05-22
Hi, yes please.

---

### Post by ping128 on 2012-05-22
It's weird.
I rebooted it, but it didn't finish rebooting. It just stopped at some point with nothing on the screen, so I had to manually turn off. I turned it on again without wired connection. The wireless didn't work. So I restarted it again with wired connection, the wireless's working.

---

### Post by wildmanne39 on 2012-05-22
Hi, strange please post the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by ping128 on 2012-05-22
```
ping128@admin:~$ 
ping128@admin:~$ cat /etc/modprobe.d/blacklist.conf
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
blacklist bcm43xx

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
blacklist dell-laptop
blacklist dell-laptop
blacklist wl
blacklist bcma
blacklist bcma
blacklist bcma
blacklist bcma
blacklist brcmsmac
ping128@admin:~$ 

```
Thanks.

---

### Post by wildmanne39 on 2012-05-22
Hi, we need to remove the wl driver from the blacklist please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
then remove this complete line [COLOR="Red"]blacklist wl[/COLOR]
save and close gedit then reboot with the wired connection unplugged.
Thanks

---

### Post by ping128 on 2012-05-22
The wireless still doesn't work. The triangle is empty.

---

### Post by wildmanne39 on 2012-05-22
Hi, please post a screenshot of your network manger icon drop down menu it should look like this.

Also post the output of:
```
lsmod | grep wl
sudo iwlist scan
```
Thanks

---

### Post by ping128 on 2012-05-22
With my wireless working, I get 
```
ping128@admin:~$ lsmod | grep wl
wl                   2646601  0 
lib80211               14040  1 wl

```

for "sudo iwlist scan", it's too long to fit in the terminal, I just redirect it to a file.
```
wlan0     Scan completed :
          Cell 01 - Address: 58:6D:8F:01:58:B4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"thehousejew"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002375cefe40
                    Extra: Last beacon: 132ms ago
                    IE: Unknown: 000B746865686F7573656A6577
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B000103104700109A003DDF296BD0330670EA3A2488A79C10210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: A6:79:77:9B:0C:95
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000008682ff6d24
                    Extra: Last beacon: 1056ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
          Cell 03 - Address: 00:13:10:C7:91:F9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Black Mesa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bd952b493
                    Extra: Last beacon: 884ms ago
                    IE: Unknown: 000A426C61636B204D657361
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0706555349010B1A
                    IE: Unknown: 0C120F0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD15000AF50A02E0C000030103050E04FF000100110101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010F0003A4000027A4000042435E0062322F00
          Cell 04 - Address: 64:80:99:1E:19:59
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WIN-KUH7OQOD3IB-61830"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=01cd3850dbf18068
                    Extra: Last beacon: 1044ms ago
                    IE: Unknown: 001557494E2D4B5548374F514F443349422D3631383330
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD0B0017350101000000000000
          Cell 05 - Address: 68:7F:74:3A:A0:D2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Cisco87328"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005f32b3c62d
                    Extra: Last beacon: 976ms ago
                    IE: Unknown: 000A436973636F3837333238
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD6B0050F204104A00011010440001021041000100103B0001031047001019E2A1958F93042E1FA46663ACFE47D5102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081100000000000000000000000000000000000000
          Cell 06 - Address: 58:6D:8F:50:15:70
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"ShyTiger"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bbf672ae0c
                    Extra: Last beacon: 968ms ago
                    IE: Unknown: 00085368795469676572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001054F6B98D00A968CE1CC6EFCEF79ADA10102100074C696E6B7379731023000D4C696E6B7379732045323530301024000776312E302E30301042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 08:86:3B:54:54:5F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"belkin.45f"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015643a9384
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 000A62656C6B696E2E343566
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B00010310470010EA09874CCC4C63683B680F62E5E9EC211021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303520763110240007312E30302E30331042000E31323131323947453131363836351054000800060050F20400011011001D42656C6B696E204E343530444220576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 58:6D:8F:50:15:72
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"ShyTiger-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bbf673a8b8
                    Extra: Last beacon: 904ms ago
                    IE: Unknown: 000E53687954696765722D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 2E:25:B3:88:97:BE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=ffffff4c17828a6f
                    Extra: Last beacon: 620ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020011000000
          Cell 10 - Address: 00:25:9C:D4:5A:5E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"juliakayla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00015c0b0b377180
                    Extra: Last beacon: 852ms ago
                    IE: Unknown: 000A6A756C69616B61796C61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 11 - Address: 5C:D9:98:5A:6A:6C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Miley 570"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000df97a2ef
                    Extra: Last beacon: 684ms ago
                    IE: Unknown: 00094D696C657920353730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071900000000000000000000000000000000000000
                    IE: Unknown: 3D1606071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000000000000100000005CD9985A6A6C10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363031104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363031100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 12 - Address: 00:23:69:C9:F7:FE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"LHC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c066cee89
                    Extra: Last beacon: 808ms ago
                    IE: Unknown: 00034C4843
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B0001031047001000000000000010000000002369C9F7FE1021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303110420001301054000800060050F20400011011000757525435344732100800020084103C000101
          Cell 13 - Address: 02:28:28:5C:70:5B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"HPD110a.57449F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000a320b7c24a
                    Extra: Last beacon: 740ms ago
                    IE: Unknown: 000E485044313130612E353734343946
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
          Cell 14 - Address: 20:4E:7F:BB:46:BF
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f412fbc554
                    Extra: Last beacon: 724ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD270050F204104A000110104400010210470010AE554F423E5F01E11E1F9CE0E895A125103C000103
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: 98:FC:11:8F:16:02
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Skynet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000090119df830
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 0006536B796E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000


```

---

### Post by wildmanne39 on 2012-05-22
Hi, what is the brand of your computer?

Can you run those commands when you can not connect please.

---

### Post by ping128 on 2012-05-22
My computer is Dell inspiron 14R, N4010.
I run those commands when I can't connect already. It's in the first picture.

It's strange that only way I can make my wireless working is to plug the wired connection and restart my laptop.
After that, it will work fine, even though I unplug my wired connection later.

---

### Post by ping128 on 2012-05-22
I also notice that sometimes my wireless's just up without wired connection. It's about 10%.

---

### Post by wildmanne39 on 2012-05-22
Hi please do:
```
sudo rmmod -f dell_wmi
```
when you can not connect wirelessly and tell me if it comes on.

This command is for testiung so if you reboot it will wipe out the changes made by the command but if it works will can make it permmanent.
Thanks

---

### Post by ping128 on 2012-05-22
After pressing Enter, nothing happens. I don't know why wired connection makes the wireless working.

---

### Post by ping128 on 2012-05-22
I somehow tried rebooting it again without the wired connection, and the wireless detected...sometimes it doesn't. I think all we are doing it correct. It just doesn't work all times. haha anyway thank you very much for helping me

Another good way is after I turn on my computer, and the wireless doesn't start searching. I fix it by suspendIng my laptop, then log in back again. It's working every time I did it!

---

### Post by wildmanne39 on 2012-05-22
Hi, try this when it will not work.
```
sudo modprobe wl
```
Thanks

---

### Post by ping128 on 2012-05-22
Hey, somehow I got it working. I didn't really know what we did make it working. But now it starts to work fine all the time without the wired cable. Thank you very much!!!

---

### Post by kevdog on 2012-05-22
Great help but gosh darn how i hate threads like these!

---

### Post by wildmanne39 on 2012-05-22
Hi, your welcome I hope it stays working! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

