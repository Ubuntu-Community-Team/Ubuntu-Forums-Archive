---
title: "wireless problem"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by browndusk on 2011-10-15
hello!
  I have ubuntu 11.10 my wireless show all the available network but when I click to connect to the network it just cannot connect(the wireless icon at the top right hand corner just blinks and blinks but nothing happens) I get the same message over and over again saying authentication required by wireless network. Its not that I don't know the password but it doesn't work and when I switch back to windows7 everything seems to work fine. 
  I am fairly new user of Ubuntu can anybody help me with this.  
my pc = del presario CQ62
wirless adapter =  Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

P.s: please let me know if any additional information needed

---

### Post by dude_4297 on 2011-10-15
try going to settings then to the networking and then find your router and scroll throught the settigns at the top

---

### Post by atconley on 2011-10-15
I have (what seems to me to be) exactly the same problem, but with the **RTL8192CU**.  I had hoped that 11.10 would fix it but no cigar.

**Browndusk's** description of the problematic behaviour is spot on.  Networks can be seen (that is, their SSID's come up) but when you try to connect, after trying to connect for 20 seconds or so, it asks for a new password, and this repeats *ad infinitum*.  I turned off wireless security (WPA) but the same thing happened (minus asking for the password).  Also, no joy with NDISwrapper or trying to install Realtek's drivers.

I have tried to follow **Dude_4297's** advice but I'm not sure I understand it properly.

Help would be sincerely appreciated.  Of course, I am very happy to provide more information; please just tell me what commands to give the terminal and I will provide the results.

Cheers ;)

---

### Post by atconley on 2011-10-16
Some more information:

**lsmod** returns (sniped):
```
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
```**lsusb** returns (sniped):
```
Bus 001 Device 007: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
```Note that the code here is 'RTL81_88_CU_S_' rather than 'RTL81_92_CU' as it is everywhere else.  Not sure whether that is relevant.

**iwconfig** returns:
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
```**nmtool** returns:
```
- Device: wlan0  [blah] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connecting (configuring)
  Default:           no
  HW Address:        [snip]

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    blah:            Infra, [snip], Freq 2412 MHz, Rate 54 Mb/s, Strength 89
```

---

### Post by gps123 on 2011-10-16
Subscribed...I'm having the exact same problem as atconley, and exactly the same code returns.:popcorn:

---

### Post by meajohan on 2011-10-16
Same here to, but i have the RTL8188CUS, had to get back to 11.04 :( and waiting for a solution. when i check the realtek driver page it says that the driver only supports Linux driver for Kernel 2.6.38(and earlier).. its 3 something in ubunti 11.10.

---

### Post by nbrebol on 2011-10-16
same here, there are some other threads with wireless issues upon upgrade to 11.10, but those seem to be specific to people with Broadcom wireless cards. this problem seems to be specific to the Realtec one. perhaps you should update the title to make it more specific to all of out setup? also, ive been searching through the forums and will post if i find a solution

---

### Post by browndusk on 2011-10-16
more or less my terminal gives the same output as **atconley **any help is really appreciated :confused:

---

### Post by gps123 on 2011-10-16
> **meajohan said:**
> Same here to, but i have the RTL8188CUS, had to get back to 11.04 :( and waiting for a solution. when i check the realtek driver page it says that the driver only supports Linux driver for Kernel 2.6.38(and earlier).. its 3 something in ubunti 11.10.

I saw this too.  Wouldn't it make sense that the kernel was backwards compatible?  Also, I think I read in Ocelot development notes that the RTL8192CU (specifically) was supported.

---

### Post by jonathan0 on 2011-10-16
Have RTL8192cu to and have the same problem. Can't install realtek driver ether.

---

### Post by browndusk on 2011-10-17
Hi Jonathan!    have you tried installing ndiswrapper(windows wireless driver) if you don't. you can easily get that app from software center and try downloading the windows version of you driver and install your downloaded windows wireless driver via ndiswrapper.If you can't find windows driver for your wireless let me know, I have once stumbled upon that site but can't remember at the moment. Thats all i know if you haven't been able to install the driver.

---

### Post by gps123 on 2011-10-17
There are Linux drivers on the Realtek site, so he shouldn't need to use ndiswrapper.  Though since none of us can get this working, it wouldn't hurt to try the Windows driver as well.

---

### Post by wildmanne39 on 2011-10-17
Hi, alright let&#347; see if we can get this working.

1. Does everyone in this thread have this same usb adapter?
```
Bus 001 Device 007: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
```

2. If you installed ndiswrapper please remove it with the following commands, no other driver will work as long as it is installed. 
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Run those commands one line at a time, and you will not see any output from the commands unless there were errors.

Now have everyone tried:
```
sudo modprobe rtl8192cu
```
If that does not bring it to life I will need to see the output from the following commands please:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan0 | tail -n25
```
 post it here by clicking on new reply and click # and paste the information between the brackets.

When I ask for this information I need to see all the output from each command do not edit the information.
Thank you

---

### Post by jonathan0 on 2011-10-17
Here is the output I got.```
root@jonathan-AOA110:/home/jonathan# lsmod
Module                  Size  Used by
arc4                   12473  2 
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
sparse_keymap          13658  0 
bnep                   17923  2 
rfcomm                 38408  0 
acerhdf                14140  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254125  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
serio_raw              12990  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
i915                  505108  3 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  0 
jmb38x_ms              17406  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               15857  1 jmb38x_ms
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
r8169                  43104  0 
root@jonathan-AOA110:/home/jonathan# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
root@jonathan-AOA110:/home/jonathan# modprobe rtl8192cu
root@jonathan-AOA110:/home/jonathan# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux jonathan-AOA110 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
root@jonathan-AOA110:/home/jonathan# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:be:2c:42
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.32 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:71010000-71010fff memory:71000000-7100ffff memory:71020000-7103ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:1f:1f:dd:57:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
root@jonathan-AOA110:/home/jonathan# nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1E:68:BE:2C:42

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.32
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        00:1F:1F:DD:57:E0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HotFishingN11:   Infra, 30:46:9A:67:66:9A, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA2
    go4look:         Infra, 00:22:3F:23:A7:EC, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WEP


root@jonathan-AOA110:/home/jonathan# lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:015b]
    Kernel driver in use: r8169
root@jonathan-AOA110:/home/jonathan# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@jonathan-AOA110:/home/jonathan# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@jonathan-AOA110:/home/jonathan# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:3F:23:A7:EC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"go4look"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000191683de183
                    Extra: Last beacon: 368ms ago
                    IE: Unknown: 0007676F346C6F6F6B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 30:46:9A:67:66:9A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"HotFishingN11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002586aa4193
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000D486F7446697368696E674E3131
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

root@jonathan-AOA110:/home/jonathan# iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
root@jonathan-AOA110:/home/jonathan# cat /var/log/syslog | grep -e rtl -e firmware -e wlan0 | tail -n25
Oct 17 16:22:53 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 17 16:22:53 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): supplicant interface state: ready -> inactive
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0) starting connection 'HotFishingN11'
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0/wireless): connection 'HotFishingN11' has security, and secrets exist.  No new secrets needed.
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 17 16:22:54 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): supplicant interface state: inactive -> scanning
Oct 17 16:22:55 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 17 16:22:55 jonathan-AOA110 kernel: [   60.886952] wlan0: direct probe to 30:46:9a:67:66:9a (try 1/3)
Oct 17 16:22:55 jonathan-AOA110 kernel: [   61.084123] wlan0: direct probe to 30:46:9a:67:66:9a (try 2/3)
Oct 17 16:22:56 jonathan-AOA110 kernel: [   61.284160] wlan0: direct probe to 30:46:9a:67:66:9a (try 3/3)
Oct 17 16:22:56 jonathan-AOA110 kernel: [   61.484094] wlan0: direct probe to 30:46:9a:67:66:9a timed out
Oct 17 16:23:01 jonathan-AOA110 kernel: [   67.262566] wlan0: direct probe to 30:46:9a:67:66:9a (try 1/3)
Oct 17 16:23:02 jonathan-AOA110 kernel: [   67.460105] wlan0: direct probe to 30:46:9a:67:66:9a (try 2/3)
Oct 17 16:23:02 jonathan-AOA110 kernel: [   67.660106] wlan0: direct probe to 30:46:9a:67:66:9a (try 3/3)
Oct 17 16:23:02 jonathan-AOA110 kernel: [   67.860093] wlan0: direct probe to 30:46:9a:67:66:9a timed out
Oct 17 16:23:07 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): device state change: config -> disconnected (reason 'user-requested') [50 30 39]
Oct 17 16:23:07 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Oct 17 16:23:07 jonathan-AOA110 NetworkManager[461]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
root@jonathan-AOA110:/home/jonathan#

```

---

### Post by jonathan0 on 2011-10-17
Thank you. The ndiswrapper works but as soon as you close the window it stops working. Maybe I did not install it right.

---

### Post by wildmanne39 on 2011-10-17
Hi jonathan0, which network are you trying to connect too?
Thank you

---

### Post by gps123 on 2011-10-17
Here are my outputs.  Thank you in advance.  I don't know how to get rid of the smileys, so everywhere there is a smiley should be "colon o."

```
cat /etc/lsb-release; uname -a
```desktop@desktop-Dell-DXC051:~$ cat /etc/lsb-release;uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux desktop-Dell-DXC051 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```
sudo lshw -C network
```desktop@desktop-Dell-DXC051:~$ sudo lshw -c network
[sudo] password for desktop: 
  *-network               
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:b6:02:e6
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:efbfb000-efbfbfff ioport:ccc0(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@5:1
       logical name: wlan0
       serial: 00:a1:b0:83:35:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```
nm-tool
```desktop@desktop-Dell-DXC051:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:B6:02:E6

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [internet] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:A1:B0:83:35:3F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    internet:        Infra, 00:18:F8:E4:25:19, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WEP
    IAN!DSL:         Infra, A0:21:B7:5F:33:F8, Freq 2422 MHz, Rate 54 Mb/s, Strength 92 WEP
    2WIRE560:        Infra, 00:26:50:04:D4:41, Freq 2422 MHz, Rate 54 Mb/s, Strength 95 WPA

```
lspci -nnk | grep -iA2 net
```desktop@desktop-Dell-DXC051:~$ lspci -nnk | grep -iA2 net
03:08.0 Ethernet controller [0200]: Intel Corporation N10/ICH 7 Family LAN Controller [8086:27dc] (rev 01)
    Subsystem: Dell Device [1028:01ac]
    Kernel driver in use: e100

```
lsusb
```desktop@desktop-Dell-DXC051:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1516:1213 CompUSA 
Bus 005 Device 006: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business

```
iwconfig
```desktop@desktop-Dell-DXC051:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```
rfkill list all
```desktop@desktop-Dell-DXC051:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
sudo iwlist scan
```desktop@desktop-Dell-DXC051:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```
iwlist chan
```desktop@desktop-Dell-DXC051:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz

```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan0 | tail -n25
```desktop@desktop-Dell-DXC051:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan0 | tail -n25
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0/wireless): connection 'internet' has security, and secrets exist.  No new secrets needed.
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 17 20:11:04 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): supplicant interface state: inactive -> scanning
Oct 17 20:12:03 desktop-Dell-DXC051 NetworkManager[726]: <warn> Activation (wlan0/wireless): association took too long.
Oct 17 20:12:03 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct 17 20:12:03 desktop-Dell-DXC051 NetworkManager[726]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct 17 20:12:04 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): supplicant interface state: scanning -> inactive
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0/wireless): connection 'internet' has security, and secrets exist.  No new secrets needed.
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 17 20:12:07 desktop-Dell-DXC051 NetworkManager[726]: <info> (wlan0): supplicant interface state: inactive -> scanning
desktop@desktop-Dell-DXC051:~$

---

### Post by wildmanne39 on 2011-10-17
Hi gps123, make sure your ipv6 is set to ignore in the network icon in the top right corner by clicking on edit connections then go into your wireless connection.
Thank you

---

### Post by wildmanne39 on 2011-10-17
Hi gps123, if that does not help, please install wicd then completely remove network manager and its config files but only after you install wicd, then restart your computer.
Thank you

---

### Post by gps123 on 2011-10-18
> **wildmanne39 said:**
> Hi gps123, make sure your ipv6 is set to ignore in the network icon in the top right corner by clicking on edit connections then go into your wireless connection.
Thank you

This didn't work.  I can't easily install wicd, as I don't have a wired connection.  I also can't figure out how to install it from USB...

I'll try to find a really long cat 6 cable and post the outcome after wicd is installed.

---

### Post by wildmanne39 on 2011-10-18
Hi, okay please understand this is a new release and we are going to have to try several things possibly to get it to work.
Thank you

---

### Post by nbrebol on 2011-10-18
here is my output:

```
nbrebol@kcinlober:/$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux kcinlober 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux
nbrebol@kcinlober:/$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 01
       serial: c8:0a:a9:a5:e7:62
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb v2.07 ip=192.168.0.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 memory:f8a00000-f8a0ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.2
       logical name: wlan2
       serial: 00:21:2f:38:bf:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.0.0-12-generic-pae firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bgn
nbrebol@kcinlober:/$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        C8:0A:A9:A5:E7:62

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             205.171.3.25


- Device: wlan2 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        00:21:2F:38:BF:AE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


nbrebol@kcinlober:/$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Lenovo Device [17aa:38cf]
	Kernel driver in use: tg3
nbrebol@kcinlober:/$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 004: ID 5986:0190 Acer, Inc 
nbrebol@kcinlober:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
nbrebol@kcinlober:/$ rfkill list all
1: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no
nbrebol@kcinlober:/$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan2     No scan results

nbrebol@kcinlober:/$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan2     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.412 GHz (Channel 1)

nbrebol@kcinlober:/$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan0 | tail -n25
Oct 17 23:02:45 kcinlober kernel: [69932.416706] rtl8192cu: MAC address: 00:21:2f:38:bf:ae
Oct 17 23:02:45 kcinlober kernel: [69932.416715] rtl8192cu: Board Type 0
Oct 17 23:02:45 kcinlober kernel: [69932.469230] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
Oct 17 23:02:45 kcinlober kernel: [69932.469641] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
Oct 17 23:02:45 kcinlober NetworkManager[977]: <info> (wlan2): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 13)
Oct 17 23:02:45 kcinlober kernel: [69932.758863] rtl8192cu: MAC auto ON okay!
Oct 17 23:02:45 kcinlober kernel: [69932.792225] rtl8192cu: Tx queue select: 0x05
Oct 17 23:02:45 kcinlober kernel: [69932.793344] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
Oct 17 23:02:46 kcinlober kernel: [69933.400158] rtl8192cu: MAC auto ON okay!
Oct 17 23:02:46 kcinlober kernel: [69933.435457] rtl8192cu: Tx queue select: 0x05
Oct 17 23:02:46 kcinlober kernel: [69933.436341] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
nbrebol@kcinlober:/$ 

