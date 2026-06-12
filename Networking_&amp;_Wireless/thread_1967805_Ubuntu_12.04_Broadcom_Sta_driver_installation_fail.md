---
title: "Ubuntu 12.04 Broadcom Sta driver installation failed"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by natethegreat131 on 2012-04-28
My computer is a HP Pavilion dm5.  On all previous releases of Ubuntu I would open up additional drivers, plug my computer into ethernet and install the driver and all would be fine.  Now when I do that I get:

"Sorry, installation of this driver failed.  Please have a look at the log file for details: /var/log/jockey.log"

Thanks in Advance - Natethegreat131

---

### Post by chili555 on 2012-04-28
Please see here: [http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey](http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey)

If your pci.id is the same, please proceed. If it's different, post it here and we'll work out a fix.

---

### Post by victorano on 2012-05-01
Thanks, this solution fixed my pci.id [14e4:4315]

---

### Post by sergidelmoral on 2012-05-04
that works on my pc!
thank you very very much

toshiba portege r700 with same broadcom

:)

---

### Post by tarsofagundes on 2012-06-18
works on my notebook dell inspiron 1428 !!! :P:P

---

### Post by edub9 on 2012-06-18
[B]Broadcom STA Wireless drivers not working on Dell inspiron 1440, Ubuntu 12.04 live thumbdrive with persistence enabled. My pcid is [14e4:4315]

it was working right after i installed and ran the system for the first time but not after. :confused:
[/B]

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

Also please use normal font's
Thank you

---

### Post by rishipopat on 2012-08-12
Hi Everyone,

I am a newbee to the Linux world and would need some help. I have a Dell Studio and have installed Ubuntu 12.04 on it. I cannot connect to wireless networks

Following is the outputs of the commands I ran. Please let me know what are my next steps

[FONT=monospace]_**cat /etc/lsb-release; uname -a**_

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


_**lspci -nnk | grep -iA2 net**_
04:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card [1028:000d]
    Kernel driver in use: wl
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:029f]
    Kernel driver in use: tg3

_**lsusb**_
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63fa Microdia 
Bus 002 Device 002: ID 05ac:1294 Apple, Inc. iPhone 3GS
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick



_**iwconfig**_
lo        no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

eth0      no wireless extensions.

_** rfkill list all**_
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

_** lsmod**_
root@ubuntu:~# lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
ipheth                 13526  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 47199  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
r852                   18277  0 
sm_common              16865  1 r852
uvcvideo               72627  0 
nand                   54955  2 r852,sm_common
videodev               98259  1 uvcvideo
nand_ids               12723  1 nand
v4l2_compat_ioctl32    17128  1 videodev
hid                    99559  1 usbhid
mtd                    33087  2 sm_common,nand
r592                   18144  0 
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87603  0 
memstick               16569  1 r592
nand_ecc               13230  1 nand
serio_raw              13211  0 
i915                  468651  3 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ir_lirc_codec          12859  0 
drm_kms_helper         46978  1 i915
lirc_dev               19204  1 ir_lirc_codec
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
ir_mce_kbd_decoder     12777  0 
snd_timer              29990  2 snd_pcm,snd_seq
ir_sony_decoder        12510  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_jvc_decoder         12507  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ir_rc6_decoder         12507  0 
rc_rc6_mce             12502  0 
ir_rc5_decoder         12507  0 
wmi                    19256  1 dell_wmi
ite_cir                25775  0 
ir_nec_decoder         12507  0 
video                  19596  1 i915
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ite_cir,ir_nec_decoder
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
brcmsmac              570859  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac
usb_storage            49198  1 
uas                    18027  0 
firewire_ohci          41000  0 
sdhci_pci              18826  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci
tg3                   152032  0 
root@ubuntu:~# 
[/FONT]

---

### Post by chili555 on 2012-08-12
> I am a newbee to the Linux world and would need some help. I have a Dell Studio and have installed Ubuntu 12.04 on it. I cannot connect to wireless networksPlease do:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by rishipopat on 2012-08-12
Thanks for getting back to me. I ran the commands that you told me in a terminal window and then rebooted...nothing changed.

Was I supposed to do something else?

---

### Post by chili555 on 2012-08-12
> **rishipopat said:**
> Thanks for getting back to me. I ran the commands that you told me in a terminal window and then rebooted...nothing changed.

Was I supposed to do something else?Does it try to connect? What are your symptoms?

---

### Post by rishipopat on 2012-08-12
It does not try to connect nothing...last night I was getting the firmware not ready error...now I don't even get that...is there a step by step guide that I could follow to get my wireless working on a Dell laptop?

---

### Post by chili555 on 2012-08-12
There is no step-by-step because there are several different wireless cards supplied with Dell laptops. In order to figure out what to do, we need to follow a diagnostic process like we are here. Does your wireless card scan?```
sudo iwlist eth2 scan
```When you click the Network Manager icon, do you see your network? Can you click it and try to connect? Are you asked for a password?

---

### Post by rishipopat on 2012-08-12
Output of the command that you asked me to run is as follows:

rishi@ubuntu:~$ sudo iwlist eth2 scan
[sudo] password for rishi: 
eth2      Interface doesn't support scanning.


