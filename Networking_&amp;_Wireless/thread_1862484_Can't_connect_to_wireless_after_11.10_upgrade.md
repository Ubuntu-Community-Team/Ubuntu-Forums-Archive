---
title: "Can't connect to wireless after 11.10 upgrade"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by ajcjh on 2011-10-16
11.10 upgrade - can see networks but connection times out
I using an ASUS-U56E netbook. I just upgraded then installed 11.10 and the wireless stopped connecting. I can see all the networks but when I try to connect it just times out. Here is some basic information to start.


Centrino Wireless-N + WiMAX 6150 (Rev 67) -iwlagn driver

#iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=15 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on

#rfkill list all

0: asus-wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: asus-wimax: WiMAX
Soft blocked: no
Hard blocked: no
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

#lsmod
Module Size Used by
parport_pc 36962 0
ppdev 17113 0
bnep 18436 2
rfcomm 47946 0
bluetooth 166112 10 bnep,rfcomm
snd_hda_codec_hdmi 32040 1
snd_hda_codec_realtek 330769 1
binfmt_misc 17540 1
joydev 17693 0
arc4 12529 2
snd_hda_intel 33390 2
snd_hda_codec 104802 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel
snd_hwdep 13668 1 snd_hda_codec
snd_pcm 96755 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13324 0
snd_rawmidi 30547 1 snd_seq_midi
snd_seq_midi_event 14899 1 snd_seq_midi
snd_seq 61896 2 snd_seq_midi,snd_seq_midi_event
snd_timer 29991 2 snd_pcm,snd_seq
snd_seq_device 14540 3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo 72711 0
videodev 93004 1 uvcvideo
v4l2_compat_ioctl32 17083 1 videodev
asus_nb_wmi 12517 0
asus_wmi 20035 1 asus_nb_wmi
sparse_keymap 13890 1 asus_wmi
snd 68266 14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,s nd_seq,snd_timer,snd_seq_device
wmi 19256 1 asus_wmi
iwlagn 314213 0
mac80211 310872 1 iwlagn
i915 566711 3
cfg80211 199587 2 iwlagn,mac80211
drm_kms_helper 42558 1 i915
psmouse 73882 0
drm 236330 4 i915,drm_kms_helper
serio_raw 13166 0
soundcore 12680 1 snd
snd_page_alloc 18529 2 snd_hda_intel,snd_pcm
lp 17799 0
i2c_algo_bit 13423 1 i915
mei 41480 0
video 19412 1 i915
parport 46562 3 parport_pc,ppdev,lp
xhci_hcd 78641 0
ahci 26002 2
libahci 26861 1 ahci
atl1c 41643 0

#lshw -C network
*-network
description: Wireless interface
product: Centrino Wireless-N + WiMAX 6150
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 67
serial: 40:25:c2:52:02:f0
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:50 memory:de800000-de801fff
*-network
description: Ethernet interface
product: AR8151 v2.0 Gigabit Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: c0
serial: 14:da:e9:4f:2a:51
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128)

---

### Post by garvinrick4 on 2011-10-16
> wlan0 IEEE [COLOR=Red]802.11bg[/COLOR]Do you still have a config file to remove "N" from card.
gksudo gedit /etc/modprobe.d/iwlagn.conf

Comment the one line out "#" sign in front of line. (without quotes)
and reboot will put "N" back in card functions. 
3.0 and up works with iwlagn driver by intel in N.

Do not know if that will fix your problem but should fix the config file anyway.

---

### Post by wildmanne39 on 2011-10-16
Hi garvinrick4, is this what you are talking about?
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```

To the client please try this code one line at a time and if it works we will need to make it permanent.
Thank you

---

### Post by garvinrick4 on 2011-10-16
> **wildmanne39 said:**
> Hi garvinrick4, is this what you are talking about?
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig iwlagn up
```To the client please try this code one line at a time and if it works we will need to make it permanent.
Thank you
I believe he has a the N disabled and does not need to be with "iwlagn" driver with
kernel 3.0 and up. 
Going around for a while was to just make a config file and place the line
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman][SIZE=3]In the config file /etc/modprobe.d/iwlagn.conf that user made.[/SIZE][/FONT][/COLOR] (I noticed the his card said 802.11 bg) And it is an N card. 


[COLOR=#000000][FONT=Times New Roman][SIZE=3]#You take over this thread wildmanne39 you are better with Network cards and their drives than I. [/SIZE][/FONT][/COLOR]I can do a little bcm cards and iwlagn driver for intel's. 


[COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]

---

### Post by wildmanne39 on 2011-10-16
Hi, you are correct that is the way to make it permanent,and it has been needed since upgrading to kernel 3.0.

You are doing fine.

I too struggle with some issues.

---

### Post by ajcjh on 2011-10-16
yes thank you. i did fix the config file and have not changed the post.  Still doesn't affect wireless connectivity but good catch

---

### Post by ajcjh on 2011-10-16
> **wildmanne39 said:**
> Hi garvinrick4, is this what you are talking about?
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig iwlagn up
```

To the client please try this code one line at a time and if it works we will need to make it permanent.
Thank you

I got this message for the last command

jupiter@jupiter-U56E:~$ sudo ifconfig iwlagn up
iwlagn: ERROR while getting interface flags: No such device

how do I re-enable n?

---

### Post by wildmanne39 on 2011-10-16
Hi, did you run this command one line at a time? Make sure you disconnect your wired connection first and do not restart your computer after you run the commands. 
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```

If this does not work let us know and we will go from there.
Thank you

---

### Post by wildmanne39 on 2011-10-16
Hi, I had a typo in the last command, I fixed it, now run the commands again please.
Thank you

---

### Post by garvinrick4 on 2011-10-16
> it has been needed since upgrading to kernel 3.0.Typo post 5, should be:
it has not been needed since upgrading to kernel 3.0 
"N"  in 'iwlagn" will work in 3.0 and up kernels. 

If you owned a "g'' router never new was a problem with "iwlagn", 

If you owned a "N" router had to remove "N" with config file from card. "iwlagn" driver would depreciate to not working at all without config file. (11.04 and down) 

Or install a kernel of 3.0 and up. (maverick and Natty) with upgrade in module-init-tools both links below to .deb files.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

It is my driver, you get to no em like the back of your hand.

Some users that upgraded still have config file in /etc/modprobe.d/iwlagn.conf and should be removed to work with N in 3.0 and up.

---

### Post by wildmanne39 on 2011-10-16
Hi I have helped about 10 people after they upgraded to 11.10 and they still needed that code.
Type this please
```
modinfo iwlagn
```
into the terminal and next to parm it is listed as a parameter.

So it maybe be needed by some people and not others.
Thank you

---

### Post by ajcjh on 2011-10-16
I went through the commands with the wire unplugged.  After unblocking the rfkill list (which mysteriously had soft blocks on all three) I was able to execute the last command -sudo ifconfig wlan0 up.  unfortunately my wireless still won't connect

and here is the parm section from modinfo iwlagn
depends:        mac80211,cfg80211
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (bool)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)