```

---

### Post by meajohan on 2011-10-18
I got this from the Realtek support:

Dear Sir/Madam
 
Thanks for your e-mail.
We have plan to support Kernek 3.0 in next release.
Best Regards,
Realtek Technical Support Dept.
 
 
&#23492;&#20214;&#32773;: Johan Gustafsson [meajohan@gmail.com]
&#23492;&#20214;&#26085;&#26399;: 2011&#24180;10&#26376;16&#26085; &#19978;&#21320; 04:19
&#25910;&#20214;&#32773;: wlanfae
&#20027;&#26088;: Realtek wlan usb RTL8188CUS Linux

---

### Post by wildmanne39 on 2011-10-18
Hi nbrebol, first you have your wireless set as ad-hoc it needs to be changed to infrastructure.

---

### Post by jonathan0 on 2011-10-18
Have two networks, I have tried both. Thank you.

---

### Post by jonathan0 on 2011-10-18
Install wicd then completely remove network manager, but is not connecting, and both of them say the password is wrong and I have vairfied its correct. Think you.:D

---

### Post by wildmanne39 on 2011-10-18
Hi jonathan0, please install wicd then completely remove network manager and its config files but only after you install wicd, then restart your computer.

If nothing else works we can downgrade the kernel, then use the driver that worked with it.
Thank you

---

### Post by jonathan0 on 2011-10-18
Install wicd but keep getting long time on Validating authentication in thin Bad Password. Disable WEP and WPA on wireless router, but get long time on obtaining IP address thin error out.

---

### Post by nbrebol on 2011-10-18
> **wildmanne39 said:**
> Hi nbrebol, first you have your wireless set as ad-hoc it needs to be changed to infrastructure.

ok, i changed that but still no success. i used to be able to see available networks, but now i can't even do that anymore. i have been trying to "connect to hidden network" and entering my wireless network name and passphrase but it is still getting stuck on trying to connect (just takes forever, never actually connects and keeps asking for the network passphrase)

thanks for all of your help so far

---

### Post by ecm5291 on 2011-10-18
I have the same wireless problem as all the others. I am using Ubuntu 11.10 (the latest version) & now my wireless connection does not work. Hence, I am using a wired connection which works just fine.

By the way, I am a new user so kindly be specific in your answers.  

Thank you.

Edm5291

---

### Post by wildmanne39 on 2011-10-18
Hi, I asked a friend to help us that has a lot more experience then I do, it is difficult because there are so many any this thread and not all of your log errors are the same.
Thank you

---

### Post by praseodym on 2011-10-18
Hi friends,

the Realtek drivers from their HP cannot be build so far with kernel 3.

So I recommend installing 11.04 in a Dualbootsystem or installing a mainline kernel version 2.6.38-8:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/)

or 2.6.39-4:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/)

Download _all three_ possible packages for 32 or 64bit, save them in Downloads and install it and the needed packages to compile via cable:

```
sudo dpkg -i ~/Downloads/linux-*.deb
sudo apt-get install build-essential dkms startupmanager
```

The tool startupmanager can be used to set up kernel 2.6.38 or 2.6.39, respectively, as default boot kernel. Install the driver(s) with dkms:

**RTL8188CUS**
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
```

**Driver r8712u _replaced_ by 8712u:**
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_dkms.tar.gz
sudo tar xvf rtl8712u-2.6.6.0.2_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8712u -v 2.6.6.0.2
sudo dkms build -m rtl8712u -v 2.6.6.0.2
sudo dkms install -m rtl8712u -v 2.6.6.0.2 
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

Puuuhh. For other questions, please show seperately:

```
lspci -nnk | grep -iA2 net
uname -a
lsusb
lsmod
iwconfig
```

P.S.: I recommend copy/paste in your terminal (CTRL+ALT+T) ;-)

---

### Post by wildmanne39 on 2011-10-18
Thank you praseodym, I was leaving reverting to a previous kernel as the last option, but I was not sure if that was our only option at this point but I had suspected it might be.

I appreciate your help and great instructions.

---

### Post by jonathan0 on 2011-10-18
compile driver but getting this error.```
Compile make driver ok!!
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.0.0-12-generic

```

---

### Post by jonathan0 on 2011-10-18
I have modified the realtek driver but I am geting errors, here is the code.
 osdep_service.h ```
#include <linux/smp_lock.h>
``` to ```
#include <linux/smp.h>
``` and rtw_io.h ```
#include <linux/smp_lock.h>
``` to ```
#include <linux/smp.h>
``` I hop this can help.

---

### Post by wildmanne39 on 2011-10-18
Hi jonathan0, praseodym instructions are to downgrade to the 11.04 kernel then install the driver using the code he gave, you are not suppose to modify the driver.
Thank you

---

### Post by browndusk on 2011-10-19
hi! 
I have tried installing wicd  but still no luck. every time I type in my password it replies bad password.

@prasedym can you please specify which are the three files that I am  supposed to download from this link  [http://kernel.ubuntu.com/~kernel-ppa....39.4-oneiric/   [COLOR=Black]_a_ctually  there are more than three files so I am  bit confus_ed_[/COLOR]]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/")
thanks

---

### Post by praseodym on 2011-10-19
For 32bit:

both i386.deb and the all.deb

For 64bit:

both amd64.deb and the all.deb

---

### Post by jonathan0 on 2011-10-19
I have taken the module/driver from the realtek website, unarchived it, entered the driver folder (archive). 

 Edited rtw_io.h and osdep_service.h  

Changed osdep_service.h
line 49 <linux/smp_lock.h>
to       <linux/smp.h>

Changed file rtw_io.h
line 36 <linux/smp_lock.h>
to       <linux/smp.h>

Disconnected all the network cables, unplugged the realtek dongle, rebooted, then ran sudo su then when to the realtek directory and ran ./install.sh

It then successfully compiled the driver 8192cu.ko then discovered you can plugin the dongle and your network works but when you reboot you lose network access.  

I have figured out how to install the 8192cu.ko so it will persist after reboot. FIrst you have to unplug the adapter and restart with NO network connections active so you can remove drivers.

rm 8192cu.ko in path /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless 

Then:
cd rtlwifi
cd rtl8192
ls
rm rtl8192cu.ko

copy rtl8192_8188CU_linux_v3.1.2590.20110922 8192cu.ko (directory where the driver was compiled)

to the rtl8192 directory inside of the the rtlwifi directory
rename it to rtl8192cu.ko

copy the file to /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless

So to wrap it up, delete the 8192cu.ko driver from the locations above, compile new driver replacing the lines above, then place a copy in each location above stated.

Plug in dongle, setup wireless.  Should be good to go.

---

### Post by lils001 on 2011-10-19
I am experiencing the same problems. I am a completely new to this and am confused as to which instructions I should carry out - editing within 11.10 or installing 11.04. I have additional problems however. After wireless problems in 11.10 and seeing that I didn't have problems with my onboard wireless in 11.04 (run from USB installer) I decided to revert to 11.04, only there's a bug that causes the installation to crash on my machine - Gigabyte E1500 (yes, it's a piece of cheap crap but it was a gift). I have informed of the bug @ launchpad.net as instructed but there's no solution just yet.

---

### Post by browndusk on 2011-10-20
hi!
@praseodym  
Again my wireless adapter is Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless. Does the same command will be applicable in my case as well ?? 
thank you in advance

---

### Post by praseodym on 2011-10-20
Hi browndusk,

just to be sure, post:

```
uname -a
lsusb
lsmod
```

To lils001:

Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by lils001 on 2011-10-20
Thanks for your help praseodym :)
Here's my output as requested:

```
lilly@lilly-E1500:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199]
    Kernel driver in use: r8180
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Elitegroup Computer Systems Device [1019:90b5]
    Kernel driver in use: r8169
lilly@lilly-E1500:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 008 Device 002: ID 17ef:6009 Lenovo ThinkPad Keyboard with TrackPoint
lilly@lilly-E1500:~$ lsmod
Module                  Size  Used by
michael_mic            12540  12 
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  8 
sparse_keymap          13658  0 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_seq_midi           13132  0 
cfg80211              172392  2 rtlwifi,mac80211
psmouse                73673  0 
snd_rawmidi            25241  1 snd_seq_midi
serio_raw              12990  0 
joydev                 17393  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  2 
wmi                    18744  0 
r8187se               157152  0 
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
eeprom_93cx6           12653  1 r8187se
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  4 
libahci                25727  1 ahci
r8169                  43104  0 
lilly@lilly-E1500:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  link  ESSID:"BigPond3EF0"  
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:1E:8C:03:63:37   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-32 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lilly@lilly-E1500:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```nb: I currently have no wireless connection set up for the USB wireless dongle since it isn't connecting and prevents the on-board wireless from remaining connected. The signal strength for the on-board wireless is poor and drops out or doesn't connect (it doesn't connect at all in Windows (Vista)) which is why I got the USB wireless dongle (works brilliantly in Windows). I see that the USB wireless dongle detects my network and that the signal strength is stronger than for the on-board wireless ... if only I could use it.

---

### Post by praseodym on 2011-10-21
Try the dongle alone:

```
sudo modprobe -rfv r8187se rtl8192cu
sudo modprobe -v rtl8192cu
sudo depmod -a
```
Replug the stick and try to connect.

---

### Post by browndusk on 2011-10-21
hi! 
 okay here is the the outputs
 ```
uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

```
 lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
P.S : I have already installed the kernel file that you said to download and install 
Thank you 
```
 lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
psmouse                73882  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
rtl8192se              99931  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rtlwifi               110972  1 rtl8192se
i915                  566711  3 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  2 rtl8192se,rtlwifi
snd_timer              29991  2 snd_pcm,snd_seq
cfg80211              199587  2 rtlwifi,mac80211
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
wmi                    19256  1 hp_wmi
soundcore              12680  1 snd
drm                   236330  4 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
ahci                   26002  1 
libahci                26861  1 ahci
r8169                  52788  0 

```

---

### Post by praseodym on 2011-10-21
@ browndusk:

The stick is not recognized (anymore) with "lsmod". Was it (re-)plugged in? Did you try the kernel 2.6.38-8?

---

### Post by yuwash on 2011-10-21
Although lsmod also shows me
> Module                  Size  Used by
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu, the problem seems to have lied on the acer-wmi driver. So, the suggestion at [http://fossplanet.com/f10/%5Bbug-774036%5D-%5Bnew%5D-module-acer-wmi-should-blacklisted-lenovoideapad-s-12-a-146581/#post453089]("http://fossplanet.com/f10/%5Bbug-774036%5D-%5Bnew%5D-module-acer-wmi-should-blacklisted-lenovoideapad-s-12-a-146581/#post453089") as following worked for me:
```
sudo rmmod acer-wmi
```Afterwards, noting the index of acer-wireless in ```
rfkill list
``` and then ```
rfkill unblock <that index>
``` has finally made my lenovo S205 successfully turn on wireless!

edit: you should actually rfkill unblock <index> BEFORE rmmod acer-wmi, because, otherwise, rfkill list doesn't show acer-wireless anymore.

---

### Post by lils001 on 2011-10-21
> **praseodym said:**
> Try the dongle alone:

```
sudo modprobe -rfv r8187se rtl8192cu
sudo modprobe -v rtl8192cu
sudo depmod -a
```Replug the stick and try to connect.

Done. And now the dongle is working and staying connected thanks :).
Now how do I know if it's working as it should and which wireless connection is my better option in linux?

btw, 
```
lilly@lilly-E1500:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:"BigPond3EF0"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1E:8C:03:63:37   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15250   Missed beacon:0
```Thanks so much for your help praseodym :)

---

### Post by praseodym on 2011-10-21
Add an UDEV-Rule:

```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules
```

Insert:

```
# UDEV-rule for wireless sticks
# unloads/loads driver for internal card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-Stick plugged in, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf r8187se"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick plugged out, Onboard-card activated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe r8187se"

LABEL="rules_end"
```
Save, close, and reload UDEV:

```
sudo service udev reload
```

---

### Post by browndusk on 2011-10-22
@praseodym
I have a built in wireless in my laptop I am not using the usb one. And I have installed all the kernel file which you have provided via link (I am not sure if it was good thing to do) so what should I do ???

---

### Post by atconley on 2011-10-22
Dear Wildmanne39,

I have the:
```
Bus 001 Device 007: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
```The results from the commands that you asked us to run are:
```
**andrew@bob:~$ cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux bob 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
**andrew@bob:~$ sudo lshw -C network**
[sudo] password for andrew: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: *[snip]*
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.1.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:d800(size=256) memory:f9fff000-f9ffffff memory:f9fc0000-f9fdffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: *[snip]*
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
**andrew@bob:~$ nm-tool**

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        *[snip]*

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.1.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.1.1.1

    DNS:             10.1.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        *[snip]*

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    blah:            Infra, *[snip]*, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    gargi patel:     Infra, *[snip]*, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA


**andrew@bob:~$ lspci -nnk | grep -iA2 net**
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:369c]
    Kernel driver in use: r8169
**andrew@bob:~$ lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
**andrew@bob:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
**andrew@bob:~$ rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
**andrew@bob:~$ sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: *[snip]*
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"gargi patel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b9427bb1d8
                    Extra: Last beacon: 124ms ago
                    IE: Unknown: 000B676172676920706174656C
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
          Cell 02 - Address: *[snip]*
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"blah"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f1edbe183
                    Extra: Last beacon: 660ms ago
                    IE: Unknown: 0004626C6168
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

**andrew@bob:~$ iwlist chan**
lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
**andrew@bob:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan0 | tail -n25**
Oct 22 22:42:15 bob NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 22 22:42:15 bob NetworkManager[664]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 22 22:42:15 bob NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 22 22:42:15 bob NetworkManager[664]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 22 22:42:15 bob NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 22 22:42:15 bob NetworkManager[664]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 22 22:42:15 bob NetworkManager[664]: <info> Activation (wlan0/wireless): connection 'Home' has security, and secrets exist.  No new secrets needed.
Oct 22 22:42:15 bob NetworkManager[664]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 22 22:42:15 bob NetworkManager[664]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 22 22:42:16 bob NetworkManager[664]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 22 22:42:16 bob kernel: [ 1264.647327] wlan0: direct probe to *[snip] *(try 1/3)
Oct 22 22:42:16 bob kernel: [ 1264.844067] wlan0: direct probe to *[snip] *(try 2/3)
Oct 22 22:42:16 bob kernel: [ 1265.044056] wlan0: direct probe to *[snip] *(try 3/3)
Oct 22 22:42:16 bob kernel: [ 1265.244052] wlan0: direct probe to *[snip] *timed out
Oct 22 22:42:22 bob kernel: [ 1271.014208] wlan0: direct probe to *[snip] *(try 1/3)
Oct 22 22:42:22 bob kernel: [ 1271.212051] wlan0: direct probe to *[snip] *(try 2/3)
Oct 22 22:42:22 bob kernel: [ 1271.412050] wlan0: direct probe to *[snip] *(try 3/3)
Oct 22 22:42:23 bob kernel: [ 1271.612050] wlan0: direct probe to *[snip] *timed out
Oct 22 22:42:28 bob kernel: [ 1277.368941] wlan0: direct probe to *[snip] *(try 1/3)
Oct 22 22:42:29 bob kernel: [ 1277.568041] wlan0: direct probe to *[snip] *(try 2/3)
Oct 22 22:42:29 bob NetworkManager[664]: <info> (wlan0): device state change: config -> disconnected (reason 'user-requested') [50 30 39]
Oct 22 22:42:29 bob NetworkManager[664]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Oct 22 22:42:29 bob NetworkManager[664]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Oct 22 22:42:29 bob kernel: [ 1277.768058] wlan0: direct probe to *[snip] *(try 3/3)
Oct 22 22:42:29 bob kernel: [ 1277.968032] wlan0: direct probe to *[snip] *timed out
```

---

### Post by praseodym on 2011-10-22
@ browndusk:

Boot into this kernel and install the driver RTL8188CUS as described in post #32.

---

### Post by wildmanne39 on 2011-10-22
Hi atconley, the solution is in post 32.
Thank you

---

### Post by lils001 on 2011-10-23
> **praseodym said:**
> Add an UDEV-Rule:

```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules
```Insert:

```
# UDEV-rule for wireless sticks
# unloads/loads driver for internal card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-Stick plugged in, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf r8187se"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick plugged out, Onboard-card activated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe r8187se"

LABEL="rules_end"
```Save, close, and reload UDEV:

```
sudo service udev reload
```

Was this directed at me praseodym? (yes I'm a complete and utter newbie and haven't a clue)
Also, I have to repeat the code each time I restart my laptop.
Thanks :)