Last night I seen it briefly but I do not see it any more. I run my Ubuntu installation from a pen drive. Could that be the reason?

---

### Post by chili555 on 2012-08-12
I doubt the pen drive is a problem. Let's see:```
rfkill list all
dmesg | grep -e eth -e wl
iwconfig
```Thanks.

---

### Post by rishipopat on 2012-08-12
Following are the outputs of the commands

rishi@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


rishi@ubuntu:~$ dmesg | grep -e eth -e wl
[    0.428767] i2c-core: driver [aat2870] using legacy suspend method
[    0.428769] i2c-core: driver [aat2870] using legacy resume method
[    1.820079] tg3 0000:08:00.0: eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:da:b9:c9
[    1.820084] tg3 0000:08:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.820088] tg3 0000:08:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.820091] tg3 0000:08:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   18.738103] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.966018] ipheth 2-2:4.2: Apple iPhone USB Ethernet device attached
[   19.966040] usbcore: registered new interface driver ipheth
[   21.175797] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.176474] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.181638] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.182036] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   91.805851] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  102.384042] eth1: no IPv6 routers present


rishi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

rishi@ubuntu:~$

---

### Post by chili555 on 2012-08-13
> [ 19.966018] ipheth 2-2:4.2: Apple iPhone USB Ethernet device attached
[ 19.966040] usbcore: registered new interface driver iphethI wonder if Network Manager is disabling your wireless because you have a working connection; that is the iPhone. Please detach the iPhone and do:```
sudo modprobe wl
iwconfig
```Is eth2 back in place? Any interesting errors or messages?```
dmesg | grep wl
```

---

### Post by rishipopat on 2012-08-13
iPhone disconnected...no output for sudo modprobe wl

rishi@ubuntu:~$ sudo modprobe wl
[sudo] password for rishi: 
rishi@ubuntu:~$ sudo modprobe wl
rishi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:245
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

rishi@ubuntu:~$ dmesg | grep wl
[   89.583036] wl: module license 'MIXED/Proprietary' taints kernel.
[   89.595135] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   89.595148] wl 0000:04:00.0: setting latency timer to 64
rishi@ubuntu:~$

---

### Post by rishipopat on 2012-08-13
Please let me know next steps

---

### Post by chili555 on 2012-08-14
> **rishipopat said:**
> iPhone disconnected...no output for sudo modprobe wl

rishi@ubuntu:~$ sudo modprobe wl
[sudo] password for rishi: 
rishi@ubuntu:~$ sudo modprobe wl
rishi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:245
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

rishi@ubuntu:~$ dmesg | grep wl
[   89.583036] wl: module license 'MIXED/Proprietary' taints kernel.
[   89.595135] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   89.595148] wl 0000:04:00.0: setting latency timer to 64
rishi@ubuntu:~$This all looks perfect! Does it scan?```
sudo iwlist eth2 scan
```Are there any messages here?```
dmesg | grep eth2
sudo cat /var/log/syslog | grep eth2
```Thanks.

---

### Post by unevenflow on 2012-08-14
Hey try this
```
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
```

---

### Post by dstorrez on 2012-08-21
unevenflow, I have a E1405 Inspiron and that worked perfectly.

---

### Post by yousra on 2012-11-24
> **chili555 said:**
> Please see here: [http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey](http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey)

If your pci.id is the same, please proceed. If it's different, post it here and we'll work out a fix.
Hi everyone;
I have the same problem as
natethegreat131, my pc is a Dell Inspiron mini, the problem is that I am in residence so that I don't have any ethernet access. Is there any other solutions to fix the wireless connection without the ethernet.

---

### Post by chili555 on 2012-11-24
> **yousra said:**
> Hi everyone;
I have the same problem as
natethegreat131, my pc is a Dell Inspiron mini, the problem is that I am in residence so that I don't have any ethernet access. Is there any other solutions to fix the wireless connection without the ethernet.Do you have the same device?```
lspci -nn | grep 0280
```

---

### Post by athaullah on 2013-01-30
Hi Admin,
I have installed ubuntu 12.10 in my Dell laptop inspiron 1545 but i am unable to connect wifi.
I searched for wifi driver but in vain. 
Please help.
Thanks.

---

### Post by chili555 on 2013-01-30
> **athaullah said:**
> Hi Admin,
I have installed ubuntu 12.10 in my Dell laptop inspiron 1545 but i am unable to connect wifi.
I searched for wifi driver but in vain. 
Please help.
Thanks.Please provide the information I requested in post #24.

---

### Post by gpeck157 on 2013-03-17
Hi chili555,
The output from my grep was this < Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) > Thanks.

---

### Post by chili555 on 2013-03-17
> **gpeck157 said:**
> Hi chili555,
The output from my grep was this < Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) > Thanks.Please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```You should be all set.

---

### Post by gpeck157 on 2013-03-20
Thank you. All is working fine.

---

### Post by onusprobandi on 2013-06-08
Hi there

I'm having problems installing the driver for  my broadcom wireless adapter on Ubuntu 12.04. I get the following error message:

"Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"

"lspci -nn |grep 0280" returns the following information:

02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]

I'll be very grateful for any help.

---

