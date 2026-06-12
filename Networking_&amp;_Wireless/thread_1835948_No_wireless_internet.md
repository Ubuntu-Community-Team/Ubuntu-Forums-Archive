---
title: "No wireless internet"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by bigpimpin1 on 2011-08-30
Hello,

I just switched from Windows 7 to Ubuntu 11.04. I'm liking it very much at the moment. I do have some problems though.

Yesterday, I could connect to the internet while using the wireless connection. Today, I can't. My computer can still see the available wireless networks and can even connect to our wireless network. I can't seem to surf on the internet though. But I can obtain an IP-address and everything on the wireless network interface wlan0. So that's pretty weird. So I'm guessing it's not a driver-problem perse, since it used to work?

In any case, here is the lspci-output:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller
03:00.4 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

The ethernet connection is working perfectly, btw. Hope you guys can help!

---

### Post by praseodym on 2011-08-30
Hi,

can you show additionally:

```
iwconfig
rfkill list
lsmod
dmesg | grep iwl
sudo iwlist scan
iwlist chan
```

---

### Post by bigpimpin1 on 2011-08-30
Thanks for the reply. Some outputs: 

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: sony-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
4: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
user@pc:~$ lsmod
Module                  Size  Used by
isofs                  39571  1 
nls_utf8               12493  1 
udf                    83795  0 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
rfcomm                 38125  8 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlagn                284777  0 
i915                  451068  9 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
iwlcore               148964  1 iwlagn
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  2 iwlagn,iwlcore
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
qcserial               12702  0 
usb_wwan               19711  1 qcserial
usbserial              37116  2 qcserial,usb_wwan
btusb                  18160  2 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   184164  5 i915,drm_kms_helper
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              156212  3 iwlagn,iwlcore,mac80211
soundcore              12600  1 snd
psmouse                59039  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
intel_ips              17769  0 
sony_laptop            34432  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
ahci                   21591  3 
atl1c                  36237  0 
sdhci_pci              13623  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  2 udf,firewire_core
user@user-PC:~$ dmesg | grep iwl
[   16.886654] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.886658] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   16.886729] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.886739] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.886779] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   16.901783] iwlagn 0000:02:00.0: device EEPROM VER=0x436, CALIB=0x6
[   16.901787] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   16.901823] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.901894] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
[   16.947513] iwlagn 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   16.954061] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   58.267970] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 1
[   77.640546] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 0
[   83.629409] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 3
[   90.612100] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 0
[  126.233777] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 0
[  317.389294] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 6
[  449.638214] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = 5c:35:3b:00:a5:3c tid = 0
[ 4697.174426] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 7
[ 4710.237533] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 7
[ 4719.165580] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 4
[ 4726.787050] Modules linked in: cryptd aes_i586 aes_generic binfmt_misc rfcomm sco bnep l2cap parport_pc ppdev joydev snd_hda_codec_hdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm iwlagn i915 snd_seq_midi snd_rawmidi snd_seq_midi_event iwlcore snd_seq mac80211 snd_timer snd_seq_device drm_kms_helper qcserial usb_wwan usbserial btusb snd drm uvcvideo videodev bluetooth cfg80211 soundcore psmouse snd_page_alloc i2c_algo_bit serio_raw intel_ips sony_laptop video lp parport usbhid hid firewire_ohci ahci atl1c sdhci_pci libahci sdhci firewire_core crc_itu_t
[ 4727.574106] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 7
[ 5444.605886] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 0
[ 5714.381308] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 1
[ 6074.125736] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = 5c:35:3b:00:a5:3c tid = 0
[ 7305.381777] iwlagn 0000:02:00.0: Aggregation not enabled for tid 6 because load = 1

```


```
wlan0     Scan completed :
          Cell 01 - Address: 5C:35:3B:00:A5:3C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000036fd61613d
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 000477696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001097A12
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706424500010D10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B286015C353B00A53C1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000100
          Cell 02 - Address: 00:21:29:77:58:FB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000020b15aca2e
                    Extra: Last beacon: 4512ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD710050F204104A0001101044000102103B000103104700100021297758F90021297758F90400E8001021000C4C696E6B73797320496E632E102300075752543136304E1024000776312E30322E33104200033030311054000800060050F2040001101100075752543136304E100800020088
                    IE: Unknown: DD090010180201F4010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 03 - Address: 00:23:08:7F:8F:8F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Huymans"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000223ac5a70c2
                    Extra: Last beacon: 4952ms ago
                    IE: Unknown: 00074875796D616E73
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

```

---

### Post by praseodym on 2011-08-30
"iwconfig" is missing. You may choose WPA2-AES encryption, mixed encryption sometimes causes problems. Which of the "cells" do you want to connect to?

---

### Post by bigpimpin1 on 2011-08-30
iwconfig:

```
user@user-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"wifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C:35:3B:00:A5:3C   
          Bit Rate=58.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

```

What do you mean by cell? I just want to connect to wlan0...

---

### Post by bigpimpin1 on 2011-08-30
Ok weird, right now it's working again. I didn't change anything though. Not really logical...

---

### Post by akoskm on 2011-08-30
Not sure what can you figure out from static logs but I'm usually starting the log viewer, trying to connect with wireless and looking at the changes in *syslog* after lines like this:
```

