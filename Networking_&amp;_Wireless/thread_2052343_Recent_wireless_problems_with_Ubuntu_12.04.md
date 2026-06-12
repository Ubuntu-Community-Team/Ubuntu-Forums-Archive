---
title: "Recent wireless problems with Ubuntu 12.04"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by zqjxkv on 2012-09-03
Hi guys.

Recently, I've been having a lot of trouble connecting to my university's wireless network on my Ubuntu partition. I don't think it's a problem with the university's network because my Window's partition and iPhone haven't had any problems connecting to the network. I've looked around online for a long time and kind of gave up at this point.

Basically after an arbitrary amount of time, my connection suddenly disconnects. It tries to reconnect afterwards but does not succeed. In order to reestablish the connection, usually I just disable/reenable my wireless and it works.

**1) Machine brand and model**
Lenovo T410

**2) Wireless brand, model, chipset**
```

$ lspci -nn | grep 'Network'
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 35)

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
Bus 002 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse

```

**3) Interfaces**
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:f6:ac:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2400000-f2420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2312582 (2.3 MB)  TX bytes:2312582 (2.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d7:0d:c3:88  
          inet addr:209.2.232.209  Bcast:209.2.239.255  Mask:255.255.248.0
          inet6 addr: fe80::224:d7ff:fe0d:c388/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:683371804 (683.3 MB)  TX bytes:22463256 (22.4 MB)

$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Columbia University"  
          Mode:Managed  Frequency:5.825 GHz  Access Point: D8:C7:C8:83:C6:D1   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:563  Invalid misc:103   Missed beacon:0

```

**4) Modules**
```

$ lsmod | grep "iwlwifi"
iwlwifi               332525  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211

```

**5) Kernel messages**
```

dmesg | grep "iwlwifi"
[   24.950304] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.950340] iwlwifi 0000:03:00.0: setting latency timer to 64
[   24.950390] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   24.950392] iwlwifi 0000:03:00.0: pci_resource_base = ffffc9000066c000
[   24.950394] iwlwifi 0000:03:00.0: HW Revision ID = 0x35
[   24.950560] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   24.950644] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   24.950759] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   24.971018] iwlwifi 0000:03:00.0: device EEPROM VER=0x436, CALIB=0x6
[   24.971021] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   24.971023] iwlwifi 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   24.972448] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   25.229180] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   42.300186] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   42.307342] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   42.548109] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   42.555256] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   84.192541] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d0 tid = 0
[  239.503883] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d0 tid = 0
[  293.781783] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d0 tid = 0
[  515.686777] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d0 tid = 0
[ 1624.189764] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1624.197030] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 1664.116131] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d0 tid = 0
[ 1788.839480] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 2422.154334] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) rfcomm bnep parport_pc ppdev binfmt_misc vesafb joydev snd_hda_codec_hdmi arc4 snd_hda_codec_conexant mxm_wmi btusb bluetooth uvcvideo videodev v4l2_compat_ioctl32 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm nvidia(P) snd_seq_midi snd_rawmidi snd_seq_midi_event thinkpad_acpi psmouse nvram serio_raw intel_ips snd_seq tpm_tis snd_timer snd_seq_device mac_hid wmi video iwlwifi mac80211 snd cfg80211 soundcore snd_page_alloc mei(C) lp parport usbhid hid sdhci_pci sdhci firewire_ohci firewire_core crc_itu_t e1000e
[ 2422.154411]  [<ffffffffa01cabb5>] rs_get_rate+0x65/0x1d0 [iwlwifi]
[ 2471.058976] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 4611.975301] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 5914.814459] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 6398.105046] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 6702.118686] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 7286.687740] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 7286.694958] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 7333.736315] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 7434.893025] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 7551.238523] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 7551.245716] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 7589.229011] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 7750.383981] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 7750.391257] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 7776.256821] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0
[ 8211.537295] iwlwifi 0000:03:00.0: Queue 2 stuck for 2000 ms.
[ 8211.537302] iwlwifi 0000:03:00.0: Current read_ptr 84 write_ptr 88
[ 8211.537305] iwlwifi 0000:03:00.0: On demand firmware reload
[ 8213.537482] iwlwifi 0000:03:00.0: Error sending REPLY_RXON_TIMING: time out after 2000ms.
[ 8213.537490] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 160 write_ptr 162
[ 8213.537496] iwlwifi 0000:03:00.0: Failed to send timing (-110)!
[ 8215.323679] iwlwifi 0000:03:00.0: Error: Response NULL in 'REPLY_ADD_STA'
[ 8215.327967] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 8215.335128] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 8330.737738] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:e3:31 tid = 0
[ 8399.726929] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = d8:c7:c8:83:c6:d1 tid = 0