### Post by chili555 on 2013-06-08
Please try:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
```If it still fails due to an error, please post:```
cat /var/log/jockey.log
```Thanks.

---

### Post by onusprobandi on 2013-06-09
Dear chili555

Thank you for your reply. 

There were errors. 

Do you want me to post the whole of jokey? It is really huge, and trying to attach it as a file I'm told it exceeds the forum limit in terms of size. Is there anything specific I need to look for?

---

### Post by chili555 on 2013-06-09
> **onusprobandi said:**
> Dear chili555

Thank you for your reply. 

There were errors. 

Do you want me to post the whole of jokey? It is really huge, and trying to attach it as a file I'm told it exceeds the forum limit in terms of size. Is there anything specific I need to look for?We want to see the last 20 lines or so. Please try:```
cat /var/log/jockey.log | tail -n20
```

---

### Post by onusprobandi on 2013-06-10
Here they are:

2013-06-09 17:38:57,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias',
'pci:v00008086d00001C26sv00001028sd0000049Abc0Csc03i20')
2013-06-09 17:38:57,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias',
'pci:v00008086d00001C49sv00001028sd0000049Abc06sc01i00')
2013-06-09 17:38:57,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-06-09 17:38:57,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias',
'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-06-09 17:38:57,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias', 'acpi:SMO8800:')
2013-06-09 17:38:57,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias',
'input:b0003v05CAp181Ee1125-e0,1,kD4,ramlsfw')
2013-06-09 17:38:57,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias',
'pci:v00001217d00008331sv00001028sd0000049Abc01sc80i00')
2013-06-09 17:38:57,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2298f80> about HardwareID('modalias',
'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-06-09 17:38:57,138 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:38:57,156 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:38:57,179 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:39:01,652 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:39:05,885 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-06-09 17:39:05,885 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-06-09 17:39:05,930 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:39:08,938 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:39:08,975 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:39:09,020 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-09 17:39:10,408 DEBUG: Shutting down

Thanks!

---

### Post by chili555 on 2013-06-10
Hmmmm. We don't see the specific error; let's try to provoke it if we can:```
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Again, if it fails, then show me:```
cat /var/log/jockey.log | tail -n20
```

---

### Post by onusprobandi on 2013-06-11
Hi 

Here is the full output of what I get. Various errors along the way...

```
wconradie@ubuntu:~$ sudo apt-get install --reinstall linux-headers-`uname -r`
[sudo] password for wconradie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-headers-3.5.0-23-generic is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wconradie@ubuntu:~$ sudo apt-get install --reinstall linux-headres-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headres-generic
wconradie@ubuntu:~$ sudi apt-get install --reinstall bcmwl-kernel-source
No command 'sudi' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudi: command not found
wconradie@ubuntu:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 165258 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.5.0-23-generic
Building for architecture x86_64
Building initial module for 3.5.0-23-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
Warning: No support for locale: en_US.utf8
wconradie@ubuntu:~$ sudo modprobe wl
FATAL: Module wl not found.
wconradie@ubuntu:~$ cat /var/log/jokey.log | tail -n20
cat: /var/log/jokey.log: No such file or directory
wconradie@ubuntu:~$ cat /var/log/jockey.log | tail -n20
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'acpi:DLL049A:PNP0F13:')
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'platform:dell-laptop')
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'usb:v413Cp8187d0517dcE0dsc01dp01icFFiscFFipFF')
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'acpi:PNP0200:')
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd0000049Abc07sc80i00')
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'hid:b0003g0001v0000093Ap00002510')
2013-06-11 21:24:38,385 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'usb:v05CAp181Ed1125dcEFdsc02dp01ic0Eisc02ip00')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001028sd0000049Abc0Csc03i20')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'pci:v00008086d00001C49sv00001028sd0000049Abc06sc01i00')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'acpi:SMO8800:')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'input:b0003v05CAp181Ee1125-e0,1,kD4,ramlsfw')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'pci:v00001217d00008331sv00001028sd0000049Abc01sc80i00')
2013-06-11 21:24:38,386 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x208f290> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-06-11 21:24:38,418 DEBUG: Shutting down
wconradie@ubuntu:~$ ^C
```

---

### Post by chili555 on 2013-06-11
Well, that's the issue; bcmwl-kernel-source requires linux-headers matching your running kernel version (`uname -r`). However, it can't be downloaded:> Reinstallation of linux-headers-3.5.0-23-generic is not possible, it cannot be downloaded.Is it not able to be downloaded because you have no internet connection or because it is somehow considered obsolete? Maybe you already have it installed; check:```
sudo dpkg -s linux-headers-`uname -r`
```We hope it says:> Status: install ok installedThe installation instructs us to consult:> Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.So, instead of jockey, let's have a look at:```
cat /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log  | tail -n20
```So are you conducting all this with a working ethernet connection?

---

### Post by onusprobandi on 2013-06-12
Thanks for bearing with me on this.

Seems there was indeed a problem with the ethernet connection last time - I reran the commands second last reply without errors this time, but the driver still fails to install. 

Did what you said in your last reply, and here is the result:

sudo dpkg -s linux-headers-`uname -r` 

does indeed give

> install ok installed

cat /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log | tail -n20

then gives

> wconradie@ubuntu:~$ cat /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log | tail n-20
tail: cannot open `n-20' for reading: No such file or directory
wconradie@ubuntu:~$ cat /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log | tail -n20
DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.5.0-23-generic (x86_64)
Wed Jun 12 21:26:27 SAST 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  LD      /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'

