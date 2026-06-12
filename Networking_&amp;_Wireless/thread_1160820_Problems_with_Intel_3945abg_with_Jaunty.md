---
title: "Problems with Intel 3945abg with Jaunty"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by elimoon8 on 2009-05-16
Hello!, I have been trying to get my wireless card (Intel 3945abg) to work under Jaunty Jackalope. My wireless indicator is lit, and the ethernet connection is working. I did a clean install under wubi. I am a linux beginner, so please try to provide detailed instructions if possible.

Things I've tried:
- Installing WICD
- Reinstalling network manager
- trying to use nsdwrapper, but failed miserably (somehow the system wouldn't fully boot afterwards, and trying to repair the install failed).
------------------------------------------------------------------------------------------------------------
outputs of various commands I found posted by other people with similar problems (in no particular order):

>> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:d0:3f:34  
          inet addr:192.168.1.113     Bcast:192.168.1.setomoon@ubuntu:~setomoon@ubuntu:~255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fed0:3f34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2561780 (2.5 MB)  TX bytes:364732 (364.7 KB)
          Memory:f8500000-f8520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
------------------------------------------------------------------------------------------------------------
>> lsmod | grep "iwl3945"
iwl3945                97912  0 
mac80211              217208  1 iwl3945
led_class              12036  1 iwl3945
cfg80211               38032  2 iwl3945,mac80211
-----------------------------------------------------------------------------------------------------------
>> lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                97912  0 
snd_timer              29704  2 snd_pcm,snd_seq
pcmcia                 44748  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              34108  0 
mac80211              217208  1 iwl3945
psmouse                61972  0 
sdhci_pci              15232  0 
tifm_7xx1              13824  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
pcspkr                 10496  0 
serio_raw              13316  0 
led_class              12036  1 iwl3945
sdhci                  23940  1 sdhci_pci
agpgart                42696  2 drm,intel_agp
tifm_core              15900  1 tifm_7xx1
video                  25360  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
cfg80211               38032  2 iwl3945,mac80211
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
------------------------------------------------------------------------------------------------------
>> sudo lshw -C network
[sudo] password for setomoon: 
  *-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:e0:b8:d0:3f:34
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.3-0 ip=192.168.1.113 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bitssetomoon@ubuntu:~$ ipwconfig
bash: ipwconfig: command not found
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:c1:3c:05:69:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
---------------------------------------------------------------------------------------
>> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
----------------------------------------------------------------------------------------
>> lspci | grep -i network
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
-------------------------------------------------------------------------------------------
>> dmesg | grep -i iwl3945
[   12.851055] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.851059] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   12.851122] iwl3945 0000:02:00.0: enabling device (0000 -> 0002)
[   12.851134] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.851152] iwl3945 0000:02:00.0: setting latency timer to 64
[   12.851195] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   12.851858] iwl3945 0000:02:00.0: irq 2299 for MSI/MSI-X
[   12.856688] iwl3945: Error: saturation power is -1, less than minimum expected 40
[   12.856690] iwl3945: Invalid power index
[   12.856693] iwl3945: initializing regulatory failed: -5
[   12.856870] iwl3945 0000:02:00.0: PCI INT A disabled
[   12.856877] iwl3945: probe of 0000:02:00.0 failed with error -5
-----------------------------------------------------------------------------------------------------
>> lsmod | grep -i iwl
iwl3945                97912  0 
mac80211              217208  1 iwl3945
led_class              12036  1 iwl3945
cfg80211               38032  2 iwl3945,mac80211
-------------------------------------------------------------------------------------
>> modprobe iwl3945
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ipwraw line 1: ignoring bad line starting with '“blacklist'
-----------------------------------------------------------------------------------------
>> lspci -nn | grep 'Intel'
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MC Gigabit Network Connection [8086:104d] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
-------------------------------------------------------------------------------------------------------
>> dmesg | grep "wlan0"
(running this returned nothing)
--------------------------------------------------------------------------------------------------------
>> iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
-------------------------------------------------------------------------------------------------------
>> lsb_release -d
Description:    Ubuntu 9.04
---------------------------------------------------------------------------------------------------------
>> uname -mr
2.6.28-11-generic i686  
(Note: Generally, I use kernel 2.6.28-12, but the wireless doesn't work there either)
------------------------------------------------------------------------------------------------------------

Please tell me if there is any additional output you require (and the commands associated). Any help would be appreciated! :)

---

