---
title: "Ubuntu 12.04 32bit Lenovo s10 e Ideapad Cannot connect to wireless (BCM4312)"
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by AshNova on 2013-03-27
Hi everyone,

I am trying to connect to my home wireless network on a Lenovo s10 e Ideapad. I tried using the Broadcom STA drivers through jockey and  bcmwl-kernel-source but had no luck. Installing b43-fwcutter and firmware-b43-lpphy-installer through terminal allowed me to connect but upon reboot the wireless just keeps attempting to connect and fails.

If anyone can help, I will be very grateful.

I will provide the following information in case it is useful :

```

anita@lenovo:~$  sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:08:83:90
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb v3.04 ip=192.168.10.20 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f0200000-f020ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0400000-f0403fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:23:4d:48:5f:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-39-generic-pae firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg

```

```

anita@lenovo:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux lenovo 3.2.0-39-generic-pae #62-Ubuntu SMP Wed Feb 27 22:25:11 UTC 2013 i686 i686 i386 GNU/Linux

```

```

anita@lenovo:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
	Kernel driver in use: tg3
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Kernel driver in use: b43-pci-bridge

```

```

anita@lenovo:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```

```

anita@lenovo:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```

anita@lenovo:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i915                  423466  2 
ums_realtek            17920  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_timer              28931  2 snd_pcm,snd_seq
b43                   342669  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  17948  0 
mac80211              436493  1 b43
snd                    62218  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             158479  1 btusb
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
psmouse                86520  0 
cfg80211              178877  2 b43,mac80211
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
serio_raw              13027  0 
bcma                   25651  1 b43
video                  19115  1 i915
ideapad_laptop         17890  0 
sparse_keymap          13658  1 ideapad_laptop
mac_hid                13077  0 
lp                     17455  0 
parport                40930  1 lp
usb_storage            39683  1 ums_realtek
ssb                    50691  1 b43
tg3                   141414  0 

```

Thank you.

---

### Post by Hadaka on 2013-03-27
Hi, to calrify you said..
"firmware-b43-lpphy-installer through terminal allowed me to connect but  upon reboot the wireless just keeps attempting to connect and fails."
so it looks like all was well untill you booted..is this correct?
if so..please do...
```
sudo modprobe b43
```
*IF it connects then do..
```
sudo su
echo b43 >> /etc/modules
exit
```
this will load the module every time you boot.
thanks.

---

### Post by AshNova on 2013-03-27
Hi Hadaka,

Yes, it seemed to be working fine until I rebooted.

I tried :

sudo modprobe b43

But it doesn't work. :(

Thanks.

---

### Post by Hadaka on 2013-03-27
Hi, ok lets try a different driver..
please do..
```
sudo apt-get remove --purge firmware-b43-lpphy-installer
sudo modprobe -r b43
```
then install...please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
that bring it to life?

---

### Post by AshNova on 2013-03-28
Did this :

```

sudo apt-get remove --purge firmware-b43-lpphy-installer
sudo modprobe -r b43

```

rebooted, then did this :

```

sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

```

Didn't work, just kept on trying to connect, fail, trying to connect again...

So I rebooted again but still no luck.

---

### Post by AshNova on 2013-03-28
Ok after shutting down and booting, the wireless works but a wired connection has to be present during boot up. 

Otherwise during boot up, it says "Waiting for network configuration...Waiting for network configuration for 60 more seconds..."

Then it boots up without networking.

If a wired connection is plugged in, the wireless connects as well. The ethernet cable can then be removed.

---

### Post by AshNova on 2013-03-28
It sort of works after I do this :
```
sudo mousepad /etc/network/interfaces
```
and removed this from interfaces :
 
# The primary network interface
auto eth0
iface eth0 inet dhcp

but it stops working after a while until next reboot.

---

### Post by Hadaka on 2013-03-28
Hi your /etc/network/interfaces should look like this..
```
auto lo
iface lo inet loopback
 
```

---

### Post by delamite on 2013-03-28
Huh, 
my s10 gave me no troubles with Ubuntu. It only gave me troubles when re-loading windows, because the WI-FI is part of the power management utilities. And I made the classic error of not having the external WI-FI switch turned on. I realize this is no help, but possibly may lead to a fix to your problem.

---

### Post by AshNova on 2013-03-28
> **Hadaka said:**
> Hi your /etc/network/interfaces should look like this..
```
auto lo
iface lo inet loopback
 
```

Hi Hadaka,

Yes, mine looks like that. :) 

But it was still timing out when I downloaded a lot of files or large files.

So after editing interfaces, I did this :

```
sudo mousepad /etc/modprobe.d/b43-pci-bridge.conf

```
and added the line :
options b43-pci-bridge.conf nohwcrypt=1

Also in network-manager, under IPv6 settings, I changed "Method" to Ignore.

So far it seems to be working, except that downloads via synaptic,terminal and websites like ubuntuforums.org seem a bit slow. Normal web browsing,streaming and http downloads seem fine. I will test for a few more days.

Thank you :)

---

### Post by AshNova on 2013-04-08
After extensive usage, I decided to purge linux-firmware-nonfree and install the Broadcom STA drivers through jockey. 

I'm not sure why the STA drivers did not work intially but everything seems to be fine now.

Also my interfaces looks like this :

```
auto lo
iface lo inet loopback
```

And I deleted everything in b43-pci-bridge.conf

---