Thanks!

---

### Post by chili555 on 2013-06-12
Hmmmm. Although your question refers to 12.04...:> I'm having problems installing the driver for my broadcom wireless adapter on Ubuntu 12.04....I think your kernel version matches 12.10, isn't that correct?>  linux-headers-[COLOR="#FF0000"]3.5.0-23[/COLOR]-generic is not possible, it cannot be downloaded. The error you reported is a bug that was fixed in a later version of the Broadcom driver: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/994255](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/994255)

I suggest you download and try a later version than 5.100.82.38+bdcom; for instance,here: [http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

Be sure to get either the 32- or 64-bit version as appropriate:```
arch
```32-bit will return i686 and 64-bit will retun x86_64. Download the .deb package to your desktop and then do:```
cd Desktop
sudo dpkg -i bcmwl*.deb
sudo modprobe wl
```Now does it work?

---

### Post by onusprobandi on 2013-06-13
That sorted it out - wireless working perfectly now.

Thanks again for all your help!

---

### Post by eWzczyM on 2013-09-11
Hello, I am not sure whether this is the right place to post. I was wondering if anybody could help me. I have just installed Ubuntu and am having great trouble installing the Broadcom driver. I know nothing about Linux and have been trying various things from the forums to get it working, so far with no success.

---

### Post by eWzczyM on 2013-09-11
Further information:

blanka@B-Aspire-one:~$ dmesg | grep -e eth -e wl
[    0.272236] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
[    0.272253] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.285218] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
[    8.958714] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.095379] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
blanka@B-Aspire-one:~$

---

### Post by eWzczyM on 2013-09-11
And: 

