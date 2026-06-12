---
title: "Wireless Network not connecting"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by JazzTrmpter on 2010-08-08
[FONT=Arial]Hi.
I know there are so many other threads about this, but there have been no solutions (that I have found) so far for me yet.  I have to say I started my own because everybody's setup is different, and I couldn't find one person with the same.  However, the same problems exist for so many people.  

So, I have a Dell Inspiron 531 and am dual booting Vista and Ubuntu 10.04.  I am using the Linksys WUSB100 wireless USB adapter with the rt2870[/FONT][I][FONT=Arial] chipset.  The wireless USB adapter does pick up other networks, including my own, and when I try to join, it asks for the password, as usual.  However, after a minute or less the password prompt pops up again.  There is no incorrect password message, it just doesn't connect.  
Here is the output of a few commands (lsusb, lsmod, ifconfig, route, [/FONT][/I]cat /etc/resolv.conf).

```
~$ lsusb
Bus 002 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1737:0070 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
rt2870sta             461811  0 
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
rt2800usb              31531  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
snd_timer              19098  2 snd_pcm,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
led_class               2864  1 rt2x00lib
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
font                    7557  1 fbcon
nvidia               9961216  38 
bitblit                 4707  1 fbcon
mac80211              205146  2 rt2x00usb,rt2x00lib
softcursor              1189  1 bitblit
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                31724  1 nvidia
soundcore               6620  1 snd
i2c_nforce2             5199  0 
cfg80211              126517  2 rt2x00lib,mac80211
vga16fb                11385  1 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
psmouse                63245  0 
dell_wmi                1793  0 
k8temp                  3024  0 
lp                      7028  0 
crc_ccitt               1339  1 rt2800usb
serio_raw               3978  0 
dcdbas                  5422  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
pata_amd                8766  0 
forcedeth              49556  0 
sata_nv                19440  1 

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:7d:61:43  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe7d:6143/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12380261 (12.3 MB)  TX bytes:1285143 (1.2 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:d9:4d:b7  
          inet6 addr: fe80::21e:e5ff:fed9:4db7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3290 (3.2 KB)  TX bytes:12534 (12.5 KB)

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
david@ubuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain lv.cox.net
search lv.cox.net
nameserver 68.105.28.11
nameserver 68.105.29.11
nameserver 68.105.28.12
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 192.168.1.1
~$ 

```If you need anymore output of other commands, let me know and I will put them up ASAP.  Thanks in advance! :D

**[update 8.8.2010] ** I did a little more research and am proud to say I am on a wireless connection at the moment.  Here's what I did:Run these commands, making changes to the latter.

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic

``````
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```Change the entire file to:

> [INDENT][main]
plugins=ifupdown,keyfile


 [ifupdown]
managed=true


 [ifdown]
managed=true


 [ifup]
managed=true
[/INDENT]Now restart your computer, make sure the wired connection is unplugged because it uses the wired over the wireless.

The blog on wordpress.com did say the connection was not very stable at first or very fast.  I will post back before posting as solved.

Here's my sources:
[http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/](http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/)
[http://edtake.wordpress.com/2010/05/04/ubuntu-slow-wireless-after-upgrading-to-10-04/](http://edtake.wordpress.com/2010/05/04/ubuntu-slow-wireless-after-upgrading-to-10-04/)

**[update 8.8.2010]**  Alright, about 15 minutes after using a steady wireless connection it all of a sudden dropped.  I am connected again after re-entering my password at the password prompt for the wireless network.

---

### Post by dineshs on 2010-08-09
post #3 in this thread says that a *similar* problem was solved by updating
[http://ubuntuforums.org/showthread.php?t=1548353](http://ubuntuforums.org/showthread.php?t=1548353)

---

### Post by Talon2 on 2010-08-09
This bug might shed some light:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

Feel free to jump in and add your experience to this bug.

---

### Post by ScorpiA on 2010-08-09
Worked perfectly.. thanks for the edit on that buddy :)

---