```

**6) Network configuration**
```

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 00:26:2d:f6:ac:ce
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:0d:c3:88
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-29-generic firmware=9.221.4.1 build 25532 ip=209.2.232.209 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f2000000-f2001fff

```

**7) Doesn't support scanning**

**8) Ubuntu version**
Ubuntu 12.04.1 LTS

**9) Kernel/architecture**
3.2.0-29-generic x86_64

Any help would be appreciated.

---

### Post by chili555 on 2012-09-03
You have the same driver and I believe you need the same solution as here: [http://ubuntuforums.org/showthread.php?t=2050475&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2050475&highlight=11n_disable)

---

### Post by zqjxkv on 2012-09-03
> **chili555 said:**
> You have the same driver and I believe you need the same solution as here: [http://ubuntuforums.org/showthread.php?t=2050475&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2050475&highlight=11n_disable)

Thanks for the reply. That definitely helped but didn't completely fix the problem. Now whenever the wireless disconnects, it at least reconnects automatically so I don't have to turn the wireless off/on again.

I remember reading that somebody else had a similar problem. I'm going to try changing the IPv6 settings. Do you have any other recommendations?

---

### Post by chili555 on 2012-09-03
> I'm going to try changing the IPv6 settings. To *Ignore*, please.

---

### Post by zqjxkv on 2012-09-03
> **chili555 said:**
> To *Ignore*, please.

Ignoring IPv6 didn't work. I also tried adding bt_coex_active=N like you recently suggested in the other thread but the wireless is still unstable.

---

### Post by chili555 on 2012-09-03
I wonder if there are any clues here:```
dmesg | grep iwl
```I am a bit mystified because I also have an iwlwifi device and it's rock solid.

---

### Post by zqjxkv on 2012-09-03
I am quite puzzled myself. It was working perfectly until very recently. I wonder if it's something I installed or updated, but nothing really comes to mind. I wish Ubuntu had a System Restore like Windows.

```

$ dmesg | grep iwl
[   24.935204] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.935242] iwlwifi 0000:03:00.0: setting latency timer to 64
[   24.935291] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   24.935293] iwlwifi 0000:03:00.0: pci_resource_base = ffffc9000066c000
[   24.935295] iwlwifi 0000:03:00.0: HW Revision ID = 0x35
[   24.935560] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   24.935757] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   24.935894] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   24.952796] iwlwifi 0000:03:00.0: device EEPROM VER=0x436, CALIB=0x6
[   24.952800] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   24.952803] iwlwifi 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   24.953478] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   25.186964] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   25.189515] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   26.939795] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   26.946988] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   27.188591] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   27.195780] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  468.241393] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  468.248579] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  468.840983] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  468.848276] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  513.022991] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  513.030127] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  513.674981] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  513.682111] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 3116.508910] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 3116.516109] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[ 3117.134017] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 3117.141178] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1

```

---

### Post by chili555 on 2012-09-03
It looks perfectly normal, I see nothing to fix.

You might try:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic [COLOR="Red"]<--or -pae if you are running a PAE kernel[/COLOR]
```Find out about PAE with:```
uname -r
```Reboot and let me know if there is improvement.

For example:> chili@LAPTOP60:~$ uname -r
3.2.0-29-generic-[COLOR="Red"]pae[/COLOR]Therefor, I'd need to install linux-backports-modules-cw-3.3-precise-generic-pae.

---

### Post by zqjxkv on 2012-09-03
Well, I ended up messing up my network by trying to use Wicd, since I read some people had luck with it. Instead, Wicd just gets stuck on obtaining the IP address and I am having trouble restoring Network Manager without Internet. I tried saving the .deb on a USB for Network Manager but it doesn't install due to dependency errors.

If nothing else works, I may just switch back to Windows since this is giving me so much trouble :/.

**EDIT**
Wicd connected now?

**EDIT 2**
Wireless seems to be working without a hitch using Wicd for some reason. Only downside is that I won't be able to use my uni's secure wireless until I figure out how to make a WPA2/tunneled TLS/PAP template. I kind of want to try reinstalling network-manager and network-manager-gnome.

---

### Post by rfporto on 2012-09-12
I have the same issue, did you end up solving this problem?  If so, what did you do?

---

