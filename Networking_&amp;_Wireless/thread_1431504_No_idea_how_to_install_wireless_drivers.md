---
title: "No idea how to install wireless drivers"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by justint on 2010-03-16
Hi all

I'm about to chuck my Ubuntu Dell Mini Laptop in the trash, have tried everything and read everything, but there seems no easy way to install the wireless drivers.

I've really had enough.

Any ideas anyone, please...

Justin

---

### Post by draperdt on 2010-03-16
So, what is happening? Are you not able to connect to internet? LOL.

I think you should give us some info on what your current position is, before we all start helping you out.

---

### Post by justint on 2010-03-17
Thanks for the reply, sorry my message is a bit short, have been fiddling for so long have lost track of what to put anymore.
 
On my Dell Inspiron Mini 10v originally I had Ubuntu 8.04 and it all was all working fine, but then I installed 9.10 and now there is no connection to the wireless card.
 
I realise that I need to install the windows drivers for the Dell Wireless 1397 Mini Card onboard, but this bit seems so complicated that I sit in the corner and gibber.
 
So yes, I can't connect to any wireless networks (or even see any).
 
I have tried downloading the Dell drivers, although I am not sure which files I need from the ones contained in the download for my card. I have also downloaded Ndiswrapper, but this software makes my head go soft.
 
I did try installing the Netbook Remix and this allowed me to see the wireless networks, but would not allow me to connect as the authentication was more than putting in a simple passphrase. I think that the Netbook Remix installed a broadcom wireless driver, and I assume that this didn't suit the Dell Wireless 1397 Mini Card very much.
 
You may have guessed that I am a novice ubuntu user. Though quite computer experienced. When I posted the message I was on the verge of sticking the whole lot in the trash!
 
Thanks
 
Justin

---

### Post by bkratz on 2010-03-17
> **justint said:**
> Thanks for the reply, sorry my message is a bit short, have been fiddling for so long have lost track of what to put anymore.
 
On my Dell Inspiron Mini 10v originally I had Ubuntu 8.04 and it all was all working fine, but then I installed 9.10 and now there is no connection to the wireless card.
 
I realise that I need to install the windows drivers for the Dell Wireless 1397 Mini Card onboard, but this bit seems so complicated that I sit in the corner and gibber.
 
So yes, I can't connect to any wireless networks (or even see any).
 
I have tried downloading the Dell drivers, although I am not sure which files I need from the ones contained in the download for my card. I have also downloaded Ndiswrapper, but this software makes my head go soft.
 
I did try installing the Netbook Remix and this allowed me to see the wireless networks, but would not allow me to connect as the authentication was more than putting in a simple passphrase. I think that the Netbook Remix installed a broadcom wireless driver, and I assume that this didn't suit the Dell Wireless 1397 Mini Card very much.
 
You may have guessed that I am a novice ubuntu user. Though quite computer experienced. When I posted the message I was on the verge of sticking the whole lot in the trash!
 
Thanks
 
Justin

I believe that you will find that the Dell 1397 wireless card is simply a renamed Broadcom card ( most likey the BCM4312 ) which is why it is trying to use the Broadcom drivers.

To verify this you can, in the terminal (Applications>>Accessories>>terminal or whatever the equivalent is in the version you are using ) type in

lspci | grep Wireless

(that is LSPCI in lowercase, W in uppercase) and see the output. You might as well also do a

rfkill list

and copy/paste the output back here.

---

### Post by chili555 on 2010-03-17
I am confident we can get this going pretty easily. We are going to poke around under the hood a bit which will involve some terminal commands. Also, we may need to download a few things, so temporarily, we will need to have an ethernet connection. Can you please walk that little Mini over to the router and hook up?

First, let's see where we are. Let's find out what you have and if it has an appropriate driver. Please open Applications > Accessories > Terminal and do:```
sudo lshw -C network
```There will be two sections, one for your wired ethernet card and one for wireless. If you can tell which is wireless, post it here; otherwise, post all. Also, please post:```
iwconfig
```Let's take one step at a time and we'll conquer the Mini; it will not conquer us!

EDIT: My colleague bkratz is very good at these things; he'll help you well.

---

### Post by julio.tomaschitz on 2010-03-17
Try to discover the driver/chipset name, and search at synaptic. Download everything and reboot the system. 
Oh, take a look if the wireless light/button are pressed. Most of laptops you can enable/disable the wireless networking.

