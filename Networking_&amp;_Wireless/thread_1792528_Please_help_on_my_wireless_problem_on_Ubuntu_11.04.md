---
title: "Please help on my wireless problem on Ubuntu 11.04"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by kheong on 2011-06-28
First of all I'm using HP Pavilion dv4 2115 tx 

lpcsi 


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

> Bus 002 Device 004: ID 090c:137b Feiya Technology Corp. 
Bus 002 Device 003: ID 04b4:1220 Cypress Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 138a:0005 DigitalPersona, Inc 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


iconfig
> eth0      Link encap:Ethernet  HWaddr 70:5a:b6:89:c2:7b  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::725a:b6ff:fe89:c27b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8984685 (8.9 MB)  TX bytes:997313 (997.3 KB)
          Interrupt:41 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:81:fd:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



lsmod
> 
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath9k                 103669  0 
uvcvideo               66851  0 
i915                  450979  7 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               75143  1 uvcvideo
joydev                 17322  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ir_sony_decoder        12493  0 
mac80211              257001  1 ath9k
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
ath9k_common           13611  1 ath9k
drm                   184133  3 i915,drm_kms_helper
psmouse                59039  0 
ath9k_hw              300328  2 ath9k,ath9k_common
hp_accel               21632  0 
rc_rc6_mce             12454  0 
ir_jvc_decoder         12490  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc6_decoder         12490  0 
ath                    19141  2 ath9k,ath9k_hw
fglrx                2434640  0 
i2c_algo_bit           13184  1 i915
intel_ips              17769  0 
cfg80211              156212  3 ath9k,mac80211,ath
serio_raw              12990  0 
lis3lv02d              19285  1 hp_accel
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
ene_ir                 22309  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
input_polldev          13735  1 lis3lv02d
rc_core                25760  9 ir_lirc_codec,ir_sony_decoder,rc_rc6_mce,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ene_ir
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
usb_storage            43946  0 
hid                    77084  1 usbhid
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  46630  0 


[FONT=Verdana]
[/FONT]sudo lshw -C network
> 
 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 0c:60:76:81:fd:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:e6400000-e640ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 70:5a:b6:89:c2:7b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:e2404000-e2404fff memory:e2400000-e2403fff memory:e2420000-e243ffff


Description:    Ubuntu 11.04
2.6.38-8-generic-pae i686
sudo /etc/init.d/networking restart

---

### Post by bkratz on 2011-06-28
What problems are you experiencing? It all looks pretty healthy. Can you not see available networks or not connect to one?

---

### Post by kheong on 2011-06-28
the first problem will be my wireless card is not able to detect any wireless connection, please help!

---

### Post by josephmills on 2011-06-28
could we see a ```
rfkill list all 
``` thanks

---

### Post by kheong on 2011-06-28
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes


thanks :)

---

### Post by josephmills on 2011-06-28
> **kheong said:**
> 0: phy0: Wireless LAN
    Soft blocked: no
  [COLOR="Red"]  Hard blocked: yes[/color]
1: hp-wifi: Wireless LAN
    Soft blocked: no
   [COLOR="red"] Hard blocked: yes[/color]
[COLOR="red"]2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
[/color]

thanks :)


hit your wireless switch the do a ```
rfkill unblock all 
```anything if not please make sure the wifi switch is turned on if it is a dell try fn+f2   then paste ```
rfkill list all 
``` again thanks

---

### Post by kheong on 2011-06-28
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


the wireless in on but still not able to find any network. please adviseeee

---

### Post by josephmills on 2011-06-28
could we see a ```
sudo iwlist scan
```yuo can take out mac address and ip also  thanks

---

### Post by kheong on 2011-06-28
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:A4:BC:58:19
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"yapwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004e0388818f
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 000779617077696669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010118
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020200000000

---

### Post by josephmills on 2011-06-28
I take it then when you try to connect and enter password it just sits there and spins ?then asks again ?

---

### Post by kheong on 2011-06-28
nope i'm not able to click any wifi devices. please guide me

---

### Post by josephmills on 2011-06-28
try ```
sudo modprobe ath9k
```  anything?

---

### Post by kheong on 2011-06-29
i couldn't proceed the password, it seems like not allow me to input the password at all. if i press enter, it still cannot apply the password

---

### Post by RochJer on 2011-06-29
I was experiencing the same issue with other thread I posted few days ago. I have same screenshot issue as kheong had - wifi devices disappeared after installing Linux Kernel 3.0 and when before it disappears, I could not apply passwords on my 2WIRE108 as my wifi device.

---

### Post by sanderj on 2011-06-29
> **kheong said:**
> i couldn't proceed the password, it seems like not allow me to input the password at all. if i press enter, it still cannot apply the password

Is this your own system?
Did you install Ubuntu yourself?
Are you using the account under which you installed Ubuntu? Or are you using an additional account?

Reason: only the user that did the install has the rights to setup networking.

---

### Post by RochJer on 2011-06-29
> **kheong said:**
> i couldn't proceed the password, it seems like not allow me to input the password at all. if i press enter, it still cannot apply the password

I did the same thing and did change my router settings on 2Wire modem - WPA2-TKIP, WPA and WPA2 TKIP, WEP Open and Shared. Ubuntu 11.04 still deny me the wifi access with any passwords I have entered, including key OR password.

---

### Post by Drone4four on 2011-06-29
I'm experiencing a very similar problem.  

> **josephmills said:**
> I take it then when you try to connect and enter password it just sits there and spins ?then asks again ?

This is exactly the symptom I experience with the wifi in the classroom in which I am trying to connect.  My thread is here: [http://ubuntuforums.org/showthread.php?t=1658885](http://ubuntuforums.org/showthread.php?t=1658885)

---

### Post by kheong on 2011-06-30
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

---

