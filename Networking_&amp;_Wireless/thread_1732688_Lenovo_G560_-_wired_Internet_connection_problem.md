---
title: "Lenovo G560 - wired Internet connection problem"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by chaushev on 2011-04-18
Hey guys, 
I am new to linux. I started with installing Ubuntu 10.10 on my laptop Lenovo G560 along with my Windows 7, so I had a dual boot system.

**Right after the installation I had wired Internet connection working. The problem was that after few minutes browsing and especially after starting to update, either from terminal or GUI menu, the connection went down.** Under Windows 7 I had absolutely no issues regarding Internet connection - neither wired nor wireless. I tried to add manually all IP addresses and change different settings but nothing seamed to work.
**On the other hand, I had absolutely no problems with my wireless connection which comes from the same ISP.**
 I updated my system using terminal: sudo aot-get update / sudo apt-get upgrade
All finished successfully and after reboot, no matter what settings and changes I made I could only connect to wireless network. Its like my LAN stopped working. Since my wireless signal is only 40%, I would really like to set my cable connection.
As I said I am quite new and nuub to Linux but I wish to learn. Here is some info taken with lspci command. If you need additional information I will do my best to post as soon as possible.
> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
** Thanks in advance**

---

### Post by Sergei_K on 2011-04-18
Sometimes network manager can couse such problems. Try removing it and setting up your connection by means of /etc/network/interfaces

---

### Post by MooPi on 2011-04-18
Can you give us the contents of /etc/network/interfaces
```
gedit /etc/network/interfaces
```

---

### Post by chaushev on 2011-04-18
Ok so I am currently connected to the wireless. Here is what the file reads:
> auto lo
iface lo inet loopback


---

### Post by MooPi on 2011-04-18
> **chaushev said:**
> Ok so I am currently connected to the wireless. Here is what the file reads:

```
gksudo gedit /etc/network/interfaces
```
Add this to the end of the file
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by chaushev on 2011-04-18
I suppose eth0 is supposed to be the name of my wired connection. In my case it is "Wired connection". I did what you said, and the result:

When i log in I see the network icon in the upper right corner loading. I also get some activity in the "Network box" (yellow and reg graph). In half a min trying to connect I get msg -  Disconnected. Pretty much the same when I try different no matter what settings to the wired connection. Here is a screen of what is goin on:
[B]
[IMG]http://img864.imageshack.us/img864/6257/screenshot1gu.png[/IMG]
[/B]

---

### Post by MooPi on 2011-04-18
Okay not an easy fix. from a terminal can you give us 
```
lsmod
```
and again the contents of 
```
etc/network/interfaces
```
and ```
ifconfig
```

---

### Post by chaushev on 2011-04-18
Okay here it is. Just to be clear - is it a problem if I give the output of those commands while connected to the wireless network - it's my neighbors access point - we got same ISP. 
**lsmod**
> dimitar@dimitar:~$ sudo lsmod
[sudo] password for dimitar: 
Module                  Size  Used by
michael_mic             1744  8 
arc4                    1165  4 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_hda_codec_nvhdmi    13615  4 
nvidia               9329739  41 
snd_hda_codec_conexant    30003  1 
snd_hda_intel          22235  3 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7736  0 
uvcvideo               55847  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
wl                   1959533  0 
video                  18712  0 
output                  1883  1 video
serio_raw               4022  0 
intel_agp              26566  0 
snd                    49038  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  2 lib80211_crypt_tkip,wl
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19198  4 
r8169                  36521  0 
mii                     4425  1 r8169
libahci                21728  1 ahci
dimitar@dimitar:~$ 
**sudo gedit etc/network/interfaces**
empty ?! ...