Sucess

---

### Post by justint on 2010-03-17
lspci | Wireless

produces no result


rfkill list

0: compal-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: compal-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no


[FONT=monospace]

sudo lshw -C network





PCI (sysfs)

*-network

description: Network controller

product: BCM4312 802.11b/g

vendor: Broadcom Corporation

physical id: 0

bus info: pci@0000:03:00.0

version: 01

width: 64 bits

clock: 33MHz

capabilities: pm msi pciexpress bus_master cap_list

configuration: driver=b43-pci-bridge latency=0

resources: irq:17 memory:f0100000-f0103fff

*-network

description: Ethernet interface

product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

vendor: Realtek Semiconductor Co., Ltd.

physical id: 0

bus info: pci@0000:04:00.0

logical name: eth0

version: 02

serial: 00:26:b9:9d:68:9e

size: 10MB/s

capacity: 100MB/s

width: 64 bits

clock: 33MHz

capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s

resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)













iwconfig

lo no wireless extensions.



eth0 no wireless extensions.


[/FONT]

---

### Post by aeiah on 2010-03-17
> **justint said:**
> 
description: Network controller

product: BCM4312 802.11b/g

vendor: Broadcom Corporation



well there you go. i dont know who broadcom are paying off to get in everyone's laptop but it can get damn annoying.

try this:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

edit: i changed the url

---

### Post by justint on 2010-03-17
Ok, thanks, will try it, although when I had the broadcom driver installed I was able to see networks but not able to connect as it would ask for:
WEP 40/128-bit
WEP 128-bit
LEAP
Dynamic WEP

Which would mean not a simple passphrase.

Most networks I have used have just a short word.

Anyway, first I need to get the driver!

---

### Post by justint on 2010-03-17
I activated and installed the Broadcom STA wireless driver, but no networks show.

---

### Post by bkratz on 2010-03-17
> **justint said:**
> I activated and installed the Broadcom STA wireless driver, but no networks show.

could you post the output of 

```
lsmod
```

(LSMOD in lowercase)?  It is rather lengthy so you should use the code tags above (#)      


The [code ] goes before the [/code] goes after the list, it will help clean up the listing.  We need to see the modules loaded.


Probably should post

sudo lshw -C network

again also.

---

### Post by bradmayne04 on 2010-03-18
> **justint said:**
> I activated and installed the Broadcom STA wireless driver, but no networks show.
 
that's weird.  I have a broadcom driver and it's working.  Did you install from the install disk??  Is the wireless light actually on?  Is the driver enabled??  lemme know.  I've had probs w/ many wireless cards in the past but have found w/ patience you will get it working.

---

### Post by justint on 2010-03-18
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
usb_storage            52768  0 
snd_hda_codec_realtek   203328  1 
joydev                 10240  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
snd_seq_oss            28576  0 
b43                   122200  0 
snd_seq_midi            6464  0 
dell_wmi                2564  0 
x_tables               16544  1 ip_tables
mac80211              181140  1 b43
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
snd_timer              22276  2 snd_pcm,snd_seq
compal_laptop           3728  0 
cfg80211               93052  2 b43,mac80211
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            14336  2 uvcvideo,videodev
dcdbas                  7292  0 
psmouse                56500  0 
led_class               4096  1 b43
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35524  1 b43
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video







  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:9d:68:9e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.142 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)







> **bradmayne04 said:**
> that's weird.  I have a broadcom driver and  it's working.  Did you install from the install disk??  Is the wireless  light actually on?  Is the driver enabled??  lemme know.  I've had probs  w/ many wireless cards in the past but have found w/ patience you will  get it working.

there is no wireless light on the Dell mini. not sure if you can switch the wireless on and off, there is no hard switch anyway. the driver is enabled. the install was from a disk which I burnt from the download on the ubuntu site.

---

### Post by bkratz on 2010-03-18
> **justint said:**
> Module                  Size  Used by
[COLOR="Red"]
b43                   122200  0 

ssb                    35524  1 b43
[/COLOR]

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
      [COLOR="Red"] configuration: driver=b43-pci-bridge latency=0[/COLOR]
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:9d:68:9e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.142 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)




there is no wireless light on the Dell mini. not sure if you can switch the wireless on and off, there is no hard switch anyway. the driver is enabled. the install was from a disk which I burnt from the download on the ubuntu site.