---

### Post by praseodym on 2011-10-23
@lils001: Yes, it was for you. There is a solution for the driver rtl8192cu:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip dkms
```
_For 11.04:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
```
_For 11.10:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
```
_Installation:_
```
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```
Reboot.

---

### Post by gacor on 2011-10-23
Coolio, this worked for me!!!

---

### Post by Borunco on 2011-10-23
> **praseodym said:**
> @lils001: Yes, it was for you. There is a solution for the driver rtl8192cu:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip dkms
```_For 11.04:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
```_For 11.10:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
```_Installation:_
```
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```Reboot.

Hi, praseodym
I was on another thread and wildmanne39 refer d me to this thread to try post #55 did that and did not work. My problem is after a11.10 upgrade from 11.04 my wireless only connects every third or fourth  boot, and I have only been able to see the drop-down icon on the top right corner two times out of maybe ten connections in the past week. I'm still kind of new to codes but always very exited to learn. if you can help i would appreciated much. Let me know what to post, thank you both for your help in the forum, hope one day I can be of help.:wink:

---

### Post by praseodym on 2011-10-23
Great :guitar:

You (all) should check, which kernel is installed with

```
uname -r
```
and install the metapackage of the kernel headers suitable for you architecture (generic, generic-pae, etc).

```
sudo apt-get install linux-headers-generic
```

Otherwise dkms makes problems while compiling the driver automatically.

---

### Post by praseodym on 2011-10-23
Hi Borunco,

please show:

```
lspci -nnk | grep -iA2 net
uname -a
lsusb
lsmod
iwconfig
sudo iwlist scan
rfkill list
```
What computer do you have?

---

