---
title: "Ubuntu 11.04 Natty: Wireless connects but no internet"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by chickendude on 2011-05-17
So I've been battling for a while to even get Ubuntu on my netbook (with no CD drive). I've finally gotten it installed, the only thing is that now internet (wifi) doesn't work. On the Live CD (USB) it connected fine and everything was perfect, but now it connects but I can't access the internet. I sort of hacked everything together so I'm sure I'm missing something, or several things...

The card is: Atheros AR2427

I also tried installing Wicd, but it doesn't seem to want to connect (it just tells me I've entered an invalid password). It could be because I think NetworkManger is still running... I don't know... help? Thanks!

---

### Post by Hippytaff on 2011-05-17
Try ```
killall nm-applet
``` to stop Network manager.
 
The wireless script in the link below will also be helpful. If it doesn't fix the problem it will output all the necessary information for people more knowlegable than me (Chilli555) to trouble shoot the probelm.

---

### Post by chili555 on 2011-05-17
> I sort of hacked everything together so I'm sure I'm missing something, or several things...I think my colleague Hippytaff will want to see:```
ifconfig
```When he sees a 10.43.42.xx IP address; he'll deduce that you 'Created New Wireless Network' that is, created an ad-hoc connection, not computer-to-router. Then you two will undo it and start fresh.

---

### Post by Hippytaff on 2011-05-17
wow - genious stuff
 
How canonical haven't head hunted you I have no idead ;)

---

### Post by chickendude on 2011-05-17
Ok, after killing NetworkManager I still couldn't connect with Wicd, and was about to post the results from the wireless script when I realized I hadn't restarted NM and figured it'd probably be better to run the script with NM connected, and now it appears that everything (for the moment) is working. Thanks for the help guys, I suppose I can mark this thread as solved now. Thanks again!

---

### Post by Hippytaff on 2011-05-17
Excellent - Glad it's sorted :)
 
It could be that the interfaces file was borked. If you come accross the same probelm again try removing the interfaces file /etc/network/interface

---

### Post by chili555 on 2011-05-17
> **Hippytaff said:**
> Excellent - Glad it's sorted :)
 
It could be that the interfaces file was borked. If you come accross the same probelm again try removing the interfaces file /etc/network/interface
I wouldn't remove it; the loopback stanza is required. You certainly could remove other lines like wlan0, etc., but leave the loopback intact, please.

---

### Post by Hippytaff on 2011-05-17
I stand corrected :)

---

### Post by chickendude on 2011-05-20
I don't know what happened, but yesterday everything went wrong. Now my Windows partition is completely inoperable (not a huge loss, but still...) and the internet is gone again. The only thing I can think of is that I uninstalled Wicd. I checked the /etc/network/interface file and it was empty. And the ifconfig command shows IP address: 192.168.1.34

I'll post the results from Hippytaff's script shortly in case any kind soul is willing to help me out :)

---

### Post by josephmills on 2011-05-20
> **Hippytaff said:**
> wow - genious stuff
 
How canonical haven't head hunted you I have no idead ;)

+1 I wonder the same

---

