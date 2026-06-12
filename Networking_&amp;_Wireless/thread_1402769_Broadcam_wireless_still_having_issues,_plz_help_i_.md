---
title: "Broadcam wireless still having issues, plz help i dnt wanna go back to vista :("
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by actsofaith on 2010-02-09
Hi
  After days of research, I managed to finally get my broadcom sta wireless 'active and ready to use', yet i still cant seem to log on to the internet. Their is  blue light on for the wireless indicating its on, and i am picking up wireless signals, but when i try to log on to my network it says "wireless disconnected" every time. Im kinda stuck at this point, so here i am asking for your help, any leads will be appreciated. 
Please keep your answers noob friendly!
thanks in advance

---

### Post by Tim_nz on 2010-02-09
does a wired connection work?
what card and drivers are you using? run in terminal "lspci" (without quotes)

---

### Post by actsofaith on 2010-02-09
> **Tim_nz said:**
> does a wired connection work?
what card and drivers are you using? run in terminal "lspci" (without quotes)
hi  TIm, thanks for replying 
 i dont have a wired connection, im using a broadcom bcm4312 as my network controller and a realtek as ethernet controller, heres what i get for lspci 
**************************************************************
[COLOR=black][FONT=Verdana]~$ lshw -c network[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]WARNING: you should run this program as super-user.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]PCI (sysfs)  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  *-network               [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       description: Wireless interface[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       product: BCM4312 802.11b/g[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       vendor: Broadcom Corporation[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       physical id: 0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       bus info: pci@0000:02:00.0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       logical name: eth1[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       version: 01[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       serial: 00:21:00:55:84:f6[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       width: 64 bits[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       clock: 33MHz[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       capabilities: bus_master cap_list ethernet physical wireless[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       resources: irq:18 memory:d8500000-d8503fff[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  *-network[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       physical id: 0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       logical name: eth0[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       version: 02[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       serial: 00:1e:ec:bb:96:03[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       width: 64 bits[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       clock: 33MHz[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       capabilities: bus_master cap_list rom ethernet physical[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]       resources: irq:31 ioport:3000(size=256) memory:d2410000-d2410fff(prefetchable) memory:d2400000-d240ffff(prefetchable) memory:d2420000-d243ffff(prefetchable)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]fadwa@seaglass:~$ [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]fadwa@seaglass:~$ lspci[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller[/FONT][/COLOR]

---

### Post by actsofaith on 2010-02-09
can any of the passerby's tell me how i can check to see  if i properly installed my bcm4312? im not sure how i got it to work, i jus messed with it based on the many threads ive been reading, so any code would be appreciated
thansk

---

### Post by bkratz on 2010-02-09
Also, please  post the output of

iwconfig

and also

sudo iwlist scan

---

### Post by actsofaith on 2010-02-09
heres everything you need to know 
**[COLOR=black][FONT=Verdana]1 ) Machine Brand and Model (PC/Laptop)[/FONT][/COLOR]**[COLOR=black][FONT=Verdana]:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]HP Pavilian [/FONT][/COLOR]

**[COLOR=black][FONT=Verdana]2 ) Wireless Brand, Model and Wireless Chipset:[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E P[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]([/FONT][/COLOR][COLOR=red][FONT=Verdana]hint[/FONT][/COLOR][COLOR=black][FONT=Verdana]) use **grep** to get only information about the Wireless[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$ [/FONT][/COLOR]

**[COLOR=black][FONT=Verdana]3 ) check interface:[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang] ifconfig[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]eth0      Link encap:Ethernet  HWaddr 00:1e:ec:bb:96:03  [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          collisions:0 txqueuelen:1000 [/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          Interrupt:31 Base address:0xc000 [/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]eth1      Link encap:Ethernet  HWaddr 00:21:00:55:84:f6  [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          inet6 addr: fe80::221:ff:fe55:84f6/64 Scope:Link[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          RX packets:0 errors:0 dropped:0 overruns:0 frame:2301[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          TX packets:7 errors:6 dropped:0 overruns:0 carrier:0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          collisions:0 txqueuelen:1000 [/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          RX bytes:0 (0.0 B)  TX bytes:2450 (2.4 KB)[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          Interrupt:18 [/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lo        Link encap:Local Loopback  [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          RX packets:8 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          collisions:0 txqueuelen:0 [/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]fadwa@seaglass:~$ iwconfig[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lo        no wireless extensions.[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]eth0      no wireless extensions.[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]eth1      IEEE 802.11  Nickname:""[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]          Access Point: Not-Associated   [/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]([/FONT][/COLOR][COLOR=red][FONT=Verdana]hint[/FONT][/COLOR][COLOR=black][FONT=Verdana]) if the Wireless interface name is wlan0 you can also use[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Batang] iwconfig wlan0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]wlan0     No such device[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
**[COLOR=black][FONT=Verdana]4 ) Check for modules:[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$  lsmod[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]Module                  Size  Used by[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]udf                    80900  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]crc_itu_t               1852  1 udf[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]b43                   122136  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]ssb                    35300  1 b43[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]mac80211              181236  1 b43[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]cfg80211               93052  2 b43,mac80211[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]nls_iso8859_1           3740  1 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]nls_utf8                1568  1 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]isofs                  31620  2 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]nls_cp437               5372  1 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]vfat                   10716  1 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]fat                    51452  1 vfat[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]binfmt_misc             8356  1 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]ppdev                   6688  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_hda_codec_intelhdmi    12860  1 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_hda_codec_idt      59844  1 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_hda_intel          26920  2 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_hwdep               7200  1 snd_hda_codec[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_pcm_oss            37920  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_mixer_oss          16028  1 snd_pcm_oss[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_seq_dummy           2656  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_seq_oss            28576  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]joydev                 10272  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]hp_accel               11228  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lis3lv02d               7452  1 hp_accel[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_seq_midi            6432  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]ndiswrapper           185404  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_rawmidi            22208  1 snd_seq_midi[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]jmb38x_ms               9600  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]iptable_filter          3100  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lib80211_crypt_tkip     8636  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_timer              22276  2 snd_pcm,snd_seq[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]psmouse                56180  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]memstick               10072  1 jmb38x_ms[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]uvcvideo               59080  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]ip_tables              11692  1 iptable_filter[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lp                      8964  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]input_polldev           3716  1 lis3lv02d[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]sdhci_pci               7100  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]serio_raw               5280  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]wl                   1272936  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]sdhci                  17472  1 sdhci_pci[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]videodev               36736  1 uvcvideo[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lirc_ene0100            8096  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]led_class               4096  3 b43,hp_accel,sdhci[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]v4l1_compat            14496  2 uvcvideo,videodev[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]soundcore               7264  1 snd[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lib80211                6432  2 lib80211_crypt_tkip,wl[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]x_tables               16544  1 ip_tables[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]lirc_dev               10804  1 lirc_ene0100[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]parport                35340  2 ppdev,lp[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]snd_page_alloc          9156  2 snd_hda_intel,snd_pcm[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]fbcon                  36640  72 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]tileblit                2460  1 fbcon[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]font                    8124  1 fbcon[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]bitblit                 5372  1 fbcon[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]softcursor              1756  1 bitblit[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]usb_storage            52544  2 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]r8169                  32064  0 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]mii                     5212  1 r8169[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]i915                  221064  3 [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]drm                   159584  3 i915[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]i2c_algo_bit            5760  1 i915[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]intel_agp              27484  2 i915[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]agpgart                34988  2 drm,intel_agp[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]video                  19380  1 i915[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]output                  2780  1 video[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]([/FONT][/COLOR][COLOR=red][FONT=Verdana]hint[/FONT][/COLOR][COLOR=black][FONT=Verdana]) search for the Wireless module[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$ lsmod | grep "wlan_module_name"[/FONT][/COLOR]

[COLOR=black][FONT=Courier New]**couldnt get an output for this[/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]5 ) Kernel boot messages[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$ [/FONT][/COLOR]

[COLOR=black][FONT=Verdana]([/FONT][/COLOR][COLOR=red][FONT=Verdana]hint[/FONT][/COLOR][COLOR=black][FONT=Verdana]) the same as in (4)

**6 ) Network configuration**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$  *-network               [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][SIZE=3][FONT=Batang]       description: Wireless interface[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       product: BCM4312 802.11b/g[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       vendor: Broadcom Corporation[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       physical id: 0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       bus info: pci@0000:02:00.0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       logical name: eth1[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       version: 01[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       serial: 00:21:00:55:84:f6[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       width: 64 bits[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       clock: 33MHz[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       resources: irq:18 memory:d8500000-d8503fff[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]  *-network[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       description: Ethernet interface[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       physical id: 0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       bus info: pci@0000:03:00.0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       logical name: eth0[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       version: 02[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       serial: 00:1e:ec:bb:96:03[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       size: 10MB/s[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       capacity: 100MB/s[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       width: 64 bits[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       clock: 33MHz[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Batang]       resources: irq:31 ioport:3000(size=256) memory:d2410000-d2410fff(prefetchable) memory:d2400000-d240ffff(prefetchable) memory:d2420000-d243ffff(prefetchable)[/FONT][/SIZE][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
**[COLOR=black][FONT=Verdana]7 ) Scan for networks:[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$  iwlist scan[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]lo        Interface doesn't support scanning.[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]eth0      Interface doesn't support scanning.[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Courier New]eth1      Interface doesn't support scanning.[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]([/FONT][/COLOR][COLOR=red][FONT=Verdana]hint[/FONT][/COLOR][COLOR=black][FONT=Verdana]) the same as in (3)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$ iwlist scan wlan0[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]iwlist: unknown command `wlan0' (check 'iwlist --help').[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
**[COLOR=black][FONT=Verdana]8 ) Ubuntu Version: [/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$ lsb_release -d[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]Description:      Ubuntu 9.10[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
**[COLOR=black][FONT=Verdana]9 ) Kernel/architecture (including 32 vs. 64 bit): [/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]$ uname -mr[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][FONT=Courier New]2.6.31-14-generic i686[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
**[COLOR=black][FONT=Verdana]10 ) Restarting the network:[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo /etc/init.d/networking restart[/FONT][/COLOR]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[COLOR=black][SIZE=3][FONT=Batang] * Reconfiguring network interfaces...                                   [ OK ]$ sudo /etc/init.d/networking restart[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Verdana]Add this information to the post, even is the output is and error, and more if you have, and describe your issue.[/FONT][/COLOR]

---

### Post by wojox on 2010-02-09
I have the same card. Used:

```
sudo apt-get install bcmwl-kernel-source
```

Reboot and your done.

---

### Post by bkratz on 2010-02-09
Since I see the modules b43, and ssb above along with the correct wl, I think posting #2 of this thread will probably help. (Read the whole thread first, of course to see if your symptoms match).

[http://www.uluga.ubuntuforums.org/showthread.php?t=1308533](http://www.uluga.ubuntuforums.org/showthread.php?t=1308533)


did you try to use ndiswrapper previously, I see that module also.

---

### Post by Tristan Tonks on 2010-02-09
That chipset is a classic problem, the solution is there as I have solved it on three laptops now in the last year but unfortunatly each one was different. The one consistent element of the final solutions was NdisWrapper.

[INDENT]sudo apt-get install NDISwrapper[/INDENT]

The program enables the use of windows driver for the network card. You will also need to ensure you have the correct driver for the chipset. the last one I used was bcmw15.inf if I remember correctly.
It is one of the more difficult jobs but it is possible and worth it so good luck.
I will try to find the links to the other posts.

This is the other program I used along with a forum that nicely explains it's implementation, you will still need the driver though which you can find in your windows system32/drivers if you still have it on your computer.

fwcutter is the program but not sure if you can apt-get  *it*.

[http://www.linuxquestions.org/questions/linux-newbie-8/no-wireless-connection-after-installing-ubuntu-on-my-acer-travelmate-5520-help-621197/]("http://www.linuxquestions.org/questions/linux-newbie-8/no-wireless-connection-after-installing-ubuntu-on-my-acer-travelmate-5520-help-621197/")

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> Since I see the modules b43, and ssb above along with the correct wl, I think posting #2 of this thread will probably help. (Read the whole thread first, of course to see if your symptoms match).
 
[http://www.uluga.ubuntuforums.org/showthread.php?t=1308533](http://www.uluga.ubuntuforums.org/showthread.php?t=1308533)
 
 
did you try to use ndiswrapper previously, I see that module also.
  
thanks for the thread, i tried the sudo modprobe -r b43 ssb wl 
sudo modprobe wl and sudo iwlist scan they all cam back with  "Warning: all config files need .conf" is this something i should be worried about?

---

### Post by bkratz on 2010-02-09
No that is just a normal warning ignore it



By the way did your AP's show up when you did the sudo iwlist scan?

---

### Post by actsofaith on 2010-02-09
> **Tristan Tonks said:**
> That chipset is a classic problem, the solution is there as I have solved it on three laptops now in the last year but unfortunatly each one was different. The one consistent element of the final solutions was NdisWrapper.
[INDENT]sudo apt-get install NDISwrapper
[/INDENT]The program enables the use of windows driver for the network card. You will also need to ensure you have the correct driver for the chipset. the last one I used was bcmw15.inf if I remember correctly.
It is one of the more difficult jobs but it is possible and worth it so good luck.
I will try to find the links to the other posts.
 
This is the other program I used along with a forum that nicely explains it's implementation, you will still need the driver though which you can find in your windows system32/drivers if you still have it on your computer.
 
fwcutter is the program but not sure if you can apt-get *it*.
 
[http://www.linuxquestions.org/questions/linux-newbie-8/no-wireless-connection-after-installing-ubuntu-on-my-acer-travelmate-5520-help-621197/](http://www.linuxquestions.org/questions/linux-newbie-8/no-wireless-connection-after-installing-ubuntu-on-my-acer-travelmate-5520-help-621197/)
 
Hi Tristan, 
i took ndiswrapper route, then used fwcutter , that helped activate the broadband card, from what i can remember i used bcmw5.inf and  bcmw5.sys, those two i got from two different sources, makes me wonder if mayb i set things up wrong?? im not even sure where to go from here, really for me a difficult thing can be near friggin impossible hehe if you come up with somtin  like a thread that might apply 
pls let me know

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> No that is just a normal warning ignore it
 
 
 
By the way did your AP's show up when you did the sudo iwlist scan?
ive got something roughly looking like 
lo- interface dsnt support blah
eth0-same
eth1- scan completed and there are seven cells , looks like there from my wireless router 
seems good till i  try to Actually connect

---

### Post by bkratz on 2010-02-09
Well it sounds like you are just about there. Are you using any encryption and if so can you temporarily remove it to see if you can connect?
What happens when you actually try to connect?



By the way I found another really good thread about your card   (esp post 12)

[http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf](http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf)

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> Well it sounds like you are just about there. Are you using any encryption and if so can you temporarily remove it to see if you can connect?
What happens when you actually try to connect?
 
 
 
By the way I found another really good thread about your card (esp post 12)
 
[http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf](http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf)
 
thats comforting, i am looking at the thread as i type and it looks like some useful info,  kudos for that, about the encryption , i really wouldnt know if i was, im not even sure what that is or how i could find that out, tell me then ill let you know 
thanks for bearing with me, you have helpd alot

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> Well it sounds like you are just about there. Are you using any encryption and if so can you temporarily remove it to see if you can connect?
What happens when you actually try to connect?
 
 
 
By the way I found another really good thread about your card (esp post 12)
 
[http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf](http://ubuntuforums.org/showthread.php?t=1347483&highlight=bcmwl5.inf)
 
help, post #12 worked in the wrong way for me , my internet is now disabled??!? how can i undo this?
i think im back to scratchh ='(((

---

### Post by bkratz on 2010-02-09
Try 

sudo modprobe wl

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> Try 
 
sudo modprobe wl
 goody, i have wifi now, can connect and all \\:D/almost there,
now i jus have to get  the websites too load 
btw your awesome!

---

### Post by bkratz on 2010-02-09
So you actually can connect now?  Are you saying that you just can't access websites now?  If so, how do you have network manager setup?  I will have to do some more searching to see what we should do next, if I am interpreting what you are saying correctly.

Can you actually ping websites by address or name?

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> So you actually can connect now? Are you saying that you just can't access websites now? If so, how do you have network manager setup? I will have to do some more searching to see what we should do next, if I am interpreting what you are saying correctly.
 
Can you actually ping websites by address or name?
 right, thats xctly wat im saying cant access websites, ur soo good at this heheh
k, well i dont have a network manager, network tools has the ping option so that could be , i tried it with a website had to force quit, ip address  shows 5 packets sent and 5 recieved, 100 %

---

### Post by bkratz on 2010-02-09
so, you were able to ping ip addresses, but not by names?

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> so, you were able to ping ip addresses, but not by names?
yea like i could ping yahoo ip 209.191.93.53, tho when i try to get to yahoo in the brwser its says server not found
hope this clarifies it

---

### Post by bkratz on 2010-02-09
> **actsofaith said:**
> yea like i could ping yahoo ip 209.191.93.53, tho when i try to get to yahoo in the brwser its says server not found
hope this clarifies it

There is a whole section here

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

on " 4.5. Connected but no internet
4.5.1. DNS"

That may be of some help. I will do some searching, but it may take awhile.

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> There is a whole section here
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
 
on " 4.5. Connected but no internet
4.5.1. DNS"
 
That may be of some help. I will do some searching, but it may take awhile.
 
thanks again , i checked out the site both options didnt apply because my ipv6 was disabled by default, tho i have been looking around researching, nothing good yet, im about ready for a short hiatus,ill  pick this up tomorrow,hope to hear from u again by then 
v. kind of you to assist me with all my noobnesss ^_^

---

### Post by actsofaith on 2010-02-09
> **bkratz said:**
> There is a whole section here
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
 
on " 4.5. Connected but no internet
4.5.1. DNS"
 
That may be of some help. I will do some searching, but it may take awhile.
ignore my last message, im online , best feelin ever!!
i had the wrong dns for nameserver , this site was alot of help [http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/](http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/)
 its a good now  thanks so much now i can put this thread as [Solved]:guitar:

---

### Post by northd_tech on 2010-02-10
If it helps anyone else, here is a good older thread about the Broadcom wireless chipset family:

**Re: How to install native broadcom drivers for BCM4311, BCM4312, BCM4321, and BCM432**
[http://ubuntuforums.org/showthread.php?t=896713&page=21](http://ubuntuforums.org/showthread.php?t=896713&page=21)

I've been seeing a lot of posts lately about trouble with the Broadcom 4312 (and it is nearly always with Karmic 9.10).  My Broadcom 4321AG has been working perfectly under 64-bit Jaunty 9.04 using the proprietary Broadcom STA driver for several months now.

---

### Post by bkratz on 2010-02-10
> **actsofaith said:**
> ignore my last message, im online , best feelin ever!!
i had the wrong dns for nameserver , this site was alot of help [http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/](http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/)
 its a good now  thanks so much now i can put this thread as [Solved]:guitar:

Boy it is nice to wake up and see everything is good with the world! Congratulations you worked hard.  To mark the thread solved please go to the thread tools above and select [mark as solved]. This will help others find and see your effort.


By the way, thanks for the link, I archived it.

---

