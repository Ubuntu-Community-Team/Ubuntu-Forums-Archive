---
title: "Realtek Semiconductor Co., Ltd. RTL8192E Cannot See Network?"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by cjlmack on 2011-08-26
Hi, 
I've recently installed Ubuntu 11.04 and everything has been working great, except I cannot see ANY wireless networks, Wired works fine, and while on Windows 7 I can connect fine.
lspci -v gives me a wall of text, the end is:

> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8152
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 2000 [size=256]
    Memory at d4600000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl819xE
    Kernel modules: r8192se_pci, r8192e_pci


And iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Don't know if you need this, but lsmod|grep 819:
> r8192se_pci           524220  0 
cfg80211              178528  1 r8192se_pci
r8192e_pci            277396  0Any help is appreciated :p

---

### Post by praseodym on 2011-08-26
Hello,
there are two drivers loaded, blacklist the wrong one:

```
echo "blacklist r8192se_pci" | sudo tee /etc/modprobe.d/blacklist-r8192se_pci.conf
```
and reboot. Check:

```
iwconfig
lspci -nnk | grep -iA2 Realtek
lsmod #complete!
dmesg | egrep 'rtl8|r8'
sudo iwlist scan
rfkill list
```

---

### Post by cjlmack on 2011-08-26
Didn't get any networks, I did get a strange message on start up though, it was brief, I think it said 'did not accept connection, kill it-' 
```
callum@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

callum@ubuntu:~$ lspci -nnk | grep -iA2 Realtek
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8152]
    Kernel driver in use: rtl819xE
    Kernel modules: r8192se_pci, r8192e_pci
callum@ubuntu:~$ lsmod #complete!
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
i915                  514985  3 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72195  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
psmouse                73535  0 
r8192e_pci            277396  0 
videodev               82052  1 uvcvideo
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13166  0 
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
sparse_keymap          13898  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci
callum@ubuntu:~$ dmesg | egrep 'rtl8|r8'
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b7800000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    5.227562] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.227615] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.227670] r8169 0000:02:00.0: setting latency timer to 64
[    5.227750] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    5.228275] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc90005088000, 00:1e:33:c9:41:13, XID 04c00000 IRQ 43
[   18.074474] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   18.445861] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   18.445867] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   18.445878] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.445885] rtl819xE 0000:03:00.0: setting latency timer to 64
[   19.497611] r8169 0000:02:00.0: eth0: link down
[   20.100034] rtl819xE:Download Firmware: Put code fail!
[   20.100040] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   20.100043] rtl819xE:ERR in init_firmware()
[   20.100046] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   63.109509] r8169 0000:02:00.0: eth0: link up
[  119.263855] r8169 0000:02:00.0: eth0: link down
callum@ubuntu:~$ sudo iwlist scan
[sudo] password for callum: 
Sorry, try again.
[sudo] password for callum: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

Is what I got from: 
 	Code:
 	iwconfig lspci -nnk | grep -iA2 Realtek lsmod #complete! dmesg | egrep 'rtl8|r8' sudo iwlist scan rfkill list 
I'd be happy to give you any more data if you need it

---

### Post by praseodym on 2011-08-26
Firmware-error in "dmesg". Try the newest file **linux-firmware** fron 11.10 (copy/paste):

```
wget [http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb)
sudo dpkg -i linux-*.deb
```
Reboot and check again.

---

### Post by cjlmack on 2011-08-26
Same thing I'm afraid, 
```
callum@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

callum@ubuntu:~$ lspci -nnk | grep -iA2 Realtek
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8152]
    Kernel driver in use: rtl819xE
    Kernel modules: r8192se_pci, r8192e_pci
callum@ubuntu:~$ lsmod #complete!
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  515121  3 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42136  1 i915
psmouse                73535  0 
videodev               82052  1 uvcvideo
soundcore              12680  1 snd
serio_raw              13166  0 
v4l2_compat_ioctl32    17078  1 videodev
r8192e_pci            277396  0 
drm                   227534  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13898  0 
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci
callum@ubuntu:~$ dmesg | egrep 'rtl8|r8'
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b7800000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    5.252887] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.252942] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.252999] r8169 0000:02:00.0: setting latency timer to 64
[    5.253076] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    5.253605] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc90005088000, 00:1e:33:c9:41:13, XID 04c00000 IRQ 43
[   19.209778] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   19.361591] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   19.361597] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   19.361609] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.361617] rtl819xE 0000:03:00.0: setting latency timer to 64
[   20.870781] r8169 0000:02:00.0: eth0: link down
[   21.470096] rtl819xE:Download Firmware: Put code fail!
[   21.470103] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   21.470106] rtl819xE:ERR in init_firmware()
[   21.470110] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   77.463644] r8169 0000:02:00.0: eth0: link up
callum@ubuntu:~$ sudo iwlist scan
[sudo] password for callum: 
Sorry, try again.
[sudo] password for callum: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by northd_tech on 2011-08-26
> **cjlmack said:**
>  **lsmod**
Module                  Size  Used by
**r8192e_pci  **          277396  0 
[COLOR=Red]**r8169  **[/COLOR]                48022  0 