### Post by Knowsnothing on 2011-05-20
I posted this [http://ubuntuforums.org/showthread.php?t=1763100](http://ubuntuforums.org/showthread.php?t=1763100) awhile back.  It seems a little similar to this, but I'm not sure. :confused:

Basically, I connect to a wired or wireless network fine, but then can't access anything.  I can however connect via proxy.  I would really appreciate any help! :P

---

### Post by chickendude on 2011-05-20
Here're the results from the wireless script (it's rather long, sorry about that):
```

Version: 1.1 (Development)
vendredi 20 mai 2011, 10:07:43 (UTC+0200)

***********************************************************************************************
Running networking services
***********************************************************************************************
NetworkManager is running
************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

************************************
        Kernel
************************************

Linux crushUbuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
************************************
          List of drivers
************************************

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
i915                  450944  3 
ath9k                 103633  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
binfmt_misc            13213  1 
eeepc_wmi              18771  0 
sparse_keymap          13666  1 eeepc_wmi
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 ath9k
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
psmouse                73312  0 
drm                   180037  4 i915,drm_kms_helper
ath9k_common           13611  1 ath9k
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              300328  2 ath9k,ath9k_common
videodev               75143  1 uvcvideo
ath                    19141  2 ath9k,ath9k_hw
serio_raw              12990  0 
cfg80211              156212  3 ath9k,mac80211,ath
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 

************************************
        pci wireless devices
************************************

02:00.0 Network controller [0280]: Atheros Communications Inc. AR2427 Wireless Network Adapter (PCI-Express) [168c:002c] (rev 01)
	Subsystem: AzureWave Device [1a3b:1112]
	Kernel driver in use: ath9k
	Kernel modules: ath9k

************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network
       description: Wireless interface
       product: AR2427 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:08:76:43
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.34 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:3c:58:74
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.1.34 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7fc0000-f7ffffff ioport:ec00(size=128)


************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 20:cf:30:3c:58:74  
          inet adr:192.168.1.34  Bcast:192.168.1.255  Masque:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:44 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:399 erreurs:0 :0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:67749 (67.7 KB) Octets transmis:67749 (67.7 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:08:76:43  
          inet adr:192.168.1.34  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::76f0:6dff:fe08:7643/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:555 erreurs:0 :0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:40225 (40.2 KB) Octets transmis:16603 (16.6 KB)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WLAN_616C"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:23:F8:70:61:6D   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:76   Missed beacon:0

************************************
 Rfkill Blocks
************************************

0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

************************************

*************************************************************************
interfaces
*************************************************************************
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.34
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1

**************************************************************************
resolv.conf
**************************************************************************
# Generated by NetworkManager
domain Home
search Home
nameserver 192.168.1.1

**************************************************************************
Modules file
**************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp

*************************************************************************
Blacklist file
*************************************************************************
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

**************************************************************************
Files in folder /etc/modprobe.d/*
**************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf

***************************************************************************
NetworkManager.state
***************************************************************************

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

****************************************************************************
nm_applet_file
****************************************************************************
/etc/NetworkManager/nm-system-settings.conf does not exist

***************************************************************************
Route info
***************************************************************************
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

******************************************************************************
Using nm-tool
******************************************************************************

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unmanaged
  Default:           no
  HW Address:        20:CF:30:3C:58:74

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto WLAN_616C] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        74:F0:6D:08:76:43

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *WLAN_616C:      Infra, 00:23:F8:70:61:6D, Freq 2427 MHz, Rate 54 Mb/s, Strength 64 WPA
    cinesa:          Infra, 00:14:BF:72:E2:85, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WEP
    WLAN_78:         Infra, 00:23:F8:CE:B6:6D, Freq 2452 MHz, Rate 54 Mb/s, Strength 28 WEP
    WLAN_2805:       Infra, 00:1A:2B:89:C9:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



******************************************************************************
Using iwlist scan
******************************************************************************
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:F8:70:61:6D
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"WLAN_616C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015e2c17e41
                    Extra: Last beacon: 672ms ago
                    IE: Unknown: 0009574C414E5F36313643
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1A:2B:89:C9:59
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"WLAN_2805"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001039b3b8fcb
                    Extra: Last beacon: 832ms ago
                    IE: Unknown: 0009574C414E5F32383035
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F4010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B0001031047001032DFCD0F96F34230464C50C5667F07F71021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080000000000000000000000000000000000000000
          Cell 03 - Address: 00:14:BF:72:E2:85
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"cinesa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000142d1bd93d9
                    Extra: Last beacon: 388ms ago
                    IE: Unknown: 000663696E657361
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004


********************************************************************************
Checking connectivity
********************************************************************************
./wireless_script_1.2.sh: ligne 509: ((: 192.168.1.1 == 1  : erreur de syntaxe : opérateur arithmétique non valable (le symbole erroné est ".168.1.1 == 1 ")
ping: unknown iface 1
_unsucessfully_ pinged 192.168.1.1
Ping failure to router

******************************************************************************************
******************************************************************************************
Log file: /var/log/syslog
******************************************************************************************
******************************************************************************************

May 20 09:54:08 crushUbuntu NetworkManager[445]: <info> Scheduling stage 5
May 20 09:54:08 crushUbuntu NetworkManager[445]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
May 20 09:54:08 crushUbuntu NetworkManager[445]: <info> Done scheduling stage 5
May 20 09:54:08 crushUbuntu NetworkManager[445]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
May 20 09:54:08 crushUbuntu NetworkManager[445]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
May 20 09:54:08 crushUbuntu avahi-daemon[438]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.34.
May 20 09:54:08 crushUbuntu avahi-daemon[438]: New relevant interface wlan0.IPv4 for mDNS.
May 20 09:54:08 crushUbuntu avahi-daemon[438]: Registering new address record for 192.168.1.34 on wlan0.IPv4.
May 20 09:54:08 crushUbuntu kernel: [   89.139659] composite sync not supported
May 20 09:54:09 crushUbuntu NetworkManager[445]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
May 20 09:54:09 crushUbuntu NetworkManager[445]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 20 09:54:09 crushUbuntu NetworkManager[445]: <info> Policy set 'Auto WLAN_616C' (wlan0) as default for IPv4 routing and DNS.
May 20 09:54:09 crushUbuntu NetworkManager[445]: <info> Activation (wlan0) successful, device activated.
May 20 09:54:09 crushUbuntu NetworkManager[445]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
May 20 09:54:10 crushUbuntu avahi-daemon[438]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::76f0:6dff:fe08:7643.
May 20 09:54:10 crushUbuntu avahi-daemon[438]: New relevant interface wlan0.IPv6 for mDNS.
May 20 09:54:10 crushUbuntu avahi-daemon[438]: Registering new address record for fe80::76f0:6dff:fe08:7643 on wlan0.*.
May 20 09:54:18 crushUbuntu NetworkManager[445]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 20 09:54:18 crushUbuntu NetworkManager[445]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 20 09:54:19 crushUbuntu kernel: [   99.592041] wlan0: no IPv6 routers present
May 20 09:54:19 crushUbuntu NetworkManager[445]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 20 09:54:59 crushUbuntu ntpdate[1636]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
May 20 09:54:59 crushUbuntu ntpdate[1636]: no servers can be used, exiting
May 20 10:04:35 crushUbuntu kernel: [  715.558887] composite sync not supported
May 20 10:08:07 crushUbuntu NetworkManager[445]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 20 10:08:37 crushUbuntu ntfs-3g[1979]: Version 2010.8.8 external FUSE 28
May 20 10:08:37 crushUbuntu ntfs-3g[1979]: Mounted /dev/sda1 (Read-Write, label "", NTFS 3.1)
May 20 10:08:37 crushUbuntu ntfs-3g[1979]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
May 20 10:08:37 crushUbuntu ntfs-3g[1979]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096,default_permissions
May 20 10:08:37 crushUbuntu ntfs-3g[1979]: Global ownership and permissions enforced, configuration type 1
Cannot find log file /var/log/messages

******************************************************************************************
******************************************************************************************
Log file: /var/log/kern.log
******************************************************************************************
******************************************************************************************

May 20 09:54:02 crushUbuntu kernel: [   82.819843] composite sync not supported
May 20 09:54:03 crushUbuntu kernel: [   83.602976] composite sync not supported
May 20 09:54:05 crushUbuntu kernel: [   85.544147] usb 1-3: new high speed USB device using ehci_hcd and address 3
May 20 09:54:05 crushUbuntu kernel: [   85.730628] usbcore: registered new interface driver uas
May 20 09:54:05 crushUbuntu kernel: [   85.772483] Initializing USB Mass Storage driver...
May 20 09:54:05 crushUbuntu kernel: [   85.782340] scsi4 : usb-storage 1-3:1.0
May 20 09:54:05 crushUbuntu kernel: [   85.789442] usbcore: registered new interface driver usb-storage
May 20 09:54:05 crushUbuntu kernel: [   85.789452] USB Mass Storage support registered.
May 20 09:54:06 crushUbuntu kernel: [   86.845338] scsi 4:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
May 20 09:54:06 crushUbuntu kernel: [   86.846881] sd 4:0:0:0: Attached scsi generic sg1 type 0
May 20 09:54:07 crushUbuntu kernel: [   88.145034] sd 4:0:0:0: [sdb] 7806976 512-byte logical blocks: (3.99 GB/3.72 GiB)
May 20 09:54:07 crushUbuntu kernel: [   88.145639] sd 4:0:0:0: [sdb] Write Protect is off
May 20 09:54:07 crushUbuntu kernel: [   88.145652] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
May 20 09:54:07 crushUbuntu kernel: [   88.146812] sd 4:0:0:0: [sdb] No Caching mode page present
May 20 09:54:07 crushUbuntu kernel: [   88.146825] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 20 09:54:07 crushUbuntu kernel: [   88.153159] sd 4:0:0:0: [sdb] No Caching mode page present
May 20 09:54:07 crushUbuntu kernel: [   88.153173] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 20 09:54:07 crushUbuntu kernel: [   88.181172]  sdb: sdb1
May 20 09:54:07 crushUbuntu kernel: [   88.187294] sd 4:0:0:0: [sdb] No Caching mode page present
May 20 09:54:07 crushUbuntu kernel: [   88.187308] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 20 09:54:07 crushUbuntu kernel: [   88.187318] sd 4:0:0:0: [sdb] Attached SCSI removable disk
May 20 09:54:08 crushUbuntu kernel: [   88.568722] wlan0: authenticate with 00:23:f8:70:61:6d (try 1)
May 20 09:54:08 crushUbuntu kernel: [   88.588059] wlan0: authenticated
May 20 09:54:08 crushUbuntu kernel: [   88.588137] wlan0: associate with 00:23:f8:70:61:6d (try 1)
May 20 09:54:08 crushUbuntu kernel: [   88.591381] wlan0: RX AssocResp from 00:23:f8:70:61:6d (capab=0x411 status=0 aid=2)
May 20 09:54:08 crushUbuntu kernel: [   88.591392] wlan0: associated
May 20 09:54:08 crushUbuntu kernel: [   88.592256] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 20 09:54:08 crushUbuntu kernel: [   89.139659] composite sync not supported
May 20 09:54:19 crushUbuntu kernel: [   99.592041] wlan0: no IPv6 routers present
May 20 10:04:35 crushUbuntu kernel: [  715.558887] composite sync not supported

************************************
        pci wireless devices
************************************

02:00.0 Network controller [0280]: Atheros Communications Inc. AR2427 Wireless Network Adapter (PCI-Express) [168c:002c] (rev 01)
	Subsystem: AzureWave Device [1a3b:1112]
	Kernel driver in use: ath9k
	Kernel modules: ath9k

************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network
       description: Wireless interface
       product: AR2427 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:08:76:43
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.34 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:3c:58:74
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.1.34 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7fc0000-f7ffffff ioport:ec00(size=128)


************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 20:cf:30:3c:58:74  
          inet adr:192.168.1.34  Bcast:192.168.1.255  Masque:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:44 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:399 erreurs:0 :0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:67749 (67.7 KB) Octets transmis:67749 (67.7 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:08:76:43  
          inet adr:192.168.1.34  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::76f0:6dff:fe08:7643/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:601 erreurs:0 :0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:42641 (42.6 KB) Octets transmis:16603 (16.6 KB)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WLAN_616C"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:23:F8:70:61:6D   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:76   Missed beacon:0

************************************
 Rfkill Blocks
************************************

0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

************************************
Finished <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

http://wireless.kernel.org/en/users/Drivers

```

