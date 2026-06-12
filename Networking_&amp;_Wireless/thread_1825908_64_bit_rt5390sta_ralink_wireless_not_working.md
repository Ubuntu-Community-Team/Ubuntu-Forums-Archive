---
title: "64 bit rt5390sta ralink wireless not working"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by cbolton12000 on 2011-08-15
I installed the driver from Ralink (2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO) and followed the instructions in other threads and my card does not work. I am getting this message. 
"$ dmesg | grep -e rt5 -e wlan
[   14.454006] rt5390sta: module license 'unspecified' taints kernel.
 I have also installed the Ralink RutilT program using synaptic. I can see my wireless device and many others around me but I can't connect. Any ideas?
It's a Compac CQ56 64 bit.:confused:

---

### Post by varunendra on 2011-08-16
Hello cbolton12000, and welcome to the forums!

I'd like to get the related info the standard and more comprehensive way.
Open a terminal, enter the following commands one by one and post their outputs in your new post here:
```
ifconfig -a
iwconfig
sudo lshw -C network
lsmod | grep rt
rfkill list all
```Copy each set of output with your cursor, and paste it here in your new post. Wrap each set of outputs in [noparse]```
..and..
```[/noparse] tags separately to display them in a formatted and more readable way in the post. You can do it automatically by selecting the pasted text, then clicking on the **#** symbol at the top of the edit box.

---

### Post by cbolton12000 on 2011-08-17
eth0      Link encap:Ethernet  HWaddr 78:ac:c0:55:21:52  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7aac:c0ff:fe55:2152/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121576949 (121.5 MB)  TX bytes:5715943 (5.7 MB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

---

### Post by cbolton12000 on 2011-08-17
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by cbolton12000 on 2011-08-17
*-network               
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rt2860 latency=0
       resources: irq:16 memory:93500000-9350ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 78:ac:c0:55:21:52
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.109 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA

---

### Post by cbolton12000 on 2011-08-17
parport_pc             36959  0 
rt5390sta            1332701  0 
parport                46458  3 parport_pc,ppdev,lp

"rfkill list all" did not return anything
I have also uninstalled the Ralink RutilT program, it is for another card and I didn't want to mud things up.

---

### Post by varunendra on 2011-08-18
Sorry for a late response. I've got super busy for a couple of days. May not get back until monday (or maybe even later). A few quick observations:-
> **cbolton12000 said:**
> 
  *-network DISABLED
       description: **Wireless interface**
       physical id: 2
**        logical name: ra0**
       capabilities: ethernet physical wireless
       configuration: broadcast=yes [COLOR=Red]**driver=RALINK WLAN**[/COLOR] multicast=yes wireless=Ralink STA

While your lsmod has:-
> **cbolton12000 said:**
> parport_pc             36959  0 
**rt5390sta **           1332701  0 
parport                46458  3 parport_pc,ppdev,lp
Accordingly following are a few quick suggestions:

[LIST]
[*]Make sure the wireless interface is physically turned 'On'
[*]Check if it is enabled in BIOS
[*]Some BIOS have an inbuilt feature to DISABLE wireless interface when there is a wired connection (ethernet). So make sure to disconnect the LAN cable, wait a few second, and re-run lshw -C network to see if the wireless interface (ra0) gets enabled.
[*]currently, the **rt5390sta **driver doesn't seem to be in use although it is loaded by kernel (output of lsmod). Try adding RALINK WLAN driver to blacklist.conf file and restart to see if **rt5390sta **gets loaded instead.
[/LIST]
To add RALINK WLAN to blacklist, open gedit as super user:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```and add "blacklist RALINK WLAN" (without quotes) at the bottom of the file. Save it, and close the file. Restart computer for the change to take effect.

Apart from this, please post the complete output of:
```
lsmod
```And please wrap your outputs in code tags. Many potential troubleshooters who can otherwise take interest and solve your problem may not look at your posts when it is unformatted and cluttered.
You only have to add [noparse]```
 and 
```[/noparse] tags at the beginning and end of the outputs.

For example:-
1) [COLOR=DarkRed]This is text without code tags[/COLOR]

2)you have to add [noparse]```
 and 
```[/noparse] around it so that it looks like:
[noparse]```
[/noparse][COLOR=DarkRed]This is text with code tags[/COLOR][noparse]
```[/noparse]

As its effect, the text in your post will look like:
```
[COLOR=DarkRed]This is text with code tags[/COLOR]
```

---

### Post by cbolton12000 on 2011-08-19
Checked bios, no issues there, blacklisted RALINK WLAN.
re-run lshw -C network ```
  *-network UNCLAIMED     
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:93500000-9350ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 78:ac:c0:55:21:52
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff 
```
lsmod ```
Module                  Size  Used by
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  346 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
binfmt_misc            17565  1 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13706  0 
snd_timer              29602  2 snd_pcm,snd_seq
sparse_keymap          13898  1 hp_wmi
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usblp                  18233  0 
lp                     17825  0 
psmouse                73535  0 
serio_raw              13166  0 
soundcore              12680  1 snd
joydev                 17606  0 
parport                46458  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
hid_logitech           17693  0 
ff_memless             13097  1 hid_logitech
usbhid                 46956  1 hid_logitech
hid                    91020  2 hid_logitech,usbhid
i915                  515121  3 
drm_kms_helper         42136  1 i915
ahci                   25951  2 
r8169                  48022  0 
libahci                26642  1 ahci
drm                   227534  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915

```
Thanks!

---

### Post by praseodym on 2011-08-21
Did you adjust the files ~/RTZ2860STA.dat and ~/os/linux/config.mk before compiling? Otherwise the original Realtek-drivers dont work with both network-manager and wpa_supplicant. [Here]("http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747") is a modified driver version, but with german settings in RT2860STA.dat. You may modify it to your country settings before compiling

---

### Post by lkjoel on 2011-08-22
Could you run the Network Info script (in my signature), and attach the generated file?

---

