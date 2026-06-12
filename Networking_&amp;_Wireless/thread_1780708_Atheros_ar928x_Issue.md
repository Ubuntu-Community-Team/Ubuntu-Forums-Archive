---
title: "Atheros ar928x Issue"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by dyserenity on 2011-06-12
Hi--

Here's my general information: 

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

 lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 058f:3831 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:cc:3f:7b:2c  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe3f:7b2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:833175 (833.1 KB)  TX bytes:184505 (184.5 KB)
          Interrupt:26 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lsmod | grep "ath9k"
ath9k                  67819  0 
ath9k_common            2551  1 ath9k
mac80211              225459  2 ath9k,ath9k_common
ath9k_hw              223661  2 ath9k,ath9k_common
ath                     8041  2 ath9k,ath9k_hw
cfg80211              144266  4 ath9k,ath9k_common,mac80211,ath
led_class               2864  2 ath9k,hp_accel




I'm running 10.04 on 2.6.32-32-generic i686. I have an HP laptop with an Atheros AR928x wireless card, which needs the ath9k driver to run. I installed it via 
sudo apt-get install linux-backports-modules-wireless-lucid-generic

which installs with no errors. Rfkill say my hardware and software aren't talking to each other correctly:

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Toggling the hardware switch does nothing.

Modinfo gives me: 

modinfo ath9k
filename:       /lib/modules/2.6.32-32-generic/updates/compat-wireless-2.6.34/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9AB4886D47AE2784A3C51B7
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,led-class,ath,cfg80211,ath9k_common
vermagic:       2.6.32-32-generic SMP mod_unload modversions 586 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)

I tried installing compat-wireless, but that gave me fatal errors when I tried to run modprobe to actvate ath9k. Enable wireless in the menu bar is grayed out and unchecked. How on Earth do I get my wireless running?

Thanks!

---

### Post by josephmills on 2011-06-12
I might not be able to help n00b myself but could we please see a ```
lsmod 
``` and a ```
lspci -nn | grep Ath
``` thanks

---

### Post by dyserenity on 2011-06-12
Here you go:

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
arc4                    1153  2 
snd_hda_codec_idt      52042  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ath9k                  76634  0 
mac80211              258840  1 ath9k
snd_seq_oss            26722  0 
ath9k_common            2443  1 ath9k
snd_seq_midi            4557  0 
radeon                677684  3 
snd_rawmidi            19056  1 snd_seq_midi
ath9k_hw              285368  2 ath9k,ath9k_common
ttm                    49943  1 radeon
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ath                    14268  2 ath9k,ath9k_hw
drm_kms_helper         29329  1 radeon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211              162408  3 ath9k,mac80211,ath
joydev                  8740  0 
drm                   162377  5 radeon,ttm,drm_kms_helper
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57374  0 
hp_accel               11144  0 
compat                 19251  3 ath9k,mac80211,cfg80211
video                  17375  0 
output                  1871  1 video
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 radeon
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
pcmcia_core            32964  1 compat
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  3 ath9k,hp_accel,compat
k8temp                  3152  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 


lspci -nn | grep Ath
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)


I uninstalled the generic package completely and installed compat in the meantime. I still have the exact same problem.

---

### Post by josephmills on 2011-06-12
are you trying to connect to wep or wpa/wpa2 ? take down the security for a second then see if it connects.

---

### Post by josephmills on 2011-06-12
could we also see a ```
dmesg | grep ath9k
``` thanks

---

### Post by dyserenity on 2011-06-12
Under wireless networks, it says "wireless is disabled". When I right click, enable wireless is grayed out. 

dmesg | grep ath9k
[    9.888662] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.888675] ath9k 0000:08:00.0: setting latency timer to 64
[   10.398611] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.399586] Registered led device: ath9k-phy0

---

### Post by josephmills on 2011-06-12
> **dyserenity said:**
> Under wireless networks, it says "wireless is disabled". When I right click, enable wireless is grayed out. 