### Post by Borunco on 2011-10-23
[COjose@jose-desktop:~$ uname -r
3.0.0-12-generic
jose@jose-desktop:~$ sudo apt-get install linux-headers-generic
[sudo] password for jose: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libfolks-telepathy22 libpanel-applet-3-0 libpanel-applet-4-0 libswscale0
  libio-string-perl libunity4 libnux-0.9-common diffstat gir1.2-vte-0.0
  libnux-0.9-0 libindicator3 intltool-debian libedataserverui1.2-11
  libclass-accessor-perl unity-place-applications patchutils g++-4.5
  libboost-program-options1.42.0 libcamel1.2-19 libpostproc51 libapt-pkg-perl
  libboost-thread1.42.0 libavformat52 libdvbpsi6 libboost-serialization1.42.0
  libboost-date-time1.42.0 libfolks22 libnet-domain-tld-perl
  libparse-debianchangelog-perl gettext libebook1.2-10 libgdata11 libgwibber1
  libdbusmenu-gtk3 libsub-name-perl libecal1.2-8 libipc-run-perl
  libnet-ip-perl libstdc++6-4.5-dev libnet-dns-perl unity-place-files
  gir1.2-appindicator-0.1 liboverlay-scrollbar-0.1-0 libedata-cal1.2-10
  gnome-panel-bonobo libedata-book1.2-8 libio-pty-perl python-wsgi-intercept
  libunistring0 libunity-misc0 libdigest-hmac-perl libemail-valid-perl
  libquicktime1 lintian libgtkglext1 libmatroska3 gir1.2-panelapplet-4.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jose@jose-desktop:~$ 
Is This right? and do I re-boot?

---

### Post by Borunco on 2011-10-23
Right now I'm posting with the comp. in question, altho I'm connected can't see the drop down icon.
Thank you

---

### Post by Borunco on 2011-10-23
jose@jose-desktop:~$ lspci -nnk | grep -iA2 net
01:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
    Kernel driver in use: 8139too
jose@jose-desktop:~$ uname -a
Linux jose-desktop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
jose@jose-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
jose@jose-desktop:~$ lsmod
Module                  Size  Used by
vesafb                 13489  1 
rfcomm                 38408  0 
arc4                   12473  2 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
nvidia               4708682  22 
ppdev                  12849  0 
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
snd_wavefront          34737  0 
snd_cs4236             29294  0 
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236
snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib
snd_mpu401             13847  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_seq_midi           13132  0 
snd_rawmidi            25241  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_pcm                80468  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
serio_raw              12990  0 
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  4 snd_wss_lib,snd_opl3_lib,snd_seq,snd_pcm
shpchp                 32356  0 
i2c_nforce2            12906  0 
snd_page_alloc         14115  3 snd_wss_lib,snd_intel8x0,snd_pcm
ns558                  12654  0 
gameport               15060  2 ns558
snd                    55902  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
parport_pc             32114  1 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
8139cp                 22636  0 
sata_nv                23379  0 
pata_amd               13753  2 
floppy                 60310  0 
jose@jose-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:"MiFi2372 8050"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:E8:0B:36:C0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

jose@jose-desktop:~$ sudo iwlist scan
[sudo] password for jose: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan2     Scan completed :
          Cell 01 - Address: 00:26:E8:0B:36:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"MiFi2372 8050"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000103ee3179
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000D4D694669323337322038303530
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

jose@jose-desktop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jose@jose-desktop:~$ 
Srry for delay, had to reboot three times to connect.
The comp. is a old build that i use to work out kinks in new realesses.
I think is a atholon 2.5 ghz with 2 gig of ram

---

### Post by praseodym on 2011-10-23
Ok, update the driver as described in #55 for 11.10

---

### Post by Borunco on 2011-10-23
[CODjose@jose-desktop:~$ lspci -nnk | grep -iA2 net
01:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
    Kernel driver in use: 8139too
jose@jose-desktop:~$ uname -a
Linux jose-desktop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
jose@jose-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
jose@jose-desktop:~$ lsmod
Module                  Size  Used by
vesafb                 13489  1 
rfcomm                 38408  0 
arc4                   12473  2 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
nvidia               4708682  22 
ppdev                  12849  0 
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
snd_wavefront          34737  0 
snd_cs4236             29294  0 
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236
snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib
snd_mpu401             13847  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_seq_midi           13132  0 
snd_rawmidi            25241  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_pcm                80468  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
serio_raw              12990  0 
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  4 snd_wss_lib,snd_opl3_lib,snd_seq,snd_pcm
shpchp                 32356  0 
i2c_nforce2            12906  0 
snd_page_alloc         14115  3 snd_wss_lib,snd_intel8x0,snd_pcm
ns558                  12654  0 
gameport               15060  2 ns558
snd                    55902  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
parport_pc             32114  1 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
8139cp                 22636  0 
sata_nv                23379  0 
pata_amd               13753  2 
floppy                 60310  0 
jose@jose-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:"MiFi2372 8050"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:E8:0B:36:C0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

jose@jose-desktop:~$ sudo iwlist scan
[sudo] password for jose: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan2     Scan completed :
          Cell 01 - Address: 00:26:E8:0B:36:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"MiFi2372 8050"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000103ee3179
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000D4D694669323337322038303530
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

jose@jose-desktop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jose@jose-desktop:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip dkms
[sudo] password for jose: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfolks-telepathy22 libpanel-applet-3-0 libpanel-applet-4-0 libswscale0
  libio-string-perl libunity4 libnux-0.9-common diffstat gir1.2-vte-0.0
  libnux-0.9-0 libindicator3 intltool-debian libedataserverui1.2-11
  libclass-accessor-perl unity-place-applications patchutils g++-4.5
  libboost-program-options1.42.0 libcamel1.2-19 libpostproc51 libapt-pkg-perl
  libboost-thread1.42.0 libavformat52 libdvbpsi6 libboost-serialization1.42.0
  libboost-date-time1.42.0 libfolks22 libnet-domain-tld-perl
  libparse-debianchangelog-perl gettext libebook1.2-10 libgdata11 libgwibber1
  libdbusmenu-gtk3 libsub-name-perl libecal1.2-8 libipc-run-perl
  libnet-ip-perl libstdc++6-4.5-dev libnet-dns-perl unity-place-files
  gir1.2-appindicator-0.1 liboverlay-scrollbar-0.1-0 libedata-cal1.2-10
  gnome-panel-bonobo libedata-book1.2-8 libio-pty-perl python-wsgi-intercept
  libunistring0 libunity-misc0 libdigest-hmac-perl libemail-valid-perl
  libquicktime1 lintian libgtkglext1 libmatroska3 gir1.2-panelapplet-4.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,086 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 190219 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu1 (using .../build-essential_11.5ubuntu1_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.2-1ubuntu4 (using .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.0.0-12-generic 3.0.0-12.20 (using .../linux-headers-3.0.0-12-generic_3.0.0-12.20_i386.deb) ...
Unpacking replacement linux-headers-3.0.0-12-generic ...
Preparing to replace unzip 6.0-4ubuntu1 (using .../unzip_6.0-4ubuntu1_i386.deb) ...
Unpacking replacement unzip ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu1) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up linux-headers-3.0.0-12-generic (3.0.0-12.20) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
Setting up unzip (6.0-4ubuntu1) ...
jose@jose-desktop:~$ wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz)
--2011-10-23 15:39:58--  [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz)
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 909344 (888K) [application/octet-stream]
Saving to: `rtl8192cu-3.1.2590_11.10_dkms.tar.gz.1'

100%[======================================>] 909,344      297K/s   in 3.0s    

2011-10-23 15:40:04 (297 KB/s) - `rtl8192cu-3.1.2590_11.10_dkms.tar.gz.1' saved [909344/909344]

jose@jose-desktop:~$ sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
rtl8192cu-3.1.2590/
rtl8192cu-3.1.2590/src/
rtl8192cu-3.1.2590/src/os_dep/
rtl8192cu-3.1.2590/src/include/
rtl8192cu-3.1.2590/src/hal/
rtl8192cu-3.1.2590/src/core/
rtl8192cu-3.1.2590/src/os_dep/linux/
rtl8192cu-3.1.2590/src/include/byteorder/
rtl8192cu-3.1.2590/src/hal/rtl8192c/
rtl8192cu-3.1.2590/src/core/efuse/
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/
rtl8192cu-3.1.2590/dkms.conf
rtl8192cu-3.1.2590/Makefile
rtl8192cu-3.1.2590/src/wlan0dhcp
rtl8192cu-3.1.2590/src/runwpa
rtl8192cu-3.1.2590/src/Makefile
rtl8192cu-3.1.2590/src/Kconfig
rtl8192cu-3.1.2590/src/ifcfg-wlan0
rtl8192cu-3.1.2590/src/clean
rtl8192cu-3.1.2590/src/os_dep/osdep_service.c
rtl8192cu-3.1.2590/src/include/xmit_osdep.h
rtl8192cu-3.1.2590/src/include/wlan_bssdef.h
rtl8192cu-3.1.2590/src/include/wifi.h
rtl8192cu-3.1.2590/src/include/usb_vendor_req.h
rtl8192cu-3.1.2590/src/include/usb_osintf.h
rtl8192cu-3.1.2590/src/include/usb_ops.h
rtl8192cu-3.1.2590/src/include/usb_hal.h
rtl8192cu-3.1.2590/src/include/sta_info.h
rtl8192cu-3.1.2590/src/include/sdio_osintf.h
rtl8192cu-3.1.2590/src/include/sdio_ops_xp.h
rtl8192cu-3.1.2590/src/include/sdio_ops_linux.h
rtl8192cu-3.1.2590/src/include/sdio_ops_ce.h
rtl8192cu-3.1.2590/src/include/sdio_ops.h
rtl8192cu-3.1.2590/src/include/sdio_hal.h
rtl8192cu-3.1.2590/src/include/rtw_xmit.h
rtl8192cu-3.1.2590/src/include/rtw_version.h
rtl8192cu-3.1.2590/src/include/rtw_security.h
rtl8192cu-3.1.2590/src/include/rtw_rf.h
rtl8192cu-3.1.2590/src/include/rtw_recv.h
rtl8192cu-3.1.2590/src/include/rtw_qos.h
rtl8192cu-3.1.2590/src/include/rtw_pwrctrl.h
rtl8192cu-3.1.2590/src/include/rtw_p2p.h
rtl8192cu-3.1.2590/src/include/rtw_mp_phy_regdef.h
rtl8192cu-3.1.2590/src/include/rtw_mp_ioctl.h
rtl8192cu-3.1.2590/src/include/rtw_mp.h
rtl8192cu-3.1.2590/src/include/rtw_mlme_ext.h
rtl8192cu-3.1.2590/src/include/rtw_mlme.h
rtl8192cu-3.1.2590/src/include/rtw_led.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl_set.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl_rtl.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl_query.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl.h
rtl8192cu-3.1.2590/src/include/rtw_ht.h
rtl8192cu-3.1.2590/src/include/rtw_event.h
rtl8192cu-3.1.2590/src/include/rtw_efuse.h
rtl8192cu-3.1.2590/src/include/rtw_eeprom.h
rtl8192cu-3.1.2590/src/include/rtw_debug.h
rtl8192cu-3.1.2590/src/include/rtw_cmd.h
rtl8192cu-3.1.2590/src/include/rtw_byteorder.h
rtl8192cu-3.1.2590/src/include/rtl8192d_xmit.h
rtl8192cu-3.1.2590/src/include/rtl8192d_spec.h
rtl8192cu-3.1.2590/src/include/rtl8192d_rf.h
rtl8192cu-3.1.2590/src/include/rtl8192d_recv.h
rtl8192cu-3.1.2590/src/include/rtl8192d_led.h
rtl8192cu-3.1.2590/src/include/rtl8192d_hal.h
rtl8192cu-3.1.2590/src/include/rtl8192d_dm.h
rtl8192cu-3.1.2590/src/include/rtl8192d_cmd.h
rtl8192cu-3.1.2590/src/include/rtl8192c_xmit.h
rtl8192cu-3.1.2590/src/include/rtl8192c_sreset.h
rtl8192cu-3.1.2590/src/include/rtl8192c_spec.h
rtl8192cu-3.1.2590/src/include/rtl8192c_rf.h
rtl8192cu-3.1.2590/src/include/rtl8192c_recv.h
rtl8192cu-3.1.2590/src/include/rtl8192c_led.h
rtl8192cu-3.1.2590/src/include/rtl8192c_hal.h
rtl8192cu-3.1.2590/src/include/rtl8192c_event.h
rtl8192cu-3.1.2590/src/include/rtl8192c_dm.h
rtl8192cu-3.1.2590/src/include/rtl8192c_cmd.h
rtl8192cu-3.1.2590/src/include/recv_osdep.h
rtl8192cu-3.1.2590/src/include/pci_osintf.h
rtl8192cu-3.1.2590/src/include/pci_ops.h
rtl8192cu-3.1.2590/src/include/pci_hal.h
rtl8192cu-3.1.2590/src/include/osdep_intf.h
rtl8192cu-3.1.2590/src/include/osdep_ce_service.h
rtl8192cu-3.1.2590/src/include/nic_spec.h
rtl8192cu-3.1.2590/src/include/mp_custom_oid.h
rtl8192cu-3.1.2590/src/include/mlme_osdep.h
rtl8192cu-3.1.2590/src/include/ip.h
rtl8192cu-3.1.2590/src/include/if_ether.h
rtl8192cu-3.1.2590/src/include/ieee80211_ext.h
rtl8192cu-3.1.2590/src/include/ieee80211.h
rtl8192cu-3.1.2590/src/include/hal_init.h
rtl8192cu-3.1.2590/src/include/Hal8192DUTestHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192DUHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192DPhyReg.h
rtl8192cu-3.1.2590/src/include/Hal8192DPhyCfg.h
rtl8192cu-3.1.2590/src/include/Hal8192DETestHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192DEHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192CUHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192CPhyReg.h
rtl8192cu-3.1.2590/src/include/Hal8192CPhyCfg.h
rtl8192cu-3.1.2590/src/include/Hal8192CEHWImg.h
rtl8192cu-3.1.2590/src/include/h2clbk.h
rtl8192cu-3.1.2590/src/include/farray.h
rtl8192cu-3.1.2590/src/include/ethernet.h
rtl8192cu-3.1.2590/src/include/drv_types_xp.h
rtl8192cu-3.1.2590/src/include/drv_types_linux.h
rtl8192cu-3.1.2590/src/include/drv_types_ce.h
rtl8192cu-3.1.2590/src/include/drv_types.h
rtl8192cu-3.1.2590/src/include/drv_conf.h
rtl8192cu-3.1.2590/src/include/cmd_osdep.h
rtl8192cu-3.1.2590/src/include/circ_buf.h
rtl8192cu-3.1.2590/src/include/basic_types.h
rtl8192cu-3.1.2590/src/include/autoconf.h
rtl8192cu-3.1.2590/src/hal/hal_init.c
rtl8192cu-3.1.2590/src/core/rtw_xmit.c
rtl8192cu-3.1.2590/src/core/rtw_wlan_util.c
rtl8192cu-3.1.2590/src/core/rtw_sta_mgt.c
rtl8192cu-3.1.2590/src/core/rtw_security.c
rtl8192cu-3.1.2590/src/core/rtw_rf.c
rtl8192cu-3.1.2590/src/core/rtw_recv.c
rtl8192cu-3.1.2590/src/core/rtw_pwrctrl.c
rtl8192cu-3.1.2590/src/core/rtw_p2p.c
rtl8192cu-3.1.2590/src/core/rtw_mp_ioctl.c
rtl8192cu-3.1.2590/src/core/rtw_mp.c
rtl8192cu-3.1.2590/src/core/rtw_mlme_ext.c
rtl8192cu-3.1.2590/src/core/rtw_mlme.c
rtl8192cu-3.1.2590/src/core/rtw_ioctl_set.c
rtl8192cu-3.1.2590/src/core/rtw_ioctl_rtl.c
rtl8192cu-3.1.2590/src/core/rtw_ioctl_query.c
rtl8192cu-3.1.2590/src/core/rtw_io.c
rtl8192cu-3.1.2590/src/core/rtw_ieee80211.c
rtl8192cu-3.1.2590/src/core/rtw_eeprom.c
rtl8192cu-3.1.2590/src/core/rtw_debug.c
rtl8192cu-3.1.2590/src/core/rtw_cmd.c
rtl8192cu-3.1.2590/src/os_dep/linux/xmit_linux.c
rtl8192cu-3.1.2590/src/os_dep/linux/usb_intf.c
rtl8192cu-3.1.2590/src/os_dep/linux/sdio_intf.c
rtl8192cu-3.1.2590/src/os_dep/linux/recv_linux.c
rtl8192cu-3.1.2590/src/os_dep/linux/pci_intf.c
rtl8192cu-3.1.2590/src/os_dep/linux/os_intfs.c
rtl8192cu-3.1.2590/src/os_dep/linux/mlme_linux.c
rtl8192cu-3.1.2590/src/os_dep/linux/ioctl_linux.c
rtl8192cu-3.1.2590/src/include/byteorder/swabb.h
rtl8192cu-3.1.2590/src/include/byteorder/swab.h
rtl8192cu-3.1.2590/src/include/byteorder/little_endian.h
rtl8192cu-3.1.2590/src/include/byteorder/generic.h
rtl8192cu-3.1.2590/src/include/byteorder/big_endian.h
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_sreset.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_dm.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_cmd.c
rtl8192cu-3.1.2590/src/core/efuse/rtw_efuse.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_halinit.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192cu-3.1.2590/src/include/rtw_io.h
rtl8192cu-3.1.2590/src/include/osdep_service.h
jose@jose-desktop:~$ sudo dkms add -m rtl8192cu -v 3.1.2590
Error! DKMS tree already contains: rtl8192cu-3.1.2590
You cannot add the same module/version combo more than once.
jose@jose-desktop:~$ sudo dkms build -m rtl8192cu -v 3.1.2590
Module rtl8192cu/3.1.2590 already built for kernel 3.0.0-12-generic/4
jose@jose-desktop:~$ sudo dkms install -m rtl8192cu -v 3.1.2590
Module rtl8192cu/3.1.2590 already installed on kernel 3.0.0-12-generic/i686
jose@jose-desktop:~$ 
Ok this is what I got, I will re-boot now

---

### Post by praseodym on 2011-10-23
Sometimes blanks in the ESSID make problems, rename your network to be sure

---

### Post by Borunco on 2011-10-23
Sorry been trying to connect, I still have the same problem. I saw your postabove dont where to do that? is it in the network manager? with this problem i dont have many options their.

---

### Post by Borunco on 2011-10-23
I'm posting from my net book, because I was having a hard time connecting. thank your for all your help. I have to stop for today, I will try tomorrow. 
thank again for all your help
Borunco

---

### Post by praseodym on 2011-10-23
Connect via cable to your router and type in your router-IP-address in a browser. You should be able to change the ESSID there. After that remove (not edit) your wireless connection setup in the nm and create a new one.

---

### Post by lils001 on 2011-10-23
@praseodym
> **praseodym said:**
> @lils001: Yes, it was for you. There is a solution for the driver rtl8192cu:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip dkms
```_For 11.04:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
```_For 11.10:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
```_Installation:_
```
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```Reboot.

Ok, first of all I'm sick and took this entire message to mean only to proceed with the code in the above post (#55). So I did all of this and then reboot. Wireless connection wasn't happening automatically so I plugged in the ethernet cable. Both wireless devices were visible and despite removing the 'connection' info for the onboard one the dongle would not connect. I then carried out your earlier instructions to single out the usb dongle. This worked, however it does try connecting even if I have the ethernet cable plugged in. 
Then I remember that post #49 was directed at me and decided (since I'm so new to this) that what you'd posted must have been complete commands and proceeded. ... At [LABEL="device_check] I forgot to check before pressing enter and thus returned on [LAVEL="device_cjecl] :|. The next line was entirely blank except for [>]. Typing [exit] did nothing. I closed the terminal. I was going to start again but then thought I would perhaps be creating a mess somewhere if I did. So here I am asking: what should I do? Sorry for the mess.
Also, was I suppose to read and follow post #58 before commencing #55? Thanks.

---

### Post by praseodym on 2011-10-24
You can directly use #55.

---

### Post by lils001 on 2011-10-24
Well that's what I did and it didn't seem to be successful :(

output was as follows:
```
lilly@lilly-E1500:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip dkms
[sudo] password for lilly: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev patch
0 upgraded, 12 newly installed, 2 reinstalled, 0 to remove and 22 not upgraded.
Need to get 9,753 kB of archives.
After this operation, 29.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://au.archive.ubuntu.com/ubuntu/ oneiric/main libstdc++6-4.6-dev i386 4.6.1-9ubuntu3 [1,589 kB]
Get:2 http://au.archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6 i386 4.6.1-9ubuntu3 [6,187 kB]
Get:3 http://au.archive.ubuntu.com/ubuntu/ oneiric/main g++ i386 4:4.6.1-2ubuntu5 [1,434 B]
Get:4 http://au.archive.ubuntu.com/ubuntu/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5 [171 kB]
Get:5 http://au.archive.ubuntu.com/ubuntu/ oneiric/main patch i386 2.6.1-2 [86.5 kB]
Get:6 http://au.archive.ubuntu.com/ubuntu/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5 [473 kB]
Get:7 http://au.archive.ubuntu.com/ubuntu/ oneiric/main build-essential i386 11.5ubuntu1 [5,920 B]
Get:8 http://au.archive.ubuntu.com/ubuntu/ oneiric/main dkms all 2.2.0.2-1ubuntu4 [72.3 kB]
Get:9 http://au.archive.ubuntu.com/ubuntu/ oneiric/main fakeroot i386 1.17-1 [81.6 kB]
Get:10 http://au.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:11 http://au.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-xs-perl i386 0.04-1build1 [13.8 kB]
Get:12 http://au.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:13 http://au.archive.ubuntu.com/ubuntu/ oneiric/main linux-headers-3.0.0-12-generic i386 3.0.0-12.20 [830 kB]
Get:14 http://au.archive.ubuntu.com/ubuntu/ oneiric/main unzip i386 6.0-4ubuntu1 [178 kB]
Fetched 9,753 kB in 10s (919 kB/s)                                             
Selecting previously deselected package libstdc++6-4.6-dev.
(Reading database ... 149213 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.1-9ubuntu3_i386.deb) ...
Selecting previously deselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.1-9ubuntu3_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.1-2ubuntu5_i386.deb) ...
Selecting previously deselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.0.3ubuntu5_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6.1-2_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.0.3ubuntu5_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu1_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_i386.deb) ...
Selecting previously deselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously deselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-1build1_i386.deb) ...
Selecting previously deselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Preparing to replace linux-headers-3.0.0-12-generic 3.0.0-12.20 (using .../linux-headers-3.0.0-12-generic_3.0.0-12.20_i386.deb) ...
Unpacking replacement linux-headers-3.0.0-12-generic ...
Preparing to replace unzip 6.0-4ubuntu1 (using .../unzip_6.0-4ubuntu1_i386.deb) ...
Unpacking replacement unzip ...
Processing triggers for man-db ...
Setting up libdpkg-perl (1.16.0.3ubuntu5) ...
Setting up patch (2.6.1-2) ...
Setting up dpkg-dev (1.16.0.3ubuntu5) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-1build1) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up linux-headers-3.0.0-12-generic (3.0.0-12.20) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-12-generic /boot/vmlinuz-3.0.0-12-generic
Setting up unzip (6.0-4ubuntu1) ...
Setting up libstdc++6-4.6-dev (4.6.1-9ubuntu3) ...
Setting up g++-4.6 (4.6.1-9ubuntu3) ...
Setting up g++ (4:4.6.1-2ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu1) ...
lilly@lilly-E1500:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
--2011-10-24 11:12:18--  http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 909344 (888K) [application/octet-stream]
Saving to: 'rtl8192cu-3.1.2590_11.10_dkms.tar.gz'

