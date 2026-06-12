---
title: "Suddenly Wired &amp; wireless not working"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by JacquiOh on 2010-02-20
Fortunately I have mobile broadband.

Just suddenly my computer doesn't recognise when I plug in an ethernet cable and mostly won't connect wirelessly. It does intermittently, but it's not reliable.

I have Ubuntu 9.04 -- I haven't been able to upgrade because I didn't have real broadband. Now that I've signed up to broadband, I can't connect using my laptop! 

Hardware is fine; I can connect in Vista. 

Laptop is a Dell XPS 1330, the draft n network card that caused me much heartache in the early days!

Any ideas? I've tried deleting the wired connection and seeing would it detect the cable, but it didn't.

Thanks :)

---

### Post by northd_tech on 2010-02-20
I would advise staying with ubuntu 9.04 with all the problems I've been reading about with Karmic 9.10- but that's just my opinion (and what I have done on my own laptop).  One of my relatives also went back to 32-bit ubuntu a couple of times since he was having so much trouble on his 64-bit laptop under ubuntu.

Can you post the results of the following terminal commands so that we can narrow down what kind of hardware you are working with?

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

---

### Post by JacquiOh on 2010-02-20
> lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

> lsmod
Module                  Size  Used by
usbhid                 42336  0 
btusb                  19608  2 
ppp_deflate            12800  0 
zlib_deflate           28312  1 ppp_deflate
bsd_comp               13568  0 
ppp_async              16896  1 
crc_ccitt              10112  1 ppp_async
option                 28036  1 
usbserial              39656  4 option
usb_storage            99648  0 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
ndiswrapper           193436  0 
sbp2                   30476  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         436148  5 
uvcvideo               63368  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_midi           14336  0 
joydev                 18368  0 
compat_ioctl32          9344  1 uvcvideo
snd_rawmidi            29696  1 snd_seq_midi
snd_pcm                83076  3 snd_hda_intel,snd_pcm_oss
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7233756  40 
snd_timer              29704  2 snd_pcm,snd_seq
videodev               41600  1 uvcvideo
ieee80211_crypt_tkip    16896  0 
video                  25872  6 
v4l1_compat            21764  2 uvcvideo,videodev
snd                    62756  18 snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              15200  1 snd
wl                   1281364  0 
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
psmouse                61972  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
pcspkr                 10496  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
dcdbas                 15264  0 
serio_raw              13444  0 
sdhci_pci              15232  0 
ricoh_mmc              11904  0 
sdhci                  23940  1 sdhci_pci
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

> Linux UbuBunny 2.6.28-18-generic #59-Ubuntu SMP Thu Jan 28 01:23:03 UTC 2010 i686 GNU/Linux
> 
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:1e:4c:c7:41:c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth3
       version: 02
       serial: 00:1d:09:5e:3f:0f
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:ee:d7:96:94:3d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

> 
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:4c:c7:41:c7  
          inet6 addr: fe80::21e:4cff:fec7:41c7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:114
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

eth3      Link encap:Ethernet  HWaddr 00:1d:09:5e:3f:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85055 (85.0 KB)  TX bytes:85055 (85.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.206.27.250  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:23237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10002657 (10.0 MB)  TX bytes:7107557 (7.1 MB)

> lo        no wireless extensions.

eth3      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

Thank you :)

---

### Post by northd_tech on 2010-02-20
> **JacquiOh said:**
> 
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: **Broadcom** Corporation **BCM4328** [COLOR=Blue]802.11a/b/g/n[/COLOR] (rev 03)                      

That's a Broadcom 4328 wireless adapter.  As luck would have it, guess what my laptop has:

```
lspci

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```Vista calls my Wireless interface a 4321AG, but ubuntu calls it "4328."  Either way, it was really easy to get my wireless working using the older ndiswrapper and Windows driver method, but I prefer the STA driver from Broadcom lately. 

Can you go into System > Administration > Hardware Drivers and see anything "Broadcom" related?  It might help if you can take a screenshot using the Print Screen button (or else Applications > Accessories > Screenshot ) and post it here.

If you can't see any of the proprietary Broadcom drivers, you can download them from the link on this thread:

[http://ubuntuforums.org/showpost.php?p=8848805&postcount=2](http://ubuntuforums.org/showpost.php?p=8848805&postcount=2)

Also, according to this:

> Linux UbuBunny 2.6.28-18-generic #59-Ubuntu SMP Thu Jan 28 01:23:03 UTC 2010 i686 GNU/Linux                      you are running a 32-bit 2.6.28-18-generic kernel, so you will want to download the 32-bit STA driver if you can't see anything under Hardware Drivers above.

---

### Post by northd_tech on 2010-02-20
For some reason, the quote function is giving me trouble today.   Here is what I notice in your lsmod results:

> l
Module                  Size  Used by
**[COLOR=Red]ndiswrapper           193436  0 [/COLOR]**
ieee80211_crypt_tkip    16896  0 
**wl**                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,[B]wl
[/B] It is possible that you have a conflict with ndiswrapper.  The "wl" is the Broadcom "STA" driver (which works pretty well for my wireless).

How about posting the results of this command:

> less /etc/modprobe.d/blacklist

less /etc/modprobe.d/blacklist.conf
I can't seem to find my networking configuration file right now (my install might not need one), but I'll do some more looking.

edit:  let's also see the results of:

> less /etc/modules 

---

### Post by JacquiOh on 2010-02-20
I looked at the hardware drivers and the STA driver is active

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ndiswrapper
ndiswrapper

---

### Post by northd_tech on 2010-02-20
> **JacquiOh said:**
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ndiswrapper
ndiswrapper                      

OK- let's try disabling that ndiswrapper line (and you can just delete the 2nd one).  Open a terminal and use this command to edit this file:

```
gksu gedit /etc/modules
```Change it to something like this:

```
# /etc/modules: kernel modules to load at boot time.
 #
 # This file contains the names of kernel modules that should be loaded
 # at boot time, one per line. Lines beginning with "#" are ignored.
 
 lp
 sbp2

# Disabling ndiswrapper due to possible conflict with Broadcom STA driver module "wl"
 # ndiswrapper
```Then save the file and exit gedit.  You will probably need to reboot, and some people have mentioned needing to Remove the Broadcom STA driver in Hardware Drivers, re-Active the STA driver and then reboot to get the wireless working.

Do you have an icon for the Gnome Network Manager up by your volume control and system clock (upper right screen) after disabling ndiswrapper?  If so, does it say anything about "enable wireless" or show your wireless router?

If you don't see the Network Manager, we might need to install a few more things.

---

### Post by bigmen on 2010-02-20
I think that u have to reinstall the hardware part...
u mate try that?

---

### Post by JacquiOh on 2010-02-20
I disabled the ndiswrapper and deactived/reactivated the sta driver.

Wireless is now working! Wired, not so much, but I can't check to make sure the wired in the hotel works anyway, so I'll check on the wife's laptop tomorrow. 

Thank you for all your help! I'll check back in tomorrow.

---

### Post by northd_tech on 2010-02-20
Glad it's fixed- my HP DV98xx laptop has been one of the easiest under several flavors of Linux that I've ever seen (NVIDIA video is also quite good, and my nForce cabled ethernet has worked "out of the box" with every single Linux I've ever tried).

It would be good to mark this thread as solved Jacqui so that other readers will know it worked.  (Or you could tag it with "working wifi" but I already used my 2 tags for the Broadcom models).

---

### Post by JacquiOh on 2010-02-22
OK wireless is working but wired still isn't. 

Anyone have any ideas?

---

### Post by northd_tech on 2010-02-22
Well, **lspci **says your cabled ethernet is one of these:

Ethernet controller: **Broadcom** Corporation **NetLink BCM5906M** Fast Ethernet  PCI Express (rev 02)

Unfortunately, my HP has one of these:

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)

I would search the forum for "broadcom 5906M" or "broadcom 5906" and see what comes up.  There should be some threads about it already- you might read those and post a link to the output above.

I just reviewed your output, and the **sudo lshw -C network** command gave this:
> *-network
       description: Ethernet interface
       product: **NetLink BCM5906M **Fast Ethernet PCI Express
       vendor: **Broadcom** Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       **logical name: eth3**
       version: 02
       serial: 00:1d:09:5e:3f:0f
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on **broadcast=yes driver=tg3  driverversion=3.94 **latency=0 link=no **module=tg3** multicast=yes  port=twisted pairI also saw a "tg3" module loaded in the results of the lsmod command above, but I'm not sure if there should also be more related modules that aren't there or what.

I'm not sure what to tell you with that Broadcom **NetLink BCM5906M **ethernet though.  You might check their website though- they do have a Linux wireless "STA" driver available (and that is still pretty rare in the Linux world).  They did have a contact email address for the STA driver page, but you might want to search this forum first- there's probably several threads on that NetLink card already.

---

