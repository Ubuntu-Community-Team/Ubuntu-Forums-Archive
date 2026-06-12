---
title: "No Network Connection -- 11.04"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by RockaRolla20 on 2012-10-17
[INDENT][/INDENT]Hey all, I recently reconfigured my wireless connection in my house, and am running an old school Belkin wifi card (Atheros AR2413A chipset) in my computer until I can upgrade to a dual band N card. I have no access to a wired connection for my computer at this time, and I am having a hard time getting the wireless configured correctly.
[INDENT][/INDENT]I am using WPA for encryption on my wifi, below is the current config of my system....

```
:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: Atheros Communications Inc. Device 0018 (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a2)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:08.0 Ethernet controller [0200]: Atheros Communications Inc. Device [168c:0018] (rev 01)

:~$ lsusb
Bus 002 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 002 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 002: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:66:2f:37:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2032 (2.0 KB)  TX bytes:2032 (2.0 KB)

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

:~$ lsmod
Module                  Size  Used by
ath_pci               198001  0 
wlan                  252376  1 ath_pci
ath_hal               435109  1 ath_pci
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
vesafb                 13761  1 
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
snd_hda_codec_realtek   336771  1 
joydev                 17606  0 
usb_storage            53538  1 
nvidia              10709116  40 
usbhid                 46956  0 
hid                    91020  1 usbhid
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ppdev                  17113  0 
edac_core              53845  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
k8temp                 13016  0 
edac_mce_amd           23464  0 
psmouse                73535  0 
serio_raw              13166  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36959  1 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
uas                    17996  0 
forcedeth              63555  0 
pata_amd               14130  0 
sata_nv                32054  3 

:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=96 maxlatency=28 mingnt=8
       resources: memory:dbfd0000-dbfdffff

:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.


```

I have trying for almost to get this configured for almost a week now and haven't been able to solve it yet. Any help would be greatly appreciated.

---

### Post by chili555 on 2012-10-17
> am running an old school Belkin wifi card (*Atheros AR2413A* chipset) in my computer Where? I don't see it in any of your readings. I see an Atheros ethernet device, but not wireless.

---

### Post by RockaRolla20 on 2012-10-17
I guess I had assumed the Atheros device showing up within lspci was the Wifi card  instead of ethernet. The board has a built in ethernet port but it went "bad" a while ago (which is the reason I haven't beeen using the computer). I will pull the MOBO info when I get home tonight and verify what chipset was built into the board.

I know I had tried to follow some other tutorials for setting up Atheros wifi cards. Could I have messed a configuration up somewhere?

---

### Post by chili555 on 2012-10-17
Pardon me. I am mistaken. Although the Atheros is shown as ethernet and shows as class 0200, its device ID says it's a wireless device! Usually, wireless is class 0280. Nvidia motherboards are nothing if not....different!> Ethernet controller [0200]: Atheros Communications Inc. Device [[COLOR="Red"]168c:0018[/COLOR]]

Sorry about my misstep.

Your device ought to work with the driver ath5k. Let's load it and see what happens:```
sudo modprobe ath5k
dmesg | grep ath
```We will probably need to blacklist a conflicting driver.

---

### Post by RockaRolla20 on 2012-10-17
The board is a Micro ATX and due to the size of my video card, only one slot is available.

If the PCI slot is bad? I will also try to reseat the card tonight as well.

---

### Post by chili555 on 2012-10-17
> **RockaRolla20 said:**
> The board is a Micro ATX and due to the size of my video card, only one slot is available.

If the PCI slot is bad? I will also try to reseat the card tonight as well.Please read my edit.

Let's take a big swing at this. When you get home, please do:```
sudo su
echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist.conf
echo ath5k >> /etc/modules
exit
```Reboot and let us have your report.

---

### Post by RockaRolla20 on 2012-10-17
So, here is what I accomplished...
[LIST]
[*]Re-seat Wireless Card
[*]Disabled onboard NIC via BIOS
[*]Ran code suggested above
[*]Restarted system
[/LIST]
And, it worked!

```

:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"DunkelRitter_2.4"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 10:BF:48:D3:42:D8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:177   Missed beacon:0

vboxnet0  no wireless extensions.

:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7750 (7.7 KB)  TX bytes:7750 (7.7 KB)

wlan1     Link encap:Ethernet  HWaddr 00:11:50:d5:c8:10  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fed5:c810/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9924271 (9.9 MB)  TX bytes:778112 (778.1 KB)

```

I am not sure what the code you listed did, but I greatly appreciate it.

---

### Post by chili555 on 2012-10-17
Glad it's working! Would you please use thread tools at the top to mark solved?

---