100%[======================================>] 909,344      155K/s   in 7.3s    

2011-10-24 11:12:27 (122 KB/s) - 'rtl8192cu-3.1.2590_11.10_dkms.tar.gz' saved [909344/909344]

lilly@lilly-E1500:~$ sudo tar xvf rtl8192cu-3.1.2590_11.10dkms.tar.gz -C /usr/src
tar: rtl8192cu-3.1.2590_11.10dkms.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
lilly@lilly-E1500:~$ sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
rtl8192cu-3.1.2590/
rtl8192cu-3.1.2590/src/
rtl8192cu-3.1.2590/src/os_dep/
rtl8192cu-3.1.2590/src/include/
rtl8192cu-3.1.2590/src/hal/
rtl8192cu-3.1.2590/src/core/
rtl8192cu-3.1.2590/src/os_dep/linux/
rtl8192cu-3.1.2590/src/include/byteorder/
rtl8192cu-3.1.2590/src/hal/rtl8192c/
rtl8192cu-3.1.2590/src/core/efuse/
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/
rtl8192cu-3.1.2590/dkms.conf
rtl8192cu-3.1.2590/Makefile
rtl8192cu-3.1.2590/src/wlan0dhcp
rtl8192cu-3.1.2590/src/runwpa
rtl8192cu-3.1.2590/src/Makefile
rtl8192cu-3.1.2590/src/Kconfig
rtl8192cu-3.1.2590/src/ifcfg-wlan0
rtl8192cu-3.1.2590/src/clean
rtl8192cu-3.1.2590/src/os_dep/osdep_service.c
rtl8192cu-3.1.2590/src/include/xmit_osdep.h
rtl8192cu-3.1.2590/src/include/wlan_bssdef.h
rtl8192cu-3.1.2590/src/include/wifi.h
rtl8192cu-3.1.2590/src/include/usb_vendor_req.h
rtl8192cu-3.1.2590/src/include/usb_osintf.h
rtl8192cu-3.1.2590/src/include/usb_ops.h
rtl8192cu-3.1.2590/src/include/usb_hal.h
rtl8192cu-3.1.2590/src/include/sta_info.h
rtl8192cu-3.1.2590/src/include/sdio_osintf.h
rtl8192cu-3.1.2590/src/include/sdio_ops_xp.h
rtl8192cu-3.1.2590/src/include/sdio_ops_linux.h
rtl8192cu-3.1.2590/src/include/sdio_ops_ce.h
rtl8192cu-3.1.2590/src/include/sdio_ops.h
rtl8192cu-3.1.2590/src/include/sdio_hal.h
rtl8192cu-3.1.2590/src/include/rtw_xmit.h
rtl8192cu-3.1.2590/src/include/rtw_version.h
rtl8192cu-3.1.2590/src/include/rtw_security.h
rtl8192cu-3.1.2590/src/include/rtw_rf.h
rtl8192cu-3.1.2590/src/include/rtw_recv.h
rtl8192cu-3.1.2590/src/include/rtw_qos.h
rtl8192cu-3.1.2590/src/include/rtw_pwrctrl.h
rtl8192cu-3.1.2590/src/include/rtw_p2p.h
rtl8192cu-3.1.2590/src/include/rtw_mp_phy_regdef.h
rtl8192cu-3.1.2590/src/include/rtw_mp_ioctl.h
rtl8192cu-3.1.2590/src/include/rtw_mp.h
rtl8192cu-3.1.2590/src/include/rtw_mlme_ext.h
rtl8192cu-3.1.2590/src/include/rtw_mlme.h
rtl8192cu-3.1.2590/src/include/rtw_led.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl_set.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl_rtl.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl_query.h
rtl8192cu-3.1.2590/src/include/rtw_ioctl.h
rtl8192cu-3.1.2590/src/include/rtw_ht.h
rtl8192cu-3.1.2590/src/include/rtw_event.h
rtl8192cu-3.1.2590/src/include/rtw_efuse.h
rtl8192cu-3.1.2590/src/include/rtw_eeprom.h
rtl8192cu-3.1.2590/src/include/rtw_debug.h
rtl8192cu-3.1.2590/src/include/rtw_cmd.h
rtl8192cu-3.1.2590/src/include/rtw_byteorder.h
rtl8192cu-3.1.2590/src/include/rtl8192d_xmit.h
rtl8192cu-3.1.2590/src/include/rtl8192d_spec.h
rtl8192cu-3.1.2590/src/include/rtl8192d_rf.h
rtl8192cu-3.1.2590/src/include/rtl8192d_recv.h
rtl8192cu-3.1.2590/src/include/rtl8192d_led.h
rtl8192cu-3.1.2590/src/include/rtl8192d_hal.h
rtl8192cu-3.1.2590/src/include/rtl8192d_dm.h
rtl8192cu-3.1.2590/src/include/rtl8192d_cmd.h
rtl8192cu-3.1.2590/src/include/rtl8192c_xmit.h
rtl8192cu-3.1.2590/src/include/rtl8192c_sreset.h
rtl8192cu-3.1.2590/src/include/rtl8192c_spec.h
rtl8192cu-3.1.2590/src/include/rtl8192c_rf.h
rtl8192cu-3.1.2590/src/include/rtl8192c_recv.h
rtl8192cu-3.1.2590/src/include/rtl8192c_led.h
rtl8192cu-3.1.2590/src/include/rtl8192c_hal.h
rtl8192cu-3.1.2590/src/include/rtl8192c_event.h
rtl8192cu-3.1.2590/src/include/rtl8192c_dm.h
rtl8192cu-3.1.2590/src/include/rtl8192c_cmd.h
rtl8192cu-3.1.2590/src/include/recv_osdep.h
rtl8192cu-3.1.2590/src/include/pci_osintf.h
rtl8192cu-3.1.2590/src/include/pci_ops.h
rtl8192cu-3.1.2590/src/include/pci_hal.h
rtl8192cu-3.1.2590/src/include/osdep_intf.h
rtl8192cu-3.1.2590/src/include/osdep_ce_service.h
rtl8192cu-3.1.2590/src/include/nic_spec.h
rtl8192cu-3.1.2590/src/include/mp_custom_oid.h
rtl8192cu-3.1.2590/src/include/mlme_osdep.h
rtl8192cu-3.1.2590/src/include/ip.h
rtl8192cu-3.1.2590/src/include/if_ether.h
rtl8192cu-3.1.2590/src/include/ieee80211_ext.h
rtl8192cu-3.1.2590/src/include/ieee80211.h
rtl8192cu-3.1.2590/src/include/hal_init.h
rtl8192cu-3.1.2590/src/include/Hal8192DUTestHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192DUHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192DPhyReg.h
rtl8192cu-3.1.2590/src/include/Hal8192DPhyCfg.h
rtl8192cu-3.1.2590/src/include/Hal8192DETestHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192DEHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192CUHWImg.h
rtl8192cu-3.1.2590/src/include/Hal8192CPhyReg.h
rtl8192cu-3.1.2590/src/include/Hal8192CPhyCfg.h
rtl8192cu-3.1.2590/src/include/Hal8192CEHWImg.h
rtl8192cu-3.1.2590/src/include/h2clbk.h
rtl8192cu-3.1.2590/src/include/farray.h
rtl8192cu-3.1.2590/src/include/ethernet.h
rtl8192cu-3.1.2590/src/include/drv_types_xp.h
rtl8192cu-3.1.2590/src/include/drv_types_linux.h
rtl8192cu-3.1.2590/src/include/drv_types_ce.h
rtl8192cu-3.1.2590/src/include/drv_types.h
rtl8192cu-3.1.2590/src/include/drv_conf.h
rtl8192cu-3.1.2590/src/include/cmd_osdep.h
rtl8192cu-3.1.2590/src/include/circ_buf.h
rtl8192cu-3.1.2590/src/include/basic_types.h
rtl8192cu-3.1.2590/src/include/autoconf.h
rtl8192cu-3.1.2590/src/hal/hal_init.c
rtl8192cu-3.1.2590/src/core/rtw_xmit.c
rtl8192cu-3.1.2590/src/core/rtw_wlan_util.c
rtl8192cu-3.1.2590/src/core/rtw_sta_mgt.c
rtl8192cu-3.1.2590/src/core/rtw_security.c
rtl8192cu-3.1.2590/src/core/rtw_rf.c
rtl8192cu-3.1.2590/src/core/rtw_recv.c
rtl8192cu-3.1.2590/src/core/rtw_pwrctrl.c
rtl8192cu-3.1.2590/src/core/rtw_p2p.c
rtl8192cu-3.1.2590/src/core/rtw_mp_ioctl.c
rtl8192cu-3.1.2590/src/core/rtw_mp.c
rtl8192cu-3.1.2590/src/core/rtw_mlme_ext.c
rtl8192cu-3.1.2590/src/core/rtw_mlme.c
rtl8192cu-3.1.2590/src/core/rtw_ioctl_set.c
rtl8192cu-3.1.2590/src/core/rtw_ioctl_rtl.c
rtl8192cu-3.1.2590/src/core/rtw_ioctl_query.c
rtl8192cu-3.1.2590/src/core/rtw_io.c
rtl8192cu-3.1.2590/src/core/rtw_ieee80211.c
rtl8192cu-3.1.2590/src/core/rtw_eeprom.c
rtl8192cu-3.1.2590/src/core/rtw_debug.c
rtl8192cu-3.1.2590/src/core/rtw_cmd.c
rtl8192cu-3.1.2590/src/os_dep/linux/xmit_linux.c
rtl8192cu-3.1.2590/src/os_dep/linux/usb_intf.c
rtl8192cu-3.1.2590/src/os_dep/linux/sdio_intf.c
rtl8192cu-3.1.2590/src/os_dep/linux/recv_linux.c
rtl8192cu-3.1.2590/src/os_dep/linux/pci_intf.c
rtl8192cu-3.1.2590/src/os_dep/linux/os_intfs.c
rtl8192cu-3.1.2590/src/os_dep/linux/mlme_linux.c
rtl8192cu-3.1.2590/src/os_dep/linux/ioctl_linux.c
rtl8192cu-3.1.2590/src/include/byteorder/swabb.h
rtl8192cu-3.1.2590/src/include/byteorder/swab.h
rtl8192cu-3.1.2590/src/include/byteorder/little_endian.h
rtl8192cu-3.1.2590/src/include/byteorder/generic.h
rtl8192cu-3.1.2590/src/include/byteorder/big_endian.h
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_sreset.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_dm.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/rtl8192c_cmd.c
rtl8192cu-3.1.2590/src/core/efuse/rtw_efuse.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/usb_halinit.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8192cu-3.1.2590/src/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192cu-3.1.2590/src/include/rtw_io.h
rtl8192cu-3.1.2590/src/include/osdep_service.h
lilly@lilly-E1500:~$ sudo dkms add -m rtl8192cu -v 3.1.2590

