---
title: "Getting eth instead of wlan"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by lordbux on 2011-11-11
Ok SO:
[B][COLOR="Green"]
Please note: this is a new found trouble and did not have this till some weeks back.[/COLOR][/B]

I have a Ethernet port and a Wireless card (on board).
but when i check ifconfig i get a strange output.
```

eth0      Link encap:Ethernet  HWaddr 1c:75:08:86:ef:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 

eth1      Link encap:Ethernet  HWaddr 4c:ed:de:a2:fd:49  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4eed:deff:fea2:fd49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:402551 errors:11 dropped:0 overruns:0 frame:355006
          TX packets:351108 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:231549343 (231.5 MB)  TX bytes:133451644 (133.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44415600 (44.4 MB)  TX bytes:44415600 (44.4 MB)



```

I get 2 eth connections instead of one eth and a wlan.
**What is causing this.**

The result for iwconfig clearly shows that
the eth1 got in place of wlan0
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:177  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

and for information reasons i am posting my lspci output:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```
[B][COLOR="Green"]
My wireless is a broadcom device.[/COLOR][/B]

[B]
For research and study reasons i need this as wlan0 itself as this condition do not permit me to use many tools and hardware i use for my project.[/B]

Please provide a work around. whom ever can.

Thanks in advance.:popcorn:
:(

USING TOSHIBA C660 Laptop

---

### Post by haqking on 2011-11-11
as mentioned previously in your other closed thread here [http://ubuntuforums.org/showthread.php?t=1878817](http://ubuntuforums.org/showthread.php?t=1878817), you are better off seeking advice in a aircack forum or similar.

such as [http://www.aircrack-ng.org](http://www.aircrack-ng.org)

There is plenty on there referencing broadcom. And any tools similar will work will eth1, it doesnt have to be wlan0

good luck

---

### Post by lordbux on 2011-11-11
> **haqking said:**
> as mentioned previously in your other closed thread, you are better off seeking advice in a aircack forum or similar.

such as [http://www.aircrack-ng.org](http://www.aircrack-ng.org)

There is plenty on there referencing broadcom. And any tools similar will work will eth1, it doesnt have to be wlan0

good luck

thanx bro, but it is not about aircrack alone, my devices do not recognize. eth1 as wireless. as i can't change those firmwares. 

sorry if i am sounding  off minded.  but the thing is.
[B]I found wlan0 when i put in the liveCD or used BackTrack Live From USB.
[/B]
So the trouble maybe correctable right.

---

### Post by haqking on 2011-11-11
> **lordbux said:**
> thanx bro, but it is not about aircrack alone, my devices do not recognize. eth1 as wireless. as i can't change those firmwares. 

sorry if i am sounding  off minded.  but the thing is.
[B]I found wlan0 when i put in the liveCD or used BackTrack Live From USB.
[/B]
So the trouble maybe correctable right.

you need to update the firmware of your device then, the correct firmware/drivers for your device (for your purposes) will be found on the aircrack/bt wiki.

example [http://www.aircrack-ng.org/doku.php?id=broadcom](http://www.aircrack-ng.org/doku.php?id=broadcom)

good luck

---

### Post by sffvba[e0rt on 2011-11-11
*Thread **closed** for **review**.*


404

---

### Post by Iowan on 2011-11-11
OP, 
[SOLVED] is not the only (or even the primary) reason that threads get closed.

---

### Post by sffvba[e0rt on 2011-11-11
*Thread **re-opened**.*


404

---

### Post by wildmanne39 on 2011-11-11
Hi, did your change happen when you upgraded ubuntu?

Post the results of:
```
lspci -nnk | grep -iA2 net
```
and we will see if a different driver can be used.
Thank you

---

### Post by lordbux on 2011-12-18
> **wildmanne39 said:**
> Hi, did your change happen when you upgraded ubuntu?

Post the results of:
```
lspci -nnk | grep -iA2 net
```
and we will see if a different driver can be used.
Thank you

My working Version of ubuntu is 10.04 Lucid
Not been upgraded, was a fresh install.

ya had run software updates tho

```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Kernel driver in use: r8169
	Kernel modules: r8169
06:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl

```

**Sorry for late reply had exams n stuff :)**
**Thanks mods for reopening the thread, luv ya all**

---

### Post by wildmanne39 on 2011-12-18
Hi, you are getting eth1 because of the driver you are using, it looks like you can use the b43 driver also.

Please let me know what version of ubuntu you are using.

This should get you going.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
unplug your wired connection and reboot.
Thank you

---

### Post by lordbux on 2011-12-18
oops ran into trouble

```
sudo apt-get install b43-fwcutter firmware-b43-installerReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer

```

---

### Post by wildmanne39 on 2011-12-18
Hi, were you connected to the internet when you tried to install b43?
Thanks

---

### Post by lordbux on 2011-12-18
> **wildmanne39 said:**
> Hi, were you connected to the internet when you tried to install b43?
Thanks

yes even now i am
It seems it is not in repositories the firmware installer

---

### Post by wildmanne39 on 2011-12-18
Hi, r u still running 10.04 ubuntu?
Thanks

---

### Post by lordbux on 2011-12-18
> **wildmanne39 said:**
> Hi, r u still running 10.04 ubuntu?
Thanks

yep 10.04 Lucid Lynx

---

### Post by wildmanne39 on 2011-12-18
Hi, okay this is what you need to do it may or may not work but it is the only way that I know of to change the eth1 to wlan0.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter
```
Then unplug wired connection and reboot.
Thank you

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
Hey I run 10.04 and it is in the repos... you need to enable all of them.
I need firmware-b43-installer and I installed it just the other day...  (I reinstalled 10.04 side-by-side with 11.10)
Cheers!

---

### Post by lordbux on 2011-12-18
> **wildmanne39 said:**
> Hi, okay this is what you need to do it may or may not work but it is the only way that I know of to change the eth1 to wlan0.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter
```
Then unplug wired connection and reboot.
Thank you

Wireless interface is no longer identified after doing this
and i checked repos no sight of the firmware-b43-installer

any way thanks for the idea, it may help me solve some problem with my BT5 tho it din work here.

So is there any other way this can be tackled

---

### Post by wildmanne39 on 2011-12-18
Hi, the firmware installer is not needed in 10.04 that is why I changed the command.

Please show results of the command:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

Before you change back to the other driver.
Thanks

---

### Post by lordbux on 2011-12-18
Please note
I have reinstalled the STA driver and removed b43 fwcutter

As i can't get connected in that condition brother:(

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
pci_stub                1102  1 
vboxpci                14531  0 
vboxnetadp              6808  0 
vboxnetflt             16652  0 
vboxdrv               249862  3 vboxpci,vboxnetadp,vboxnetflt
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   216061  1 
iptable_nat             3543  0 
nf_nat                 15560  1 iptable_nat
i915                  289683  4 
nf_conntrack_ipv4      10346  3 iptable_nat,nf_nat
nf_conntrack           60975  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          1549  0 
iptable_filter          1369  0 
ip_tables               9899  3 iptable_nat,iptable_mangle,iptable_filter
snd_hda_intel          20799  2 
x_tables               14175  2 iptable_nat,ip_tables
snd_hda_codec          87096  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34603  0 
snd_mixer_oss          13929  1 snd_pcm_oss
snd_pcm                71646  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1498  0 
snd_seq_oss            27626  0 
snd_seq_midi            4621  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48042  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18710  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     7596  0 
snd                    56687  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 i915
psmouse                63677  0 
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
uvcvideo               57406  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
intel_agp              24375  2 i915
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
drm                   163651  5 i915,drm_kms_helper
serio_raw               3978  0 
agpgart                31724  2 intel_agp,drm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  6 
r8169                  34140  0 
mii                     4381  1 r8169

```

---

### Post by wildmanne39 on 2011-12-18
Hi, it is possible that you never will but I was going to give you commands to run so I could get the information needed to try to make it connect with the other driver.
Thanks

---

### Post by lordbux on 2011-12-19
> **wildmanne39 said:**
> Hi, it is possible that you never will but I was going to give you commands to run so I could get the information needed to try to make it connect with the other driver.
Thanks

thats fine....so is there some hope bro :)

---

### Post by wildmanne39 on 2011-12-19
Hi, probably not with 10.04 if you upgraded to 11.10 then possibly.
Thanks

---

### Post by lordbux on 2011-12-19
> **wildmanne39 said:**
> Hi, probably not with 10.04 if you upgraded to 11.10 then possibly.
Thanks

ok then .. will work on it

---

