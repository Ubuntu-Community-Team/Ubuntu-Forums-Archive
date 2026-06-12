---
title: "Network - wired connection problem"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by mohamed1042002 on 2011-04-19
i don't know why no one answer me it's my third post in this web site and non answer to help me .......
thx to all

---

### Post by Rubi1200 on 2011-04-19
Hi and welcome to the forums :-)

First thing I want to say is that although I understand you want to get things working as quickly as possible, you need to understand that this is a volunteer forum. Nobody gets paid to help and sometimes the person who knows exactly how to fix your problem may be asleep in another part of the world.

Okay, lecture time over.

I am not a networking expert, but this is the information you need to post here if you want us to help you.

1. go to Applications > Accessories > Terminal and run this command:
```
sudo lshw -C network
```You can copy and paste the results from the terminal into a new post

2. we also need to see the results of this command:
```
ifconfig
```3. finally, the contents of the following file can also help:

```
cat /etc/network/interfaces
```Again, post the information here.

I hope someone will come along and help you soon, but you need to be patient please.

---

### Post by Elfy on 2011-04-19
Please do not post duplicates - I've closed the other 2 threads and renamed this one.

Have a look at - [http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by josephmills on 2011-04-19
When some one puts a code in they want to you to go to **Applications-->Accessories--> Terminal ** then type in the code (hint) to paste in the terminal press **shift+ctrl+v **To copy it is **shift+ctrl+c**
hope that this helps you
also please take a look at this 
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
thank you and welcome to Ubuntu:)

---

### Post by josephmills on 2011-04-19
>  i still got problem in net connection after i do all wat people said .
 i need a good answer tell me how to fix it.** and continou answer me not give me just 1 answer and leave.** i got wired connection using Ubuntu 10.10 and im new using ubuntu pls tell me where i must write the words not to write codes and i don't where i must do it.
 Another Question..... what is the best version of Ubuntu didn't had that problems?
 as i saw that Ubuntu 10.10 had same problem for all people.
 thx to all
 mohamed
where are you ???????????

---

### Post by mohamed1042002 on 2011-04-19
[FONT=Arial Black][SIZE=3][COLOR=YellowGreen]sry for all for what i wrote. i was mad form Ubuntu i know no one get money from that and help people for nothing and im greatful for that thx to all and i repeat im sry [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=YellowGreen]im late becuz i was being in Ubuntu try to fix it[/COLOR][/SIZE]
[FONT=Arial Black][SIZE=3][COLOR=Red] first         Sudo  lshw -C network :[/COLOR][/SIZE][/FONT]
 
[FONT=Arial Black][SIZE=2][COLOR=Black]*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:02:fa:12
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:47 memory:f4000000-f4000fff
 *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:1a:d6:7a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:c000(size=256) memory:f8000000-f8000fff memory:80000000-8001ffff
[/COLOR][/SIZE][/FONT]
[FONT=Arial Black][SIZE=3][COLOR=Red]second     ifconfig [/COLOR][/SIZE][/FONT]
 

[FONT=Arial Black][SIZE=2][COLOR=Black]eth0      Link encap:Ethernet  HWaddr 00:1e:68:1a:d6:7a  
          inet6 addr: fe80::21e:68ff:fe1a:d67a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080 (1.0 KB)  TX bytes:4757 (4.7 KB)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9600 (9.6 KB)  TX bytes:9600 (9.6 KB)[/COLOR][/SIZE][/FONT]

[FONT=Arial Black][SIZE=3][COLOR=Red]third      cat /etc/network/interfaces[/COLOR][/SIZE][/FONT]


[FONT=Arial Black][SIZE=2][COLOR=Black]auto lo
iface lo inet loopback[/COLOR][/SIZE][/FONT]

---

### Post by josephmills on 2011-04-19
hi  again could we see a ```
dmesg | grep iwl3945
``` amd a ```
rfkill list all 
``` and a ```
lsmod
``` and a ```
dmesg | grep r8169 
``` thanks

---

### Post by mohamed1042002 on 2011-04-19
[FONT=Arial][SIZE=3][COLOR=YellowGreen]here what u want im sry for late but im turned btween Ubuntu and Window7[/COLOR][/SIZE][/FONT]
[FONT=Arial Black][SIZE=3][COLOR=Red]dmesg | grep iwl3945
[/COLOR][/SIZE][/FONT]
[FONT=Arial Black][SIZE=2][COLOR=Black][   15.682624] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   15.682628] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   15.682710] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.682725] iwl3945 0000:02:00.0: setting latency timer to 64
[   15.785964] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   15.785968] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945BG
[   15.786187] iwl3945 0000:02:00.0: irq 47 for MSI/MSI-X
[/COLOR][/SIZE][/FONT]
[FONT=Arial Black][SIZE=3][COLOR=Red]rfkill list all[/COLOR][/SIZE][/FONT]

[FONT=Arial][SIZE=2][COLOR=Black]0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
[/COLOR][/SIZE][/FONT]
[FONT=Arial Black][SIZE=3][COLOR=Red]lsmod[/COLOR][/SIZE][/FONT]

