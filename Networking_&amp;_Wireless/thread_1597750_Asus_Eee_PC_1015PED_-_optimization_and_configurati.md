---
title: "Asus Eee PC 1015PED - optimization and configuration"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by drabowicz on 2010-10-15
I installed Ubuntu 10.10 today Netbook Edition on the Asus Eee PC 1015PED.

[SIZE=1]Specifications for Asus Eee PC 1015PED:
Atom  455, 1.66 GHz, 1Gb ram, 250Gb drive, Bluetooth 3.0, 0.3 megapixel  webcam, Gigabit Ethernet, WSVGA (1024x600), sound card compatible with  the HD audio connector, d-dub, three USB 2.0 ports, 6-cell - lithium Ion - 4400mAh, WiFi 802.11 b/g/n.[/SIZE]

Please solve the problem or an indication of the package to install.
Please tutorial under the title, which services to disable to boost performance.
**Please in the first place to help you connect to the Internet.**
Please help especially to the netbook'a - Asus Eee PC 1015PED.

I updated everything on connection via cable.
Detects the connection, but when it connects after a while.. "Wireless - Network Disconnected".

Sorry for my language ; )
```
**[COLOR=Red]lsmod[/COLOR]**
Module                  Size  Used by 
joydev                 10272  0 
usbhid                 38208  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
bridge                 47952  0 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel 
stp                     2272  1 bridge 
bnep                   12060  2 
snd_hwdep               7200  1 snd_hda_codec 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              22276  2 snd_pcm,snd_seq 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
x_tables               16544  1 ip_tables 
lp                      8964  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
uvcvideo               59080  0 
psmouse                56180  0 
videodev               36736  1 uvcvideo 
atl1c                  30880  0 
v4l1_compat            14496  2 uvcvideo,videodev 
eeepc_laptop           13936  0 
soundcore               7264  1 snd 
parport                35340  2 ppdev,lp 
btusb                  11856  2 
serio_raw               5280  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm 
fbcon                  36640  72 
tileblit                2460  1 fbcon 
font                    8124  1 fbcon 
bitblit                 5372  1 fbcon 
softcursor              1756  1 bitblit 
i915                  221064  3 
drm                   159584  3 i915 
i2c_algo_bit            5760  1 i915 
intel_agp              27484  2 i915 
agpgart                34988  2 drm,intel_agp 
video                  19380  1 i915 
output                  2780  1 video
``````
**[COLOR=Red]lspci[/COLOR]**
00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge 
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller 
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02) 
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0) 
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
``````
**[COLOR=Red]ifconfig[/COLOR]**
 eth0      Link encap:Ethernet  HWaddr 20:cf:30:43:23:a8   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:54551595 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:7038 errors:0 dropped:0 overruns:0 carrier:4  
           collisions:0 txqueuelen:1000  
           RX bytes:12080395 (12.0 MB)  TX bytes:699972 (699.9 KB)  
           Interrupt:46  
 

 eth1      Link encap:Ethernet  HWaddr 74:f0:6d:7e:68:5d   
           inet6 addr: fe80::76f0:6dff:fe7e:685d/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:17 Base address:0xc000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:46 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:46 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:4762 (4.7 KB)  TX bytes:4762 (4.7 KB)  
 
``````
**[COLOR=Red]iwconfig[/COLOR]**
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 eth1      IEEE 802.11  Access Point: Not-Associated    
           Link Quality:5  Signal level:0  Noise level:169  
           Rx invalid nwid:0  invalid crypt:0  invalid misc:0
 
``````
**[COLOR=Red]iwlist scan[/COLOR]**
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 eth1      Interface doesn't support scanning.
 
```

---

### Post by drabowicz on 2010-10-16
I'm waiting for any response.

---

### Post by 0x656b694d on 2010-11-11
Hey, any luck with wifi so far?

i'm thinking about buying one. Any other problems?

---

### Post by laurenbanjo on 2010-11-11
> **0x656b694d said:**
> Hey, any luck with wifi so far?

i'm thinking about buying one. Any other problems?

I downloaded UNR 10.10 on my netbook (Acer AspireOne D255) and at first it didn't detect any networks, so I was all mad yesterday. but today for some reason it's working fine. I haven't yet been disconnected and I've been on wifi for over three hours now.

EDIT: Well, I *assume* the wireless on UNR works. It didn't work at home yesterday. I tried it at school today and it detected networks but I couldn't connect 'cause I didn't know the passwords. When I got home I booted into the Desktop Edition (UNR comes with this!) and it worked no problem on this. Later on I can check UNR for you if you want.

---

### Post by 0x656b694d on 2010-11-12
laurenbanjo, thanks, i think i'll try UNR, but i'd like to be sure i can use wifi. Not sure the chipsets of Acer AspireOne and Asus eeePC are the same.

drabowicz noticed that in Asus 1015PED the wifi device had been recognized as
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
and didn't work.

---

### Post by 0x656b694d on 2010-11-12
So, the most interesting thing is if 1015PED can see the networks around and connect to them.
I got a Wifi-USB stick (Ralink), and can use it only as a router of my cable connection, it hardly can see any networks.

---

### Post by Azyx on 2011-01-06
I'm not sure about your problems.. but have you 'activated' the Wifi Fn+antenna-symbol' or have you checked BIOS-settings?

Does the graphic work well?

I'm intersted to by this ASUS, but if Ubuntu doesent work, I don't want to buy it.

---

### Post by 0x656b694d on 2011-01-06
Hi,

Well, i had to upgrade to 11.04 because i could not connect to some free public (unsecured) wifi networks with 10.10.

So i have all the Alpha issues now, but have wifi working everywhere.
No problems with graphics at all.

Just Unity interface is strange and unusable. So i'm running classic Gnome desktop.

The only problem actually is that indicator-application-service eats 100% CPU when trying to find wifi networks. So I have to remove indicator applet from the panel and kill the indicator-application-service.
Other things works fine.
(i wasn't able to make a few Fn keys working, so i cannot turn off touchpad. Brightness and sound volume buttons work).

If you'll buy one, don't format the entire HDD. You'll need a small partition for boot booster (can be restored though) and one (~20 GB) for ExpressGate. I wasn't able to install express gate from Ubuntu.

---

### Post by Azyx on 2011-01-07
> **0x656b694d said:**
> Hi,

Well, i had to upgrade to 11.04 because i could not connect to some free public (unsecured) wifi networks with 10.10.

So i have all the Alpha issues now, but have wifi working everywhere.
No problems with graphics at all.

Just Unity interface is strange and unusable. So i'm running classic Gnome desktop.

The only problem actually is that indicator-application-service eats 100% CPU when trying to find wifi networks. So I have to remove indicator applet from the panel and kill the indicator-application-service.
Other things works fine.
(i wasn't able to make a few Fn keys working, so i cannot turn off touchpad. Brightness and sound volume buttons work).

If you'll buy one, don't format the entire HDD. You'll need a small partition for boot booster (can be restored though) and one (~20 GB) for ExpressGate. I wasn't able to install express gate from Ubuntu.

ok. thanx for the tip. Does ExpressGate work fine?

---

### Post by 0x656b694d on 2011-01-07
ExpressGate worked fine until i deleted it :) so don't delete the EFI partitions.

Although i didn't try to use ExpressGate in public places so not sure how good wifi under it.

Now, with 11.04 i have no issues with wifi. If i cannot connect to a network, i ask to reset the router and after that i'm in.

---