callum@ubuntu:~$ dmesg | egrep 'rtl8|r8'
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b7800000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    5.252887] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.252942] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.252999] r8169 0000:02:00.0: setting latency timer to 64
[    5.253076] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    5.253605] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc90005088000, 00:1e:33:c9:41:13, XID 04c00000 IRQ 43
[   19.209778] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   19.361591] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   19.361597] rtl819xE 0000:03:00.0: power state changed by ACPI to D0
[   19.361609] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.361617] rtl819xE 0000:03:00.0: setting latency timer to 64
[   20.870781] r8169 0000:02:00.0: eth0: link down
[   21.470096] rtl819xE:Download Firmware: Put code fail!
[   21.470103] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   21.470106] rtl819xE:ERR in init_firmware()
[   21.470110] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   77.463644] r8169 0000:02:00.0: eth0: link up

It looks to me like you've got a module conflict with the **bolded** parts above- I went through** several month**s of hell (including multiple emails to "Kidman" at Realtek to get their sourcecode updated multiple times for the 64-bit variety) on a relative's Toshiba with Realtek 8192[COLOR=Blue]**E**[/COLOR] (which is VERY different from the Realtek 8192[COLOR=Green]**SE**[/COLOR]).

I'll need to do some digging, but this is a minor blacklist and/or /etc/modules fix, as I recall.  [COLOR=Gray]Have you tried any of the more recent threads tagged "realtek 8192e"?
[/COLOR]
[http://ubuntuforums.org/tags.php?tag=realtek+8192e](http://ubuntuforums.org/tags.php?tag=realtek+8192e)

After a brief search, my posts #44 & 46 might help on this thread:

[http://ubuntuforums.org/showpost.php?p=10760256&postcount=44](http://ubuntuforums.org/showpost.php?p=10760256&postcount=44)

EDIT:  Actually, that Realtek [COLOR=Red]8169[/COLOR] could be the correct module for a cabled ethernet connection, but I still believe that you need the wireless blacklist fix at my posts #44 & 46 on the thread immediately above

---

### Post by praseodym on 2011-08-27
A User of the german forum got the driver from Realtek, see [here]("http://forum.ubuntuusers.de/post/3164172/"). Driver version rtl8192e_linux_2.6.0015.1013.2010 attached, it worked there.

Edit: filesize too big, get it via:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/3164172/rtl8192e_linux_2.6.0015.1013.2010.tar.gz
```

Can you show:

```
modinfo r8192e | egrep 'versi|filen'
```
Obviously Draft-N in the 5 GHz region did not work.

---

### Post by cjlmack on 2011-08-27
Sorry for the late post,
I installed the driver, but I couldn't complete the last ```
./wlan0up or ./wlan1up
```step,

Maybe it's because my iwconfig doesn't scan for wlan anymore?

```
callum@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

and:```
 callum@ubuntu:~$ modinfo r8192e | egrep 'versi|filen'
ERROR: modinfo: could not find module r8192e
callum@ubuntu:~$ modinfo RTL8192E | egrep 'versi|filen'
ERROR: modinfo: could not find module RTL8192E
callum@ubuntu:~$ 
```

I now get ```
callum@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

callum@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
callum@ubuntu:~$ modinfo RTL8192E | egrep 'versi|filen'
ERROR: modinfo: could not find module RTL8192E
callum@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

callum@ubuntu:~$ modinfo r8192e | egrep 'versi|filen'
ERROR: modinfo: could not find module r8192e
callum@ubuntu:~$ modinfo RTL8192E | egrep 'versi|filen'
ERROR: modinfo: could not find module RTL8192E
callum@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

callum@ubuntu:~$ lspci -nnk | grep -iA2 Realtek
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8152]
    Kernel modules: r8192e_pci
callum@ubuntu:~$ lsmod #complete!
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336771  1 
joydev                 17606  0 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
i915                  515121  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
ndiswrapper           249811  0 
drm_kms_helper         42136  1 i915
serio_raw              13166  0 
drm                   227534  4 i915,drm_kms_helper
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13898  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci
callum@ubuntu:~$ dmesg | egrep 'rtl8|r8'
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b7800000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    5.204669] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.204723] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.204778] r8169 0000:02:00.0: setting latency timer to 64
[    5.204857] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    5.205377] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc90005088000, 00:1e:33:c9:41:13, XID 04c00000 IRQ 43
[   21.046145] r8169 0000:02:00.0: eth0: link down
[   21.046153] r8169 0000:02:00.0: eth0: link down
[   22.734722] r8169 0000:02:00.0: eth0: link up
[   67.351040] r8169 0000:02:00.0: eth0: link down
[  322.437239] r8169 0000:02:00.0: eth0: link up
callum@ubuntu:~$ sudo iwlist scan
[sudo] password for callum: 
Sorry, try again.
[sudo] password for callum: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

callum@ubuntu:~$ rfkill list
```

when doing
```
iwconfig lspci -nnk | grep -iA2 Realtek lsmod #complete! dmesg | egrep 'rtl8|r8' sudo iwlist scan rfkill list
```
No more put code fails, 

I'm thinking it's as simple as finding out why iwconfig doesn't show wlan?

---

### Post by praseodym on 2011-08-27
You have to uninstall ndiswrapper completely first:


```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
and reboot. The command line is:

```
modinfo r8192e[COLOR="Red"]_pci[/COLOR] | egrep 'versi|filen'
```
plus:
```
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by northd_tech on 2011-08-27
I think you still don't have the correct module loaded (or have some incorrect ones in conflict).  Let's see the following:

```
lsmod
sudo lshw -C network
cat /etc/issue
cat /etc/lsb-release
ifconfig -a
cat /etc/modules
cat /etc/modprobe.d/* | egrep '819|rtl|rt2|rt3|rt6|rt7|rt8|rtl'

```You also might want to try this:

```
sudo ./wlan0up
```(but you will need to be in the correct Realtek 8192E "build" directory first for it to work).  If you can't find that command, try this and post the result:

```
locate wlan0up
```Also, on my relative's Realtek 8192E, the **working** module was named "r8192_pci," not "r8192**[COLOR=Red]e_pci[/COLOR]**" (hence the need for the 2 blacklist lines).

---

### Post by cjlmack on 2011-08-27
It works!

Followed Praseodym's advice, And it is working great! 
Thank you for your help guys, If I could do something for you, I would, But i'm damned awful with Linux and Ubuntu. :(

Thanks again, Best of luck for whatever you need luck for!

---

### Post by northd_tech on 2011-08-27
Hi CJ- I've been known to work for beer before (and the NY Giants/Jets game was postponed until Monday due to Hurricane Irene so I'm pretty bored right now) ;).

