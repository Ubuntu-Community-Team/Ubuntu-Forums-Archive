---
title: "Broadcom Wireless in 10.04 (LTS)"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by BigYellowDog on 2011-01-18
I have a Dell Inspiron 1464, I can not get the wireless to start.  I can see my wireless router when I scan for wireless devices in knetwork manager.  But there is a yellow shield next to it, so I'm guessing something is missing.  I also see no network activity with tcpdump on another box on my home network 

```

[rob] ~ $ uname -a
Linux laptop 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
[rob] ~ $ 

``````

[rob] ~ $ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:76:9d:50
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:24:11:28
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.5 latency=0 multicast=yes
       resources: irq:31 ioport:2000(size=256) memory:f0810000-f0810fff(prefetchable) memory:f0800000-f080ffff(prefetchable) memory:f0820000-f083ffff(prefetchable)
[rob] ~ $ 

```

```

[rob] ~ $ lsmod
Module                  Size  Used by                                                                                                                                                           
ppdev                   6375  0                                                                                                                                                                 
fbcon                  39270  71                                                                                                                                                                
tileblit                2487  1 fbcon                                                                                                                                                           
font                    8053  1 fbcon                                                                                                                                                           
bitblit                 5811  1 fbcon                                                                                                                                                           
softcursor              1565  1 bitblit                                                                                                                                                         
vga16fb                12757  0                                                                                                                                                                 
vgastate                9857  1 vga16fb                                                                                                                                                         
snd_hda_codec_intelhdmi    13090  1                                                                                                                                                             
snd_hda_codec_realtek   279008  1                                                                                                                                                               
i915                  323510  2                                                                                                                                                                 
snd_hda_intel          25741  2                                                                                                                                                                 
dell_wmi                2177  0                                                                                                                                                                 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel                                                                                                     
snd_hwdep               6924  1 snd_hda_codec                                                                                                                                                   
snd_pcm_oss            41394  0                                                                                                                                                                 
snd_mixer_oss          16299  1 snd_pcm_oss                                                                                                                                                     
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss                                                                                                                         
snd_seq_dummy           1782  0                                                                                                                                                                 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
drm_kms_helper         30742  1 i915
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62595  0 
lib80211_crypt_tkip     8676  0 
videodev               40518  1 uvcvideo
joydev                 11104  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
snd                    71251  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             7941  0 
psmouse                64576  0 
serio_raw               4918  0 
dcdbas                  6886  1 dell_laptop
drm                   198948  3 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
intel_agp              29319  2 i915
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83472  1 usbhid
ahci                   37870  3 
r8169                  39714  0 
mii                     5237  1 r8169
[rob] ~ $ 

```

```

[rob] ~ $ rfkill list
[rob] ~ $ 

```

---

### Post by nm_geo on 2011-01-18
BigYellow,

It appears you may not have rfkill installed in your Kubuntu. 

Check in Synaptic or:

```
sudo apt-get update
sudo apt-get install rfkill
rfkill list  
```Here is mine rfkill list (switch enabled):
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Now with my switch off:

greg@greg-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
 
More to get:

```
sudo apt-get install hwinfo grep
sudo hwinfo --netcard 
```

---

### Post by BigYellowDog on 2011-01-18
I had rfkill installed, now I have 2 different ones now.  Neither one produces any output.

```

[rob] ~ $ dpkg -l |grep rfkill                                                                                                                                                                 
ii  rfkill                               0.3-3                                           tool for enabling and disabling wireless dev                                                           
[rob] ~ $ 


```I tried removing with *sudo apt-get --purge remove rfkill* and reinstalling, still no output.