---

### Post by wildmanne39 on 2011-10-16
Hi, please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n25
```
```
nm-tool
```
Thank you

---

### Post by ajcjh on 2011-10-16
I appreciate your time and help

#lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
	Kernel driver in use: iwlagn
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c

#rfkill list all
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wimax: WiMAX
	Soft blocked: no
	Hard blocked: no
5: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no

#sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
                  
          Cell 03 - Address: 00:22:6B:56:FC:3C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"stephenlarkin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000153346d1fc
                    Extra: Last beacon: 616ms ago
                    IE: Unknown: 000D7374657068656E6C61726B696E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000226B48FC3C103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000400000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
         
#sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n25
Oct 16 19:22:30 jupiter-U56E NetworkManager[913]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 16 19:22:31 jupiter-U56E kernel: [11359.219688] wlan0: direct probe to 00:22:6b:48:fc:3c (try 1/3)
Oct 16 19:22:31 jupiter-U56E NetworkManager[913]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 16 19:22:31 jupiter-U56E kernel: [11359.416975] wlan0: direct probe to 00:22:6b:48:fc:3c (try 2/3)
Oct 16 19:22:31 jupiter-U56E kernel: [11359.616634] wlan0: direct probe to 00:22:6b:48:fc:3c (try 3/3)
Oct 16 19:22:31 jupiter-U56E kernel: [11359.816330] wlan0: direct probe to 00:22:6b:48:fc:3c timed out
Oct 16 19:22:33 jupiter-U56E kernel: [11361.821357] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 16 19:22:39 jupiter-U56E kernel: [11367.483460] wlan0: direct probe to 00:22:6b:48:fc:3c (try 1/3)
Oct 16 19:22:39 jupiter-U56E kernel: [11367.680620] wlan0: direct probe to 00:22:6b:48:fc:3c (try 2/3)
Oct 16 19:22:39 jupiter-U56E kernel: [11367.880345] wlan0: direct probe to 00:22:6b:48:fc:3c (try 3/3)
Oct 16 19:22:40 jupiter-U56E kernel: [11368.080036] wlan0: direct probe to 00:22:6b:48:fc:3c timed out
Oct 16 19:22:42 jupiter-U56E kernel: [11370.081055] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 16 19:22:47 jupiter-U56E kernel: [11375.679650] wlan0: direct probe to 00:22:6b:48:fc:3c (try 1/3)
Oct 16 19:22:47 jupiter-U56E kernel: [11375.876424] wlan0: direct probe to 00:22:6b:48:fc:3c (try 2/3)
Oct 16 19:22:48 jupiter-U56E kernel: [11376.076109] wlan0: direct probe to 00:22:6b:48:fc:3c (try 3/3)
Oct 16 19:22:48 jupiter-U56E kernel: [11376.275815] wlan0: direct probe to 00:22:6b:48:fc:3c timed out
Oct 16 19:22:50 jupiter-U56E kernel: [11378.328761] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 16 19:22:56 jupiter-U56E kernel: [11383.994923] wlan0: direct probe to 00:22:6b:48:fc:3c (try 1/3)
Oct 16 19:22:56 jupiter-U56E kernel: [11384.196006] wlan0: direct probe to 00:22:6b:48:fc:3c (try 2/3)
Oct 16 19:22:56 jupiter-U56E kernel: [11384.395721] wlan0: direct probe to 00:22:6b:48:fc:3c (try 3/3)
Oct 16 19:22:56 jupiter-U56E kernel: [11384.595412] wlan0: direct probe to 00:22:6b:48:fc:3c timed out
Oct 16 19:22:58 jupiter-U56E kernel: [11386.656357] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 16 19:23:03 jupiter-U56E NetworkManager[913]: <info> (wlan0): device state change: config -> disconnected (reason 'user-requested') [50 30 39]
Oct 16 19:23:03 jupiter-U56E NetworkManager[913]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Oct 16 19:23:03 jupiter-U56E NetworkManager[913]: <info> (wlan0): supplicant interface state: authenticating -> disconnected

#nm-tool
State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        14:DA:E9:4F:2A:51

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.15.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        40:25:C2:52:02:F0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    qwest4096:       Infra, 00:24:37:28:33:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WEP
    happyhollow:     Infra, E0:46:9A:4B:34:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA
    Carol 1937:      Infra, A0:21:B7:9C:7D:10, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA
    xhurch:          Infra, 00:13:10:74:BC:AA, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    SMCWBR14S-N4_AP: Infra, 00:22:2D:B2:46:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    mbira:           Infra, 30:46:9A:81:7C:5C, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Epiphone:        Infra, 00:1F:F3:C1:1C:CD, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    stephenlarkin:   Infra, 00:22:6B:48:FC:3C, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    HPEF924A:        Ad-Hoc, 02:2C:BC:0C:05:08, Freq 2457 MHz, Rate 11 Mb/s, Strength 20
    BronzeFish-guest:Infra, C0:C1:C0:8E:86:D6, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    myqwest3193:     Infra, 00:24:7B:A4:89:DA, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BronzeFish:      Infra, C0:C1:C0:8E:86:D5, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    TribeNetwork:    Infra, 58:6D:8F:07:1F:B9, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    HOME-E518:       Infra, 78:CD:8E:1F:E5:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    wheninpdx:       Infra, C0:3F:0E:81:9B:13, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Apple Network 2d6bcf: Infra, 00:1B:63:2D:6B:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Brooklyn import: Infra, 00:25:9C:29:25:1B, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    BENNETT:         Infra, 00:09:5B:D4:D8:DC, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA

---

### Post by wildmanne39 on 2011-10-16
Hi, I have to get off here for tonight, I will look at this tomorrow and help you if someone else has not before then.
Thank you

---

### Post by ajcjh on 2011-10-16
thanks again for your help

---

### Post by wesbuntu on 2011-10-17
Hi guys!

I have the same computer with exactly the same issue. I just wanted to mention that I tried the upstream kernel (v3.1-rc9) with no luck there either. I also wanted to mention that the iwlagn section of dmesg ends with a series of "fail to flush all tx fifo queues".

---

### Post by wildmanne39 on 2011-10-17
Hi please show the results of:
```
 cat /etc/modprobe.d/iwlagn.conf
