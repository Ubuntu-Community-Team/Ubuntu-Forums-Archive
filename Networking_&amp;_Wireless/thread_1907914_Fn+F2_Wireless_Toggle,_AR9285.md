---
title: "Fn+F2 Wireless Toggle, AR9285"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by Zyland on 2012-01-12
Problem - Wireless disabled by hardware switch.

I thought I could hit FN+f2 (Laptop is a Asus K61LC), but that only seems to toggle the soft lock, not the hard lock.

Example:

> USER@USER-K61IC:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes

Hitting Fn + F2 results in:
> USER@USER-K61IC:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: yes

Now, using event to monitor the presses of the Fn + F2
> USER@USER-K61IC:~$ rfkill event
1326375094.101854: idx 0 type 1 op 0 soft 1 hard 1
1326375098.155679: idx 0 type 1 op 2 soft 0 hard 1
1326375098.869131: idx 0 type 1 op 2 soft 1 hard 1
1326375099.313037: idx 0 type 1 op 2 soft 0 hard 1
1326375099.847744: idx 0 type 1 op 2 soft 1 hard 1
^Z 
[1]+ Stopped rfkill event

lspci: 
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


So, all I can really seem to find suggest loading the laptop through windows and hitting the switch, something I don't have available to me right now. I'm using Ubuntu, and the wired connection is how I'm connecting to you now. Any pointers I should follow to try and resolve this? Thanks for any and all assistance.

I've now been through about 20 threads, and even more bug reports. I've tried the following that did NOT work:

sudo service Network-Manager stop
sudo rmmod -f acer_wmi
sudo modprobe -r acer_wmi
sudo rfkill unblock all
sudo service Network-Manager start
(Most bug reports and threads seemed to end after unblock all was mentioned, which doesn't work for me)

(my assumption is that the acer part didn't work due to that not being the driver type being used)

---

### Post by wildmanne39 on 2012-01-12
Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Zyland on 2012-01-12
cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux clare47-K61IC 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net
```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
	Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop [1043:16d5]
	Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave Device [1a3b:1089]
	Kernel driver in use: ath9k

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```
rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

lsmod
```
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  1 
snd_hda_codec_hdmi     32040  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
ath9k                 127538  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
joydev                 17693  0 
cfg80211              199587  3 ath9k,mac80211,ath
serio_raw              13166  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
binfmt_misc            17540  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_laptop            19722  0 
sparse_keymap          13890  1 asus_laptop
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
nouveau               728662  3 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
drm                   236290  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
r8169                  52788  0 
wmi                    19256  1 mxm_wmi
video                  19412  1 nouveau
ahci                   26002  2 
libahci                26861  1 ahci

```

---

### Post by wildmanne39 on 2012-01-12
Hi, double check and make sure those are the keys that turn your wireless on then you can do the following.
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit.
```
rmmod -f ath9k
rfkill unblock all
modprobe ath9k
```
Proofread carefully, save and close gedit. Reboot and tell us is it working now.
Thank you

---

### Post by Zyland on 2012-01-12
Did as you asked, there isn't a difference. I'm informed that Wireless is disabled by hardware switch still. Thanks for the assistance thus far.

---

### Post by wildmanne39 on 2012-01-12
Hi, go into your bios and make sure it is not turned off in there, then if I need to I will do some more research.

In almost all cases the commands I gave you to put in that file fixes the issue.

Did you reboot? also you can open that file again and make sure the file is still there.
Thanks

---

### Post by Zyland on 2012-01-12
It is enabled in BIOs. I also tried to disable it to see if that would make a difference, it did not.

The file is still edited with the extra commands.

I have rebooted numerous times, as that was something that had fixed the issue for others. When rebooting, I can toggle the LED via Fn+F2, which I can't do once Ubuntu is fully loaded.

My research showed that there has been issues with the Fn+F2 combination not toggling the hard lock for a lot of people, and most resolved with either commands listed in this thread, or booting into a windows dual boot and toggling it. I don't have access to windows at the moment, but a MINT LIveCD (which worked for a handful) did not work for me.

I hope that information helps with your research. I've pretty much resigned to baseline into windows (this is a smaller hard drive), making sure the wireless works, then going back to Ubuntu. If I can't come up with another solution in the next few days, this is what I'll probably do.

---

### Post by wildmanne39 on 2012-01-12
Hi, try this please:
```
sudo rmmod -f mxm_wmi
```
Thanks

---

### Post by Zyland on 2012-01-12
sudo rmmod -f mxm_wmi

```
ERROR: Removing 'mxm_wmi': Resource temporarily unavailable

```

---

### Post by wildmanne39 on 2012-01-12
Hi, please try it this way.
```
sudo ifconfig wlan0 down
sudo rmmod -f mxm_wmi
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
Thanks

---

### Post by Zyland on 2012-01-12
```
USER@USER-K61IC:~$ sudo ifconfig wlan0 down
USER@USER-K61IC:~$ sudo rmmod -f mxm_wmi
ERROR: Removing 'mxm_wmi': Resource temporarily unavailable
USER@USER-K61IC:~$ sudo rmmod -f ath9k
USER@USER-K61IC:~$ sudo modprobe ath9k nohwcrypt=1
USER@USER-K61IC:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

```

Want me to try rfkill unblock all?

---

### Post by wildmanne39 on 2012-01-12
Hi, you can try it again with sudo, I will try to find something else to try.
Thanks

---

### Post by Zyland on 2012-01-12
```
USER@USER-K61IC:~$ sudo rfkill unblock all
USER@USER-K61IC:~$ rfkill list
2: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

Well, that is interesting. 

0: phy0: Wireless LAN
Changed to 
2: phy2: Wireless LAN

---

### Post by wildmanne39 on 2012-01-12
Hi, also please post the out put of:
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e etork -e radio -e switch | tail -n75
```
Thanks

---

### Post by Zyland on 2012-01-12
```
Jan 12 11:59:54 USER-K61IC kernel: [   20.145548] ath9k 0000:04:00.0: setting latency timer to 64
Jan 12 11:59:54 USER-K61IC kernel: [   20.286791] ath: EEPROM regdomain: 0x60
Jan 12 11:59:54 USER-K61IC kernel: [   20.286795] ath: EEPROM indicates we should expect a direct regpair map
Jan 12 11:59:54 USER-K61IC kernel: [   20.286799] ath: Country alpha2 being used: 00
Jan 12 11:59:54 USER-K61IC kernel: [   20.286801] ath: Regpair used: 0x60
Jan 12 11:59:54 USER-K61IC kernel: [   20.372761] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Jan 12 11:59:54 USER-K61IC kernel: [   20.374645] Registered led device: ath9k-phy0
Jan 12 11:59:54 USER-K61IC kernel: [   20.425257] elantech: assuming hardware version 2, firmware version 4.1.1
Jan 12 11:59:54 USER-K61IC kernel: [   20.611888] type=1400 audit(1326391194.371:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=979 comm="apparmor_parser"
Jan 12 11:59:54 USER-K61IC NetworkManager[696]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Jan 12 11:59:54 USER-K61IC NetworkManager[696]: <info> WiFi now disabled by radio killswitch
Jan 12 11:59:54 USER-K61IC NetworkManager[696]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jan 12 11:59:54 USER-K61IC NetworkManager[696]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jan 12 11:59:54 USER-K61IC NetworkManager[696]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 12 18:16:40 USER-K61IC kernel: [    1.688810] Console: switching to colour frame buffer device 170x48
Jan 12 18:16:40 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/net/eth0, iface: eth0)
Jan 12 18:16:40 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 12 18:16:40 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 12 18:16:40 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 12 18:16:40 USER-K61IC NetworkManager[736]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 12 18:16:40 USER-K61IC NetworkManager[736]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan 12 18:16:40 USER-K61IC NetworkManager[736]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan 12 18:16:40 USER-K61IC NetworkManager[736]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan 12 18:16:40 USER-K61IC kernel: [   20.014870] ath9k 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 17 (level, low) -> IRQ 17
Jan 12 18:16:40 USER-K61IC kernel: [   20.014880] ath9k 0000:04:00.0: setting latency timer to 64
Jan 12 18:16:40 USER-K61IC kernel: [   20.107186] elantech: assuming hardware version 2, firmware version 4.1.1
Jan 12 18:16:40 USER-K61IC kernel: [   20.129049] ath: EEPROM regdomain: 0x60
Jan 12 18:16:40 USER-K61IC kernel: [   20.129053] ath: EEPROM indicates we should expect a direct regpair map
Jan 12 18:16:40 USER-K61IC kernel: [   20.129057] ath: Country alpha2 being used: 00
Jan 12 18:16:40 USER-K61IC kernel: [   20.129059] ath: Regpair used: 0x60
Jan 12 18:16:41 USER-K61IC kernel: [   20.272684] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Jan 12 18:16:41 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 12 18:16:41 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 12 18:16:41 USER-K61IC kernel: [   20.320288] Registered led device: ath9k-phy0
Jan 12 18:16:41 USER-K61IC NetworkManager[736]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Jan 12 18:16:41 USER-K61IC NetworkManager[736]: <info> WiFi now disabled by radio killswitch
Jan 12 18:16:41 USER-K61IC NetworkManager[736]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jan 12 18:16:41 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jan 12 18:16:41 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 12 18:16:47 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jan 12 18:16:48 USER-K61IC NetworkManager[736]: <info> WiFi now enabled by radio killswitch
Jan 12 18:16:48 USER-K61IC NetworkManager[736]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/ieee80211/phy0/rfkill0 disappeared
Jan 12 18:16:48 USER-K61IC kernel: [   27.301838] ath9k 0000:04:00.0: PCI INT A disabled
Jan 12 18:16:48 USER-K61IC kernel: [   27.301888] ath9k: Driver unloaded
Jan 12 18:16:48 USER-K61IC kernel: [   27.329185] ath9k 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 17 (level, low) -> IRQ 17
Jan 12 18:16:48 USER-K61IC kernel: [   27.329200] ath9k 0000:04:00.0: setting latency timer to 64
Jan 12 18:16:48 USER-K61IC NetworkManager[736]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/ieee80211/phy1/rfkill1) (driver (unknown))
Jan 12 18:16:48 USER-K61IC kernel: [   27.377732] ath: EEPROM regdomain: 0x60
Jan 12 18:16:48 USER-K61IC kernel: [   27.377735] ath: EEPROM indicates we should expect a direct regpair map
Jan 12 18:16:48 USER-K61IC kernel: [   27.377739] ath: Country alpha2 being used: 00
Jan 12 18:16:48 USER-K61IC kernel: [   27.377741] ath: Regpair used: 0x60
Jan 12 18:16:48 USER-K61IC kernel: [   27.379575] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
Jan 12 18:16:48 USER-K61IC NetworkManager[736]: <info> WiFi now disabled by radio killswitch
Jan 12 18:16:48 USER-K61IC kernel: [   27.384397] Registered led device: ath9k-phy1
Jan 12 18:16:48 USER-K61IC NetworkManager[736]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 4)
Jan 12 18:16:48 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jan 12 18:16:48 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 12 19:00:22 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jan 12 19:00:22 USER-K61IC NetworkManager[736]: <info> WiFi now enabled by radio killswitch
Jan 12 19:00:22 USER-K61IC NetworkManager[736]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/ieee80211/phy1/rfkill1 disappeared
Jan 12 19:00:22 USER-K61IC kernel: [ 2641.734010] ath9k 0000:04:00.0: PCI INT A disabled
Jan 12 19:00:22 USER-K61IC kernel: [ 2641.734086] ath9k: Driver unloaded
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.521870] ath9k 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 17 (level, low) -> IRQ 17
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.521890] ath9k 0000:04:00.0: setting latency timer to 64
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.570700] ath: EEPROM regdomain: 0x60
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.570703] ath: EEPROM indicates we should expect a direct regpair map
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.570707] ath: Country alpha2 being used: 00
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.570709] ath: Regpair used: 0x60
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.572637] ieee80211 phy2: Selected rate control algorithm 'ath9k_rate_control'
Jan 12 19:00:40 USER-K61IC kernel: [ 2659.573548] Registered led device: ath9k-phy2
Jan 12 19:00:40 USER-K61IC NetworkManager[736]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/ieee80211/phy2/rfkill2) (driver (unknown))
Jan 12 19:00:40 USER-K61IC NetworkManager[736]: <info> WiFi now disabled by radio killswitch
Jan 12 19:00:40 USER-K61IC NetworkManager[736]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 6)
Jan 12 19:00:40 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jan 12 19:00:40 USER-K61IC NetworkManager[736]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:16.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.

```

---

### Post by wildmanne39 on 2012-01-12
Hi, please post the output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
```
Thanks

---

### Post by Zyland on 2012-01-12
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by wildmanne39 on 2012-01-12
Hi, it might help to install a newer kernel or an older one but that is not something I feel comfortable giving directions on how to do, you may want to start a thread in general or absolute section on changing kernels.

I recommend trying the newer Kernel first.
Thanks

---

### Post by Zyland on 2012-01-12
I had tried an older one, and in recovery, but I'll see what I can do for the newer. Thanks for your time and effort, wildmanne39.

---

### Post by wildmanne39 on 2012-01-12
Hi, your welcome! I wish I could have solved it for you.

---