### Post by chili555 on 2009-05-16
Well! Buried in all this information are a few keys to your issue.> WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ipwraw line 1: ignoring bad line starting with '“blacklist'Did you try to install the ipwraw drivers, or what? Please open a terminal and do:```
cat /etc/modprobe.d/ipwraw
```Please post the result and we'll try to get this fixed up.> [ 12.856688] iwl3945: Error: saturation power is -1, less than minimum expected 40
[ 12.856690] iwl3945: Invalid power index
[ 12.856693] iwl3945: initializing regulatory failed: -5
[ 12.856870] iwl3945 0000:02:00.0: PCI INT A disabled
[ 12.856877] iwl3945: probe of 0000:02:00.0 failed with error -5Ouch! The module loads but won't actually work. Let's try a simple fix first, before we resort to harsher measures:```
sudo apt-get install linux-backports-modules-jaunty-generic
```This package has a newer ipw3945 module and it's associated firmware. Reboot and do:```
dmesg | grep iwl3945
```Then we will see if your card comes to life.

---

### Post by calrogman on 2009-05-16
> **elimoon8 said:**
> >> sudo lshw -C network
[sudo] password for setomoon: 
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32


Your network is unclaimed,  unfortunately I do not know exactly how to rectify the problem.

I just felt I should chip in and say this is exactly the same problem I have with my 3945abg, and if I find a solution (I'll be up all night Googling) I will be sure to post it here!

---

### Post by chili555 on 2009-05-16
> Your network is unclaimed, unfortunately I do not know exactly how to rectify the problem.Generally, a network device is Unclaimed when the driver has not associated with the device. In his case, the iwl3945 driver loads but not correctly:> iwl3945: probe of 0000:02:00.0 failed with error -5 I suggest you open a terminal and do:```
sudo modprobe iwl3945
dmesg | grep iwl3945
```Are there any clues as to why your driver didn't associate?

---

### Post by calrogman on 2009-05-17
Just after boot:
```
[   10.630337] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   10.630340] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   10.630407] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.630422] iwl3945 0000:08:00.0: setting latency timer to 64
[   10.630512] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   10.630848] iwl3945 0000:08:00.0: irq 2299 for MSI/MSI-X
[   10.686540] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   13.244078] iwl3945: Radio Frequency Kill Switch is On:
```

This last line is the problem, I don't have a hardware RF kill switch.

I think it may be possible to load the iwl3945 firmware in such a way as to disable any software kill switches which may be installed in my laptop (which is, in case you are wondering, a Fujitsu Siemens Amilo Li 2735 (Version 20)), but I couldn't actually find any specific documentation on this.

Edit: I just poked around in /sys/bus/pci/drivers/iwl3945/0000:08:00.0/rfkill/rfkill0 and catted a file called uevent.

> RFKILL_NAME=3945ABG
RFKILL_TYPE=wlan
RFKILL_STATE=2


What do you think of editing that last line? - **That doesn't work.** Nothing in /sys/bus/pci/drivers/iwl3945/$BUS/ appears to work.

---

### Post by chili555 on 2009-05-17
According to the data sheet for your Fujitsu, Fn+F1 is 'WLAN on/off.' I suggest you open:```
sudo tail -f /var/log/messages
```Leave the terminal open. Watch it as you manipulate the key combination and see if any messages are thrown out indicating signs of life for your wireless.

---

### Post by elimoon8 on 2009-05-17
> **chili555 said:**
> Did you try to install the ipwraw drivers, or what?

I believe I did. I tried pretty much everything I could find on the forums (not that I understood what I was doing in most cases). Somehow I killed my ethernet connection as well :( (while looking for a fix for my wireless), so I'll be sure to try your fix as soon as I figure out how to get it working again! Thanks for your time! :D

---

### Post by calrogman on 2009-05-18
> **chili555 said:**
> According to the data sheet for your Fujitsu, Fn+F1 is 'WLAN on/off.' I suggest you open:```
sudo tail -f /var/log/messages
```Leave the terminal open. Watch it as you manipulate the key combination and see if any messages are thrown out indicating signs of life for your wireless.

Unfortunately the Fn+F1 key combination is handled by a piece of Windows only software developed by Fujitsu Siemens called "Launch Manager" (entirely closed source), using this key combination under Ubuntu, or any other distro, has no effect.

Running Launch Manager through WINE is also futile, as Launch Manager fails to intercept any key presses when run in this manner.

---

### Post by chili555 on 2009-05-18
Is the module *acerhk* loaded? Learn with:```
lsmod | grep acer
```If it is, please try:```
sudo su
echo on > /proc/driver/acerhk/wirelessled
```Does your wireless come to life?

---

### Post by calrogman on 2009-05-18
The acerhk module is not loaded, using modprobe to load it, then using echo on > /proc/driver/acerhk/wirelessled doesn't do anything.

---

### Post by chili555 on 2009-05-18
Please post:```
cat /proc/driver/acerhk/wirelessled
```

---

### Post by calrogman on 2009-05-18
> **chili555 said:**
> Please post:```
cat /proc/driver/acerhk/wirelessled
```

That could be a problem...

```
root@linx:~# cd /proc/driver/acerhk/
root@linx:/proc/driver/acerhk# cat wirelessled
root@linx:/proc/driver/acerhk# echo on > wirelessled
root@linx:/proc/driver/acerhk# cat wirelessled
root@linx:/proc/driver/acerhk# echo 1 > wirelessled
root@linx:/proc/driver/acerhk# cat wirelessled
root@linx:/proc/driver/acerhk#
```

The kernel doesn't give any output while this is happening.

---

### Post by chili555 on 2009-05-18
Please post:```
cd /proc/driver/acerhk/

ls
```Is a file called *wirelessled* even there?

---

### Post by calrogman on 2009-05-18
I find your lack of faith disturbing.

```
root@linx:~# cd /proc/driver/acerhk; ls; cd -
blueled  info  key  led  wirelessled
/root
root@linx:~#
```

---

### Post by elimoon8 on 2009-05-20
so I got my ethernet working (*sheepish* Turns out the real problem was that my internet connection was down -- happens rarely, so I didn't consider it as a possible problem.)

I did as you asked, and I got:

>> dmesg | grep iwl3945
[   13.113969] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.113973] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   13.114086] iwl3945 0000:02:00.0: enabling device (0000 -> 0002)
[   13.114096] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.114114] iwl3945 0000:02:00.0: setting latency timer to 64
[   13.135411] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   13.135429] iwl3945 0000:02:00.0: PCI INT A disabled
[   13.135796] iwl3945: probe of 0000:02:00.0 failed with error -5

I don't know what to make of it.

---

### Post by elimoon8 on 2009-09-12
*bump* 
I never got a reply after this point. Anyone have a clue as to where the previous posters were going?

---