---

### Post by chili555 on 2011-05-20
> ifconfig command shows IP address: 192.168.1.34
Now you should be connected to the internet. Please try:```
ping -c3 www.google.com
```Can you reach web pages in Firefox?

---

### Post by chickendude on 2011-05-20
Nope. It says it is searching for the host and after a few minutes times out. I've tried in Firefox and using other applications, such as the chat app. It shows that I'm connected, though. Also, I don't know if this is important, but never before did it connect so quickly to wireless. It takes less than a second for the "Wireless connection established" thing to pop up, in previous versions it took at least fifteen or so seconds... Do you think it might be a permissions thing?

I'll post the ping results after rebooting, right now I'm back on my Windows partition.

---

### Post by chili555 on 2011-05-20
I just noticed this and had to stop to take a tranquilizer. What explains this???> [COLOR="Red"]eth0 [/COLOR]     Link encap:Ethernet  HWaddr 20:cf:30:3c:58:74  
          inet adr:[COLOR="Red"]192.168.1.34[/COLOR]  Bcast:192.168.1.255  Masque:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:44 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:399 erreurs:0 :0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:67749 (67.7 KB) Octets transmis:67749 (67.7 KB)

[COLOR="Red"]wlan0[/COLOR]     Link encap:Ethernet  HWaddr 74:f0:6d:08:76:43  
          inet adr:[COLOR="Red"]192.168.1.34[/COLOR]  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::76f0:6dff:fe08:7643/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:555 erreurs:0 :0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:40225 (40.2 KB) Octets transmis:16603 (16.6 KB)