```
```
iwconfig
```
According to the errors messages it is a problem with n speed.
Thank you

---

### Post by ajcjh on 2011-10-17
I no iwlagn.conf file exists

iwconfig-
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=15 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on

---

### Post by wildmanne39 on 2011-10-17
Hi, there are many networks in your area, which one are trying to connect too? Also we should try this, do not restart your computer after you enter the code.
```
sudo iwconfig wlan0 power off
```
if that does not help change your n speed in your router to b,g speed.
Thank you

---

### Post by wesbuntu on 2011-10-17
Below is a comparison of two commands run from a working version and a non-working version. Like agcjh I have no iwlagn.config file in either of these versions. The 11.10 version is a fresh install on this computer and the 11.04 version is run live from USB on the same system. When I ran these commands I was at a location with only one access point in range and no security on it.

**** 11.10 ****
```

$ uname -r
3.0.0-12-generic

$ cat /etc/modprobe.d/iwlagn.conf
cat: /etc/modprobe.d/iwlagn.conf: No such file or directory

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```**** 11.04 ****
```

$ uname -r
2.6.38-8-generic

$ cat /etc/modprobe.d/iwlagn.conf
cat: /etc/modprobe.d/iwlagn.conf: No such file or directory

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"welcometodu"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:EB:62:4C:C0   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:27   Missed beacon:0