[FONT=Arial][SIZE=2][COLOR=Black]Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_si3054     3440  1 
snd_hda_codec_realtek   217980  1 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
nouveau               516971  2 
iwl3945                85550  0 
snd_rawmidi            17783  1 snd_seq_midi
iwlcore               127415  1 iwl3945
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56633  1 nouveau
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231541  2 iwl3945,iwlcore
drm_kms_helper         30200  1 nouveau
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
hp_wmi                  5191  0 
drm                   168054  4 nouveau,ttm,drm_kms_helper
intel_agp              26360  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
snd                    49006  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  8735  0 
psmouse                59033  0 
cfg80211              144470  3 iwl3945,iwlcore,mac80211
mtd                    18877  2 sm_common,nand
serio_raw               4022  0 
soundcore                880  1 snd
video                  18712  0 
i2c_algo_bit            5168  1 nouveau
agpgart                32011  3 ttm,intel_agp,drm
output                  1883  1 video
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sdhci_pci               6339  0 
firewire_ohci          21106  0 
sdhci                  15890  1 sdhci_pci
firewire_core          46643  1 firewire_ohci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
ahci                   19013  0 
r8169                  36489  0 
libahci                21667  3 ahci
mii                     4425  1 r8169[/COLOR][/SIZE][/FONT]

[FONT=Arial Black][SIZE=3][COLOR=Red]dmesg | grep r8169[/COLOR][/SIZE][/FONT]

[FONT=Arial][SIZE=2][COLOR=Black][    0.891570] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.891598] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.891656] r8169 0000:06:00.0: setting latency timer to 64
[    0.891760] r8169 0000:06:00.0: irq 44 for MSI/MSI-X
[    0.910860] r8169 0000:06:00.0: eth0: RTL8101e at 0xf80a4000, 00:1e:68:1a:d6:7a, XID 94200000 IRQ 44
[   16.231242] r8169 0000:06:00.0: eth0: link up
[   16.231253] r8169 0000:06:00.0: eth0: link up[/COLOR][/SIZE][/FONT]

---

### Post by josephmills on 2011-04-19
try ```
rfkill unblock all
``` then ```
rfkill list all
``` then post thanks

---

### Post by mohamed1042002 on 2011-04-19
i wish i say thanks but nothing happen . still no connection 
that appear in terminal 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yesrfkill unblock all
 
i lost my mind with Ubuntu

---

### Post by josephmills on 2011-04-19
> **mohamed1042002 said:**
> [COLOR=Olive][SIZE=3][FONT=Arial Black]i wish i say thanks but nothing happen . still no connection 
that appear in terminal 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    **Hard blocked: yes**
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    **Hard blocked: yes**
2: phy0: Wireless LAN
    Soft blocked: no
    **Hard blocked: yes**    rfkill unblock all
 
i lost my mind with Ubuntu 
[/FONT][/SIZE][/COLOR]

all the parts that are in bold are some of the things that are going wrong when it says ```
hard blocked:yes
```  that means that the device is turned off and you need to turn it on there should be a button for this. try this until it says  ```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``` that will mean that the switch is turned on.

---

### Post by mohamed1042002 on 2011-04-19
[FONT=Arial Black][SIZE=3][COLOR=Black]im sry but 
what codes i must repeat ? [/COLOR][/SIZE][/FONT]

---

### Post by josephmills on 2011-04-19
> **mohamed1042002 said:**
> [FONT=Arial Black][SIZE=3][COLOR=Black]im sry but 
what codes i must repeat ? [/COLOR][/SIZE][/FONT]

you need to turn the computer off plug in the ethernet cord then turn it back on again after rebooting. press your **wireless button** on your machine. It is turned off. You need to turn it on. What kind of computer is this?

---

### Post by mohamed1042002 on 2011-04-19
[FONT=Arial Black][SIZE=4][COLOR=Black]it's HP Pavilion 6700notebook [/COLOR][/SIZE][/FONT]

---

### Post by mohamed1042002 on 2011-04-19
I Still have the problem .I don't know why i can't fix it

---

### Post by josephmills on 2011-04-19
Wireless button
Your computer has a wireless button 1 that will enable or disable
all integrated wireless devices simultaneously. In addition, a
wireless light 2 indicates the computer’s overall wireless state
(enabled or disabled). The wireless light does not reflect the
status of individual devices (unless the computer has only one
wireless device). When the wireless light is on, one or more of the
wireless devices are on.

---

### Post by mohamed1042002 on 2011-04-19
im sry for my stuiped mind but im not understand what should i do ?

---

### Post by josephmills on 2011-04-19
press the button until it turns on (the light will change color)

---

### Post by Iowan on 2011-04-19
I don't mean to compound your problems... :(
From Code of Conduct:
> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

---

### Post by mohamed1042002 on 2011-04-19
i do all what u say i turnd it on and still got  no connection with wired 
any new ideas

---

### Post by josephmills on 2011-04-19
> **mohamed1042002 said:**
> i do all what u say i turnd it on and still got  no connection with wired 
any new ideas

show me ```
rfkill list all
``` again please

---

### Post by mohamed1042002 on 2011-04-19
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by josephmills on 2011-04-19
could I please see ```
cd /etc/apt/sources.list.d
``` then ```
ls
```

---

### Post by mohamed1042002 on 2011-04-20
when i put the frist code then the second nothing appear 
but when i just put the second code first that appear 

Desktop    Downloads         Music     pppoeconf  Templates
Documents  examples.desktop  Pictures  Public     Videos

---

### Post by mohamed1042002 on 2011-04-20
i still wait for any help here 
pls if any one can help me  he just do it i'll be greatful for him

---

### Post by Elfy on 2011-04-20
Please stop bumping your thread.

Once in 24 hours is sufficient.

---

### Post by dineshs on 2011-04-21
_Wired_
From lshw -C network the device is
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
And the driver loaded is
driver=r8169
This may be the problem(I am not sure).
_Wireless_
Should work since it is enabled now (Unplug ethernet cable and try to connect wireless)
Can you post the output of ```
ipconfig /all
```on [COLOR="Red"]Windows[/COLOR] (when the connection is working) ?

---