**ifconfig**
> dimitar@dimitar:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:21:0d:04  
          inet6 addr: fe80::8aae:1dff:fe21:d04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:423346 (423.3 KB)  TX bytes:12247 (12.2 KB)
          Interrupt:45 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:26:82:7c:41:ea  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:82ff:fe7c:41ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15475 errors:0 dropped:0 overruns:0 frame:198730
          TX packets:15419 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17622859 (17.6 MB)  TX bytes:3740509 (3.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1936 (1.9 KB)  TX bytes:1936 (1.9 KB)

dimitar@dimitar:~$ 


---

### Post by MooPi on 2011-04-18
Looks like your connected but not to eth0. Your using eth1.
```
gksudo gedit /etc/network/interfaces
```
Add this to the end of the file. 
```
# The primary network interface
auto eth1
iface eth1 inet dhcp
```

Proofread , save and reboot.

---

### Post by chaushev on 2011-04-18
I made the changes and rebooted as you said. When i logged back I didn't have my network icon in the upper right corner of the screen. No Internet connection again ...
[IMG]http://img88.imageshack.us/img88/4065/screenshot2lx.png[/IMG]

So I edited the file again and removed the lines you told me to add, leaving it like this:
> auto lo
iface lo inet loopback                      >reboot
 
Here is what happened. This time it seams to have connected to some wired network and It didnt show the disconected msg. No Internet though ...

[IMG]http://img814.imageshack.us/img814/1969/screenshot3ua.png[/IMG]

:neutral:

---

### Post by MooPi on 2011-04-18
Sorry but check last post I made because I had an error in the code.

```
# The primary network interface
auto eth1
iface eth1 inet dhcp
```
I listed iface eth0 inet dhcp incorrectly.

---

### Post by chaushev on 2011-04-18
I edited like this and rebooted:
[IMG]http://img859.imageshack.us/img859/7186/screenshot4f.png[/IMG]

When I logged I got a msg that lan cable is plugged. The network graph showed movement but there was no Internet connection. I tried to reconnect but still no Internet. After reboot I also had my wireless menu inactive(gray) so I had to edit back to 
> auto lo
iface lo inet loopbackso I can connect and post here.

edit: I am thinking ..is it perhaps because of my network drivers? Do I have the ones I need ? I did a little google search and I see other have troubles with wired connection with my ethernet model too.

---

### Post by MooPi on 2011-04-18
lsmod shows that you are using r8196 and that should be the correct driver

---

### Post by chaushev on 2011-04-18
any other ideas ?

---

### Post by chaushev on 2011-04-19
:(

---

### Post by MooPi on 2011-04-19
Yes if you insert the live CD and check if your ethernet port is functioning check lsmod in terminal and it should indicate the proper driver for your laptop. I will guess that r8169 works and it is just a setting away from working correctly.

---

### Post by chaushev on 2011-04-19
I booted with the Live CD. At first I did not seam to have Internet. Tried to load google.com from mozila firefox - no result. I quickly tried to add a weather thingy to the panel, and it acually showed some numbers, but after trying to update the info it went inactive again. 
Here is the lsmod info
> 
ubuntu@ubuntu:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
lp                      7342  0 
dm_crypt               11385  0 
parport                31492  3 parport_pc,ppdev,lp
snd_hda_codec_nvhdmi    12879  4 
snd_hda_codec_conexant    29736  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8735  0 
snd                    49006  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
squashfs               25209  1 
aufs                  152358  4500 
nls_cp437               4931  1 
isofs                  30022  1 
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
usbhid                 36882  0 
nouveau               516971  2 
hid                    67742  1 usbhid
ttm                    56633  1 nouveau
drm_kms_helper         30200  1 nouveau
ahci                   19013  0 
video                  18712  0 
drm                   168054  4 nouveau,ttm,drm_kms_helper
output                  1883  1 video
intel_agp              26360  0 
r8169                  36489  0 
libahci                21667  3 ahci
agpgart                32011  3 ttm,intel_agp,drm
mii                     4425  1 r8169
i2c_algo_bit            5168  1 nouveau
ubuntu@ubuntu:~$ I also got a system msg that I need some additional drivers:
[IMG]http://img121.imageshack.us/img121/7180/screenshotdj.png[/IMG]

after activating these drivers nothing changed.still no Internet
=======

Perhaps I should try install from the live cd in a virtual box? Right after the Ubuntu installation about a week ago as mentioned in my first post I had Internet. I will do a clean virtual box install and post lsmod info again.

---

### Post by chaushev on 2011-04-19
OK so I am posting right now from a new clean ubuntu installation. No updates done - i have Internet.
Here is lsmod info
> lstest@test-VirtualBox:~$ sudo lsmod
[sudo] password for test: 
Module                  Size  Used by
binfmt_misc             6599  1 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
parport_pc             26058  0 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  8735  0 
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
i2c_piix4               8635  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
e1000                  97525  0 
ahci                   19013  0 
libahci                21667  3 ahci
test@test-VirtualBox:~$ 


---

### Post by MooPi on 2011-04-19
This is odd. The driver that is working is e1000, which is an Intel chip. Take note and if your ethernet goes down a possible solution could be to blacklist r8169 in /etc/modprobe.d/blacklist.conf .
Example, of addition to blacklist
```
#blacklist realtek r8169 letting Intel e1000 work
blacklist r8169
``` 
You'll probably need to add e1000 to /etc/modules if this happens.
Also to start the module,```
sudo modprobe e1000
```
I'm not comfortable with this conclusion but if it works all the better

---

### Post by chaushev on 2011-04-19
Another strange thing just happened. I logged into Linux to try the stuff you suggested and I had wired Internet connection all working fine. For about 10min I browsed the web and it was all fine. I even got another lsmod and connection info while working. After few more minutes though it got lost again and neither changing ip's nor restart seamed to work. Really odd behavior.  I am going to do what you said now...

here is the lsmod while Inet is working just fine:
> dimitar@dimitar:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_hda_codec_nvhdmi    13615  4 
nvidia               9329739  41 
snd_hda_codec_conexant    30003  1 
snd_hda_intel          22235  1 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
uvcvideo               55847  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
snd_timer              19067  2 snd_pcm,snd_seq
lib80211_crypt_tkip     7736  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   1959533  0 
intel_agp              26566  0 
psmouse                59033  0 
serio_raw               4022  0 
snd                    49038  11 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  2 lib80211_crypt_tkip,wl
soundcore                880  1 snd
video                  18712  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19198  4 
libahci                21728  1 ahci
r8169                  36521  0 
mii                     4425  1 r8169
dimitar@dimitar:~$ 


---

### Post by chaushev on 2011-04-19
So ...I didn't post the last few hours because I wanted to test. I did exactly what you told me to. Changed what you have suggested the way you wrote it. Result:

**I have wired Internet connection! I do not get the annoying msg that my network has gone offline and unplugged. BUT ...after some random time, 20,30min  or an hour+ the Internet just goes down. No message, no error, nothing - the Internet icon in the corner stays the same. Ive been trying to figure out what exactly causes this to happen but couldn't rly find out. I may browse without a problem, leave the laptop idle for lets say 10min and when I come back - no Internet. So far only reboot seams to fix the problem.**

We certainly have some progress dealing with the problem, its just this annoying thing left. Thanks for all MooPi

---