You did say earlier that you had installed the STA driver, right.  The items that are red above are indicative of using the b43 driver and I see no module (unless I/m blind) like WL showing which would indicate the STA driver.  How did you install it?

---

### Post by justint on 2010-03-18
I just went into sys>admin>hardware drivers and selected B43 driver, must say I didn't really know what I was doing

actually I thought I selected STA but the hardware drivers says B43 is active

---

### Post by bkratz on 2010-03-18
> **justint said:**
> I just went into sys>admin>hardware drivers and selected B43 driver, must say I didn't really know what I was doing

actually I thought I selected STA but the hardware drivers says B43 is active

Most of this was copied from another thread, we may have to disable the b43, but I don't think so


```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

"Quoted from  Ayuthia "

You might try the following:
```

echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules
sudo update-initramfs -u
```

This will prevent the b43 and ssb modules from loading and it will load the wl module. The update-initramfs will update the system boot information so that it will not try to load the b43 and ssb during the boot process.


Oh and reboot!
Hope that helps.

---

### Post by justint on 2010-03-18
I have swapped over to the STA driver and I can now see networks, however I can't connect to the one in the house. It has 8 letters and the authemtication is asking for:
WEP 40/128-bit
WEP 128-bit
LEAP
Dynamic WEP

and not a simple passphase.

One step forward!

This is the point I had arrived to with the netbook remix.

---

### Post by bkratz on 2010-03-18
Since it is your network can you temporarily remove the encryption, just for a short time to make sure you can connect and that everything else is OK?

---

### Post by justint on 2010-03-18
ummmm... it isn't actually my network, live in a shared house and it is setup by the landlady. Yes it would be nice to remove the encryption. :( I've been craving a network with no passphrase.

The network is ok though as I am using it now with my desktop running vista. With the 8 letter passphrase.

---

### Post by bkratz on 2010-03-18
How about posting the output of 


sudo iwlist scan 

and

sudo lshw -C network

so we can make sure that the right driver is associated.

---

### Post by bkratz on 2010-03-18
> **justint said:**
> ummmm... it isn't actually my network, live in a shared house and it is setup by the landlady. Yes it would be nice to remove the encryption. :( I've been craving a network with no passphrase.

The network is ok though as I am using it now with my desktop running vista. With the 8 letter passphrase.

I don't really know why the options for wpa don't show up in your selections. Could you also go to synaptic package manager and search for wpa. It should find wpa-supplicant ( spelling might be wrong) and see if it is installed?

---

### Post by justint on 2010-03-19
**sudo apt-get update && sudo apt-get install bcmwl-kernel-source**

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release    
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release [44.1kB]
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [81.3kB]       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages [191kB]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [24.4kB]    
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]     
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [38.8kB]
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages [14B]  
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources [56.6kB]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [7,689B]   
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources [14B]   
Get: 15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages [112kB]  
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B]
Get: 17 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]   
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources [28.4kB]  
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages [7,369B]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources [4,025B]
Fetched 642kB in 1s (532kB/s)                      
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.







**sudo iwlist scan **

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:1B:11:EF:BA:44
                    ESSID:"bedsits"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-29 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:22:3F:41:01:E6
                    ESSID:"SKY79652"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-67 dBm  Noise level:-87 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:18:39:21:A6:E4
                    ESSID:"()Bazzer"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-87 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s



**sudo lshw -C network**

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: 70:1a:04:ae:40:99
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:9d:68:9e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.180 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)







> **bkratz said:**
> I don't really know why the options for wpa don't show up in your selections. Could you also go to synaptic package manager and search for wpa. It should find wpa-supplicant ( spelling might be wrong) and see if it is installed?

wpa-supplicant installed 0.6.9-3Ubuntu1

---

### Post by bkratz on 2010-03-19
It looks like you are real close. As I said earlier I don't know why wpa doesn't show up as an option. I know the STA driver will work with it. Hopefully someone with that knowledge will jump in. I will google and look through threads to see if I can find more information.

---

### Post by bkratz on 2010-03-19
Found a command worth running in this thread

[http://ubuntuforums.org/showpost.php?p=8994108&postcount=6](http://ubuntuforums.org/showpost.php?p=8994108&postcount=6)

Of course you would have to change it to eth2 ( in your case ). 
Does this command give us anything interesting?

---

### Post by justint on 2010-03-19
**sudo iwlist eth2 auth**

eth2      Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
          Current Key management :
        802.1x
          Current Pairwise cipher :
        none
          Current Pairwise cipher :
        none
          Current TKIP countermeasures : no
          Current Drop unencrypted : yes
          Current Authentication algorithm :
        open
          Current Receive unencrypted EAPOL : no
          Current Roaming control : no
          Current Privacy invoked : no

---

### Post by justint on 2010-03-19
Now this is interesting!

I tried to connect to other networks in the area to see what happens and they gave me the WPA & WPA2 Personal options _only_

But if I go for the wifi here I am given the other options, none of which will authenticate.

:confused:

---

### Post by bkratz on 2010-03-19
> **justint said:**
> Now this is interesting!

I tried to connect to other networks in the area to see what happens and they gave me the WPA & WPA2 Personal options _only_

But if I go for the wifi here I am given the other options, none of which will authenticate.

:confused:

Out of curiosity ( by the way I am still looking ) which of the A/P's listed above are you trying to connect to?   It's not hidden is it?

---

### Post by justint on 2010-03-19
I have tried them all. If it is hidden I don't know how to unhide it.

---

### Post by bkratz on 2010-03-19
> **justint said:**
> I have tried them all. If it is hidden I don't know how to unhide it.

The essid (name) would be hidden at the AP not your system. When you connect in windows which one is it? Just curious to see what the earlier listing shows about encryption.

---

### Post by sille777 on 2010-03-19
I too had issues with wireless with my Dell Inspiron 6000 using a Broadcom wirless minipci internal wireless card.

After installing Xubuntu 9.10 and getting all the updates from a wired connection.
and a couple reboots.

I followed the directions from this page as indicated from a screen showing after the original install when it tells me to remove the live CD from the tray:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Reboot after this command:

[QUOTE=b43 - Linux Wireless website]**Ubuntu/Debian**

 In recent versions of Ubuntu and  Debian, installing the b43-fwcutter package will handle everything for  you: [INDENT]   ```
