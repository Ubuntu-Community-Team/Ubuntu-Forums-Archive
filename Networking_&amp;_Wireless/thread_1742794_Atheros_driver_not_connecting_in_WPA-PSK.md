---
title: "Atheros driver not connecting in WPA-PSK"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by n3140f on 2011-04-29
I am a linux novice.  I have been using Ubuntu since version 6.10, usually in a dual boot situation with various hand me down machines with XP.  

Now I have a HP Pavillion dm3 1030us.

I had Win7 until I made a mistake in gparted and had no backup and no install disk.

I am trying to connect to a Linksys WRT54G2.  It worked great before, but with this Ubuntu install, having no Windows on it, I think I may have a driver problem.

I had to zero wipe the drive and this is the very first time I have not been able to connect.

My Ubuntu experience was so good I was lazy and have not learned the terminal and bash shell as I should have.

I know that this machine has the AR 5009 adapter on the PCIe.

I tried ndiswrapper and did not succeed.

I did everything suggested in this thread:  [http://ubuntuforums.org/showpost.php...46&postcount=5](http://ubuntuforums.org/showpost.php...46&postcount=5)

This one also:  [http://ubuntuforums.org/showthread.php?t=1484242&highlight=atheros](http://ubuntuforums.org/showthread.php?t=1484242&highlight=atheros)

Here is the output from iwconfig:  lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:13 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:101888  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here is the output of lsmod:  Module                  Size  Used by
rfcomm                 32575  4 
binfmt_misc             6599  1 
sco                     7867  2 
bnep                    9305  2 
l2cap                  38677  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
ndiswrapper           184207  0 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_idt      54951  1 
uvcvideo               55879  0 
fglrx                2252513  257 
btusb                  10969  2 
wlan_scan_sta          12012  1 
ath_rate_sample        11424  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
joydev                  8767  0 
snd_timer              19067  2 snd_pcm,snd_seq
hp_wmi                  5223  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ath_pci               179564  0 
bluetooth              53007  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                59033  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               13204  0 
agpgart                32011  1 fglrx
serio_raw               4022  0 
i2c_piix4               8635  0 
soundcore                880  1 snd
lis3lv02d               8556  1 hp_accel
input_polldev           3491  1 lis3lv02d
video                  18712  0 
k8temp                  3228  0 
led_class               2633  1 hp_accel
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
wlan                  220184  4 wlan_scan_sta,ath_rate_sample,ath_pci
shpchp                 29886  0 
output                  1883  1 video
ath_hal               396940  3 ath_rate_sample,ath_pci
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40492  0 
ahci                   19326  2 
r8169                  36553  0 
mii                     4425  1 r8169
libahci                21728  1 ahci


Now I have lost the way and don't know how to attack the problem.  I just don't know enough about networks to solve this.

Here is the output of lspci:  00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
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


here is the output of sudo modprobe ath9k:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Here is the output of ifconfig:  

ath0      Link encap:Ethernet  HWaddr 00:22:5f:ee:e7:16  
          inet6 addr: fe80::222:5fff:feee:e716/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21600 (21.6 KB)  TX bytes:10800 (10.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:21:cc:3f:73:9f  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe3f:739f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5549090 (5.5 MB)  TX bytes:763977 (763.9 KB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3760 (3.7 KB)  TX bytes:3760 (3.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-22-5F-EE-E7-16-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172288 errors:0 dropped:0 overruns:0 frame:4150
          TX packets:5928 errors:71 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:25104565 (25.1 MB)  TX bytes:466340 (466.3 KB)
          Interrupt:17 

I know for sure that the hardware is a Atheros 5009, but now I may have a wrong driver in there and was not able to use ndisgtk or madwifi to fix it.  I do have the 5009 driver.

Can one of you help me with this?  

Thank you in advance,


n3140f

---