```

I will try your more recent suggestion. If you have any other suggestions you would like to show output for from the working versus non-working versions let me know.

Thank you much for your help

---

### Post by garvinrick4 on 2011-10-17
> Running with 2.6.38-8 and running with N speeds 65 Mb/s and with N 802.11 bgnWhat if OP were to download that kernel or 2.6.39 oneiric and install and run 11.10 with.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-oneiric/")
[COLOR=Red]EDIT>[/COLOR] confirmed with 2.6.38.8 kernel do not use 2.6.39 use below.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38.8-natty/")
Download:
all.deb
headers 64 bit
image 64 bit

after download click on them one at a time and will download thru Ubuntu software center.
Install in that order downloaded.

If asks for module-init-tools upgrade do the same with 64 bit in lower left of this page in .deb
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500)

  Choose that kernel to boot from in 11.10. Does the internet work now in 11.10

---

### Post by ajcjh on 2011-10-17
power off didn't help.  I will try switching the router if it doesn't mess up the connection for my friends computer (I'm a guest) 
It seems to me that it is an Intel issue and they need to update their drivers.  I may just end up switching back to 11.04 for now, and upgrading again after a few new kernels come out.
If I do change the router speed and it works, then I'll let you know

---

### Post by garvinrick4 on 2011-10-17
> It seems to me that it is an Intel issueIt is an Intel issue I do believe and could be in the 3.0 and up kernel with just a few. I have same driver
with no problems at all. A few of you have the problem.( iwlagn 0000:02:00.0: fail to flush all tx fifo queues)
Only take a minute or two to run the 2.6.39 kernel and check out if that is the issue, just might be.
If not of course that is OK,  will bow out. Enjoy your Ubuntu. (Let us know if you tried 2.6.38 or 39 kernel.)

---

### Post by ajcjh on 2011-10-17
> **wildmanne39 said:**
> Hi, there are many networks in your area, which one are trying to connect too? Also we should try this, do not restart your computer after you enter the code.
```
sudo iwconfig wlan0 power off
```
if that does not help change your n speed in your router to b,g speed.
Thank you

I also deleted the extra networks in that post
I also changed the router and no change...

---

### Post by wildmanne39 on 2011-10-17
Hi, you can try what garvinrick4 mentioned it is not a bad idea, but I prefer that he helps with that, I few days ago I helped someone upgrade to the 3.0 kernel, by trying it in virtualbox first and it worked, then after he installed it, it worked a couple of boot ups and then it stopped, and I checked mine and it had stopped also, I think it was just some bug in the 3.0 kernel but I am not sure about that.
Thank you

---

### Post by ajcjh on 2011-10-17
> **garvinrick4 said:**
> It is an Intel issue I do believe and could be in the 3.0 and up kernel with just a few. I have same driver
with no problems at all. A few of you have the problem.( iwlagn 0000:02:00.0: fail to flush all tx fifo queues)
Only take a minute or two to run the 2.6.39 kernel and check out if that is the issue, just might be.
If not of course that is OK,  will bow out. Enjoy your Ubuntu. (Let us know if you tried 2.6.38 or 39 kernel.)

Well, tried 2.6.39 with no luck.  Thanks for the input though.  This is the first time I've had an issue with Ubuntu that took more than a day to solve so I can't complain.

---

### Post by wildmanne39 on 2011-10-17
Hi, please install wicd then remove network manager completely config files and all, but you must install wicd first.

Then restart your computer.
Thank you

---

### Post by ajcjh on 2011-10-18
Installed wicd. still won't connect to wireless but now gives the error "connection failed: bad password" and I am 100% sure it is the right one.
When I log into the router it says that it is WPA2 protected, (TKIP or AES encryption) but in wicd when it lists the connection it says that it is WEP...

---

### Post by wildmanne39 on 2011-10-18
Hi, since we have changed somethings please post the commands from post 13 again except the first command.
Thank you

---

### Post by ajcjh on 2011-10-18
> **wildmanne39 said:**
> Hi, since we have changed somethings please post the commands from post 13 again except the first command.
Thank you

0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wimax: WiMAX
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

 Cell 02 - Address: 00:22:6B:48:FC:3C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"stephenlarkin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000022907155
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 000D7374657068656E6C61726B696E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000226B48FC3C103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000

Oct 17 21:06:31 jupiter-U56E kernel: [ 1380.481333] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:06:31 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: starting -> ready
Oct 17 21:06:31 jupiter-U56E NetworkManager[937]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 17 21:06:31 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: ready -> inactive
Oct 17 21:07:08 jupiter-U56E dhclient: Listening on LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:07:08 jupiter-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:07:09 jupiter-U56E kernel: [ 1418.296594] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:07:09 jupiter-U56E kernel: [ 1418.424203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:07:09 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: inactive -> down
Oct 17 21:07:09 jupiter-U56E NetworkManager[937]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'supplicant-failed') [30 20 10]
Oct 17 21:07:09 jupiter-U56E NetworkManager[937]: <info> (wlan0): deactivating device (reason 'supplicant-failed') [10]
Oct 17 21:07:09 jupiter-U56E kernel: [ 1418.656548] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:07:09 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: starting -> ready
Oct 17 21:07:09 jupiter-U56E NetworkManager[937]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 17 21:07:09 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: ready -> inactive
Oct 17 21:07:31 jupiter-U56E dhclient: Listening on LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:07:31 jupiter-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:07:32 jupiter-U56E kernel: [ 1441.331345] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:07:32 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: inactive -> down
Oct 17 21:07:32 jupiter-U56E NetworkManager[937]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'supplicant-failed') [30 20 10]
Oct 17 21:07:32 jupiter-U56E NetworkManager[937]: <info> (wlan0): deactivating device (reason 'supplicant-failed') [10]
Oct 17 21:07:32 jupiter-U56E kernel: [ 1441.548022] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:07:32 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: starting -> ready
Oct 17 21:07:32 jupiter-U56E NetworkManager[937]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 17 21:07:32 jupiter-U56E NetworkManager[937]: <info> (wlan0): supplicant interface state: ready -> inactive

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        40:25:C2:52:02:F0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    happyhollow:     Infra, E0:46:9A:4B:34:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA
    Linksys:         Infra, 00:23:69:1C:EE:4F, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    TTD:             Infra, 00:1E:E5:65:FB:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    HPEF924A:        Ad-Hoc, 02:2C:BC:0C:05:08, Freq 2457 MHz, Rate 11 Mb/s, Strength 19
    HotSpotSystem.com-XHURCHES: Infra, 00:13:10:74:BC:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    BronzeFish-guest:Infra, C0:C1:C0:8E:86:D6, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    Brooklyn import: Infra, 00:25:9C:29:25:1B, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    mbira:           Infra, 30:46:9A:81:7C:5C, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    myqwest3193:     Infra, 00:24:7B:A4:89:DA, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Apple Network 2d6bcf: Infra, 00:1B:63:2D:6B:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    TribeNetwork:    Infra, 58:6D:8F:07:1F:B9, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    HOME-E518:       Infra, 78:CD:8E:1F:E5:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Epiphone:        Infra, 00:1F:F3:C1:1C:CD, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BronzeFish:      Infra, C0:C1:C0:8E:86:D5, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    wheninpdx:       Infra, C0:3F:0E:81:9B:13, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    BENNETT:         Infra, 00:09:5B:D4:D8:DC, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    stephenlarkin:   Infra, 00:22:6B:48:FC:3C, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        14:DA:E9:4F:2A:51

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.15.1

---

### Post by wildmanne39 on 2011-10-18
Hi, is stephenlarkin the network you want to connect too?

Please see if you can change your wpa/wpa2 setting in your router to just wpa2.

Do you still have wicd installed? Did you completely remove network mangager because in the error messages it shows network manager.
Thank you

---

### Post by ajcjh on 2011-10-18
Yes stephenlarkin. I guess I don't know how to completely remove network manager. The router says security mode is WPA2 personal, it does not say anything about WPA/WPA2...
OK got rid of network manager, nm-tool won't work, wicd sees stephenlarkin as WPA2, new ouput is:
jupiter@jupiter-U56E:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n25
Oct 17 21:46:53 jupiter-U56E kernel: [  177.769277] wlan0: direct probe to 00:22:6b:48:fc:3c (try 1/3)
Oct 17 21:46:53 jupiter-U56E kernel: [  177.965601] wlan0: direct probe to 00:22:6b:48:fc:3c (try 2/3)
Oct 17 21:46:53 jupiter-U56E kernel: [  178.165404] wlan0: direct probe to 00:22:6b:48:fc:3c (try 3/3)
Oct 17 21:46:53 jupiter-U56E kernel: [  178.365209] wlan0: direct probe to 00:22:6b:48:fc:3c timed out
Oct 17 21:46:55 jupiter-U56E kernel: [  180.367223] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 17 21:46:59 jupiter-U56E dhclient: Listening on LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:46:59 jupiter-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:47:01 jupiter-U56E kernel: [  185.853799] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 17 21:47:10 jupiter-U56E dhclient: Listening on LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:47:10 jupiter-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:47:11 jupiter-U56E kernel: [  195.573654] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:47:11 jupiter-U56E kernel: [  195.742544] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:47:11 jupiter-U56E dhclient: Listening on LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:47:11 jupiter-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:52:02:f0
Oct 17 21:47:11 jupiter-U56E kernel: [  196.413636] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 17 21:47:23 jupiter-U56E kernel: [  207.766309] wlan0: direct probe to 00:22:6b:48:fc:3c (try 1/3)
Oct 17 21:47:23 jupiter-U56E kernel: [  207.963958] wlan0: direct probe to 00:22:6b:48:fc:3c (try 2/3)
Oct 17 21:47:23 jupiter-U56E kernel: [  208.163768] wlan0: direct probe to 00:22:6b:48:fc:3c (try 3/3)
Oct 17 21:47:23 jupiter-U56E kernel: [  208.363574] wlan0: direct probe to 00:22:6b:48:fc:3c timed out
Oct 17 21:47:25 jupiter-U56E kernel: [  210.377566] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 17 21:47:33 jupiter-U56E kernel: [  218.375877] wlan0: direct probe to 00:22:6b:48:fc:3c (try 1/3)
Oct 17 21:47:34 jupiter-U56E kernel: [  218.573491] wlan0: direct probe to 00:22:6b:48:fc:3c (try 2/3)
Oct 17 21:47:34 jupiter-U56E kernel: [  218.773271] wlan0: direct probe to 00:22:6b:48:fc:3c (try 3/3)
Oct 17 21:47:34 jupiter-U56E kernel: [  218.973055] wlan0: direct probe to 00:22:6b:48:fc:3c timed out
Oct 17 21:47:36 jupiter-U56E kernel: [  220.979089] iwlagn 0000:02:00.0: fail to flush all tx fifo queues

---

### Post by wildmanne39 on 2011-10-18
Hi, this shows it is both.
```
stephenlarkin: Infra, 00:22:6B:48:FC:3C, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
```

You have to have your computer wired to the router then in a broswer type 192.168.0.1 into the address bar and hopefully that will bring up a web page with your router settings in it.

Then click on security settings and have a look, also look in wireless settings in the internet icon in the top right corner of your desktop by clicking on edit connection then wireless.

Please post the result of this command.
```
ps aux | grep nm-apple
```
did you use software center to install wicd? and is that how you uninstalled network manager?
Thank you

---

### Post by ajcjh on 2011-10-18
It is interesting since in the router wireless security settings there isn't even an option to choose both....and security just has firewall settings and VPN passthrough.

$ ps aux | grep nm-apple
jupiter   2801  0.0  0.0  13448   900 pts/0    S+   21:54   0:00 grep --color=auto nm-apple

I used software center to install wicd, and uninstall network manager.  I then went into synaptic package manager and did a complete removal of the rest.

---

### Post by wildmanne39 on 2011-10-18
Hi, try it like this please:
```
sudo apt-get --purge remove network-manager-gnome
```
Then reboot.
Thank you

---

### Post by ajcjh on 2011-10-18
still no luck
Thank you for all your time and help with this

---

### Post by wildmanne39 on 2011-10-18
Hi, you did  an upgrade and not a clean install right? that could be part of the problem.

Please let&#347; create this file since you said it does not exist.
```
gksu gedit /etc/modprobe.d/iwlagn.conf
```
Add
```
options iwlagn 11n_disable=1
```
Then reboot.
Thank you

---

### Post by netxph on 2011-10-18
I have exactly the same problem (well, it has been since I keep jumping from one Linux OS to the other).

Maybe these information will help *Linux* experts out there. :)

* Last working Linux Kernel version for our iwlagn is 2.6.38, any version before that will not work, and any versions after that will not work either. Upgrading/Downgrading to 2.6.38 was my only option, but then, it's too much work to downgrade/upgrade since I need to build different drivers to this version as well.
* Tested this with Debian and Ubuntu
* Wicd/Update NM does not solve it
* Adding/removing the 11n_disable config does not work either
* Changing from 64-bit to 32-bit does not work either
* Tried changing different frequencies in my router does not work either

I've been waiting for months now for the solution for this. This is what I feared with Ubuntu 11.10 when I learned that they are getting 3.x kernel :(

---

### Post by PatrickZ on 2011-10-18
I also have a 64 bit system that can't connect to wireless after 11.10 upgrade. I'm running the ubuntustudio version. When clicking on the network manger applet it states that both wired and wireless connections are "unmanaged". The wired connection works anyway, the wireless does not.

---

### Post by ajcjh on 2011-10-18
Well wildmanne39, still nothing.  It was initially an upgrade and now two clean installs.  It looks like I'm in the same boat as netxph, playing the waiting game.  Thanks again for all your time.  I'll keep my eyes open and try sending Intel the bug information.  Until something changes it looks like I'm reverting to 11.04

---

### Post by garvinrick4 on 2011-10-18
> I also have a 64 bit system that can't connect to wireless after 11.10  upgrade. I'm running the ubuntustudio version. When clicking on the  network manger applet it states that both wired and wireless connections  are "unmanaged". The wired connection works anyway, the wireless does  not.Now this Thread has been about Intel card and iwlagn driver problems, if you have broadcom (bcm) then that
is just loading correct driver and not a problem.
```
lspci -nn | grep 0280
```> * Last working Linux Kernel version for our iwlagn is 2.6.38, any  version before that will not work, and any versions after that will not  work either. Upgrading/Downgrading to 2.6.38 was my only option, but  then, it's too much work Download the 3 in your 32 or 64 bit
all.deb
headers
image
Click on them in that order will install thru Ubuntu software sources. (all takes just a few minutes)
reboot and choose the 2.6.38 kernel to boot from,  at least until this iwlagn problem gets straightened out.
[]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-natty/")_[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/)_

#This is not with all machines and iwlagn driver some still work out of box,  no one seems to have figured out the common denominator as of yet besides works with 2.6.38 kernel.

---

### Post by PatrickZ on 2011-10-18
It is not a broadcom card it's a  Intel Corporation Ultimate N WiFi Link 5300.

---

### Post by garvinrick4 on 2011-10-18
> **PatrickZ said:**
> It is not a broadcom card it's a  Intel Corporation Ultimate N WiFi Link 5300.
Mostly I wrote that post incase new users are looking at it and do not realize that if they have a broadcom
card it is usually in most all cases easily handled with correct driver.

---

### Post by wesbuntu on 2011-10-18
My card is an Intel Centrino Wireless-N + WiMAX 6150, I have been following this thread and trying everything. The only way I could get it to work is with a downgrade to the 2.6.38 kernel (2.6.38.8 specifically) as per garvinrick4's instructions. I tried a number of kernels in the oneric tree including 3.1-rc9 and a number of 2.6.39 release candidates in order to find that one specific kernel that caused the problem. It really seems to be the transition from 2.6.38 to 2.6.39, but I did not try every 2.6.39-rc.

I will look through the change logs but I probably wont be able to see the trigger due to lack of knowledge. Is there a preferred location to report this as a bug?

---

### Post by garvinrick4 on 2011-10-18
> Is there a preferred location to report this as a bug?Bugs are reported in Launchpad.net in upper right hand corner of Ubuntu page. Join launchpad it has all things Ubuntu in it. 
Then report your findings, will come in handy for users with same. Thank you for reporting to thread, you will make a difference in[COLOR=Red] letting users know it works[/COLOR] in 2.6.38.8 as the highest kernel. 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38.8-natty/")

---

### Post by wildmanne39 on 2011-10-18
Hi ajcjh, okay I am sorry we did not get it working.

---

### Post by wildmanne39 on 2011-10-18
Hi PatrickZ, try what is in post 3 and it will only work until you reboot, if that does not work we will need to get information from you before suggesting any further action.
Thank you

---

### Post by PatrickZ on 2011-10-18
I did as stated in post #3. Still nothing...

---

### Post by wildmanne39 on 2011-10-18
Hi PatrickZ, please post the results of these commands.
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
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 -e wpa | tail -n35 
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by PatrickZ on 2011-10-18
```
patrick@a91-154-132-38:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux a91-154-132-38 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
patrick@a91-154-132-38:~$ sudo lshw -C network
[sudo] password for patrick: 
  *-network               
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:76:6a:aa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f4100000-f4101fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:91:cc:2b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.100.27 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:4000(size=256) memory:f4200000-f4200fff memory:f4000000-f400ffff memory:f4020000-f403ffff
patrick@a91-154-132-38:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        00:90:F5:91:CC:2B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unmanaged
  Default:           no
  HW Address:        00:16:EA:76:6A:AA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