Creating symlink /var/lib/dkms/rtl8192cu/3.1.2590/source ->
                 /usr/src/rtl8192cu-3.1.2590

DKMS: add Completed.
lilly@lilly-E1500:~$ sudo dkms build -m rtl8192cu -v 3.1.2590

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all.............
cleaning build area....

DKMS: build Completed.
lilly@lilly-E1500:~$ sudo dkms install -m rtl8192cu -v 3.1.2590

8192cu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod.......

DKMS: install Completed.
```

---

### Post by praseodym on 2011-10-24
Reboot, plug in the stick and check:

```
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | egrep 'rtl|r8'
modinfo rtl8192cu
```

---

### Post by flipbrad on 2011-10-24
Following the steps in #55 did not unfortunately solve the problem for me. 

Connection still only forms after a reboot or after pulling out the USB dongle then putting it back in. Once formed it will often stop functioning (despite network manager still saying it's connected) with the 'Invalid misc' count in iwconfig increasing, and thereafter, trying to reconnect to it times out or prompts for the password repeatedly.

No problems when (dual)booted into Win7

Ubuntu 11.10 64bit
Kernel: 3.0.0-12 generic
Router: 802.11g mode (no n mode), visible SSID

lsusb:
```
(...) Bus 001 Device 004: IS 0bda:8176 Realtek (...) RTL8188CUS 802.11n WLAN
```

lsmod:
```
(...) rtl8192cu   103210   0
rtl8128c_common     75767   1   rtl8192cu
rtlwifi     110972  1   rtl8192cu
mac80211     310872  3  rtl8192cu, rtl8192c_common, rtlwifi
cfg80211   199587  2  rtlwifi, mac80211
(...)
```

iwconfig
```

lo [no..], eth0 [no...]
wlan 0 
IEEE 802.11bgn ESSID: off/any
Mode: managed
Access Point: Not-Associated
Tx-Power=20dBm
Retry long limit:7
RTS thr=2347B
Fragment thr: off
Power Management: off
```

rfkill list: nothing blocked

iwlist scan: no scan results (but network manager sees 3 APs - mine and my neighbours

dmesg | egrep 'rtl|r8'
```
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88013fa00000 s79616 r8192 d22784 u1048576
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u1048576 alloc=1*2097152
[    1.330504] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.330525] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.330572] r8169 0000:05:00.0: setting latency timer to 64
[    1.330653] r8169 0000:05:00.0: irq 44 for MSI/MSI-X
[    1.334498] r8169 0000:05:00.0: eth0: RTL8168e/8111e at 0xffffc9000064e000, 00:25:22:c2:fe:03, XID 0c200000 IRQ 44
[   11.121712] rtl8192cu: MAC address: 00:02:72:a1:80:78
[   11.121719] rtl8192cu: Board Type 0
[   11.148562] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   11.150770] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.151145] usbcore: registered new interface driver rtl8192cu
[   11.208340] Error: Driver 'rtl8192cu' is already registered, aborting...
[   11.996065] rtl8192cu: MAC auto ON okay!
[   12.030029] rtl8192cu: Tx queue select: 0x05
[   12.030791] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
[   12.635754] r8169 0000:05:00.0: eth0: link down
[  402.434937] rtl8192cu: MAC address: 00:02:72:a1:80:78
[  402.434945] rtl8192cu: Board Type 0
[  402.437432] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  402.437819] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  402.457900] rtl8192cu: MAC auto ON okay!
[  402.492984] rtl8192cu: Tx queue select: 0x05
[  402.493868] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
```

modinfo rtl8192cu
```

filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     9550D79A3F9B707741FF904
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3359p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3358p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-12-generic SMP mod_unload modversions 

```

---

### Post by praseodym on 2011-10-24
Set up an udev-rule for the stick:

```
gksudo gedit /etc/udev/rules.d/10_wlan_stick.rules 
```
Insert:

```
# UDEV-Rule for RTL8188CUS 802.11n WLAN ID 0bda:8176
SUBSYSTEM=="usb", ATTR{idVendor}=="0bda", ATTR{idProduct}=="8176", RUN+="/sbin/modprobe rtl8192cu"
```
Save, close and restart udev:
```
sudo service udev reload
```

---

### Post by flipbrad on 2011-10-24
Hi praseodym

Thanks for the attention you're giving this thread.

Unfortunately, creating the rule as you suggested hasn't achieved anything. Still getting timeouts even when network manager reports successful connection (with 'invalid packet' count increasing in iwconfig) and then unable to reconnect when selecting the SSID (shown as connected) in network manager's drop-down indicator; it will take a long time then ask for the password again.

I may attempt to downgrade my kernel. Alternatively, I can get a later version from oneiric-proposed. What do you think?

Is there anything else I can do to help you diagnose the problem?

---

### Post by praseodym on 2011-10-24
Which encryption mode do you use? I recommend WPA2-AES, not mixed or WEP. Otherwise try Wicd:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```

Choose **wlan0** as interface name and **wext** as driver.

---

### Post by flipbrad on 2011-10-24
WPA2. I'll try wicd, and if that fails, I'll try an older kernel than 3.0.

---

### Post by flipbrad on 2011-10-24
Wicd results: not promising.

Wicd fails to connect (prompting for passwords) - unless I unplug the adaptor and then stick it back in again, at which point it works first time. 

Pages then refuse to load, incrementing the 'Invalid misc' count under iwconfig. 

This is basically the same behaviour as under network manager.

---

### Post by praseodym on 2011-10-24
Try to debug:

```
gksu gedit /etc/wpa_supplicant/wpa_supplicant.conf 
```
Add:
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
ssid="[COLOR="Red"]YourESSID[/COLOR]"
scan_ssid=1
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk="[COLOR="Red"]YourKey[/COLOR]"
}
```
Start the debug-mode:
```
sudo service network-manager stop
sudo killall wpa_supplicant
sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d 
```
Stop it after 30 s and post the output.

---

### Post by flipbrad on 2011-10-24
OK. results after a fresh unplug/replug of the usb dongle:
```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 0
   id=0 ssid='house9'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: 00:02:72:a1:80:78
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): e2 36 c7 66 27 08 5e ca 94 fc 37 cf b1 9e 2d bc
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=16
State: DISCONNECTED -> SCANNING
Scan SSID - hexdump_ascii(len=6):
     68 6f 75 73 65 39                                 house9          
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 5 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 1083 bytes of scan results (2 BSSes)
BSS: Start scan result update 1
BSS: Add new id 0 BSSID 00:22:3f:96:10:2f SSID 'House10'
BSS: Add new id 1 BSSID 00:18:4d:1a:70:96 SSID 'house9'
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip RSN IE - GTK cipher mismatch
Try to find non-WPA AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - non-WPA network not allowed
No suitable network found
Setting scan request: 5 sec 0 usec
EAPOL: disable timer tick
EAPOL: Supplicant port status: Unauthorized
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 1083 bytes of scan results (2 BSSes)
BSS: Start scan result update 2
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip RSN IE - GTK cipher mismatch
1: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - non-WPA network not allowed
1: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
No suitable network found
Setting scan request: 5 sec 0 usec
Scan SSID - hexdump_ascii(len=6):
     68 6f 75 73 65 39                                 house9          
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 1083 bytes of scan results (2 BSSes)
BSS: Start scan result update 3
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip RSN IE - GTK cipher mismatch
Try to find non-WPA AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - non-WPA network not allowed
No suitable network found
Setting scan request: 5 sec 0 usec
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 1083 bytes of scan results (2 BSSes)
BSS: Start scan result update 4
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip RSN IE - GTK cipher mismatch
Try to find non-WPA AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - non-WPA network not allowed
No suitable network found
Setting scan request: 5 sec 0 usec
Scan SSID - hexdump_ascii(len=6):
     68 6f 75 73 65 39                                 house9          
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 1083 bytes of scan results (2 BSSes)
BSS: Start scan result update 5
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip RSN IE - GTK cipher mismatch
1: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - non-WPA network not allowed
1: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
No suitable network found
Setting scan request: 5 sec 0 usec
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 1083 bytes of scan results (2 BSSes)
BSS: Start scan result update 6
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip RSN IE - GTK cipher mismatch
Try to find non-WPA AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - non-WPA network not allowed
No suitable network found
Setting scan request: 5 sec 0 usec
^CCTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
No keys have been configured - skip key clearing
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
BSS: Remove id 0 BSSID 00:22:3f:96:10:2f SSID 'House10'
BSS: Remove id 1 BSSID 00:18:4d:1a:70:96 SSID 'house9'
Cancelling scan request
Cancelling authentication timeout
netlink: Operstate: linkmode=0, operstate=6
```

results without the fresh unplug:
```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 0
   id=0 ssid='house9'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: 00:02:72:a1:80:78
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): e2 36 c7 66 27 08 5e ca 94 fc 37 cf b1 9e 2d bc
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=16
State: DISCONNECTED -> SCANNING
Scan SSID - hexdump_ascii(len=6):
     68 6f 75 73 65 39                                 house9          
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 5 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 1
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found
Setting scan request: 5 sec 0 usec
EAPOL: disable timer tick
EAPOL: Supplicant port status: Unauthorized
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 2
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found
Setting scan request: 5 sec 0 usec
Scan SSID - hexdump_ascii(len=6):
     68 6f 75 73 65 39                                 house9          
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 3
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found
Setting scan request: 5 sec 0 usec
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 4
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found
Setting scan request: 5 sec 0 usec
Scan SSID - hexdump_ascii(len=6):
     68 6f 75 73 65 39                                 house9          
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 5
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found
Setting scan request: 5 sec 0 usec
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 6
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found
Setting scan request: 5 sec 0 usec
^CCTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
No keys have been configured - skip key clearing
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
netlink: Operstate: linkmode=0, operstate=6
braadli@braadli-desktop:~$ 

```

---

### Post by praseodym on 2011-10-24
```
Try to find WPA-enabled AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip RSN IE - GTK cipher mismatch
Try to find non-WPA AP
0: 00:22:3f:96:10:2f ssid='House10' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - non-WPA network not allowed
```
Your ESSID is right? Please show:

```
sudo iwlist scan
```

---

### Post by flipbrad on 2011-10-24
yep, it's correct.


wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:1A:70:96
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"house9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013a7ef181
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 0006686F75736539
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010024FF7F

---

### Post by praseodym on 2011-10-24
Its a mixed WPA/WPA2 encryption. Add to the file wpa_supplicant.conf:

```
network={
ssid="[COLOR="Red"]YourESSID[/COLOR]"
scan_ssid=1
proto=[COLOR="Red"]WPA[/COLOR]
key_mgmt=WPA-PSK
pairwise=CCMP
[COLOR="Red"]group=TKIP[/COLOR]
psk="[COLOR="Red"]YourKey[/COLOR]"
}
```
and change in the other entry "group" also to [COLOR="Red"]TKIP[/COLOR]. Start the debugger again as described.

---

### Post by flipbrad on 2011-10-24
I will in a bit. First I notice that 3.0.0-12.21 kernel fixes:

" * rtlwifi: rtl8192su: Fix problem connecting to HT-enabled AP
    - LP: #868628
  * rtlwifi: Fix problem when switching connections
    - LP: #868628
* rtlwifi: rtl8192cu: Fix unitialized struct
    - LP: #868628"

[https://launchpad.net/ubuntu/+source/linux/3.0.0-13.21](https://launchpad.net/ubuntu/+source/linux/3.0.0-13.21)

so I'm going to try that first

---

### Post by flipbrad on 2011-10-24
No, that didn't work - even with 3.1.0-030100rc10-generic (let alone the 3.0 kernel available from ubuntu-proposed.

```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 0
   id=0 ssid='house9'
   id=1 ssid='house9'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: 00:02:72:a1:80:78
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): e2 36 c7 66 27 08 5e ca 94 fc 37 cf b1 9e 2d bc
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=16
State: DISCONNECTED -> SCANNING
Scan SSID - hexdump_ascii(len=6):
     68 6f 75 73 65 39                                 house9          