blanka@B-Aspire-one:~$ dmesg | grep -e eth -e wl
[    0.272236] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
[    0.272253] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.285218] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
[    8.958714] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.095379] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
blanka@B-Aspire-one:~$ blanka@B-Aspire-one:~$ dmesg | grep -e eth -e wl
blanka@B-Aspire-one:~$: command not found
blanka@B-Aspire-one:~$ [    0.272236] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
bash: syntax error near unexpected token `('
blanka@B-Aspire-one:~$ [    0.272253] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
bash: [: missing `]'
blanka@B-Aspire-one:~$ [    0.285218] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
bash: syntax error near unexpected token `('
blanka@B-Aspire-one:~$ [    8.958714] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
bash: syntax error near unexpected token `('
blanka@B-Aspire-one:~$ [   25.095379] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
bash: syntax error near unexpected token `newline'
blanka@B-Aspire-one:~$ blanka@B-Aspire-one:~$

---

### Post by eWzczyM on 2013-09-11
Just tried #21 and received this:

Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
An unsupported BCM4312 Low-Power (LP-PHY) device was found.
Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead.
Aborting.
blanka@B-Aspire-one:~$

---

### Post by wildmanne39 on 2013-09-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
Please post all information in one post.
Thanks

---

### Post by eWzczyM on 2013-09-11
> **unevenflow said:**
> Hey try this
```
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
```

@wildman - is the above what you mean?

---

### Post by wildmanne39 on 2013-09-11
Yes and this should get your wireless going.
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Thanks

---

### Post by eWzczyM on 2013-09-11
> **Wild Man said:**
> Yes and this should get your wireless going.
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Thanks

Wow! Yes, this seems to have got everything working. Thank you so much!

---

### Post by wildmanne39 on 2013-09-11
Your welcome!

---

### Post by eWzczyM on 2013-09-14
Hello, further to the above, though the wireless is now working, it is really flaky. It works for perhaps 2 minutes before disconnecting. No other computers in the house are suffering from problems, so I am guessing it's the driver.

---

### Post by wildmanne39 on 2013-09-14
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by eWzczyM on 2013-09-15
Thanks! I am hoping the report is attached.

---

### Post by varunendra on 2013-09-15
> **eWzczyM said:**
> Thanks! I am hoping the report is attached.

From your report (6th last line) -
> [   29.844284] b43-phy0 warning: Forced PIO by [COLOR="#FF0000"]use_pio module parameter[/COLOR]. This [COLOR="#FF0000"]should not be needed[/COLOR] and will result in lower performance.

Accordingly, please try -
```
echo "options b43 pio=0" | sudo tee /etc/modprobe.d/b43.conf
sudo modprobe -rv b43
sudo modprobe -v b43
```

Better now?

---

### Post by eWzczyM on 2013-09-15
> **varunendra said:**
> From your report (6th last line) -


Accordingly, please try -
```
echo "options b43 pio=0" | sudo tee /etc/modprobe.d/b43.conf
sudo modprobe -rv b43
sudo modprobe -v b43
```

Better now?

Not sure - now it seems like there is no wireless connection at all.

---

### Post by varunendra on 2013-09-15
Do a reboot then. If it still doesn't work, please show -
```
lsmod | grep b43
grep -iR [0-9a-z] /sys/module/b43/parameters/
dmesg | grep b43
```

---

### Post by eWzczyM on 2013-09-15
> **varunendra said:**
> Do a reboot then. If it still doesn't work, please show -
```
lsmod | grep b43
grep -iR [0-9a-z] /sys/module/b43/parameters/
dmesg | grep b43
```

Nothing on reboot. Above code shows:

blanka@B-Aspire-one:~$ lsmod | grep b43
b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  1 b43
blanka@B-Aspire-one:~$ grep -iR [0-9a-z] /sys/module/b43/parameters/
/sys/module/b43/parameters/pio:0
/sys/module/b43/parameters/qos:1
/sys/module/b43/parameters/btcoex:1
/sys/module/b43/parameters/bad_frames_preempt:0
/sys/module/b43/parameters/hwpctl:0
/sys/module/b43/parameters/hwtkip:0
/sys/module/b43/parameters/verbose:2
/sys/module/b43/parameters/nohwcrypt:0
blanka@B-Aspire-one:~$ dmesg | grep b43
[   11.421162] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.464517] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   23.876172] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
blanka@B-Aspire-one:~$

---

### Post by varunendra on 2013-09-15
Hmm.. no problems are detected by dmesg. For now, let's just revert the change we did, and try something else -
```
sudo sed -i 's/pio=0/nohwcrypt=1/' /etc/modprobe.d/b43.conf
sudo modprobe -rv b43
sudo modprobe -v b43
```
Any improvement?

If not, run the wireless_script again and post back the fresh report. It is strange that pio was set to 1, because its default value is 0 anyway, we shouldn't have even needed to force it to 0.

**PS:**
Does your router support N-channel? If yes, and if it is enabled, I'd suggest to try disabling it BEFORE doing the above changes (set the channel mode to b/g only). See if that alone can fix it.

---

### Post by eWzczyM on 2013-09-16
OK, I followed those steps. I do not know about the router. However, shortly after restart, the wireless came back on. It has been on for a few minutes. I will see how long it lasts. In the meantime, I have attached the report again.

---

### Post by varunendra on 2013-09-16
The report is from when the wifi is disconnected and the wired connection is working. Perhaps you generated this report before rebooting.
Are you sure the wifi is working again?

Please run the script while ethernet is disconnected and wifi is working, and post back the fresh report.

How's the connection quality by the way?

---

### Post by eWzczyM on 2013-09-16
> **varunendra said:**
> The report is from when the wifi is disconnected and the wired connection is working. Perhaps you generated this report before rebooting.
Are you sure the wifi is working again?

Please run the script while ethernet is disconnected and wifi is working, and post back the fresh report.

How's the connection quality by the way?

The connection is still holding for the time being. I think the right file is now attached.

---

### Post by varunendra on 2013-09-16
Yes, it's the correct one, no "pio" error in dmesg this time. It would be interesting to see what is its current value (while it is working). Please show us -
```
cat /sys/module/b43/parameters/pio
```

There seems to be some struggling with connectivity in the dmesg part, and the current speed, as per the report is also too slow (1 Mb/s !), despite the signal quality being solid.

You should try changing encryption settings in the router. Currently it is set to WPA/WPA2 mixed mode which does not work well with Linux drivers. Change it to pure WPA2-PSK with AES. No mixed mode, no TKIP. This should improve the connection quality and possibly the speed too.

After changing the router settings, change the encryption setting in Ubuntu Network Manager too (or better, delete the connection and create a new one, saving the new security settings in it). Then reconnect and check -
```
iwconfig
```
Is the speed any better now? If not post back and we can try some 'fixed' speed values, as higher as possible without issues.

---

### Post by eWzczyM on 2013-09-16
> **varunendra said:**
> Yes, it's the correct one, no "pio" error in dmesg this time. It would be interesting to see what is its current value (while it is working). Please show us -
```
cat /sys/module/b43/parameters/pio
```

There seems to be some struggling with connectivity in the dmesg part, and the current speed, as per the report is also too slow (1 Mb/s !), despite the signal quality being solid.

You should try changing encryption settings in the router. Currently it is set to WPA/WPA2 mixed mode which does not work well with Linux drivers. Change it to pure WPA2-PSK with AES. No mixed mode, no TKIP. This should improve the connection quality and possibly the speed too.

After changing the router settings, change the encryption setting in Ubuntu Network Manager too (or better, delete the connection and create a new one, saving the new security settings in it). Then reconnect and check -
```
iwconfig
```
Is the speed any better now? If not post back and we can try some 'fixed' speed values, as higher as possible without issues.

Ok, the first part says

blanka@B-Aspire-one:~$ cat /sys/module/b43/parameters/pio
0
blanka@B-Aspire-one:~$ 

I will try changing the router settings now.

---

### Post by eWzczyM on 2013-09-16
Incidentally, I have been receiving the following information about a bug that was automatically generated when I installed Ubuntu and the drivers. I think it refers to the same issue: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1095751](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1095751)

Is this relevant?

---

### Post by varunendra on 2013-09-16
> **eWzczyM said:**
> I think it refers to the same issue: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1095751](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1095751)

Is this relevant?

Yes it is the same bug that caused your original attempt to install sta driver to fail. There exists an even newer fixed version than suggested on that bug report page. If you wish to try here it is : [https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504)

However, the above package is for 64 bit. I'm not sure if it will install on 32 bit or not.

There is a still newer version very recently made available at Broadcom's [official site]("http://www.broadcom.com/support/802.11/linux_sta.php"), but that one will need to be compiled and installed manually. It shouldn't be much of a problem though, let me know if you wish to try that.

But if the current one's performance is okay, or can be made okay by the changes I suggested, you shouldn't need to bother with the sta driver. If you wish to try it anyway, try the launchpad one first. Either it will install smoothly (just download and double-click to install), or will fail right away giving error like "unsupported architecture".

---

### Post by eWzczyM on 2013-09-17
> **varunendra said:**
> Yes it is the same bug that caused your original attempt to install sta driver to fail. There exists an even newer fixed version than suggested on that bug report page. If you wish to try here it is : [https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504)

However, the above package is for 64 bit. I'm not sure if it will install on 32 bit or not.

There is a still newer version very recently made available at Broadcom's [official site]("http://www.broadcom.com/support/802.11/linux_sta.php"), but that one will need to be compiled and installed manually. It shouldn't be much of a problem though, let me know if you wish to try that.

But if the current one's performance is okay, or can be made okay by the changes I suggested, you shouldn't need to bother with the sta driver. If you wish to try it anyway, try the launchpad one first. Either it will install smoothly (just download and double-click to install), or will fail right away giving error like "unsupported architecture".

OK, today there is no wireless despite it working for all of yesterday. I quickly tried the launchpad link and you were, right, it said wrong architecture. I have not yet worked out how to change the wireless settings for my router. Incidentally, will it affect the other devices in my house if I change it?

---

### Post by varunendra on 2013-09-17
> **eWzczyM said:**
> I have not yet worked out how to change the wireless settings for my router. Incidentally, will it affect the other devices in my house if I change it?

If they have saved current encryption settings, then yes, you'll need to change those saved settings as well. And to change the settings in the router/access-point, please refer to your router's user manual, since they are not the same across different routers.

---

### Post by eWzczyM on 2013-09-17
> **varunendra said:**
> If they have saved current encryption settings, then yes, you'll need to change those saved settings as well. And to change the settings in the router/access-point, please refer to your router's user manual, since they are not the same across different routers.

Would it be possible to avoid this? Only I have various types of non Linux technology that depend on the wireless, and I'd rather not disturb them if there is another way.

---

### Post by varunendra on 2013-09-17
> **eWzczyM said:**
> Would it be possible to avoid this? Only I have various types of non Linux technology that depend on the wireless, and I'd rather not disturb them if there is another way.

Since that change in the router can be reverted anytime you wish, I'd suggest to make the changes temporarily to see if it help or not in the first place. Make sure to accordingly change the saved settings in Ubuntu Network Manager too, and do a reboot (on both the router and Ubuntu) to be extra sure. If it helps, at least we'd know there is one option tested successfully. After testing this, revert the changes and reboot the router. Your other devices won't know there was a change in-between.

Now, in an attempt to avoid the changes in the router (preferably after testing them anyway), you can try the 32-bit driver from the official broadcom site. Steps are -

[INDENT]1) If you already have bcmwl-kernel-source installed, unload and purge it -
```
sudo modprobe -rv wl
sudo apt-get purge bcmwl-kernel-source
```
It's just precautionary and you can ignore any warnings.., but report them back nonetheless.

2) Make sure you have linux-headers and build-essential installed to be able to build the driver -
```
sudo apt-get install linux-headers-generic build-essential
```

3) Download the official driver (32 bit in your case) from broadcom : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) Copy this file to your Desktop.

4) Right-click the downloaded package > Extract Here. This will extract a folder "hybrid-v35-nodebug-pcoem-6_30_223_141" on your Desktop.

5) Open a terminal (Ctrl-Alt-T), change to the extracted directory and build it -
```
cd Desktop/hybrid-v35-nodebug-pcoem-6_30_223_141
make
```
Ignore any warnings but if there are any Errors, report them back and Stop here.

6) Remove any other currently loaded broadcom wifi modules, then copy the driver just built above and load it -
```
sudo modprobe -rv b43 bcma brcmsmac
sudo cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
sudo depmod -a
sudo modprobe -v wl
sudo update-initramfs
```

7) To prevent the conflicting native modules from loading at next boot, blacklist them. To do so, open the /etc/modprobe.d/blacklist.conf as root -
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add the following lines to its bottom -
```
blacklist bcma
blacklist b43
blacklist brcmsmac
```

8) To test if the loaded "wl" module can load at startup, reboot and check if it is loaded with "lsmod | grep wl" command. If not, add it to /etc/modules -
```
echo "wl" | sudo tee -a /etc/modules
```[/INDENT]

If all this goes fine, you should have a working wifi. Please report back its performance. Thanks.

---

### Post by eWzczyM on 2013-09-18
OK, I've changed the settings, deleted the previous connections, rebooted both router and computer, but there is no wireless connection. I will revert back to the previous settings and try the next steps....

---

### Post by eWzczyM on 2013-09-18
> **varunendra said:**
> 
[INDENT] 
5) Open a terminal (Ctrl-Alt-T), change to the extracted directory and build it -
```
cd Desktop/hybrid-v35-nodebug-pcoem-6_30_223_141
make
```
Ignore any warnings but if there are any Errors, report them back and Stop here.
.
[/INDENT]
 
I had a problem with this step. I can see the 2 extracted folders and one file on the desktop, but I get the following error message:

blanka@B-Aspire-one:~$ cd Desktop/hybrid-v35-nodebug-pcoem-6_30_223_141
bash: cd: Desktop/hybrid-v35-nodebug-pcoem-6_30_223_141: No such file or directory
blanka@B-Aspire-one:~$

---

### Post by eWzczyM on 2013-09-18
> **eWzczyM said:**
> [/INDENT] 
I had a problem with this step. I can see the 2 extracted folders and one file on the desktop, but I get the following error message:

blanka@B-Aspire-one:~$ cd Desktop/hybrid-v35-nodebug-pcoem-6_30_223_141
bash: cd: Desktop/hybrid-v35-nodebug-pcoem-6_30_223_141: No such file or directory
blanka@B-Aspire-one:~$

My fault, I don't think I extracted it correctly. I think I am back on track now...

---

### Post by eWzczyM on 2013-09-18
> **varunendra said:**
> 
[INDENT] 
8) To test if the loaded "wl" module can load at startup, reboot and check if it is loaded with "lsmod | grep wl" command. If not, add it to /etc/modules -
```
echo "wl" | sudo tee -a /etc/modules
```
[/INDENT]

If all this goes fine, you should have a working wifi. Please report back its performance. Thanks.

OK, I have been through all these steps but it seems the wireless is still not working at all, even not intermittently as before. I had a bit of trouble with the above step as I did not know how to see if the wl module could be loaded at startup, so I ran that command anyway. There was no wireless before or after.

---

### Post by eWzczyM on 2013-09-18
I don't know if this file helps explain what's going on.

---

### Post by varunendra on 2013-09-18
I think I see a problem. One of the earlier modules "ssb" is still getting loaded, and certainly conflicting with the "wl" driver we are currently trying. Please do -
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rv ssb
sudo mv /etc/udev/rules.d/70-persistent-net.rules 70-persistent-net.rules.bak
sudo udevadm trigger
sudo modprobe -rv wl
sudo modprobe -v wl
```
Does the wifi detect any networks now? If still not, please reboot and check again. If it still can't detect networks, please post outputs of -
```
lsmod | grep -e wl -e ssb
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by eWzczyM on 2013-09-18
> **varunendra said:**
> I think I see a problem. One of the earlier modules "ssb" is still getting loaded, and certainly conflicting with the "wl" driver we are currently trying. Please do -
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rv ssb
sudo mv /etc/udev/rules.d/70-persistent-net.rules 70-persistent-net.rules.bak
sudo udevadm trigger
sudo modprobe -rv wl
sudo modprobe -v wl
```
Does the wifi detect any networks now? If still not, please reboot and check again. If it still can't detect networks, please post outputs of -
```
lsmod | grep -e wl -e ssb
cat /etc/udev/rules.d/70-persistent-net.rules
```

Now there is no network and also the light for the wireless has gone off (it has been on until now).

Output is:

blanka@B-Aspire-one:~$ lsmod | grep -e wl -e ssb
wl                   3999416  0 
cfg80211              453853  1 wl
lib80211               14040  1 wl
ssb                    51554  0 


# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="0c:ee:e6:a9:35:3c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:22:67:4d:d1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
blanka@B-Aspire-one:~$

---

### Post by varunendra on 2013-09-18
Hmm.. the ssb module is still loading for some mysterious reason. We do have some positive progress in the udev rules file, but still..

Please post the outputs of -
```
cat /etc/modules
rfkill list all
dmesg | grep -e wl -e ssb
```

And try -
```
sudo modprobe -rv ssb
sudo modprobe -rv wl
sudo modprobe -v wl
```
Still nothing?

---

### Post by eWzczyM on 2013-09-18
blanka@B-Aspire-one:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
blanka@B-Aspire-one:~$

blanka@B-Aspire-one:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
blanka@B-Aspire-one:~$ 

blanka@B-Aspire-one:~$ dmesg | grep -e wl -e ssb
[    2.420220] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.420249] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.420275] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.420299] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.420323] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.476320] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[   11.011100] wl: module license 'unspecified' taints kernel.
blanka@B-Aspire-one:~$