dmesg | grep ath9k
[    9.888662] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.888675] ath9k 0000:08:00.0: setting latency timer to 64
[   10.398611] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.399586] Registered led device: ath9k-phy0

thanks how about ```
sudo iwlist scan
``` and ```
dmesg | grep rfkill 
```

---

### Post by dyserenity on 2011-06-12
sudo iwlist scan returns:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

...And "dmesg | grep rfkill" has no apparent effect.

---

### Post by josephmills on 2011-06-12
what is the make and model of this computer?

---

### Post by dyserenity on 2011-06-12
HP Pavillion DM3

---

### Post by josephmills on 2011-06-12
IDK if you have this in your bios but while I am looking at the specs could you check your bios and make sure that it is on (wireless )in there also thanks Also do you swear to me that you have turned on #4 in pic

---

### Post by dyserenity on 2011-06-12
There's no apparent change when I press #4 - the light doesn't even change colors. No change in rfkill either.

---

### Post by josephmills on 2011-06-12
> **dyserenity said:**
> There's no apparent change when I press #4 - the light doesn't even change colors. No change in rfkill either.

nothing in the bios either?

---

### Post by dyserenity on 2011-06-12
Nothing regarding my wireless cards. 

Does Linux just... not work with my wireless card? Because I still haven't found a fix for this after six nights of screwing with it, and I kinda need wireless.

---

### Post by josephmills on 2011-06-12
> **dyserenity said:**
> Nothing regarding my wireless cards. 

Does Linux just... not work with my wireless card? Because I still haven't found a fix for this after six nights of screwing with it, and I kinda need wireless.

lets see if it is network managers fault go to ubuntu software center and download wicd then uninstall network manager then reboot anything?

---

### Post by dyserenity on 2011-06-12
I installed wicd, but how do I uninstall the network manager? From Synaptic Package Manager?

---

### Post by dyserenity on 2011-06-12
Okay, I got that removed and am now running the other one. It isn't finding any wireless networks.

---

### Post by josephmills on 2011-06-12
> **dyserenity said:**
> I installed wicd, but how do I uninstall the network manager? From Synaptic Package Manager?

yes or from ubuntu software center

---

### Post by josephmills on 2011-06-12
```
/etc/init.d/networking start
``` anything? is ```
rfkill list all 
``` still the same when you play with the switch?

---

### Post by MeOfCourse on 2011-06-13
1) This is Dyserenity's boyfriend, she was troubleshooting for me. COOLEST GIRLFRIEND EVER. 

2) That network manager thing apparently did something - the option to activate wireless networks is no longer grayed out, and I now have a "Connect" option - however, no wireless networks are actually being detected, and I'm sitting four feet from an operating router.

3) The commands you wanted:

"rfkill list all" gives:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

...while "/etc/init.d/networking start" gives:

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.71" (uid=1000 pid=6624 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

...so, taking the computer's apparently questionable advice, I put in "service networking start" and got:

start: Rejected send message, 1 matched rules; type="method_call", sender=":1.72" (uid=1000 pid=6645 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

...which I assume is not what we wanted, as I still have no wireless. Any advice would be beyond helpful.

---

### Post by MeOfCourse on 2011-06-13
Some forward progress. I used the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

... Under "Methods Using Madwifi and ath_pci" - I can now SEE the wireless networks, but when I try to connect to one, I get "Connection Failed: Unable to Get IP Address."

Different error message = progress.

EDIT:

Actually, I forgot I had Dyserenity's D-Link USB card in - it still doesn't work on my native card. On the other hand, I'm wondering if the inability to connect is because I don't have a password for the network - connecting from the desktop doesn't work, but when I actually go into WICD, it asks for a password. I'm taking it back to my place to try on my home network.

---

### Post by Cloud2 on 2011-07-11
hello i had the same problem on my hp g60 with AR928x card but i was running 11.04 the way i fixed it was by running 

rfkill unblock all


after that all worked just fine
thanks and i hope this helps

---