Starting AP scan for specific SSID(s)
ioctl[SIOCSIWSCAN]: Device or resource busy
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
Setting scan request: 1 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 2477 bytes of scan results (5 BSSes)
BSS: Start scan result update 1
BSS: Add new id 0 BSSID 00:18:4d:1a:70:96 SSID 'house9'
BSS: Add new id 1 BSSID 00:1c:df:8c:20:17 SSID 'House11Yeah'
BSS: Add new id 2 BSSID 00:0f:b5:69:45:be SSID 'House8'
BSS: Add new id 3 BSSID c8:cd:72:ad:9d:1c SSID 'SKYD9D1B'
BSS: Add new id 4 BSSID 00:22:3f:96:10:2f SSID 'House10'
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:1a:70:96 ssid='house9'
Trying to associate with 00:18:4d:1a:70:96 (SSID='house9' freq=2462 MHz)
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP fail=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portControl=Auto
EAPOL: Supplicant port status: Unauthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=22
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=69
AssocResp IE wireless event - hexdump(len=53): 01 08 82 84 8b 0c 12 96 18 24 32 04 30 48 60 6c dd 18 00 50 f2 02 01 01 84 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 09 00 03 7f 01 01 00 00 ff 7f
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:18:4d:1a:70:96
Association info event
resp_ies - hexdump(len=53): 01 08 82 84 8b 0c 12 96 18 24 32 04 30 48 60 6c dd 18 00 50 f2 02 01 01 84 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 09 00 03 7f 01 01 00 00 ff 7f
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:18:4d:1a:70:96
No keys have been configured - skip key clearing
Associated with 00:18:4d:1a:70:96
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:18:4d:1a:70:96
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 5b b5 2f 69 4c b2 49 12 d3 61 d4 76 3d 42 e3 f9 5d c0 b1 b4 31 39 45 26 a8 e7 6d ac 5a b6 c4 cd
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:18:4d:1a:70:96 (ver=2)
RSN: msg 1/4 key data - hexdump(len=0):
WPA: Renewed SNonce - hexdump(len=32): 90 dc d7 5c 46 a7 ef 0e ba 4a 5c 95 f1 c9 15 9f 73 36 15 d0 45 2e ff 86 a3 3f 96 ae 3d cc 85 a0
WPA: PTK derivation - A1=00:02:72:a1:80:78 A2=00:18:4d:1a:70:96
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=48): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:18:4d:1a:70:96
IEEE 802.1X RX: version=1 type=3 length=199
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=104
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 5b b5 2f 69 4c b2 49 12 d3 61 d4 76 3d 42 e3 f9 5d c0 b1 b4 31 39 45 26 a8 e7 6d ac 5a b6 c4 cd
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 8d 41 e9 a1 05 ba 4e 6a e4 43 e2 bf a0 71 33 6d
RSN: encrypted key data - hexdump(len=104): b6 ac 01 eb dc 46 e5 5a d8 37 78 bc cd 06 b4 6e 82 2d 7c cb 66 95 ec da e3 da 11 ed ec c4 fd 33 81 b4 40 e1 0d f5 11 fe 56 16 bb a6 c2 f9 f0 82 2b be 0f ba 60 f4 bf 5b 3d f4 62 6d db 82 81 47 7c 5b af 2e 18 e1 8d f6 e0 d3 ec 3e 9b 2c 1b a1 ba b8 01 b0 04 ef 17 9e df f4 1c 99 45 16 f0 0d 64 49 1c 04 f4 98 76 80
WPA: decrypted EAPOL-Key key data - hexdump(len=96): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:1a:70:96 (ver=2)
WPA: IE KeyData - hexdump(len=96): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 dd 26 00 0f ac 01 02 00 7c dd a5 74 ad d5 82 20 99 3a b4 63 54 90 ba f1 d0 e4 ee bb 95 8d db ba bb 70 26 1d 37 91 3e fc dd 00
WPA: RSN IE in EAPOL-Key - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: WPA IE in EAPOL-Key - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02
WPA: GTK in EAPOL-Key - hexdump(len=40): [REMOVED]
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): [REMOVED]
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:18:4d:1a:70:96 [PTK=CCMP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:18:4d:1a:70:96 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
netlink: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: Supplicant port status: Authorized
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RX EAPOL from 00:18:4d:1a:70:96
IEEE 802.1X RX: version=1 type=3 length=143
  EAPOL-Key type=2
  key_info 0x1382 (ver=2 keyidx=0 rsvd=0 Group Ack MIC Secure Encr)
  key_length=32 key_data_length=48
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 5b b5 2f 69 4c b2 49 12 d3 61 d4 76 3d 42 e3 f9 5d c0 b1 b4 31 39 45 26 a8 e7 6d ac 5a b6 c4 ce
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): d5 24 bd f4 65 f6 bf bd 3d fc 40 bc 2f a8 84 12
RSN: encrypted key data - hexdump(len=48): 3b 67 95 bc 6d c0 5c 23 94 a1 67 c5 c7 02 33 9c 1d 78 e9 3a fd ae d8 95 1e 5d 60 57 8d da bf 1a 17 4d a9 75 66 02 2d de a1 42 cb 6a 16 ce f9 d5
WPA: decrypted EAPOL-Key key data - hexdump(len=40): [REMOVED]
WPA: RX message 1 of Group Key Handshake from 00:18:4d:1a:70:96 (ver=2)
RSN: msg 1/2 key data - hexdump(len=40): dd 26 00 0f ac 01 01 00 a7 90 d0 81 07 08 b6 95 f8 ff 07 ad 28 c7 f6 e0 db 60 c8 da 5a 7a 3c c2 b6 53 1d 74 58 7b ee 84
WPA: GTK in EAPOL-Key - hexdump(len=40): [REMOVED]
RSN: received GTK in group key handshake - hexdump(len=34): 01 00 a7 90 d0 81 07 08 b6 95 f8 ff 07 ad 28 c7 f6 e0 db 60 c8 da 5a 7a 3c c2 b6 53 1d 74 58 7b ee 84
State: COMPLETED -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: Group rekeying completed with 00:18:4d:1a:70:96 [GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=16
Received 453 bytes of scan results (1 BSSes)
BSS: Start scan result update 2
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:1a:70:96 ssid='house9' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:1a:70:96 ssid='house9'
Considering within-ESS reassociation
Current BSS: 00:18:4d:1a:70:96 level=212
Selected BSS: 00:18:4d:1a:70:96 level=212
Skip roam - too small difference in signal level
^CCTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
wpa_driver_wext_deauthenticate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
BSS: Remove id 1 BSSID 00:1c:df:8c:20:17 SSID 'House11Yeah'
BSS: Remove id 2 BSSID 00:0f:b5:69:45:be SSID 'House8'
BSS: Remove id 3 BSSID c8:cd:72:ad:9d:1c SSID 'SKYD9D1B'
BSS: Remove id 4 BSSID 00:22:3f:96:10:2f SSID 'House10'
BSS: Remove id 0 BSSID 00:18:4d:1a:70:96 SSID 'house9'
Cancelling scan request
Cancelling authentication timeout
netlink: Operstate: linkmode=0, operstate=6

```

tested on older kernel: 2.6.39-02063904-generic

---

### Post by praseodym on 2011-10-24
Strange, check your key: These letters, signs, etc. are allowed:

```
a-z A-Z 0-9 ! " # $ % & '( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~
```

---

### Post by flipbrad on 2011-10-24
It's only lower caps and numbers in the password, sorry.

---

### Post by praseodym on 2011-10-24
Add the following lines to your /etc/network/interfaces:

```
iface wlan0 inet dhcp
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0
```
save, close and:

```
sudo ifdown wlan0
sudo ifup wlan0
sudo /etc/init.d/networking restart
```
Check the connection and/or debug again.

---

### Post by Borunco on 2011-10-24
Hi, praseodym
just posting to give you an update from yesterday. After I worked on my problem, by the end of the day, I could hardly connect, so this morning I was going to do a clean install, and decided to do a upgrade with the dvd, instead 
. (The first upgrade had been done with the update manager)So after upgrading with the dvd, everything went perfect and I'm now posting from the new improved problem child.:wink:
I just want to thank you for sticking in their and trying to figure it out, you guy or gals? are AWESOME

---

### Post by praseodym on 2011-10-24
Guy ;-)

Glad its working now. This kernel module is (better) supported from kernel 3.1 and on, as I read somewhere else.

---

### Post by Borunco on 2011-10-24
BTW, I also did a clean install on an old dell inspiron 1000 laptop that I was running 11.04 on, and that install went perfect, so I think the problem may be in upgrading from update manager at this time.
Thanks again

---

### Post by flipbrad on 2011-10-24
Mine was a clean install. Still not getting any joy, even with a 3.1 kernel.

---

### Post by praseodym on 2011-10-24
@flipbrad: Did you try #88?

---

### Post by Borunco on 2011-10-24
I don't know if this has anything to do with the problem but just now, I checked for available drivers, and i got a nvidia up date when i activated, my wifi dropped, i deactivated it and my wifi came back on, I know in the past i've had problems with this.
Hang in their flipbrad

---

### Post by flipbrad on 2011-10-25
praseonym: yes I did; no luck. I can post the debug logs later.

Borunco: thanks for the kind words.

Update from Realtek support: 
"Dear Sir/Madam
 
Thanks for your e-mail.
Excuse me we expect the RTL8192CU Linux driver to support kernel 3.0 in next release. And expect to formal release by middle of November.
 
Best Regards,
Realtek Technical Support Dept."

EDIT: and they will have a beta driver release on their website before mid-November. Woohoo!!

---

### Post by lils001 on 2011-10-25
@ praseodym
> **praseodym said:**
> Reboot, plug in the stick and check:

```
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | egrep 'rtl|r8'
modinfo rtl8192cu
```
output:
```
lilly@lilly-E1500:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 17ef:6009 Lenovo ThinkPad Keyboard with TrackPoint
Bus 002 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
lilly@lilly-E1500:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sparse_keymap          13658  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  2 
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
psmouse                73673  0 
serio_raw              12990  0 
r8187se               157152  0 
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
eeprom_93cx6           12653  1 r8187se
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  4 
libahci                25727  1 ahci
r8169                  43104  0 
lilly@lilly-E1500:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lilly@lilly-E1500:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lilly@lilly-E1500:~$ sudo iwlist scan
[sudo] password for lilly: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:AE:0C:90
                    ESSID:"hoot"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=41/100  Signal level=-67 dBm  Noise level=-79 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 158ms ago
          Cell 02 - Address: 00:1E:8C:03:63:37
                    ESSID:"BigPond3EF0"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=94/100  Signal level=-30 dBm  Noise level=-116 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 75ms ago
          Cell 03 - Address: 00:0F:B5:B7:98:3E
                    ESSID:"SGC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality=44/100  Signal level=-65 dBm  Noise level=-81 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 80ms ago
          Cell 04 - Address: 00:1D:7E:B3:ED:3C
                    ESSID:"AWESOME-CHEESE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=42/100  Signal level=-66 dBm  Noise level=-80 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 65ms ago

wlan2     Scan completed :
          Cell 01 - Address: 00:1D:7E:B3:ED:3C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"AWESOME-CHEESE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050e0155580
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 000E415745534F4D452D434845455345
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 070A4E412001011B020C1400
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
          Cell 02 - Address: 00:1E:8C:03:63:37
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"BigPond3EF0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e91be3186
                    Extra: Last beacon: 124ms ago
                    IE: Unknown: 000B426967506F6E6433454630
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

lilly@lilly-E1500:~$ dmesg | egrep 'rtl|r8'
[    1.089247] [COLOR=Red]r8[/COLOR]169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.089272] [COLOR=Red]r8[/COLOR]169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.089321] [COLOR=Red]r8[/COLOR]169 0000:05:00.0: setting latency timer to 64
[    1.089397] [COLOR=Red]r8[/COLOR]169 0000:05:00.0: irq 43 for MSI/MSI-X
[    1.102819] [COLOR=Red]r8[/COLOR]169 0000:05:00.0: eth0: RTL8168d/8111d at 0xf802c000, 44:87:fc:1b:c5:93, XID 081000c0 IRQ 43
[   10.918490] [COLOR=Red]r8[/COLOR]187se: module is from the staging directory, the quality is unknown, you have been warned.
[   10.925940] [COLOR=Red]r8[/COLOR]180: Initializing module
[   10.925942] [COLOR=Red]r8[/COLOR]180: Wireless extensions version 22
[   10.925943] [COLOR=Red]r8[/COLOR]180: Initializing proc filesystem
[   10.925975] [COLOR=Red]r8[/COLOR]180: Configuring chip resources
[   10.925991] [COLOR=Red]r8[/COLOR]180 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.925999] [COLOR=Red]r8[/COLOR]180 0000:04:00.0: setting latency timer to 64
[   10.932018] [COLOR=Red]rtl[/COLOR]8180_init:Error channel plan! Set to default.
[   10.932021] [COLOR=Red]r8[/COLOR]180: Channel plan is 0
[   10.932028] [COLOR=Red]r8[/COLOR]180: MAC controller is a RTL8187SE b/g
[   10.934184] [COLOR=Red]r8[/COLOR]180: usValue is 0x100
[   10.977597] [COLOR=Red]r8[/COLOR]180: EEPROM version 104
[   10.981919] [COLOR=Red]r8[/COLOR]180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   10.990350] [COLOR=Red]r8[/COLOR]180: IRQ 17
[   10.996544] [COLOR=Red]r8[/COLOR]180: Driver probe completed
[   13.719598] [COLOR=Red]r8[/COLOR]180: Bringing up iface
[   13.918109] [COLOR=Red]r8[/COLOR]180: Card successfully reset
[   14.657457] [COLOR=Red]r8[/COLOR]180: WIRELESS_MODE_G
[   14.763730] [COLOR=Red]r8[/COLOR]169 0000:05:00.0: eth0: link down
[   14.763737] [COLOR=Red]r8[/COLOR]169 0000:05:00.0: eth0: link down
[   16.503512] [COLOR=Red]r8[/COLOR]169 0000:05:00.0: eth0: link up
[   81.227752] [COLOR=Red]rtl[/COLOR]8192cu: MAC address: 00:01:11:23:17:74
[   81.227758] [COLOR=Red]rtl[/COLOR]8192cu: Board Type 0
[   81.232196] [COLOR=Red]rtl[/COLOR]8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   81.241446] ieee80211 phy0: Selected rate control algorithm '[COLOR=Red]rtl[/COLOR]_rc'
[   81.242284] usbcore: registered new interface driver [COLOR=Red]rtl[/COLOR]8192cu
[   81.284817] Error: Driver '[COLOR=Red]rtl[/COLOR]8192cu' is already registered, aborting...
[   81.330754] [COLOR=Red]rtl[/COLOR]8192cu: MAC auto ON okay!
[   81.369878] [COLOR=Red]rtl[/COLOR]8192cu: Tx queue select: 0x05
[   81.370776] [COLOR=Red]rtl[/COLOR]8192c: Loading firmware file [COLOR=Red]rtl[/COLOR]wifi/[COLOR=Red]rtl[/COLOR]8192cufw.bin
lilly@lilly-E1500:~$ modinfo rtl8192cu
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     9550D79A3F9B707741FF904
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3359p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3358p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-12-generic SMP mod_unload modversions 686 
```
nb: I kept the dongle removed until I had signed into my account

---

### Post by praseodym on 2011-10-25
Are you trying to connect to a hidden network? Hiding NWs is not a security improvement, better broadcast the ESSID. Dou you try to connect to the same AP as the internal card wants to?

---

### Post by lils001 on 2011-10-25
> **praseodym said:**
> Are you trying to connect to a hidden network? Hiding NWs is not a security improvement, better broadcast the ESSID. Dou you try to connect to the same AP as the internal card wants to?

The network is not hidden. And strangely enough I'd never seen "hoot" listed in available networks previously. A lot of the available networks appear transiently. Mostly my network has the strongest signal.

---

### Post by praseodym on 2011-10-26
AFAIK this driver is updated in kernel 3.1. You may try this one as a mainline kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc8-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc8-oneiric/)

You need all three possible packages for 32 or 64 bit. Save them in "Downloads" and install them via:

```
sudo dpkg -i ~/Downloads/linux-*.deb
```
reboot and check as checked above.

---

### Post by flipbrad on 2011-10-26
thanks for the pointer. I already use a 3.1 kernel but not sure which. Why rc8, by the way, and not a more recent one, like rc10?

---

### Post by praseodym on 2011-10-26
Doesnt matter which one. You may need to reinstall a proprietary VGA driver again if in use

---

### Post by freaksterr6676 on 2011-10-27
[QUOTE=lils001;11390673]@ praseodym


[   81.242284] usbcore: registered new interface driver [COLOR=Red]rtl[/COLOR]8192cu
[   81.284817] Error: Driver '[COLOR=Red]rtl[/COLOR]8192cu' is already registered, aborting...

I had the same error message on several PCs, which means that multiple drivers are assigned to the one device.  I don't know why the newly compiled driver has a different filename.  I fixed the issue by adding the old driver to the blacklist in /etc/modprobe.d/blacklist.conf
i.e.
sudo echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf.

I guess you could also change the filename of the new driver and copy it to where the old one was (hacky), or modify the ModName and destination in the Makefile (less hacky).

---

### Post by praseodym on 2011-10-27
Check:

```
modinfo rtl8192cu | egrep 'versi|filen'
locate rtl8192cu.ko grep lib
```
You can rename/backup the "wrong" one.

---

### Post by mfpr on 2011-10-30
> **praseodym said:**
> @lils001: Yes, it was for you. There is a solution for the driver rtl8192cu:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip dkms
```_For 11.04:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
```_For 11.10:_
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
```_Installation:_
```
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```Reboot.

