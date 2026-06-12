---
title: "Ubuntu 12.04LTS Wireless not connecting after installing updates."
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by mysteryDave on 2013-01-05
Using Ubuntu 12.04 LTS the wireless connection worked fine after initial install untill I installed some updates via the update manager.

Now it keeps trying to connect to the wireless, prompting me for credentials, but never establishes the connection.

The wireless adaptor is a Azurewave USB.


Here are the most recent updates:
unity(5.14.0-0ubuntu1,5.18.0ubuntu1)
libcupsppdc1(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
libcupsimage2(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
libcupscgi1(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
libcupsdriver1(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
libparted0debian1(2.3.8-0ubuntu5,2.3.8-0ubuntu5.1)
unity-common(5.14.0-0ubuntu1,5.18.0-0ubuntu1)
cups-client(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
cups-ppdc(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
cups-common(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
libcups2(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
liboverlay-scrollbar3-0.2-0(0.2.16-0ubuntu1,0.2.16-0ubuntu1.1)
libunity-core-5.0-5(5.14.0-0ubuntu1,5.18.0-0ubuntu1)
cups(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
unity-services(5.14.0-0ubuntu1,5.18.0-0ubuntu1)
cups-bsd(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
libudev0(175-0ubuntu9.1,175-0ubuntu9.2)
libcupsmime1(1.5.3-0ubuntu5.1,1.5.3-0ubuntu6)
liboverlay-scrollbar-0.2-0(0.2.16-0ubuntu1,0.2.16-0ubuntu1.1)
libssl1.0.0(1.0.1-4ubuntu5.3,1.0.1-5ubuntu5.5)

I tried following the solution of reverting the network manager shown in this thread:
[http://askubuntu.com/questions/146948/internet-on-ubuntu-12-04-stopped-to-work-after-installing-updates-from-the-updat](http://askubuntu.com/questions/146948/internet-on-ubuntu-12-04-stopped-to-work-after-installing-updates-from-the-updat)
but to no avail. I thought it unlikely as the network manager was not in the latest updates

I also reverted the libssl version but also no change.

```

:~$ lspci
00:00.0 Host bridge: NVIDIA Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: NVIDIA Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1)
00:0e.0 RAID bus controller: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:0e.1 RAID bus controller: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:0e.2 RAID bus controller: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: NVIDIA Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
01:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for GTX 295 (rev a3)
02:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for GTX 295 (rev a3)
02:02.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for GTX 295 (rev a3)
03:00.0 3D controller: NVIDIA Corporation GT200b [GeForce GTX 295] (rev a1)
04:00.0 VGA compatible controller: NVIDIA Corporation GT200b [GeForce GTX 295] (rev a1)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]

:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12744  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
usblp                  18307  0 
snd_hda_codec_realtek   224066  1 
adt7475                31231  0 
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
hwmon_vid              12827  1 adt7475
arc4                   12529  2 
ir_mce_kbd_decoder     12777  0 
ir_sony_decoder        12510  0 
snd_hda_intel          33773  3 
rtl8187                57035  0 
mac80211              506816  1 rtl8187
cfg80211              205544  2 rtl8187,mac80211
ir_jvc_decoder         12507  0 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
joydev                 17693  0 
ir_rc6_decoder         12507  0 
rc_imon_pad            12505  0 
ir_rc5_decoder         12507  0 
imon                   32839  0 
ir_nec_decoder         12507  0 
lm90                   20090  0 
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_imon_pad,ir_rc5_decoder,imon,ir_nec_decoder
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
eeprom_93cx6           12725  1 rtl8187
hid_logitech           26520  0 
nouveau               774641  3 
ff_memless             13097  1 hid_logitech
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87692  0 
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_multipath           23230  0 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau
nv_tco                 13687  0 
i2c_nforce2            13058  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
usbhid                 47199  1 hid_logitech
hid                    99559  2 hid_logitech,usbhid
uas                    18180  0 
usb_storage            49198  1 
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
pata_amd               14118  0 
forcedeth              63460  0 
sata_nv                32286  4 
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  2 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  5 dm_raid45,dm_mirror,dm_region_hash

:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:15:af:24:b1:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.2.0-29-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

:~$ lspci -nnk | grep -iA2 net
00:11.0 Bridge [0680]: NVIDIA Corporation MCP55 Ethernet [10de:0373] (rev a2)
	Subsystem: NVIDIA Corporation Device [10de:c55e]
	Kernel driver in use: forcedeth
--
00:12.0 Bridge [0680]: NVIDIA Corporation MCP55 Ethernet [10de:0373] (rev a2)
	Subsystem: NVIDIA Corporation Device [10de:c55e]
	Kernel driver in use: forcedeth

:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:7111 Hewlett-Packard 
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser

:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

:~$ uname -a
Linux mystery 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

:~$ cat /etc/modprobe.d/blacklist-rare-network.conf 
# Many less commonly used network protocols have recently had various
# security flaws discovered. In an effort to reduce the scope of future
# vulnerability exploitations, they are being blacklisted here so that
# unprivileged users cannot use them by default. System owners can still
# either modify this file, or specifically modprobe any needed protocols.

# ax25
alias net-pf-3 off
# netrom
alias net-pf-6 off
# x25
alias net-pf-9 off
# rose
alias net-pf-11 off
# decnet
alias net-pf-12 off
# econet
alias net-pf-19 off
# rds
alias net-pf-21 off
# af_802154
alias net-pf-36 off

```

---

### Post by mysteryDave on 2013-01-15
.

---

### Post by mysteryDave on 2013-01-15
Still no wireless. On install from the Ubuntu CD it worked out of the box, I just had to give the credentials. After that it continued to work until these updates.

Now it continually asks for credentials and does not establish the connection.

I can see 4 approaches to resolving the issue:
1) Debug the wireless as is. (I have no idea how to approach this)
2) Revert the updates. I have downloaded the previous packages from launchpad:
[https://launchpad.net/ubuntu/+source/cups/1.5.3-0ubuntu5.1](https://launchpad.net/ubuntu/+source/cups/1.5.3-0ubuntu5.1)
[https://launchpad.net/ubuntu/+source/unity/5.14.0-0ubuntu1](https://launchpad.net/ubuntu/+source/unity/5.14.0-0ubuntu1)
[https://launchpad.net/ubuntu/+source/udev/175-0ubuntu9.1](https://launchpad.net/ubuntu/+source/udev/175-0ubuntu9.1)
[https://launchpad.net/ubuntu/+source/parted/2.3-8ubuntu5.1](https://launchpad.net/ubuntu/+source/parted/2.3-8ubuntu5.1)
[https://launchpad.net/ubuntu/+source/overlay-scrollbar/0.2.16-0ubuntu1.1](https://launchpad.net/ubuntu/+source/overlay-scrollbar/0.2.16-0ubuntu1.1)
& installed using sudo dpkg -i
Still the problem persists.
3) Make a separate fresh install and copy the wireless configuration.
4) Backup my files and reinstall Ubuntu.

Having exhausted 2, and unsure on how to proceed with 1 or 3 I am leaning toward 4, but it seems quite extreme!

I've seen a couple of threads where people have similar problems but had no luck following the steps there either.

Can anyone suggest a better way please?

---

### Post by mysteryDave on 2013-01-23
After uninstalling the packages and observing no improvement after restart I attempted to boot from the Ubuntu 12.04 CD. From which the wireless originally worked.

I had a couple of failed attempts to boot from the CD due to bad sectors (My drive is in dire need of replacement.) after which I restarted normally from the hard disk and found the wireless connected and stayed connected without problems. I'm posting from the Ubuntu box now.

The immediate problem is somehow resolved, presumably by the reverting of the updates. I'll retry the updates more slowly to see if I can identify the individual one(s) that break it.

---

### Post by egidijus on 2013-01-29
I also have this problem after I updated the system (Ubuntu 12.04) two days ago. Tried to boot from LinuxMint live CD and wireless worked flawlessly, but when system boots up from hdd it cannot connect wirelessly.
I have no idea what to do :(

---

### Post by egidijus on 2013-01-29
I got it working by disabling proprietary ‘Broadcom STA Driver' from Additional Drivers and rebooting. My wireless card Broadcom BCM4313.

---