Please detach the ethernet cable and reboot and let us see:```
ifconfig
```Thanks.

I feel better now...

---

### Post by chickendude on 2011-05-21
There isn't any ethernet cable plugged in, just the power cord...

And here are the results:
```
crush@crushUbuntu:~$ ping -c3 www.google.com
ping: unknown host www.google.com
```
```
crush@crushUbuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:3c:58:74  
          inet adr:192.168.1.34  Bcast:192.168.1.255  Masque:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:44 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:384 erreurs:0 :0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:62254 (62.2 KB) Octets transmis:62254 (62.2 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:08:76:43  
          inet adr:192.168.1.33  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::76f0:6dff:fe08:7643/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:16 erreurs:0 :0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2107 (2.1 KB) Octets transmis:15095 (15.0 KB)


```

---

### Post by chili555 on 2011-05-21
If you are not actually connected, I wonder where these addresses are coming from. Did you fill in settings in Network Manager? May we see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by chickendude on 2011-05-21
Here's the interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.34
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
```

Thanks for getting back so quick! Is it something to do with the eth0 interface being static?

---

### Post by chili555 on 2011-05-22
Your wireless till looks like it's connected. Let's see:```
cat /etc/resolv.conf
ping -c3 192.168.1.1
ping -c3 74.125.47.99
```Thanks.

---

### Post by chickendude on 2011-05-22
Here're the new commands:
```
crush@crushUbuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain Home
search Home
nameserver 192.168.1.1
```
```
crush@crushUbuntu:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.34 icmp_seq=1 Destination Host Unreachable
From 192.168.1.34 icmp_seq=2 Destination Host Unreachable
From 192.168.1.34 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3
```
```
crush@crushUbuntu:~$ ping -c3 74.125.47.99
PING 74.125.47.99 (74.125.47.99) 56(84) bytes of data.
64 bytes from 74.125.47.99: icmp_req=1 ttl=47 time=1158 ms
64 bytes from 74.125.47.99: icmp_req=2 ttl=44 time=175 ms
64 bytes from 74.125.47.99: icmp_req=3 ttl=44 time=169 ms