```

[rob] ~ $ sudo hwinfo --netcard
22: PCI 300.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_14e4_4315
  Unique ID: JNkJ.reAAs+k0MA5
  Parent ID: qTvu.FaF8B+KlM_8
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Dell Wireless 1397 WLAN Mini-Card"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4315 "BCM4312 802.11b/g"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x000c "Wireless 1397 WLAN Mini-Card"
  Revision: 0x01
  Driver: "wl"
  Driver Modules: "wl"
  Device File: eth1
  Features: WLAN
  Memory Range: 0xf0400000-0xf0403fff (rw,non-prefetchable)
  IRQ: 17 (411 events)
  HW Address: c4:17:fe:76:9d:50
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN bitrates: 1 2 5.5 6 9 11 12 18 24 36 48 54
  WLAN encryption modes: WEP40 WEP104 WEP256 WEP128 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is not active
    Driver Activation Cmd: "modprobe ssb"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

23: PCI 400.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8136
  Unique ID: rBUF.pXk1FimKZ3B
  Parent ID: HnsE.Nuo71ZHOa2C
  SysFS ID: /devices/pci0000:00/0000:00:1c.5/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0434 
  Revision: 0x02
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x2000-0x2fff (rw)
  Memory Range: 0xf0810000-0xf0810fff (rw,prefetchable)
  Memory Range: 0xf0800000-0xf080ffff (rw,prefetchable)
  Memory Range: 0xf0820000-0xf083ffff (ro,prefetchable,disabled)
  IRQ: 32 (1220 events)
  HW Address: 00:26:b9:24:11:28
  Link detected: yes
  Module Alias: "pci:v000010ECd00008136sv00001028sd00000434bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)
[rob] ~ $

```

---

### Post by nm_geo on 2011-01-18
Look like a wireless driver conflict 

```
iwconfig
```paste results

Be sure your "F2" Wireless button is enabled.  Then consider blacklisting ssb.
Gotta go here.. Good Luck

---

### Post by BigYellowDog on 2011-01-19
```

[rob] ~ $ iwconfig                                                             
lo        no wireless extensions.                                               
                                                                                
eth0      no wireless extensions.                                               
                                                                                
eth1      IEEE 802.11  Access Point: Not-Associated                             
          Link Quality:5  Signal level:0  Noise level:166                       
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0                    
                                                                                
[rob] ~ $ 

```

I added ssb to my /etc/modprobe.d/blacklist.conf to no effect.

---

### Post by nm_geo on 2011-01-19
This may help BigYellow

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

I have the bcm4312 in my laptop as well, but I could not run the STA drivers in Natty 11.04.  I had to revert to the B43 driver using the B43-fwcutter and the bcmwl-modaliases it is not the recommended way but it was require at the time to get the laptop working. 

I would try the advice from the top link but remember there is always another way around it in Linux. Good Luck.

---

### Post by BigYellowDog on 2011-01-20
Looks like disabling the STA drivers helped a little.  I can get a status from rfkill, but the link does not stay up for long before becoming Hard blocked.

```

Jan 20 14:56:05 laptop kernel: [ 2743.920000] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Jan 20 14:56:06 laptop kernel: [ 2744.661045] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 20 14:56:07 laptop kernel: [ 2746.110686] b43-phy1: Radio hardware status changed to DISABLED

```

Sorry for the n00b questions, HW is not my strong point.

---

### Post by BigYellowDog on 2011-01-20
Looks like disabling the STA drivers helped a little.  I can get a status from rfkill, but the link does not stay up for long before becoming Hard blocked.

```

Jan 20 14:56:05 laptop kernel: [ 2743.920000] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Jan 20 14:56:06 laptop kernel: [ 2744.661045] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 20 14:56:07 laptop kernel: [ 2746.110686] b43-phy1: Radio hardware status changed to DISABLED

```

Sorry for the n00b questions, HW is not my strong point.

---

### Post by BigYellowDog on 2011-01-20
Looks like disabling the STA drivers helped a little.  I can get a status from rfkill, but the link does not stay up for long before becoming Hard blocked.

```

Jan 20 14:56:05 laptop kernel: [ 2743.920000] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Jan 20 14:56:06 laptop kernel: [ 2744.661045] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 20 14:56:07 laptop kernel: [ 2746.110686] b43-phy1: Radio hardware status changed to DISABLED

```

Sorry for the n00b questions, HW is not my strong point.

---

### Post by BigYellowDog on 2011-01-20
Looks like disabling the STA drivers helped a little.  I can get a status from rfkill, but the link does not stay up for long before becoming Hard blocked.

```

Jan 20 14:56:05 laptop kernel: [ 2743.920000] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Jan 20 14:56:06 laptop kernel: [ 2744.661045] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 20 14:56:07 laptop kernel: [ 2746.110686] b43-phy1: Radio hardware status changed to DISABLED

```