patrick@a91-154-132-38:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
    Subsystem: Intel Corporation Device [8086:1001]
    Kernel driver in use: iwlagn
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0806]
    Kernel driver in use: r8169
patrick@a91-154-132-38:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
patrick@a91-154-132-38:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
patrick@a91-154-132-38:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:C3:D6:36:CD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-17 dBm  
                    Encryption key:on
                    ESSID:"ElisaKoti29"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002beeeb7712
                    Extra: Last beacon: 3244ms ago
                    IE: Unknown: 000B456C6973614B6F74693239
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000187A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706464920010D10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601000CC3D636CD1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000100
          Cell 02 - Address: 00:23:08:F2:F7:38
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ElisaKoti19"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025d03a1b6cd
                    Extra: Last beacon: 3204ms ago
                    IE: Unknown: 000B456C6973614B6F74693139
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500020C7A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706464920010D10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050700000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601002308F2F7381021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000100
          Cell 03 - Address: 40:4A:03:A5:1D:27
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Elisa585"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001994fff262b1
                    Extra: Last beacon: 3104ms ago
                    IE: Unknown: 0008456C697361353835
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

patrick@a91-154-132-38:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
patrick@a91-154-132-38:~$ lsmod | grep iwl
iwlagn                314213  0 
mac80211              310872  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
patrick@a91-154-132-38:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 -e wpa | tail -n35
Oct 18 14:33:41 a91-154-132-38 kernel: [   11.842379] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
Oct 18 14:33:41 a91-154-132-38 kernel: [   11.842381] iwlagn 0000:02:00.0: Device SKU: 0Xb
Oct 18 14:33:41 a91-154-132-38 kernel: [   11.842389] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct 18 14:33:41 a91-154-132-38 kernel: [   11.842453] iwlagn 0000:02:00.0: irq 47 for MSI/MSI-X
Oct 18 14:33:41 a91-154-132-38 kernel: [   13.520268] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
Oct 18 14:33:41 a91-154-132-38 kernel: [   13.814099] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Oct 18 14:33:46 a91-154-132-38 NetworkManager[966]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 18 14:33:46 a91-154-132-38 NetworkManager[966]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 18 14:33:46 a91-154-132-38 NetworkManager[966]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 18 14:33:46 a91-154-132-38 NetworkManager[966]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 18 14:33:46 a91-154-132-38 NetworkManager[966]:    SCPlugin-Ifupdown: adding iface wlan0 to well_known_interfaces
Oct 18 14:33:46 a91-154-132-38 NetworkManager[966]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 18 14:33:47 a91-154-132-38 NetworkManager[966]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 18 14:33:47 a91-154-132-38 NetworkManager[966]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 18 14:33:47 a91-154-132-38 NetworkManager[966]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Oct 18 14:33:47 a91-154-132-38 NetworkManager[966]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 18 22:58:06 a91-154-132-38 avahi-daemon[960]: Withdrawing workstation service for wlan0.
Oct 18 22:58:06 a91-154-132-38 NetworkManager[966]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 18 22:58:06 a91-154-132-38 kernel: [30282.712429] iwlagn 0000:02:00.0: PCI INT A disabled
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.685227] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.685230] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.685301] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.685311] iwlagn 0000:02:00.0: setting latency timer to 64
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.685337] iwlagn 0000:02:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.707311] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.707313] iwlagn 0000:02:00.0: Device SKU: 0Xb
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.707329] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.707395] iwlagn 0000:02:00.0: irq 47 for MSI/MSI-X
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.709743] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
Oct 18 22:58:33 a91-154-132-38 kernel: [30309.711108] ieee80211 phy1: Selected rate control algorithm 'iwl-agn-rs'
Oct 18 22:58:33 a91-154-132-38 NetworkManager[966]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 18 22:58:33 a91-154-132-38 NetworkManager[966]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 18 22:58:33 a91-154-132-38 NetworkManager[966]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 4)
Oct 18 22:58:33 a91-154-132-38 NetworkManager[966]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Oct 18 22:58:47 a91-154-132-38 kernel: [30324.209591] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```Thanks for the help! I think I'll go and get some sleep now, be back tomorrow.

---

### Post by wildmanne39 on 2011-10-18
Hi, which network are you trying to connect too?

Do this please to change to managed mode.
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlan0 mode Managed
```
```
sudo ifconfig wlan0 up
```

