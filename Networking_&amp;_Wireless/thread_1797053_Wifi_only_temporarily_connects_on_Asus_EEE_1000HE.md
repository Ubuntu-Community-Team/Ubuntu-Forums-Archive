---
title: "Wifi only temporarily connects on Asus EEE 1000HE"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by nosehat on 2011-07-04
I've got an** Asus EEE 1000HE**, and it's worked fine for a long time with the EEEBUNTU distro (a distro based on Jaunty (i think) with a custom kernel).  Unfortunately, Eeebuntu is no longer maintained, so I recently did a clean install of **Ubuntu 10.04.2**.  I am now unable to get my wifi to work reliably.

 The wifi tries to connect for a while, then pops up the "Wireless  Network Authentication Required" window.  If I hit "connect" it will try  again for a while, then pop up the window.  Etc.  Note I know that my connection information is OK.  I haven't mistyped the password (see below).  Also note that the wifi antenna is turned on.  For example, iwlist scan is able to find my network.

There is a weird twist though:  The netbook is always able to connect through an ethernet cable on eth0 just fine.  **If I boot the netbook with the ethernet cable plugged in, the wifi instantly connects as well!**  I can then unplug the ethernet cable (eth0 goes away), but I am still able to use the wifi connection for about 5 minutes before it disconnects, and goes back to trying and failing to connect.

This behavior is 100% replicable--the wifi always works fine (for about 5 minutes) if it boots with the ethernet cable plugged in.  Very rarely, the wifi will also connect on boot without the ethernet cable, but that is not replicable.