Aug 30 16:01:18 turing NetworkManager[787]: <info> Activation (wlan0) starting connection 'myAP'

```
by this I can actively follow whats happening not just with the wireless card, but between the card and the other parts of my system (like network manager).
Identifying the problem by this way could be easier.

---

### Post by bigpimpin1 on 2011-08-30
I just rebooted and now the wifi's off again. Really frustrating.

I checked out the syslog, but no real warnings or errors are noticable. All seems to be working correctly. I just can't connect to the internet. The settings seem to be correct as well.

The result of ifconfig:

```
user@user-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:be:eb:77:35  
          inet addr:192.168.0.233  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:beff:feeb:7735/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5624 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:1105181 (1.1 MB)  TX bytes:6897503 (6.8 MB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23340 (23.3 KB)  TX bytes:23340 (23.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:14:ea:dc:a8  
          inet addr:192.168.0.234  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:14ff:feea:dca8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1504356 (1.5 MB)  TX bytes:369081 (369.0 KB)

```

---

### Post by wildmanne39 on 2011-08-30
Hi, try this to see if it comes back on if it does we will need to blacklist it to make it persistent.
```
sudo rmmod -f sony-laptop
```
Thank you

---

### Post by bigpimpin1 on 2011-08-30
Should I replace "sony-laptop" with some other name, like the name of my laptop? It can't find either and the wireless connection is not coming up.

---

### Post by wildmanne39 on 2011-08-30
Hi, no run the command just as it is, if it does not work we will go from there.
Thank you

---

### Post by bigpimpin1 on 2011-08-30
It didn't work. I think the first time it did remove a folder, but it didn't get the connection back on. The network manager does say that I'm connected to the wireless network, I just can't ping anywhere..

---

### Post by bigpimpin1 on 2011-08-30
I tried something else: I just disabled networking and then re-enabled it. It automatically connected to the wireless network and I could ping my router (first time). Maybe you can go from there?

---

### Post by wildmanne39 on 2011-08-30
Hi, I am researching it right now, it seems to be a bug in the firmware, I am trying to find a fix for it.

---

### Post by wildmanne39 on 2011-08-30
Hi, it is the same that I fixed for someone else that is what I thought but I had to make sure, do what I mention in post 7 of this link and it should get you working.
[http://ubuntuforums.org/showthread.php?p=11121782#post11121782](http://ubuntuforums.org/showthread.php?p=11121782#post11121782)
Thank you

---

### Post by bigpimpin1 on 2011-08-30
What I did:

```


user@user-PC:~$ gksu gedit /etc/modprobe.d/options.conf

(gedit:4359): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4359): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.36U30V': No such file or directory

(gedit:4359): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4359): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3JJT0V': No such file or directory

(gedit:4359): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
user@user-PC:~$ gksu gedit /etc/modprobe.d/options.conf

(gedit:4379): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.FZQ10V': No such file or directory

(gedit:4379): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4379): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.ZE2Y0V': No such file or directory

(gedit:4379): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

I saved it to the file but there were no other lines in it. 
Is this normal? Thanks for your help.

---

### Post by wildmanne39 on 2011-08-30
Hi, yes it should have been empty.

---

### Post by bigpimpin1 on 2011-08-30
And the errors are normal as well?

The wireless is still working for now. In any case, thank you very much for your advice. It was very good!

---

### Post by wildmanne39 on 2011-08-30
Hi, your welcome! give it a couple of hours to make sure, then would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by bigpimpin1 on 2011-08-30
I just put my laptop in hibernate and put it back on. Wifi wasn't working again. I just had to disable networking and enable it again. Then wireless was working again. So I'll probably have to do that each time. Not ideal though.. Weird the fix you mentioned is not working for me apparently.

---

### Post by wildmanne39 on 2011-08-30
Hi, I will do some more research it may be a hibernation issue with it.

Before it was not working most of the time even with out being hibernated is that correct?
Thank you

---

### Post by bigpimpin1 on 2011-08-30
Yes, that's correct. Thanks for the effort mate.

---

### Post by wildmanne39 on 2011-08-30
Ok, then this might be a separate issue.

There are many work arounds  that are listed for this driver I will have to research and see if one is for waking up after hibernating.

You might check you bios and make sure it is set to wake on lan.
Thank you

---

### Post by bigpimpin1 on 2011-08-30
Yeah it probably is, restarting did work: the wireless connection worked immediately! I'll check for the WOL in the bios.

---

### Post by bigpimpin1 on 2011-08-30
Can't seem to find the wake on lan-options in the BIOS. Looks like Sony just kept the most important options in the BIOS, like boot-options, etc. So I can't be sure about that...

---

### Post by bigpimpin1 on 2011-08-30
It seems to be working after hibernate/suspend now as well. These functions only work when I close the lid apparently, weird. But everything seems to be working. I'll wait for a couple of hours and then mark the thread solved.

Thanks for the help, again.

---

### Post by wildmanne39 on 2011-08-30
Hi, ok glad to hear it, there are a lot of other problems people usually have with suspend or hibernate, so I think you are lucky there if it is working.

---