---

### Post by PatrickZ on 2011-10-19
I tried those commands, still nothing... The network I'm trying to connect to is named ElisaKoti29.

---

### Post by wildmanne39 on 2011-10-19
Hi, 
1. Please set your encryption to wpa2 and not wpa in your router and see if that helps.

2.Make sure your router is not set to just n speed set it to a,b,n or b,g.

You hopefully will be able to enter your routers settings by typing 192.168.0.1 into the address bar of your browser.

---

### Post by pro.gangster on 2011-10-20
hi

my wireless doesn't work at all, it don't turn on

I'm using Ubuntu for the first time,but I saw the wifi problem for other  users happening after upgrading to 11.10, so after my many searches,I'm  going to downgrade if my problem doesn't solve
so,please help me on this
 
Lenovo-Ideapad U330
Intel Wifi Link 5100 AGN

I downloaded the .ucode driver (iwlwifi-5000-ucode-8.83.5.1) and copied it to /lib/firmware but it didn't work

I also tried Windows Wireless Driver app

what is the problem?
please help me

---

### Post by wildmanne39 on 2011-10-20
Hi pro.gangster, rihgt now the only way that we know for sure to get this card working is to downgrade your kernel, you can follow the directions in post 42 to do that if you want too.
Thank you

---

### Post by netxph on 2011-10-22
no loving care for us from ubuntu :( was able to make it work by downgrading the kernel. 

Has anyone filed bug regarding this already that we can monitor?

---

### Post by manuhalo on 2011-10-24
Hi,
I'm having the same problem, but during my various re-installs I noticed that wireless seems to work for some reason during the installation when it's copying packages from the cd, regardless of the fact that it doesn't work at the beginning of the installation process (connection times out and I'm asked for a password again as usual) nor after I reboot into the freshly installed system. It has happened twice so far, might even try to install again just for the sake of replicating the experiment and test if it works again. Weird...

