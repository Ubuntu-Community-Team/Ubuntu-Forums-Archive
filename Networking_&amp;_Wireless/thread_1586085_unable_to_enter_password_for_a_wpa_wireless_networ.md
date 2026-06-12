---
title: "unable to enter password for a wpa wireless network using 3945abg wireless adapter"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by skygenie on 2010-10-01
I'm trying to connect to a wireless network that uses WPA personal encryption but when I select the network, the pop-up window that asks for the encryption key does not offer WPA as an option in the drop-down menu.  I have tried editing the the connection under Network Connections / Wireless (select WPA personal and enter in password) but then when I go to connect, the pop-up window still does not offer WPA as a choice.  I have connected to WPA encrypted networks before and other networks in range also offer the WPA option but I don't have the password.  The wireless router belongs to my landlord so I don't have access to it but I could talk to her about making changes there if needed.

What can I do so I can enter in a WPA password for the network?  Thanks in advance.

Below are the outputs for the points from the sticky note.


1 ) Machine Brand and Model (PC/Laptop):
Code:

Toshiba Satellite A100

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

3 ) check interface:
Code:
$ ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:13:02:84:a0:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
4 ) Check for modules:
Code:
Not sure what I'm looking for, here, so this is the entire output.
$ lsmod

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
nls_utf8                1069  1 
isofs                  29250  1 
usb_storage            39553  2 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203374  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
pcmcia                 30784  0 
arc4                    1153  2 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121664  0 
iwl3945                68727  0 
i915                  286079  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               106050  1 iwl3945
yenta_socket           20408  1 
tifm_7xx1               3690  0 
drm_kms_helper         29297  1 i915
ath                     7611  1 ath5k
mac80211              205402  3 ath5k,iwl3945,iwlcore
sdhci_pci               5470  0 
rsrc_nonstatic         10015  1 yenta_socket
sdhci                  15462  1 sdhci_pci
snd                    54148  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core               6045  1 tifm_7xx1
drm                   162409  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
led_class               2864  4 ath5k,iwl3945,iwlcore,sdhci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24119  2 i915
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126496  5 ath5k,iwl3945,iwlcore,ath,mac80211
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7060  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
e100                   28211  0 
mii                     4381  1 e100
ieee1394               81181  1 ohci1394

5 ) Kernel boot messages

Again, I don't know what I'm looking for or what to put after grep.  This one is very long so I won't put it in now but if you want it or can tell me how to get the specific info, I'll put it up.
Code:
$ dmesg
(hint) the same as in (4)

6 ) Network configuration
Code:
$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:84:a0:c1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:da000000-da000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:47:52:0d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:dc005000-dc005fff ioport:4000(size=64)

7 ) Scan for networks:

I am trying to connect to huttonm (at the end of the list).

Code:
$ iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 9A:84:0D:E0:B0:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Jacques Meoff's Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008403e92160
                    Extra: Last beacon: 13152ms ago
                    IE: Unknown: 001D4A616371756573204D656F66662773204775657374204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C4017FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
                    IE: Unknown: DD1700039301720008000E90840DE0B0810190840DE0B08295
          Cell 02 - Address: 00:18:D1:86:26:1F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"huttonm"

8 ) Ubuntu Version: 
Code:
$ lsb_release -d

Description:	Ubuntu 10.04.1 LTS

9 ) Kernel/architecture (including 32 vs. 64 bit): 
Code:
$ uname -mr

2.6.32-25-generic i686

10 ) Restarting the network:
Code:
$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by chili555 on 2010-10-01
> Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=41/70 Signal level=-69 dBm
Encryption keyn
ESSID:"huttonm"I believe huttonm is WEP protected, not WPA. Here is what my neighbor's WEP network looks like when I scan:> Cell 02 - Address: 00:xx:xx:xx:C8:5C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:MasterHere is my WPA network:> Cell 01 - Address: 00:24:56:2A:D7:29
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"mylilrouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : [COLOR="Red"]PSK[/COLOR]I believe that if it doesn't say WPA, then it isn't WPA.

I don't undertsand this:> ath5k 121664 0
iwl3945 68727 0
[COLOR="Red"]ath[/COLOR] 7611 1 [COLOR="Red"]ath5k[/COLOR]
mac80211 205402 3 [COLOR="Red"]ath5k[/COLOR],iwl3945,iwlcoreDo you also have an Atheros wireless card connected?

---

### Post by skygenie on 2010-10-05
Thanks for your reply chili.

I guess the problem is that Ubuntu thinks that huttonm has WEP encryption but I know that it is WPA.  I have another computer with Windows and my girlfriend has a Mac.  For both of them, they connect with a WPA password.  As well, I have tried entering the password under WEP numerous times but it always comes back asking for the password (encryption key).

I do have an external USB wireless adapter that I use on occasion but wasn't connected when I did the scan.  Could that explain the part you don't understand?  I have tried to connect to huttonm through the USB adapter but had the same problem.

---