Sorry for the n00b questions, HW is not my strong point.

---

### Post by nm_geo on 2011-01-20
Ok some minor progress.

Check you Synaptic for the b43-fwcutter and bcmwl-modaliaes those are the two packages I am running in my Ubuntu Lucid 10.04.

---

### Post by BigYellowDog on 2011-01-20
I've had those installed, unless I'm missing something else.

```

[rob] ~ $ dpkg --list |grep b43
ii  b43-fwcutter                         1:012-1build1                                   Utility for extracting Broadcom 43xx firmwar
[rob] ~ $ dpkg --list |grep bcmwl
rc  bcmwl-kernel-source                  5.60.48.36+bdcom-0ubuntu3                       Broadcom 802.11 Linux STA wireless driver so
ii  bcmwl-modaliases                     5.60.48.36+bdcom-0ubuntu3                       Modaliases for the Broadcom 802.11 Linux STA
[rob] ~ $ 

```

---

### Post by nm_geo on 2011-01-20
We may need an expert here>

Let try this go to Launchpad:

[https://answers.launchpad.net/ubuntu/+addquestion](https://answers.launchpad.net/ubuntu/+addquestion)

[URL="https://answers.launchpad.net/"]
[/URL]

---

### Post by nm_geo on 2011-01-24
BigYellowDog if you are still looking.

Try this if we see B43 blacklisted from the previous install we may need to modify the blacklist file.
First 

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```Then paste here:

---

### Post by BigYellowDog on 2011-01-28
Nope never had a previous version of Ubuntu.  I previously had Fedora 12, which was the only version of Linux that I got the wireless to work with.

> 
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist wl
blacklist uart6850
blacklist twl4030_wdt


I tried removing bcm43xx from the blacklist, didn't help, is there something else I need to remove from the blacklist.   Thanks again for all your suggestions.

---

### Post by nm_geo on 2011-01-29
> **BigYellowDog said:**
> Nope never had a previous version of Ubuntu.  I previously had Fedora 12, which was the only version of Linux that I got the wireless to work with.



I tried removing bcm43xx from the blacklist, didn't help, is there something else I need to remove from the blacklist.   Thanks again for all your suggestions.

Your blacklist looks ok to me..  The bcm43xx can stay in there it is for older driver versions.


I would also remove the following (It is not needed for the B43 driver).
Just the STA driver.

bcmwl-modaliases                     5.60.48.36+bdcom-0ubuntu3                       Modaliases for the Broadcom 802.11 Linux STA.

 I am going to fire up my Lucid 10.04 and Xbuntu 10.04 and check the packages I have installed on those two.  I will add them here.

Yeah the bcmwl-modaliases is not needed from the B43( i deleted it from my Lucid 10.04), but I don't see it causing your problems. I don't have Kbuntu so I am fishing here.

I saw you have started a thread on wireless launchpad and I will be following that too.  They will ask if you are using networking-manager and if you have tried wicd instead.  You may have WPA or WEP security problems as well. The disconnects are coming from somewhere we know that.

---

### Post by nm_geo on 2011-01-30
I did a search on Kubuntu wireless manager and found this link. Might be helpful.

[http://bigbrovar.aoizora.org/index.php/2010/06/06/my-perfect-kubuntu-10-04-desktop/](http://bigbrovar.aoizora.org/index.php/2010/06/06/my-perfect-kubuntu-10-04-desktop/)

If you are running Kubuntu 10.04 you might read this too..

[http://kubuntuforums.net/forums/index.php?topic=3112581.0](http://kubuntuforums.net/forums/index.php?topic=3112581.0)

---

### Post by BigYellowDog on 2011-02-09
I removed knetwork-network manager, that fixed the hardware block issue.  Then I installed kubuntu 10.10, I had the same result, no hardware block but also no connection.  Then I booted Windows 7, I had connection issues.  The wireless kept disconnecting, eventually I got connectivity.  After connecting with Windows 7 my wireless now works with kubuntu.  knetwork-manager in 10.04 has issues.  I still don't know if connecting in Windows reset something in my wireless, or reset something on my wireless router.  I may go back to 10.04, knowing what I know now, and see if I can make it work.

---

