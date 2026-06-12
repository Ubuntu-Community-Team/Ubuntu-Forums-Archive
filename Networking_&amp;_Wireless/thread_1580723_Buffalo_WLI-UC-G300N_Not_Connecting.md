---
title: "Buffalo WLI-UC-G300N Not Connecting"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by dot09 on 2010-09-23
I have a Buffalo WLI-UC-G300N Wireless Lan Adapter that is not connecting to my wireless router.  It sees all my neighbors' wireless networks in addition to my own.  I have checked and double checked that I'm entering the wireless key correctly but it will not connect to my network.  In fact, I have tried to connect to unprotected networks and it will not connect.

The device works fine in Windows XP and Windows 7.

I downloaded the latest RALink drivers from here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
I have followed the directions here: [http://ubuntuforums.org/archive/index.php/t-960642.html](http://ubuntuforums.org/archive/index.php/t-960642.html)

In this user's instructions I step 18 part b?  But the rest I have completed without incident.  I still cannot connect.

I don't even know how to tell if I'm using the driver that shipped and was recognized or the one I just compiled and installed.

I'm not a nOOb, but I've never had to run down a problem like this so please be gentle.

I searched for other articles about my given wireless adapter and I don't see anything specific in these forums.  Your help is greatly appreciated.

---

### Post by blakep2 on 2010-09-23
What kind of router is it and does it have MAC restrictions.

---

### Post by dot09 on 2010-09-24
It's a buffalo router.  The original long range one but the model escapes me.  It's been reloaded with ddwrt for a very long time.

This PC can boot into Windows and connects fine.

---

### Post by blakep2 on 2010-09-24
Ok does it have MAC restrictions?  What is the dhcp range.  What is the ip address of the router? Are there any other access points?  Please type ipconfig in the windows machine and ifconfig in the ubuntu machine.  please paste results here.

---

### Post by dot09 on 2010-09-24
There are no MAC restrictions.  DHCP Range is .100-.200.  The router is .1.

```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:fd:--:--  
          inet addr:192.168.42.122  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::250:----:----:6680/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:338208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27520494 (27.5 MB)  TX bytes:1046088 (1.0 MB)
          Interrupt:22 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:73:bc:--:--  
          inet6 addr: fe80::21d:----:----:71fa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11573 (11.5 KB)  TX bytes:2793 (2.7 KB)
```

That'll have to do for now ;)  I have a long @$$ network cable strung to this PC and I'm typing from the Ubuntu side :)

---

### Post by dot09 on 2010-09-24
```
Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : kulai.org
   Description . . . . . . . . . . . : BUFFALO WLI-UC-G300N Wireless LAN Adapter

   Physical Address. . . . . . . . . : 00-1D-73-BC------
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::c08e:9a79:----:----%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.42.135(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Friday, September 24, 2010 7:03:42 PM
   Lease Expires . . . . . . . . . . : Saturday, September 25, 2010 7:03:41 PM
   Default Gateway . . . . . . . . . : 192.168.42.1
   DHCP Server . . . . . . . . . . . : 192.168.42.1
   DHCPv6 IAID . . . . . . . . . . . : 218111---
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-90------------------------

   DNS Servers . . . . . . . . . . . : 192.168.42.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : kulai.org
   Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet
 NIC
   Physical Address. . . . . . . . . : 00-50-8D---------
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::fcc9:2d1a:----:----%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.42.122(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Friday, September 24, 2010 7:02:44 PM
   Lease Expires . . . . . . . . . . : Saturday, September 25, 2010 7:02:43 PM
   Default Gateway . . . . . . . . . : 192.168.42.1
   DHCP Server . . . . . . . . . . . : 192.168.42.1
   DHCPv6 IAID . . . . . . . . . . . : 234901---
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-90------------------------

   DNS Servers . . . . . . . . . . . : 192.168.42.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

---

### Post by blakep2 on 2010-09-24
Do you have a wired and wireless connection on each machine.  If so this can be a problem.

---

### Post by dot09 on 2010-09-27
It's not.  I appreciate your enthusiasm.

I have tried with only the wireless.  It was only out of frustration that I ran a cable to the PC as I didn't want to search for answers on another machine and try to apply the fixes to this PC.

---

### Post by dot09 on 2010-09-27
This PC connects via the Buffalo USB wireless device in Windows 7 perfectly.  This is only an issue with my Ubuntu desktop installation.  All other things are equal.

---

### Post by blakep2 on 2010-09-28
Ok,  have you done a update on the ubuntu machine since you installed it.
Also check for driver updates.

---

### Post by dot09 on 2010-09-28
I have updated the machine many times since installing.  If checking for driver updates includes something other than running the "Update Manager" or opening the "Hardware Drivers" app in System->Administration then no, I have not.

---

### Post by dot09 on 2010-09-28
```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
rt2800usb              31531  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd_seq_midi            4557  0 
rt2x00usb               9703  1 rt2800usb
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
rt2x00lib              27509  2 rt2800usb,rt2x00usb
snd_rawmidi            19056  1 snd_seq_midi
softcursor              1189  1 bitblit
nvidia               7087672  34 
led_class               2864  1 rt2x00lib
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              205402  2 rt2x00usb,rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
vga16fb                11385  1 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vgastate                8961  1 vga16fb
cfg80211              126496  2 rt2x00lib,mac80211
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
crc_ccitt               1339  1 rt2800usb
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
psmouse                63245  0 
intel_agp              24119  1 
shpchp                 28820  0 
agpgart                31724  2 nvidia,intel_agp
serio_raw               3978  0 
lp                      7060  0 
joydev                  8708  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
usb_storage            39553  0 

```

More info.  Don't know if it's helpful.

---

### Post by blakep2 on 2010-09-28
> **dot09 said:**
> I have updated the machine many times since installing.  If checking for driver updates includes something other than running the "Update Manager" or opening the "Hardware Drivers" app in System->Administration then no, I have not.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Check this out

---