These are promising instructions - I was so hopeful, but - the last one failed.


~$ sudo dkms install -m rtl8192cu -v 3.1.2950
Error! Could not find module source directory.
Directory: /usr/src/rtl8192cu-3.1.2950 does not exist.

But this directory exists!!! Why can't it be found??

Can you help me?

---

### Post by praseodym on 2011-10-30
@mfpr: 11.04 or 11.10?

Edit: Download was 100 % successful? Remove the folder and try it again

---

### Post by flipbrad on 2011-10-30
this is the bug I'm experiencing:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/862684](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/862684)

still wondering what the invalid packets associated with this bug are...

I'm experiencing this with driver rtl8192cu version 3.1.0-030100rc10-generic. 

it says firmware=N/A under lshw for my wireless.

Is there a way of disabling 802.11n mode, since my router isn't capable of it?

---

### Post by mfpr on 2011-10-30
> **praseodym said:**
> @mfpr: 11.04 or 11.10?

Edit: Download was 100 % successful? Remove the folder and try it again

Hi there, you're really quick.

I'm running 11.10. The download was successful. 
Trying to remove the folder I got the following information:

manfred@manfred-SP35:/usr/src$ cd /rtl8192cu-3.1.2950
bash: cd: /rtl8192cu-3.1.2950: No such file or directory
manfred@manfred-SP35:/usr/src$ ls
linux-headers-3.0.0-12  linux-headers-3.0.0-12-generic  rtl8192cu-3.1.2590
manfred@manfred-SP35:/usr/src$ rm rtl8192cu-3.1.2590
rm: cannot remove `rtl8192cu-3.1.2590': Is a directory

Pretty misleading, isn't it? I'm not an experienced user so I'm rather helpless.
Thanks for answering

---

### Post by praseodym on 2011-10-30
```
sudo rm -r /usr/src/rtl8192cu-3.1.2590/
```

---

### Post by mfpr on 2011-10-30
> **praseodym said:**
> ```
sudo rm -r /usr/src/rtl8192cu-3.1.2590/
```


$ sudo rm -r /usr/src/rtl8192cu-3.1.2590/
[sudo] password for manfred: 
manfred@manfred-SP35:/usr/src$ ls
linux-headers-3.0.0-12  linux-headers-3.0.0-12-generic
manfred@manfred-SP35:/usr/src$ sudo dkms install -m rtl8192cu -v 3.1.2950
Error! Could not find module source directory.
Directory: /usr/src/rtl8192cu-3.1.2950 does not exist.


Didn't help either. I better give it up.

Thanks a lot nevertheless.

---

### Post by meajohan on 2011-11-02
i have tried everything in this thread and i cant get it to work, Is there any solution for 11.10 and kernel 3 or do we have to wait for new drivers ?

---

### Post by praseodym on 2011-11-02
Again:
```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz)
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
```

---

### Post by meajohan on 2011-11-02
> **praseodym said:**
> Again:
```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz)
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
```

after i have done this it says that the driver i activated but not in use. and i still get the password auth. popping up..

---

### Post by praseodym on 2011-11-02
Please show:

```
dmesg | grep rtl
ps aux | egrep 'Network|wicd'
```

---

### Post by meajohan on 2011-11-02
> **praseodym said:**
> Please show:

```
dmesg | grep rtl
ps aux | egrep 'Network|wicd'
```

johan@JohanAMD:~$ dmesg | grep rtl
[    8.808715] rtl8192cu: MAC address: 00:09:c9:19:b5:4e
[    8.808719] rtl8192cu: Board Type 0
[    9.038302] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    9.075154] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[    9.075526] usbcore: registered new interface driver rtl8192cu
[    9.179036] Error: Driver 'rtl8192cu' is already registered, aborting...
[   15.576701] rtl8192cu: MAC auto ON okay!
[   15.609448] rtl8192cu: Tx queue select: 0x05
[   15.610209] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
johan@JohanAMD:~$ 

johan@JohanAMD:~$ ps aux | egrep 'Network|wicd'
root       963  0.0  0.1  27916  4988 ?        Ssl  21:10   0:00 NetworkManager
root       997  0.0  0.0   2736  1188 ?        S    21:10   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-76390b93-731e-46f1-873c-442900633c7e-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
johan     2761  0.0  0.0   5684   792 pts/0    S+   21:26   0:00 egrep --color=auto Network|wicd
johan@JohanAMD:~$

---

### Post by chesaro on 2011-11-02
I'm actually having the exact same problem, since 11.04 (that's when i bought my wireless usb adapter XD) but the natty didn't support it, i downloaded the realtek driver and it just worked, sadly i have to reinstall it every time i turn on the pc, on 11.10 i was so happy it started imediately i plugged in, but it happened the same as you, i was really pissed, so, after a few months of struggle i found a not very good but efficient solution, i just installed the 10.04 version (lucid lynx) not only worked great, the driver works after restart, i just couldn't believe it, X( i really liked the 10.04 version, but changed it because of the software version, but untill that driver problem doesn't get fixed, i'll keep enjoying my fully functional wireless adapter.

Note: Sorry if it doesn't help at all, i just thing it's better to know all the choices we have

---

### Post by praseodym on 2011-11-03
@chesaro: So, you now use 11.04 or 11.10?

---

### Post by lils001 on 2011-11-06
> **praseodym said:**
> @chesaro: So, you now use 11.04 or 11.10?

as far as I read, neither builds from 2011 - 10.04 Lucid Linux

---

### Post by zxca on 2011-12-06
> **praseodym said:**
> Hi friends,

the Realtek drivers from their HP cannot be build so far with kernel 3.

So I recommend installing 11.04 in a Dualbootsystem or installing a mainline kernel version 2.6.38-8:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38.8-natty/")

or 2.6.39-4:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/")

Download _all three_ possible packages for 32 or 64bit, save them in Downloads and install it and the needed packages to compile via cable:

```
sudo dpkg -i ~/Downloads/linux-*.deb
sudo apt-get install build-essential dkms startupmanager
```The tool startupmanager can be used to set up kernel 2.6.38 or 2.6.39, respectively, as default boot kernel. Install the driver(s) with dkms:

**RTL8188CUS**
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
```**Driver r8712u _replaced_ by 8712u:**
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_dkms.tar.gz
sudo tar xvf rtl8712u-2.6.6.0.2_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8712u -v 2.6.6.0.2
sudo dkms build -m rtl8712u -v 2.6.6.0.2
sudo dkms install -m rtl8712u -v 2.6.6.0.2 
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```Puuuhh. For other questions, please show seperately:

```
lspci -nnk | grep -iA2 net
uname -a
lsusb
lsmod
iwconfig
```P.S.: I recommend copy/paste in your terminal (CTRL+ALT+T) ;-)


Is this also applicable for RTL8187. My connection is dropping off, and is asking for authentication again and again which is irritating. I have a thread here but no one replied to it. 

here's the link to my thread[http://ubuntuforums.org/showthread.php?t=1890606](http://ubuntuforums.org/showthread.php?t=1890606)

---

### Post by atconley on 2012-01-02
Hello all.  **Andrew** here from **post #3**.  I've now managed to solve my particular problem (with thanks to *Xavi López* and *heartsmagic* at [askubuntu.com]("http://ubuntuforums.org/askubuntu.com") for the post that caused me to understand what was happening; see [here]("http://askubuntu.com/questions/77314")).  Judging by the many posts on this thread, others have a variety of issues that appear to me to be different from my own.  Nonetheless, I will post what I did in case it is of use to someone else.  I hope it is.

**DESCRIPTION OF PROBLEM:**
- Ubuntu 11.10
- USB wireless 'mini'-dongle
- connects to network but no internet
- LED always on
[B]
SOLUTION:[/B]
- download most recent driver from [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772") then unzip/extract the ZIP file
- change the permissions of *install.sh* to allow execution of it as a program
```
chmod 775 install.sh
```- install the driver (when asked, select '1' for '8192cu')
```
sudo ./install.sh
```- open */etc/modprobe.d/blacklist.conf*
```
sudo gedit /etc/modprobe.d/blacklist.conf
```- blacklist the old module (which is included in the kernel) by adding the following line to that file:
```
blacklist rtl8192cu
```- open [I]/etc/modules
[/I]```
sudo gedit /etc/modules
```- add the new driver to the list of custom/additional modules that are loaded at boot by adding the following line to that file:
```
8192cu
```- restart your computer to prove that it works
- sit back and enjoy your internets :cool:

---

### Post by the8flux on 2012-01-09
thank god.  that last one did it.  Kudos!

---

### Post by vuade on 2012-03-31
#119 did it for me too - thanks you so much atconley

---

### Post by rajiv.personal on 2012-05-08
Thank you, atconley! #119 got my MicroNEXT MN-WD152B USB WiFi dongle working with Ubuntu 12.04!

---

### Post by poulou on 2012-05-08
try this ,it just worked fine on my computer.
Open a terminal then:


sudo iwconfig wlan0 power off
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

sudo apt-get update
sudo apt-get install linux-backports-modules-cw-3.3-3.2.0-24-generic
reboot, then
gksudo gedit /etc/NetworkManager/NetworkManager.conf
write a # before dns=dnsmasq  like this:#dns=dnsmasq
change managed=false
to
managed=true
save and quit
then
sudo service network-manager restart

---

### Post by vuade on 2012-12-30
Has anybody else been experiencing problems after updating to the 3.2.0-35 kernel?

For some reason, my D-link DWA-121 802.11n Wireless N 150 Pico Adapter [Realtek RTL8188CUS] uses rtl8192cu instead of 8192cu, even though rtl8192cu is blacklisted.

I read somewhere that when using 'blacklist' in /etc/modprobe/blacklist.conf the kernel might still load the module, so I even tried the "never use this module" method:

```
$ tail -3 /etc/modprobe.d/blacklist.conf 
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
```

but alas. Then also tried [this]("http://wiki.debian.org/KernelModuleBlacklisting") debian method, but still to no avail.

The strange thing is the rtl8192cu module that comes with this kernel allows me to connect for a couple of minutes, then all of a sudden I get the initial symptoms again.

I also tried to install the latest driver from REALTEK (v3.4.4_4749.20121105), but get kernel panic when it tries to remove the existing module (during rmmod of the install.sh script) and system hangs.

Does anybody have any advice?

Edit:
I believe I have figured out what causes the error condition to occur - I see it happen the moment I plug in another usb device like an ipod touch. Unplugging the network dongle also causes kernel panic. This never used to be the case with the 8192cu driver. Now to only figure out how to tell my system to use that driver (which is available via lsmod and modinfo 8192cu) instead of:

```
$ sudo lshw -C network | tail -8
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@2:5
       logical name: wlan1
       serial: 84:c9:b2:75:a1:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.0.2 multicast=yes wireless=IEEE 802.11bgn
```

---