---

### Post by Bubb2112 on 2011-10-24
Hey Guys, thanks for all of your help. I followed the instructions for downgrading the kernel (comment #22) to see if it fixes the wireless issue on an asus laptop. 

> **garvinrick4 said:**
> Choose that kernel to boot from in 11.10. Does the internet work now in 11.10

I don't see an option to choose what kernel to boot from. Did downloading & installing those 3 packages already complete the downgrade? If so, the wireless still doesn't work. But perhaps I'm not booting from the kernel I downloaded & installed? 

I'd be grateful for any help you guys can provide :)

---

### Post by garvinrick4 on 2011-10-24
IN Terminal:
```
grep menuentry /boot/grub/grub.cfg
```Find the 2.6.38 kernel you installed just to make sure is there.
Will not be first in line:

---

### Post by Bubb2112 on 2011-10-24
Yes, it's there. I only installed one ubuntu, so the boot menu doesn't load, it just loads my only instance of ubuntu 11.10. 

How do I boot from the older kernel?

---

### Post by garvinrick4 on 2011-10-24
> Yes, it's there. I only installed one ubuntu, so the boot menu doesn't load, it just loads my only instance of ubuntu 11.10. 
How do I boot from the older kernel?     Hold down the "shift key" while machine is booting will bring up the grub boot menu.
It defaults to bypass the menu when only one install.

You can download this app to select kernel I do believe, with or in graphics to make new kernel selected now default:
```
sudo apt-get install startupmanager
```rick@rick:~$ aptitude show startupmanager
```
Package: startupmanager                  
State: not installed
Version: 1.9.13-5
Priority: optional
Section: universe/utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,393 k
Depends: python, python-support (>= 0.90.0), python-glade2 (>= 2.12),
         python-gnome2 (>= 2.20), python-libxml2 (>= 2.6.30), x11-xserver-utils,
         yelp, grub | grub-pc, menu
Description: Grub, Usplash and Splash screen configuration
 StartUp-Manager configures some settings for grub, usplash and splash screens.
 It provides an easy to use interface. 
 
 It is originally a Ubuntu project, adapted for Debian.
Homepage: https://launchpad.net/startup-manager
```

---

### Post by Bubb2112 on 2011-10-24
GavinRick4,

That did it. I appreciate your help, I would have never figured that one out myself. You're a hell of an ubuntu addict, lol. 

Is the old kernel going to cause other problems, or will it just be ok until the next distribution upgrade?

---

### Post by garvinrick4 on 2011-10-25
> Is the old kernel going to cause other problems, or will it just be ok until the next distribution upgrade? I am happy it worked out for you. You will see a post in
these Forums where the "iwlagn" driver problem will be worked out and you can upgrade
your kernel. Not all Intel cards using "iwlagn" is having the problem but will be figured out
eventually. Here is link of kernels when needed. Enjoy your Ubuntu Bubb2112.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by pro.gangster on 2011-10-25
> **wildmanne39 said:**
> Hi pro.gangster, rihgt now the only way that we know for sure to get this card working is to downgrade your kernel, you can follow the directions in post 42 to do that if you want too.
Thank you

I couldn't understand the process, because I'm a new ubuntu user

Is downgrading the kernel,downgrade my ubuntu too?

---

### Post by wildmanne39 on 2011-10-25
Hi pro.gangster, yes that is the only choice that we now of at this time,garvinrick4 can help you with that if needed, I am not on much right now I am helping right some documentation for the forum.

No, it does not downgrade your ubuntu too.

Thank yougarvinrick4
I am not quite awake yet.

---

### Post by garvinrick4 on 2011-10-25
> Is downgrading the kernel,downgrade my ubuntu too?
                                                                                  No it does not.
                                > I couldn't understand the process, because I'm a new ubuntu userRun this in a terminal to tell if you have 32 or 64 bit.
```
uname -a
```If it says this below in the line then you have 64 bit any thing else you have 32 bit 
x86_64 x86_64
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-natty/")
Now going to link above you will see in bottom 5 lines two that say 32 bit and 2 that say 64 bit.
Take the 2 that are yours in 64 or 32 bit and the 1 that says all.deb and that is 3 of them to download.
all.deb ( for both 32 or 64 bit)
headers (32 or 64 bit)
image (32 or 64 bit)
Now Download them the 3 of them.
Click on them in same order and they will install through Ubuntu software center and give you the 2.6.38 kernel to choose from when you boot at the menu.
If you do not get a menu at boot it is because you only have 1 install, it takes 2 installs to show the boot menu screen (by default). So to see the boot menu entry screen hold down the shift key
at boot and will show you screen to choose 2.6.38 kernel.
If you want to make it permanent install this application and choose the kernel for it and will always open in 2.6.38 kernel.
```
sudo apt-get install startupmanager
```

---

### Post by manuhalo on 2011-10-27
Is there a bug on launchpad or any other page that we can follow to check whether they have solved the issue? I solved my problems by reverting to 11.04 as I had other issues with Oniric anyway, but it would be nice to know when it's safe to move forward. Thanks anyway!

---

### Post by garvinrick4 on 2011-10-27
> **manuhalo said:**
> Is there a bug on launchpad or any other page that we can follow to check whether they have solved the issue? I solved my problems by reverting to 11.04 as I had other issues with Oniric anyway, but it would be nice to know when it's safe to move forward. Thanks anyway!
Is not on all machines using iwlagn driver with Intel Network card, I have the same driver and works fine. No one has found common denominator as of yet. Might be smart to look around launchpad.net bugs again to see if problem with kernel and driver has been discovered. Get back here and give report if you can. Have a nice day.

---

### Post by hero1900 on 2011-10-27
i have the same issue here with Intel Corporation PRO/Wireless 3945ABG card and it sometimes connect and disconnect after while i have usb wireless adapter which i am using now but it also has problem with this new kernel its really sucks i use tp-link TL-WN722NC, so i think 11.10 have serious issue with networking. since i have another 2 friends who has same issue and with different hardware. i think ubuntu developers should seriously look in this. please help us soon i like the new ubuntu but need to go back to 10.4 now.

---

### Post by zex87 on 2011-10-27
> **hero1900 said:**
> i have the same issue here with Intel Corporation PRO/Wireless 3945ABG card and it sometimes connect and disconnect after while i have usb wireless adapter which i am using now but it also has problem with this new kernel its really sucks i use tp-link TL-WN722NC, so i think 11.10 have serious issue with networking. since i have another 2 friends who has same issue and with different hardware. i think ubuntu developers should seriously look in this. please help us soon i like the new ubuntu but need to go back to 10.4 now.

I have the same problem with intel 4965. I'm very sad for this. I hope in a kernel  update, becouse I love ubuntu and last function....

---

### Post by wildmanne39 on 2011-10-27
Hi, for the people with the 3945
[http://ubuntuforums.org/showthread.php?t=1859558&page=3](http://ubuntuforums.org/showthread.php?t=1859558&page=3)
Post 21.
If that does not work then try this please:
[http://ubuntuforums.org/showthread.php?t=1865420&page=2](http://ubuntuforums.org/showthread.php?t=1865420&page=2)
Post 12.

I am not on much right now, I am helping someone with a guide for the forum.
Good Luck

---

### Post by smaring on 2011-10-30
I have the oh-so-dreaded Intel 5100 AGN inside my HP Pavilion dv7 laptop.

I was able to connect to my AP on my cell phone just fine, but had trouble, after the upgrade to 11.10, connecting to my also dreaded, Linksys WRT54G.

Disabling "n" capabilities on the card did not help matters.  Downgrading to a 2.6.32 kernel did not help either.

What DID help was replacing "NetworkManager" with "wicd".  That worked on both the old and new kernels WITH "n" capabilities enabled on the card.

Given my performance observations of the two kernels, however, I will DEFINITELY be sticking with the 2.6.32 kernel.  It is WAY faster and I don't see the occasional hangs that I had been experiencing on a couple different boxes running the 3.0.0 kernel.

I hope this saves some poor sole the aggravation I went through.

Cheers,
Steve Maring
Tampa, FL

---

### Post by smaring on 2011-11-11
an update ...

It would appear that a recent update now has the 3.0.X kernel working with my wireless and NetworkManager without having to use wicd.  Strangely, the 2.6.X kernel still requires wicd to connect to my AP.

-Steve Maring
Tampa, FL

---

### Post by wildmanne39 on 2011-11-11
Hi smaring, glad to hear it.
Enjoy

---

### Post by esaloch on 2012-01-16
found a solution at [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325)

```
rmmod iwlagn
modprobe iwlagn bt_coex_active=0
```

---

### Post by ajcjh on 2012-03-03
Thank you esaloch, that seemed to do the trick.
I made it permanent by editing the iwlagn.conf file

sudo gedit /etc/modprobe.d/iwlagn.conf

and adding the line:

options iwlagn bt_coex_active=0

---

### Post by netxph on 2012-03-05
> **ajcjh said:**
> Thank you esaloch, that seemed to do the trick.
I made it permanent by editing the iwlagn.conf file

sudo gedit /etc/modprobe.d/iwlagn.conf

and adding the line:

options iwlagn bt_coex_active=0

It work... mine however is...

options iwlwifi bt_coex_active=0

:)

---

### Post by Stretchkev1 on 2012-04-25
When trying the above solution I get an error message:

```
rmmod iwlagn
ERROR: Removing 'iwlagn': Operation not permitted
```

Is there a work around this?

---

### Post by wildmanne39 on 2012-04-25
Hi Stretchkev1, try it like this:
```
sudo rmmod iwlagn
```
are you sure you are using that driver?
Thanks

---

### Post by Stretchkev1 on 2012-04-25
Thank you wildmanne39. That worked brilliantly.  

Now to make the changes permanent.

---

### Post by wildmanne39 on 2012-04-25
Hi Stretchkev1, glad to help.

---

### Post by twodogs on 2012-11-09
I have Asus U56E laptop.

I'm running Mint 13 Cinnamon 64-bit / Ubuntu 12.04 with 3.2.0-23 kernel.

sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0
make permanent with
gksu gedit /etc/modprobe.d/iwl.conf
Copy/paste this line into the new file:
options iwlagn bt_coex_active=0
then, to fix slow internet
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
make permanent with
gksu gedit /etc/modprobe.d/iwlagn-disable11n.conf
options iwlagn 11n_disable=1

The first two lines do it for me (wireless works).  I created an alias...
alias wifi='sudo modprobe -r iwlagn && sudo modprobe iwlagn bt_coex_active=0'
and I have a terminal automatically open when I log in (add gnome-terminal to startup applications).  I just type in 'wifi' and enter password and I'm surfin' the net.  A little extra work but I like the extra securtiy. ;)

Hope this helps.

---

### Post by rakan21 on 2012-12-04
so I'm currently running on Elementary OS Luna, and I got the same problem. I've gone through all the solutions listed here and I got nothing. I was wondering if anyone happened to know if this problem has been fixed in 12.10? 

I realized that this problem occurred after I suspended my laptop. I was wondering if that happened with anyone else? And if so, does anyone have a solution yet?

[Found a solution after Googling for hours. And I'm sure it's been mentioned here, but I have no idea why I didn't try it. ]
[Solution "sudo gedit /etc/modprobe.d/iwlwifi.conf" and adding "options iwlwifi bt_coex_active=0" ]

---

### Post by rDwyP44y on 2012-12-04
Thank you to the experts in this field, i had this issue on my friends laptop.

the past few weeks i've been runing only Ubuntu only!  Time to get rid of Windows :)

---