sudo apt-get install b43-fwcutter
```

[/INDENT]You will be asked  to automatically fetch and install the firmware into the right  location. 
[/QUOTE]


This worked for me! And was pretty simple for a noob like me.

---

### Post by oleink on 2010-03-20
that is weird.  I use the same driver and have had no problems.  Did you try updating ubuntu and are you sure everything is working properly aka router or wifi hotspot.  Also make sure networking is enabled.

PS i too have been very frustrated with wireless problems b4

---

### Post by justint on 2010-03-21
Not really sure where to go from here, the thread really needs to be renamed: **"wireless shows but no WPA option"**
:-k

---

### Post by justint on 2010-03-22
Right, so where I have got to is that I now have a broadcom driver installed and I am able to view a list of networks.

However the one here with I think needs a WPA passphrase will only give me these options when clicking on it:

WEP 40/128-bit
WEP 128-bit
LEAP
Dynamic WEP

I have noticed that if I try to connect to other peoples networks that I am given the WPA option only and not those others.

I am desperate and am thinking of paying for support somewhere as the laptop is pretty useless at the moment. Either that or sell it :(

Thanks

Justin

---

### Post by justint on 2010-04-03
sorted: was the wifi network. the setup with ubuntu works fine.
Have o/s 9.10 and the broadcom STA driver.
all works fine :D

---

### Post by sille777 on 2011-10-01
> **sille777 said:**
> I too had issues with wireless with my Dell Inspiron 6000 using a Broadcom wirless minipci internal wireless card.

After installing Xubuntu 9.10 and getting all the updates from a wired connection.
and a couple reboots.

I followed the directions from this page as indicated from a screen showing after the original install when it tells me to remove the live CD from the tray:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Reboot after this command:

```

sudo apt-get install b43-fwcutter 

```


This worked for me! And was pretty simple for a noob like me.

I tried the above on a rebuild of the same system Fresh install of 11.04 and it seems that my wireless is still not working.  Maybe I should just revert to 10.10 uless some one knows the trick.

---

### Post by sille777 on 2011-10-01
Ok I got it!!!

I added 


[LIST]
[*]Open synaptic packet manager and install [b43-fwcutter]("http://packages.ubuntu.com/natty/i386/b43-fwcutter/download") then [firmware-b43-installer]("http://packages.ubuntu.com/en/maverick/all/firmware-b43-installer/download")
[*]Restart
[/LIST]
Presto Working WIFI!!

---