It might help some other forum readers if you post the output from the terminal commands at my post #10 for a **working** Realtek 8192E setup (like yours).

It might also help to see this hairy mess for a **working** 8192E (my relative's Realtek laptop recently moved away to college, so I can't check his):
```
sudo lspci -nnkvv | grep -iA50 etwo
```

Also the bad news- you should probably restart your Ubuntu setup several times to see if your wireless setup survives power cycling.  Also if you are running more than one Linux kernel, you might need to set up wireless for each kernel that you run.

---

### Post by cjlmack on 2011-08-27
No problem, I put the command you wanted at the start, and then the lsmod etc.

```
callum@ubuntu:~$ sudo lspci -nnkvv | grep -iA50 etwo
[sudo] password for callum: 
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8152]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 17
    Region 0: I/O ports at 2000 [size=256]
    Region 1: Memory at d4600000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number 10-21-9e-fe-ff-d2-24-00
    Kernel driver in use: rtl819xE
    Kernel modules: r8192e_pci

callum@ubuntu:~$ lsmod
Module                  Size  Used by
arc4                   12529  2 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  515121  3 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
drm_kms_helper         42136  1 i915
r8192e_pci            391865  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   227534  4 i915,drm_kms_helper
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
videodev               82052  1 uvcvideo
serio_raw              13166  0 
v4l2_compat_ioctl32    17078  1 videodev
soundcore              12680  1 snd
i2c_algo_bit           13400  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13898  0 
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
r8169                  48022  0 
ahci                   25951  1 
libahci                26642  1 ahci
callum@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:c9:41:13
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
  *-network
       description: Wireless interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:9e:21:10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE driverversion=0015.1013.2010 ip=192.168.2.14 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:d4600000-d4603fff
callum@ubuntu:~$ cat /etc/issue
Ubuntu 11.04 \n \l

callum@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
callum@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:c9:41:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31120 (31.1 KB)  TX bytes:21074 (21.0 KB)
          Interrupt:44 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8269 (8.2 KB)  TX bytes:8269 (8.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d2:9e:21:10  
          inet addr:192.168.2.14  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d2ff:fe9e:2110/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85334208 (85.3 MB)  TX bytes:24014759 (24.0 MB)
          Interrupt:17 Memory:ffffc90005188000-ffffc90005188100 

callum@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
callum@ubuntu:~$ cat /etc/modprobe.d/* | egrep '819|rtl|rt2|rt3|rt6|rt7|rt8|rtl'blacklist uart6850
blacklist r8192se_pci

```

Tutorial for driver installation is here: http://ubuntuforums.org/showthread.php?t=1239342&highlight=R8192E&page=9

---

