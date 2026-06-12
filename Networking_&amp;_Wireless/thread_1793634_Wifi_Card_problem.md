---
title: "Wifi Card problem"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by ComptutsXV on 2011-06-29
Ok, I have a TP-Link Tl-WN861N wifi card that i just got for my Ubuntu 11.04 system and im having some problems with it. 

The speeds are terrible. I have never had WiFi problems before, i normally got around 30 ping 15 mbps down and about 2 mbps up. Now with this new card i tested it and it got 473 ping 2.1 mbps down and .1 mbps up.

Are there any drivers i can install that might make it not so dsl like?

---

### Post by ComptutsXV on 2011-06-30
bump

---

### Post by Bucky Ball on 2011-06-30
I a terminal, type or paste:

```
lshw -C network
```

Post result for your card back here. TP-Link, yes, but use a chip from another manufacturer. 

Also, have you plugged in an ethernet cable, gotten updates? Checked System>Administration>Additional Drivers to see if there is anything for your card disabled?

---

### Post by ComptutsXV on 2011-06-30
*-network:0             
       description: Wireless interface
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan1
       version: 01
       serial: d8:5d:4c:be:18:c8
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.0.103 latency=168 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:ebef0000-ebefffff
  *-network:1
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:13:72:e6:83:ab
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:ebeef000-ebeeffff ioport:ccc0(size=64)
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: ham0
       serial: a6:79:90:e8:27:4a
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A multicast=yes port=twisted pair speed=10Mbit/s
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


and no there are no additional drivers for it

---

### Post by Bucky Ball on 2011-06-30
Thanks. Now the result of:

```
iwconfig
```You are using:

```
product: AR922X Wireless Network Adapter
```... with this driver:

 ```
driver=ath9k driverversion=2.6.38-8-generic
```In other words, the driver is part of your currently running kernel. If  you click your network icon, do you see your wireless network there? To get specific, could you run:

```
lspci
```... and look for the bit that starts headed 'Network Controller'. That should give you more detail about your Atheros card.

---

### Post by ComptutsXV on 2011-07-01
lo        no wireless extensions.

eth0      no wireless extensions.

ham0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"Dwyer"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:AF:F7:D8:F4:7B   
          Bit Rate=270 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0


i can connect its just really really slow

---

### Post by ComptutsXV on 2011-07-01
bump

---

### Post by ComptutsXV on 2011-07-01
also here is my lsmod results

```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
arc4                   12473  2 
binfmt_misc            13213  1 
nvidia               9766978  40 
ath9k                 103633  0 
snd_hda_codec_idt      60537  1 
mac80211              257001  1 ath9k
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_usb_audio          91410  1 
snd_pcm                80244  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
uvcvideo               66851  0 
snd_hwdep              13274  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
usbhid                 41704  0 
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
usblp                  17827  0 
dcdbas                 14054  0 
hid                    77084  1 usbhid
videodev               75143  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73312  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
firewire_ohci          31504  0 
e100                   40108  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

```

---

### Post by Bucky Ball on 2011-07-01
```
lspci
```

... in a terminal. Look for the line that starts with this:

```
03:00.0 Network controller:
```

What comes after that? We need to know what Atheros wireless card you are using exactly. You are perhaps using a dated driver from the Ubuntu repos and there might be a better one available from Atheros.

---

### Post by ComptutsXV on 2011-07-01
Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)

---

### Post by ComptutsXV on 2011-07-01
bump

---

### Post by ComptutsXV on 2011-07-02
bump

---

### Post by Bucky Ball on 2011-07-02
In the address bar of Firefox, type about:config
Click 'Agree'
Search for IPv6
'Disable IPv6=True'
Restart Firefox

Can't find much info on your card apart from the fact it generally works. Lot of 'stops working intermittently', but nothing much about slow speed. Try madwifi and see if that helps. They provide drivers for the ath9K. If you're using Network Manager you might also try wicd and vice versa but I'd go the madwifi first. Good luck. ;)

[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by gnusci on 2011-07-02
Did you try the 10.04 Live CD ?

---

### Post by danflakes on 2011-07-08
Hi

I had 10.04 running and 10.10 running fine. I didn't notice a problem. I thought it might be my install media but changed to a usb drive but still have WiFi problems. I went ahead with the install but its still not working. 

Anyone working on a fix?:confused:

---

### Post by G4dget on 2012-04-29
I have ar922x in a TP-LINK TL-WN861N mini pci card. if you are having issues connecting get rid of network manager and get wicd instead.

Using the ath9k driver and unsure of the driver version number as that is not in my lswh information. I have low signal strength and am unable to see other networks in my area that i know are there. This seems to be an issue with the kernal/driver as ubuntu states. Not sure if there is a solution to this yet

edit: i have since been able to get a specific driver installed by using```
sudo apt-get linux-backports-modules-wireless-lucid-generic
```
if you have a wired connection or just grab the packages from packages.ubuntu.com

This has not fixed my horrible signal reception issue
 I have since upgraded to the 3.0 kernal now with the new module and still bad reception. 

Anyone heard anything about a possible fix or hardware hack?

---

### Post by G4dget on 2012-05-29
Soooo.... after some extensive research and trying to fix the issue of bad connectivity and poor signal strength with my card i finally noticed that i had never plugged the antenna wires on to the wireless card as i thought they were temp probes at first (face palm) Now everything is working fine. Had some minor issues getting wicd to connect but I found that if you remove network-manager from the command line that it resolved the issue of wicd returning bad password errors.

Hope this sheds some light on the issue for someone out there.

---

### Post by Bucky Ball on 2012-05-29
You are better to remove Network Manager if you are running Wicd. Running them on the same machine is not advised and can cause issues.

---