--- 74.125.47.99 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 169.532/501.141/1158.247/464.650 ms, pipe 2
```
What is the second address?

---

### Post by chili555 on 2011-05-22
The second address is Google. Please do:```
sudo gedit /etc/resolv.conf
```Amend the file to:```
# Generated by NetworkManager
#domain Home
#search Home
nameserver 192.168.1.1
```Proofread, save and close. Also, please post:```
route -n
```We're getting close.

---

### Post by chickendude on 2011-05-22
Thanks, I've edited the file and here's the output of that command:```
crush@crushUbuntu:~$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0


```

---

### Post by chili555 on 2011-05-22
So let's try again:```
ping -c3 www.google.com
ping -c3 192.168.1.1
```Thanks.

---

### Post by chickendude on 2011-05-23
Here're the new commands:
```
crush@crushUbuntu:~$ ping -c3 www.google.com
ping: unknown host www.google.com

crush@crushUbuntu:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.34 icmp_seq=1 Destination Host Unreachable
From 192.168.1.34 icmp_seq=2 Destination Host Unreachable
From 192.168.1.34 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms
pipe 2
```Also, I tried typing in google's IP address and the page loaded just fine.

---

### Post by chili555 on 2011-05-23
As the man once said, "Madness, simply madness."

This suggests that 192.168.1.1 is not the correct address for the router. Are there other computers successfully connected? Is the gateway 192.168.1.1? What are the DNS nameservers?

---

### Post by chickendude on 2011-05-23
I'm connected to the same network right now on my Windows partition.

Here's what I can find from the properties pages:
IPv4 Address: 192.168.1.33
Default Gateway: 192.168.1.1
DHCP Server IPv4: 192.168.1.1
DNS Server IPv$4: 192.168.1.1

Is there anything else you'd like to see? Thanks a lot by the way for trying to get everything sorted out.

---

### Post by chili555 on 2011-05-23
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.34
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1Would you please amend this file to:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.34
	netmask 255.255.255.0
	#network 192.168.1.0
	#broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	#dns-nameservers 192.168.1.1
```Immediately reboot so we restart networking, Network Manager, the wireless driver and everything in sight! Then click the NM icon and do you see your network? Click it to connect.