---

### Post by eWzczyM on 2013-09-18
Still nothing. Wireless light is still off too.

---

### Post by wildmanne39 on 2013-09-18
Hi, b43 is usually the best driver for this device.

Please do:
```
sudo modprobe -r wl
sudo modprobe -r acer-wmi
sudo modprobe wl
```
Did that help?
If not we I will post another version of b43 and the firmware to try.
Thanks

---

### Post by praseodym on 2013-09-19
If it is 12.04, check the kernel:
```

uname -a
```
For kernel 3.2 and 3.5 the backport modules version 3.6 should work with the native driver brcmsmac, do not forget the missing firmware. Alternatively, try the Broadcom-STA driver from the 12.10 proposed sources:

[http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

For kernel 3.8 try the one from raring:

[http://packages.ubuntu.com/raring/bcmwl-kernel-source](http://packages.ubuntu.com/raring/bcmwl-kernel-source)

---

### Post by eWzczyM on 2013-09-19
> **Wild Man said:**
> Hi, b43 is usually the best driver for this device.

Please do:
```
sudo modprobe -r wl
sudo modprobe -r acer-wmi
sudo modprobe wl
```
Did that help?
If not we I will post another version of b43 and the firmware to try.
Thanks

No improvement after this.

---

### Post by eWzczyM on 2013-09-19
> **praseodym said:**
> If it is 12.04, check the kernel:
```

uname -a
```
For kernel 3.2 and 3.5 the backport modules version 3.6 should work with the native driver brcmsmac, do not forget the missing firmware. Alternatively, try the Broadcom-STA driver from the 12.10 proposed sources:

[http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

For kernel 3.8 try the one from raring:

[http://packages.ubuntu.com/raring/bcmwl-kernel-source](http://packages.ubuntu.com/raring/bcmwl-kernel-source)

It seems that the kernel is 3.8 as I get:

blanka@B-Aspire-one:~$ uname -a
Linux B-Aspire-one 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux

What do I do with the kernel from raring?

---

### Post by eWzczyM on 2013-09-19
> **praseodym said:**
> If it is 12.04, check the kernel:
```

uname -a
```
For kernel 3.2 and 3.5 the backport modules version 3.6 should work with the native driver brcmsmac, do not forget the missing firmware. Alternatively, try the Broadcom-STA driver from the 12.10 proposed sources:

[http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

For kernel 3.8 try the one from raring:

[http://packages.ubuntu.com/raring/bcmwl-kernel-source](http://packages.ubuntu.com/raring/bcmwl-kernel-source)

Good news! I have managed to install this package from raring, and, on restart, the wireless connection is back! I am not counting my chickens just yet, as the connection previously was quite flaky. I will use it for a bit and see how it goes. In the meantime, thank you everybody for all your assistance!

---

### Post by eWzczyM on 2013-09-19
So far, so good, all seems to be working fine. Thank you all so much!

---

### Post by varunendra on 2013-09-20
> **eWzczyM said:**
> So far, so good, all seems to be working fine. Thank you all so much!

Yay ! Thanks to the angels who came to the rescue :D

---

### Post by praseodym on 2013-09-20
Finish the installation via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-lts-raring build-essential dkms
```
Now the driver will be build after kernel upgrades automatically

---

### Post by louisewonder on 2013-11-17
Hi, I am new with Ubuntu. I install Ubuntu 12.04 and I am using HP Compaq .
Having problem with [COLOR=#000000] /var/log/jockey.log

if u can help.. 
thnk you
[/COLOR]

---

### Post by louisewonder on 2013-11-17
Hi my network controller is [0280]: Broadcom Corporation BCM4312 802.11b/b LP-PHY [14e4:4315] (rev01)
and my netbook is HP Compaq mini 110

if someone can help to connect to the wifi

---

### Post by chili555 on 2013-11-17
> **louisewonder said:**
> Hi my network controller is [0280]: Broadcom Corporation BCM4312 802.11b/b LP-PHY [14e4:4315] (rev01)
and my netbook is HP Compaq mini 110

if someone can help to connect to the wifiPlease get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```Reboot and let us have your report.

---

### Post by louisewonder on 2013-11-17
err http:// archive.ubuntu.com/ubuntu/precise/man b43-fwcutter i386 1:015-9 could not resolve 'archive.ubuntu.com'

---

### Post by chili555 on 2013-11-17
> **louisewonder said:**
> err http:// archive.ubuntu.com/ubuntu/precise/man b43-fwcutter i386 1:015-9 could not resolve 'archive.ubuntu.com'
That's not what I suggested.

---

### Post by louisewonder on 2013-11-17
it is still not work...

I got this :
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) pprecise/multiverse firmware-b43-llphy-installer all 1:015-9
could not resolve 'archive.ubuntu.com'
failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_015-9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_015-9_i386.deb) could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_015-9-all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_015-9-all.deb) could not resove 'archive.ubuntu.com'
E: unable to fetch some archives, maybe run apt-get update or try with --fix-missing ?

---

### Post by chili555 on 2013-11-17
Do you have a working wired ethernet connection as you try this?```
ping -c3 www.google.com
```Please try:```
sudo apt-get update
sudo apt-get  --fix-missing
sudo apt-get install firmware-b43-llphy-installer
```

---

### Post by louisewonder on 2013-11-17
nope. i didn't use the wired ethernet connection

---

### Post by chili555 on 2013-11-17
Can you or are you without any connectivity at all?

---

### Post by louisewonder on 2013-11-17
yes. i plug in now

---

### Post by louisewonder on 2013-11-17
done with updating.
should i reboot now? or I should do what you told me before i update it?

---

### Post by louisewonder on 2013-11-17
the wireless it's working now... thank you...

---

### Post by chili555 on 2013-11-17
> **louisewonder said:**
> the wireless it's working now... thank you...Awesome! Glad it's working.

---