Other EEE netbooks seem to have issues with multiple wireless drivers, like in [this thread]("http://ubuntuforums.org/showthread.php?t=1727945&highlight=1000he").  Perhaps something similar is happening here?  My card seems to be using rt2860sta as a driver.  I tried blacklisting it, to see if another driver was trying to load instead, but that just negated my wifi altogether.  (It's unblacklisted again)

My router is a very reliable Linksys WRT54GL with factory firmware which has never been flaky.  

I posted another thread about this in the absolute beginners forum [here]("http://ubuntuforums.org/showthread.php?t=1794076"), but I was advised to repost in this forum.

I'm at my wit's end.  This netbook will be useless without wifi.  Any suggestions?

Below is the suggested information for a first post:

Here's lspci (note there is nothing listed as "Wireless Brand" to grep out):
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
```Here's lsusb:

```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05dc:0330 Lexar Media, Inc. JumpDrive Expression
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Here's ifconfig:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:80:a1:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:13:e2:a3  
          inet6 addr: fe80::225:d3ff:fe13:e2a3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2585854 (2.5 MB)  TX bytes:0 (0.0 B)
          Interrupt:19 
```Here's iwconfig:

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: 98:FC:11:44:B1:8D   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-36 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Here's lsmod (note there's no "wlan_module_name" to grep out):

```
lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39841  1 
aes_i586                7268  142 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
dm_crypt               11331  0 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57374  0 
psmouse                63245  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
serio_raw               3978  0 
rt2860sta             481561  1 
eeepc_laptop           14331  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  287810  3 
drm_kms_helper         29329  1 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
video                  17375  1 i915
output                  1871  1 video
ahci                   32360  2 
agpgart                31724  2 drm,intel_agp
atl1e                  28018  0
```Here's dmesg | grep "wlan" (I'll be happy to post other kernel messages if it will help):

```
dmesg | grep "wlan"
[   24.200059] wlan0: no IPv6 routers present
```Here's sudo lshw -C network:

```
 *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 90:e6:ba:80:a1:db
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:25:d3:13:e2:a3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff
```Here's iwlist scan (it's working properly, and finds my wifi network and my neighbor's):

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <snip>
                    Protocol:802.11b/g
                    ESSID:"nosehatnet"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-37 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <snip>
                    Protocol:802.11b/g
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:6
                    Quality:15/100  Signal level:-84 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

```Here's the ubuntu version:

```
lsb_release -d
Description:    Ubuntu 10.04.2 LTS
```Here's the kernel/architecture:

```
uname -mr
2.6.32-32-generic i686
```Restarting the network:

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```

---

### Post by chili555 on 2011-07-05
I wonder if it's a power management issue. One of the biggest consumers of power on a laptop is the wireless radio. Because battery power is so precious, laptops have elaborate schemes to throttle down everything on a laptop if it's not in use. I believe that, in some cases, the power management is so aggressive that after two minutes or maybe less, power is reduced and the wireless disconnects. Now the wireless is *really* not in use and the wireless hasn't enough power to reconnect.

When your wireless is connected, please run:```
iwconfig
```What does it say about power management? Here is a sample from my machine.> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <snip>   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:[/COLOR]off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:61   Missed beacon:0If it's on, we could try to see if we can turn it off in System > Preferences > Power Management.

There are a few other things we could try if power management is the issue, but please confirm it first.


-------------

note to chili:  [http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67)

---

### Post by nosehat on 2011-07-05
Thanks, Chili555, I think you might be on the right track.

First, an update:  I was wrong about the ethernet cable/automatic wifi thing.  I plugged in my ethernet cable this morning and booted the netbook, hoping to get a wifi connection, and it didn't work.  It occurred to me that when I was testing this before I probably had the power chord plugged in at the same time I had the ethernet.  So I plugged in the power cord, charged up the battery to full, turned on the netbook and bingo!, the wifi connected (for about 3 minutes).  **A fully charged battery and a connected power cord are what's likely (but not certain) to produce a short-lived wifi connection.**  So far that's worked about 1/3 of the time.

Here's the result of iwconfig with the wifi connected:

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:"fishface"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 98:FC:11:44:B1:8D   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-38 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

There's no line about power management at all.  (I think "Mode:Managed" refers to something else?) 

I poked around in in System > Preferences > Power Management, but that seemed pretty rudimentary.  Is there any way to force the machine to give maximum power to the wifi card while the antenna is on?

Note:  I've got a pretty vanilla install of 10.4.2.  I haven't installed any extra acpi stuff.

---

### Post by chili555 on 2011-07-05
"Mode: Managed' means that the wireless card is being managed by the router or other access point. The AP sets the channel, bit-rate and many other details and your wireless card says, "Yes, Master." Here is my scan result:> $ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: <snip>
                    ESSID:"GBR1"
                    Protocol:IEEE 802.11bg
                    [COLOR="Red"]Mode:Master[/COLOR]
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-49 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 64ms ago
Now, as I type this, I am reviewing your scan results:> lan0     Scan completed :
          Cell 01 - Address: <snip>
                    Protocol:802.11b/g
                    ESSID:"nosehatnet"
                    [COLOR="Red"]Mode:Managed[/COLOR]
                    Channel:6
                    Quality:100/100  Signal level:-37 dBm  Noise level:-97 dBm
                    Encryption key: on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKI am like: :confused: :confused: :confused:

Is your router set to some unusual mode? Also, we have better luck with WPA2 only, not WPA/WPA2 mixed mode.

Please try turning power management off; let's see if we get an informative error, warning or other result:```
sudo iwconfig wlan0 power off
```

---

### Post by nosehat on 2011-07-05
I'm not sure if this will be useful, but here are a bunch of my linksys router's wifi settings:

```

Wireless Network Mode: Mixed
Wireless Channel: 6 - 2.437GHz
Security Mode:  WPA2 Personal
WPA Algorithms: TKIP+AES
Group Key Renewal: 3600 seconds
Wireless MAC filter: Disabled
Authentication Type: Auto
Basic Rate: Default
Transmission Rate: Auto
CTS Protection Mode: Disable
Frame Burst: Disable
Beacon Interval: 100 (milliseconds)
DTIM Interval: 1
Fragmentation Threshold: 2346
RTS Threshold: 2347
AP Isolation: Off
SecureEasySetup: Enabled

```I will point out that I haven't changed my router settings in a while, and this all worked fine when the netbook had eeebuntu on it (and these router settings work fine for the half dozen other wifi devices that use my network).

Here's the result of sudo iwconfig wlan0 power off.  I had an active wifi connection at the time I tried this:

```

Error for wireless request "Set Power Management" (8B2C) : 
    SET failed on device wlan0 ; Operation not supported.

```

---

### Post by chili555 on 2011-07-05
Is any module loaded specifically for EEE?```
lsmod | grep eee
```If so, we might remove it or manipulate its parameters; for example:```
$ modinfo eeepc-laptop
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/platform/x86/eeepc-laptop.ko
license:        GPL
description:    Eee PC Hotkey Driver
author:         Corentin Chary, Eric Cooper
srcversion:     6DF4D06541AA2FFC7EB3691
alias:          acpi*:ASUS010:*
depends:        sparse-keymap
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           hotplug_disabled:Disable hotplug for wireless device.[/COLOR] If your laptop need that, please report to acpi4asus-user@lists.sourceforge.net. (bool)

```I see nothing in your router settings that's troublesome.> Error for wireless request "Set Power Management" (8B2C) : 
    SET failed on device wlan0 ; Operation not supported.That means we the user and even we the sudo user are not permitted to monkey with power management in the usual, obvious way. I may not take 'No' for an answer.

---

### Post by nosehat on 2011-07-05
Chili555, thanks so much for your help so far!  I was about ready to throw in the towel on this one.

Here's this:

```
lsmod | grep "eee"
eeepc_laptop           14331  0 

```

And this:

```
modinfo eeepc_laptop
filename:       /lib/modules/2.6.32-32-generic/kernel/drivers/platform/x86/eeepc-laptop.ko
license:        GPL
description:    Eee PC Hotkey Driver
author:         Corentin Chary, Eric Cooper
srcversion:     C92594F44A2240F398CAA08
alias:          acpi*:ASUS010:*
depends:        
vermagic:       2.6.32-32-generic SMP mod_unload modversions 586 
parm:           hotplug_disabled:Disable hotplug for wireless device. If your laptop need that, please report to acpi4asus-user@lists.sourceforge.net. (bool)
```

That looks like it should just be controlling the hardware specific hot keys, so I'm wondering why it's messing with power management and wifi (beyond just turning it on and off)?

Still curious about power management, I tried this but it returns nothing:

```
lsmod | grep acpi
```

This might be of interest?

```
dmesg | grep "eee"
[   12.430924] eeepc_laptop: Eee PC Hotkey Driver
[   12.432323] eeepc_laptop: Hotkey init flags 0x41
[   12.432588] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[   12.441213] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[   12.441233] eeepc_laptop: Get control methods supported: 0x6101713
[   12.444732] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input7

```

Or this?

```
dmesg | grep "acpi"
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
```


Many, many thanks for your help so far!  What's the next step?

---

### Post by chili555 on 2011-07-05
> That looks like it should just be controlling the hardware specific hot keys, so I'm wondering why it's messing with power management and wifi (beyond just turning it on and off)?You are quite correct and I doubt we will find any joy with this particular module. My request was to try to find any other eee-specific modules that might have interesting parameters that we might manipulate. Not having an EEE myself (or is it EEEEEEE?), my only way to find out is to ask you to grep the modules and report. Admittedly, we're fishing at this point.

I haven't given up on power management. I am researching a package called laptop-mode-tools that has a number of parts that deal with wireless. [https://wiki.archlinux.org/index.php/Asus_Eee_PC_1000HE#laptop-mode-tools](https://wiki.archlinux.org/index.php/Asus_Eee_PC_1000HE#laptop-mode-tools)

For now, let's see if there are any clues here when the wireless dies out:```
sudo cat /var/log/syslog grep etwork | tail -n25
```

---

### Post by nosehat on 2011-07-05
Ha ha, it's rapidly turning into an "EEEEEEE" pc, you've got that right!

OK, fresh boot of the netbook with the power cord in.  It finds the wifi and autoconnects:

```
sudo cat /var/log/syslog grep etwork | tail -n25
[sudo] password for nosehat: 
cat: grep: No such file or directory
cat: etwork: No such file or directory
Jul  5 16:33:25 nosehat-laptop avahi-daemon[733]: New relevant interface wlan0.IPv4 for mDNS.
Jul  5 16:33:25 nosehat-laptop avahi-daemon[733]: Registering new address record for 192.168.1.105 on wlan0.IPv4.
Jul  5 16:33:26 nosehat-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jul  5 16:33:26 nosehat-laptop NetworkManager: <info>  Policy set 'Auto fishface' (wlan0) as default for routing and DNS.
Jul  5 16:33:26 nosehat-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jul  5 16:33:26 nosehat-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul  5 16:33:27 nosehat-laptop ntpdate[1412]: adjust time server 91.189.94.4 offset -0.335858 sec
Jul  5 16:33:51 nosehat-laptop kernel: [  109.350833] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
Jul  5 16:34:18 nosehat-laptop AptDaemon: INFO: Initializing daemon
Jul  5 16:34:31 nosehat-laptop kernel: [  149.353575] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
Jul  5 16:35:31 nosehat-laptop kernel: [  209.354616] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
Jul  5 16:36:51 nosehat-laptop kernel: [  289.357254] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
Jul  5 16:36:58 nosehat-laptop kernel: [  296.374157] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Jul  5 16:36:58 nosehat-laptop wpa_supplicant[875]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  5 16:36:58 nosehat-laptop wpa_supplicant[875]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  5 16:36:58 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jul  5 16:36:58 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul  5 16:37:03 nosehat-laptop wpa_supplicant[875]: Trying to associate with 98:fc:11:44:b1:8d (SSID='fishface' freq=2437 MHz)
Jul  5 16:37:03 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul  5 16:37:03 nosehat-laptop kernel: [  301.484788] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
Jul  5 16:37:03 nosehat-laptop kernel: [  301.485489] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Jul  5 16:37:03 nosehat-laptop wpa_supplicant[875]: Association request to the driver failed
Jul  5 16:37:03 nosehat-laptop sudo: pam_sm_authenticate: Called
Jul  5 16:37:03 nosehat-laptop sudo: pam_sm_authenticate: username = [nosehat]
Jul  5 16:37:03 nosehat-laptop sudo: pam_sm_authenticate: /home/nosehat is already mounted
```

I wait a few minutes, and it disconnects, starting its cycle of connection attempts.  Here's the result now:

```
$ sudo cat /var/log/syslog grep etwork | tail -n25
cat: grep: No such file or directory
cat: etwork: No such file or directory
Jul  5 16:39:03 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul  5 16:39:03 nosehat-laptop wpa_supplicant[875]: Association request to the driver failed
Jul  5 16:39:08 nosehat-laptop wpa_supplicant[875]: Authentication with 98:fc:11:44:b1:8d timed out.
Jul  5 16:39:08 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul  5 16:39:08 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul  5 16:39:13 nosehat-laptop kernel: [  431.583104] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
Jul  5 16:39:13 nosehat-laptop kernel: [  431.583745] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Jul  5 16:39:13 nosehat-laptop wpa_supplicant[875]: Trying to associate with 98:fc:11:44:b1:8d (SSID='fishface' freq=2437 MHz)
Jul  5 16:39:13 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul  5 16:39:13 nosehat-laptop wpa_supplicant[875]: Association request to the driver failed
Jul  5 16:39:18 nosehat-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jul  5 16:39:18 nosehat-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jul  5 16:39:18 nosehat-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jul  5 16:39:18 nosehat-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jul  5 16:39:18 nosehat-laptop wpa_supplicant[875]: Authentication with 00:00:00:00:00:00 timed out.
Jul  5 16:39:19 nosehat-laptop AptDaemon: INFO: Quiting due to inactivity
Jul  5 16:39:19 nosehat-laptop AptDaemon: INFO: Shutdown was requested
Jul  5 16:39:22 nosehat-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Jul  5 16:39:22 nosehat-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (fishface)
Jul  5 16:39:22 nosehat-laptop NetworkManager: <info>  Marking connection 'Auto fishface' invalid.
Jul  5 16:39:22 nosehat-laptop NetworkManager: <info>  Activation (wlan0) failed.
Jul  5 16:39:22 nosehat-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jul  5 16:39:22 nosehat-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jul  5 16:40:31 nosehat-laptop kernel: [  509.347483] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
Jul  5 16:42:31 nosehat-laptop kernel: [  629.349533] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
```

---

### Post by chili555 on 2011-07-05
> ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!Ah, ha!!! It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542439](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542439)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376577](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376577)

Please note:> Compiled the new 2.1.2.0 module using the link in the original post and the readme file instructions included in the archive. The error message no longer appears in the syslogs ***and the wireless card works flawlessly*** 
---
filename: /lib/modules/2.6.28-12-netbook-**[COLOR="Red"]eeepc[/COLOR]**/kernel/drivers/staging/Are you ready to compile? Your geek-o-meter certainly has pegged in the last few days!

Compiling from source sounds scary, but mortal users do it every day!

---

### Post by nosehat on 2011-07-05
I am definitely ready to compile from source, although I have not had that particular pleasure yet.  That's one of the things I really like about using Ubuntu, though.  Every frustration, even big ones, usually turns into a learning opportunity.

Funny though that this hardware's been out since 2009, the bug's been known since 2009, the "new" driver's been out since 2009, but it still hasn't made it into the standard distribution.

Where do I find the updated driver though?  The link in the original post of the bug report is dead:
> 
btw there is a new driver version 2.1.1.0 out since 3 weeks see here:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Also, how can I get the version number of my current driver?

Thanks again!

---

### Post by chili555 on 2011-07-05
> Also, how can I get the version number of my current driver?
```
modinfo rt2860sta
```> Where do I find the updated driver though? [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Download RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890) to your desktop. Hook up ye olde ethernet and get the kernel headers and build tools, like my saw and hammer:```
sudo apt-get install build-essential linux-headers-generic
```Now follow this tutorial with a couple of exceptions: [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)> You need to enter a name and an email and press accept to downloadNot needed, just press Accept.

Skip step 5 entirely. In step 6, change to:```
sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist
sudo cp /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2860sta.ko /lib/modules/`uname -r`/kernel/drivers/staging
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Skip step 9; we already handled that. You will probably encounter warnings but not errors. If you get stuck or don't understand something, stop and ask.

---

### Post by nosehat on 2011-07-05
Thanks!  I'll try that right away.

Seeking this driver myself, I stumbled upon this:

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

I notice that RutilT is in the repository.  Should I install that too?

---

### Post by chili555 on 2011-07-05
> **nosehat said:**
> Thanks!  I'll try that right away.

Seeking this driver myself, I stumbled upon this:

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

I notice that RutilT is in the repository.  Should I install that too?I doubt it. I think the newer driver will work without any other help. We can always do so later.

---

### Post by nosehat on 2011-07-05
On the revised step 6, should I replace "uname" with my user name?

I'm getting this:
```

nosehat@nosehat-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist
mv: cannot stat `/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko': No such file or directory
nosehat@nosehat-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$  
```

---

### Post by chili555 on 2011-07-05
> mv: cannot stat `/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko': No such file or directoryThat's also weird. Please do:```
sudo updatedb
locate rt2860sta.ko
```updatedb will take a few moments, please be patient. > should I replace "uname" with my user name?Nope; notice it has converted the command to use the **name** of your **r**unning kernel: 2.6.32-32-generic. uname -r is a quick way to specify your currently running kernel version without typing it all out. Hey, I'm old and lazy!

What we are trying to do is move the old, not working driver out of the way and save it, and then move the new one over in its place. 

It's late for old Chili. See you tomorrow.

---

### Post by nosehat on 2011-07-05
> uname -r is a quick way to specify your currently running kernel version without typing it all out

That's pretty useful.

Here it is:

```
$ locate rt2860sta.ko
/lib/modules/2.6.32-28-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
```

But "uname -r" returns "2.6.32-32-generic"

I notice that in /lib/modules I have extensive folders for both 32-28 and 32-32.  Could this be a problem?

---

### Post by nosehat on 2011-07-05
Looking over the instructions you linked here:   [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

and looking at your exceptions to the instructions, did you really mean for me to skip step 5 entirely?  Certainly I already have gcc thanks to installing build-essential linux-headers-generic.  But isn't part of the original step 5 where the new driver actually gets made?

---

### Post by nosehat on 2011-07-05
> **chili555 said:**
> It's late for old Chili. See you tomorrow.

Ah, cool.  I'll hold off on experimenting on my own until tomorrow!

Thanks so much for all your help so far!  You've been outrageously generous.  I definitely appreciate it!

---

### Post by chili555 on 2011-07-06
> and looking at your exceptions to the instructions, did you really mean for me to skip step 5 entirely? Certainly I already have gcc thanks to installing build-essential linux-headers-generic. But isn't part of the original step 5 where the new driver actually gets made?See there? See what happens when old Chili is a little too close to nap-time and is in a rush? Old Chili makes, as my old Performance Evaluation used to say, the occasional understandable error.

Sorry about that. Yes, Mr. Chili. we actually need to make and make install!!! Let's revise step #5 as follows:> **Step 5**
After successfully installing build tools and headers, please execute the following commands step by step in a terminal window.
```
cd Desktop/2010
```
Press Tab and the remainder will fill in automatically.
```
sudo su
make
make install
ifconfig wlan0 down
rmmod rt2860sta
exit
```I will be in the corner with my dunce cap until you post back.

---

### Post by nosehat on 2011-07-06
> the occasional understandable error.

Ha ha, not a problem at all,  It happens to me all the time. And thanks again for the help!

So the new instructions worked fine through "make" and "make install" -- bunch of warnings generated but no errors.

The next two didn't work, though, because apparently the original wireless driver is now gone?  It didn't load at all when I turned on the netbook this morning:
```

# ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
# rmmod rt2860sta
ERROR: Module rt2860sta does not exist in /proc/modules
```

Presumably something I did yesterday removed the original rt2860sta?  Or it's a fluke?

---

### Post by chili555 on 2011-07-06
When you do 'sudo make install' it installs it (not quite correctly, I might add) in /lib/modules/`uname -r`/kernel/drivers/net/wireless. Then the 'sudo cp' step copies that driver to where the system looks for it, /lib/modules/`uname -r`/kernel/drivers/staging/rt2860.

I think I see a copy and paste error. The sudo cp is supposed to be:

```
sudo cp /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2860sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/[COLOR="Red"]rt2860[/COLOR]
```Try it again and then do:```
sudo modprobe rt2860sta
modinfo rt2860sta
iwconfig
```Is the version now 2.4.0.0? Is it now working?

---

### Post by nosehat on 2011-07-06
OK, this looks promising.  I did the revised copy, now:

```
~$ sudo modprobe rt2860sta
~$ modinfo rt2860sta
filename:       /lib/modules/2.6.32-32-generic/kernel/drivers/net/wireless/rt2860sta.ko
license:        GPL
version:        2.4.0.0
srcversion:     13D46228144E2B4107ABD5C
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-32-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)
nosehat@nosehat-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```So what next?

I tried:

```
$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```So I'm not quite there yet?

Does it need a reboot at this point?

---

### Post by chili555 on 2011-07-06
> $ sudo ifconfig [COLOR="Red"]wlan0[/COLOR] up
wlan0: ERROR while getting interface flags: No such deviceThat's because your interface is now ra0. Please reboot and run:```
dmesg | grep -e ra0 -e rt2
lsmod | grep rt2
```We're close!

---

### Post by nosehat on 2011-07-06
Rebooted.

```
~$ dmesg | grep -e ra0 -e rt2
[   12.649790] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.649848] rt2860 0000:01:00.0: setting latency timer to 64
~$ lsmod | grep rt2
rt2860sta             791605  0
```

I still have no wireless, though.  Left clicking or right clicking on the little networking icon gives me no option to enable wireless yet.

---

### Post by chili555 on 2011-07-06
Can you confirm that, before you did make and make install, you did this from the link?> Step 3
Code:

gedit ./os/linux/config.mk

Use the find command to locate HAS_WPA_SUPPLICANT and make sure it is set to y for yes. It should look like this when finished:
HAS_WPA_SUPPLICANT=y


Use the find command to locate HAS_NATIVE_WPA_SUPPLICANT_SUPPORT and make sure it is set to y for yes. It should look like this when finished:
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y


Close and *save* this file.Please check. Also, is the needed .dat file in place?```
ls /etc/Wireless/RT2860STA
```Thanks.

---

### Post by nosehat on 2011-07-06
> Use the find command to locate HAS_WPA_SUPPLICANT and make sure it is set to y for yes. It should look like this when finished:
HAS_WPA_SUPPLICANT=y


Use the find command to locate HAS_NATIVE_WPA_SUPPLICANT_SUPPORT and  make sure it is set to y for yes. It should look like this when  finished:
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Ahh, I must have been tired too!  I did change the first of those, but I neglected to change the second!  So, I've changed it now.  

And yes, the needed .dat file is in place.

I will re-make the driver and attempt to copy it into the right folder and reboot.

---

### Post by nosehat on 2011-07-06
<tentative cheer>

I think it might be working.  I've successfully re-made, installed, and moved the driver.  I also added an entry for rt2860sta to /etc/modules

I've booted a couple of times, and the wifi has connected each time.

Here's the new result of the two commands you asked for, by the way:

```
~$ dmesg | grep -e ra0 -e rt2
[   12.937623] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.937683] rt2860 0000:01:00.0: setting latency timer to 64
[   14.018596] <==== rt28xx_init, Status=0
[   24.888027] ra0: no IPv6 routers present
nosehat@nosehat-laptop:~$ lsmod | grep rt2
rt2860sta             791441  1 
```

Is there anything else I need to do? 

I want to test this with a variety of battery conditions, both at home and work and on a public network, just to make sure everything is flawless.  I'll mark the thread [Solved] after a day or two of testing.

Thanks again for all your help!  I definitely owe you dinner if I'm ever in South Carolina!

---

### Post by chili555 on 2011-07-06
> the wifi has connected each time.You just repaid me all I could ever want! I'm glad it's working. If you feel you've tested enough to be confident, please use Thread Tools at the top and Mark Solved.

NB: When a later kernel version is installed, you'll need to rebuild the driver:```
cd Desktop/2010etc.
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt2860sta
exit
```

---

### Post by ahagele on 2011-07-13
Hi there,
I read through all this because I have exactly the same problem with my Eee. I'm just a bit reluctant to go through the whole compile from source action.
So a couple questions:
 - what's the quickest way to find out if my driver is also affected, apart from the obvious effect of dropping the wireless link (I've just installed 11.04)?

 - is there a way to get the driver pre-compiled and ready to run?

Thanks for your help

Andreas

---

### Post by chili555 on 2011-07-13
> - what's the quickest way to find out if my driver is also affected, apart from the obvious effect of dropping the wireless link (I've just installed 11.04)?Your wireless can drop for other reasons aside from the driver. You can have interference on the same channel as you router; most routers are set to channel 6 by default. You might try 1 or 11. Your router might have a signal strength setting; is it as high as possible? Please see attached.

You might have conflicting drivers loaded. Please open a terminal and run and post:```
lsmod | grep rt2
```Finally, unless someone has the exact same kernel as you, the exact same gcc version, etc., just emailing the pre-compiled version won't work. Moreover, why ask someone else to do the hard work for you? Actually, when you get down to it, it's not very hard. 

I was actually surprised that the built-in version didn't work as well as the compiled from source version. I learn something surprising every day.

---

### Post by ahagele on 2011-07-13
Hi Chili555,

Too true that it could be something else. I have put it to rest for now. The netbook is owned by a friend and so far it seems to work fine on his wireless network.

However the symtoms just looked the same as described here. 
I also have these little freezes, where the desktop becomes unusable for about 10-15secs and then goes just normal again. And I saw that mentioned in these bug reports you pointed to.
I don't think it's a router/power issue, as the win XP on this Eeee works fine without a hitch.
I might be back here if it fails on his network.

Will that new source make it in the standard Ubuntu release at some time?

Andreas

---

### Post by chili555 on 2011-07-13
> Will that new source make it in the standard Ubuntu release at some time?Yes. 'Some time' is, of course, a relative term.

---

### Post by BrandonSk on 2013-01-05
Dear all / Chilli :)

I followed this excellent walkthrough as I was experiencing the same symptoms. The installation seemed to be done ok, the new driver is in use and my wifi was working. So I thought it was done.

But unfortunately my wifi still refuses to work after some minutes. My system did download some updates, so I even tried the final steps you've mention to re-compile and re-insert (sorry if I use wrong terminology) the driver/module into the kernel.

All I am getting is just few minutes of wifi and then I am stuck with ethernet.

Any help? Please let me know output of which commands should I post here in order to provide necessary information.

Thanks.
Cheers,
Brandon.

---

### Post by chili555 on 2013-01-05
> **BrandonSk said:**
> Dear all / Chilli :)

I followed this excellent walkthrough as I was experiencing the same symptoms. The installation seemed to be done ok, the new driver is in use and my wifi was working. So I thought it was done.

But unfortunately my wifi still refuses to work after some minutes. My system did download some updates, so I even tried the final steps you've mention to re-compile and re-insert (sorry if I use wrong terminology) the driver/module into the kernel.

All I am getting is just few minutes of wifi and then I am stuck with ethernet.

Any help? Please let me know output of which commands should I post here in order to provide necessary information.

Thanks.
Cheers,
Brandon.As this thread is quite old, please start your own new thread and include:```
lspci -nn | grep 0280
```

---

### Post by BrandonSk on 2013-01-05
Thank you for a quick response.
Here is the new thread

[http://ubuntuforums.org/showthread.php?p=12440420#post12440420](http://ubuntuforums.org/showthread.php?p=12440420#post12440420)

and I am closing my discussion here.
Cheers,
Brandon.

---