Where does the address come from? DHCP assigned from the router or have you somehow configured these details, possibly in NM?

---

### Post by chickendude on 2011-05-23
I've updated the file with no success. I did however try "sudo ifdown eth0" and am currently writing you from my Ubuntu partition... :)

As far as the configuration, the only thing I can think of is that while trying to debug why it wasn't working I checked the interfaces file, which was empty. I added the loopback network interface bit and left the rest of the file blank. Apart from that, I just clicked on the network, typed in the password, and that's it. I can't think of anything else I may have done.

---

### Post by chickendude on 2011-05-26
Is there anything else I could try? At the moment every time I boot up I need to open up a terminal and type "sudo ifdown eth0" to access the internet. What is wrong with the eth0 interface (if that's what it's called)?

Thanks!

---

### Post by chili555 on 2011-05-26
> What is wrong with the eth0 interface (if that's what it's called)?I don't think anything at all is wrong with it. You have told Network Manager *NOT* to manage your wired ethernet by placing its configuration in /etc/network/interfaces; as well, you have directed that it start automatically:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="Red"]**auto eth0**[/COLOR]
iface eth0 inet static
	address 192.168.1.34
	netmask 255.255.255.0
	#network 192.168.1.0
	#broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	#dns-nameservers 192.168.1.1
```If that's not what you want, simply comment out the *auto* bits:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="Red"]#[/COLOR]auto eth0
iface eth0 inet static
	address 192.168.1.34
	netmask 255.255.255.0
	#network 192.168.1.0
	#broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	#dns-nameservers 192.168.1.1
```

---

### Post by chickendude on 2011-05-26
And if I plug in an ethernet cable will it automatically pick it up? I've commented it out and see if that takes care of things for good. Thanks!

---

### Post by chili555 on 2011-05-26
> And if I plug in an ethernet cable will it automatically pick it up?Probably not. You can't have it both ways; both automatic and not automatic. You will probably need to do:```
sudo ifup eth0
```

---

### Post by alaaji on 2011-05-27
Could someone help me out in here.  You seem very knowledgeable.  My router shows that it's available but when I click on it to connect, nothing ever happens.  I don't have the opportunity to enter in the password or anything.

I tried creating a new wireless network but that doesn't work either.  Is there something that I'm missing?  Please help.

---

### Post by chili555 on 2011-05-27
> **alaaji said:**
> Could someone help me out in here.  You seem very knowledgeable.  My router shows that it's available but when I click on it to connect, nothing ever happens.  I don't have the opportunity to enter in the password or anything.

I tried creating a new wireless network but that doesn't work either.  Is there something that I'm missing?  Please help.Please start your own new thread and include:```
ifconfig
route -n
```Send me a private message if I don't catch it right away.

---

