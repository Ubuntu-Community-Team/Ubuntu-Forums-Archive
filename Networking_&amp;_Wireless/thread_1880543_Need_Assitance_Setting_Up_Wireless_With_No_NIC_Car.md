---
title: "Need Assitance Setting Up Wireless With No NIC Card Available"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by stevedude on 2011-11-13
I have a DELL Inspiron 6000 where I was dual booting into Windows 7 and Ubuntu Natty 32-bit. I'm selling the laptop and just wanted to install Ubuntu alone. I did a complete fresh install of Ubuntu Oneiric 32-bit as the only OS.

I connected my CAT-5 cable to the laptop to download drivers in order to setup the wireless for the Dell laptop, but the NIC card apparently is not working. I get no Internet connection at all. The cable works fine on my other laptop. Prior to doing this fresh install, I had the wireless working fine in Natty. 

Is there a way to install the wireless drivers without a direct connection to the Internet using my cable for my laptop? All of the post/guides, I've read so far only discuss what to do if you have an Internet connection using a cable.

Thank you in advance.

---

### Post by northd_tech on 2011-11-13
We need to figure out what kind of network hardware you have so that you can download the .DEB packages on a Windows or another Linux machine (or even a Macintosh) with a good network connection to transfer via USB stick or CD(-RW).  It is possible that your drivers are on a LiveCD or LiveDVD under /pool/ too.

Anyway- can you copy and paste the results of the following terminal commands:

```

lspci
sudo lshw -C network
lsusb
ifconfig
iwconfig

```

---

### Post by stevedude on 2011-11-14
Thanks northd_tech for the reply. Sorry for the large output of text from these logs, but I will break them up into the order of your list:

[lspci output]

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

[lshw -C network output]

*-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:ea:c0:89
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=192.168.254.4 latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dfdfc000-dfdfdfff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfdfe000-dfdfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:39:64:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

[lsusb output]

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[ifconfig output]

eth0      Link encap:Ethernet  HWaddr 00:12:3f:ea:c0:89  
          inet addr:192.168.254.4  Bcast:192.168.254.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:151536 (151.5 KB)  TX bytes:151536 (151.5 KB)

[iwconfig output]

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by northd_tech on 2011-11-15
> **stevedude said:**
> **lspci**
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 

**sudo [lshw -C network** output]
*-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:ea:c0:89
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=192.168.254.4 latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dfdfc000-dfdfdfff
  *-network:1
       description: Network controller
       product: **BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller**
       vendor: **Broadcom Corporation**
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfdfe000-dfdfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:39:64:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

That's a Broadcom 4318 wireless, and while I personally consider the 4318 to be one of the 'problem children' in the Broadcom family (unlike my Broadcom 4321AG), it really shouldn't be very difficult to fix compared to many other wireless cards.  I'll just need to search here to see what is working lately with your version of Ubuntu for the 4318- there should be dozens of threads over in the Networking & Wireless sub-form.

While I forgot to give you one of* the most important* commands to run:

```
lsmod
```this **iwconfig** part tells me that your Ubuntu system is at least talking to your 4318 WiFi interface

> **iwconfig**
wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: onI think you're probably missing some firmware files for that 4318 from what I remember.

Here's a pretty simple fix using Synaptic that should work for your 4318:

[http://ubuntuforums.org/showthread.php?t=1810761&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=1810761&highlight=broadcom+4318)

If that doesn't work, then here's 2 pages worth of threads about Broadcom 4318's:

[http://ubuntuforums.org/tags.php?tag=broadcom+4318](http://ubuntuforums.org/tags.php?tag=broadcom+4318)

Just kidding- you probably only need these 2 packages, which you can install with System > Administration > Synaptic Package Manager (or else a terminal window or else an Ubuntu LiveCD/DVD):

[B]b43-fwcutter
firmware-b43-installer

[/B]Follow the directions in that first link (as in uninstall all packages involving "b43" or "broadcom" except for those 2 immediately above, then unplug the ethernet cable and restart).  

If Synaptic doesn't work for you without an internet connection, then my [highly customized] Ubuntu Lucid Lynx 10.04.3 LTS has my Broadcom drivers under **/pool/restricted/b/** on my installation LiveDVD (but that's for the Broadcom 4321-series which uses the "STA" driver which DOES NOT work for the 4318 ).  I'd give you the filenames, except mine are very different from what you need.

Alternately, just download these 2 .DEB packages to a USB stick (for either the 32bit or 64bit version that you need):

[http://packages.ubuntu.com/oneiric/i386/b43-fwcutter/download](http://packages.ubuntu.com/oneiric/i386/b43-fwcutter/download)

[http://packages.ubuntu.com/oneiric/all/firmware-b43-installer/download](http://packages.ubuntu.com/oneiric/all/firmware-b43-installer/download)

If all that still doesn't work, then you will need to blacklist some driver modules in **/etc/modprobe.d/**

It also might help to post the output of these terminal commands in addition to **lsmod** (but I'm pretty sure you said you wanted 32bit Oneric Ocelot Ubuntu) :

```
uname -a
cat /etc/lsb-release 

```

---

### Post by northd_tech on 2011-11-15
> **stevedude said:**
> 
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfdfe000-dfdfffff
  ***-network DISABLED**
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:39:64:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=b43** driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


I forgot those little tidbits of info were hiding above- you are apparently using the Broadcom "b43" module (which is absolutely correct for a 4318 ).  

That "network DISABLED" leads me to conclude yours is probably a firmware loading problem for the 4318.  Let's also take a look at this terminal output:

```
dmesg | egrep 'wl|b43|ssb'

```

---

### Post by stevedude on 2011-11-15
I really appreciate all of the time you are spending with me regarding this issue.

Since I don't have any Internet connection, I cannot use Synaptic for anything, I can't install it via Software Center and didn't see anything related to Synaptic on the Live CD. My Live CD has **/Pool/b **as a directory and I found the **b43-fwcutter **file there but not the **firmware-b43-installer **file, so I used your links and downloaded the 32-bit version to a flash drive and installed the .Deb packages in that manner.

I restarted the laptop and no wireless connection. I checked the **/etc/modprobe.d/blacklist.conf **file and saw an entry for "bcm43xx" so I edited the file with a "#" in front of the entry to (hopefully) comment it out. I restarted the laptop and nothing happens with the wireless connection.

Below are the extra logs you wanted me to submit:

[lsmod output]

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
dell_laptop            13519  0 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
b43                   318816  0 
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              272785  1 b43
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39822  0 
cfg80211              172392  2 b43,mac80211
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
yenta_socket           27428  0 
serio_raw              12990  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i915                  505108  3 
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b44                    31443  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50682  2 b43,b44
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

[dmseg output]

[    0.132142] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
[    1.572144] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.572160] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.572169] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.572179] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.628285] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0
[    1.712063] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.712073] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.712083] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.760363] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.781197] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:ea:c0:89

---

### Post by stevedude on 2011-11-15
I'm ecstatic!

I followed the Ubuntu Wireless Guide - No Internet Connection and got the wireless working. Thanks to northd_tech for your time and effort!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

---

### Post by northd_tech on 2011-11-15
> **stevedude said:**
> I'm ecstatic!

I followed the Ubuntu Wireless Guide - No Internet Connection and got the wireless working. Thanks to northd_tech for your time and effort!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)
[SIZE=4]**^^^**[/SIZE]
**NOT the dreaded manual! That's entrirely TOO drastic!!!** :D

I'm glad it's working for you.  For the benefit of other Broadcom 4318 users/owners/'fixers,' here is nearly 200 pages of "HOWTO" for that unit:

**HOWTO: Broadcom 4318 Wireless Cards  **
[http://ubuntuforums.org/showthread.php?t=197102&page=198](http://ubuntuforums.org/showthread.php?t=197102&page=198)

and the wireless.kernel.org b43 page:

> **b43 and b43legacy**
 b43 and b43legacy are drivers for the 802.11 B/G/N family of wireless chips that [Broadcom]("http://broadcom.com/products/Wireless-LAN")  produces. The choice of which driver your card uses depends on the  revision level of the 802.11 core. If your card is a BCM4306 Rev 2 or  only has 802.11b capability, it uses b43legacy. All other models use  b43. This number is read by the driver ssb, and the correct choice for  your device is made at that point.  The drivers are called bcm43xx in  mainline kernels, and b43 and b43legacy in wireless-2.6 and 2.6.24 and  later.

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by stevedude on 2011-11-16
LOL - I really should clarify what I did instead of making a broad statement.
 
Step 1 - Followed northd_tech's links to install the fw-cutter files I needed; 
[[COLOR=#000000]http://packages.ubuntu.com/oneiric/i...utter/download[/COLOR]]("http://packages.ubuntu.com/oneiric/i...utter/download")
 
[[COLOR=#000000]http://packages.ubuntu.com/oneiric/a...aller/download[/COLOR]]("http://packages.ubuntu.com/oneiric/a...aller/download")
 
Some guides state that installing these files is all that you need to do and then do a restart. No such luck for me.
 
Step 2 - I looked at my **/etc/modprobe.d/blacklist.conf** file that northd_tech recommended I do and saw that the system blacklisted my driver so I did the following:
 
sudo gedit /etc/modprobe.d/blacklist.conf and placed a "#" sign in front of the "bcm43xx" listing and saved the file and restarted the system. Still no luck
 
Step 3 - I **ONLY** followed this portion of the [[COLOR=#000000]https://help.ubuntu.com/community/Wi...ernet%20access[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access") guide;
 
 
**[Step 2.]** 
On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
 
[COLOR=red]I downloaded the files to my HOME folder[/COLOR]
 
**[Step 3.]** 
Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware: 
$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
 
[COLOR=red]I did not have a wl_apsta-3.130.20.o file, mine was called just wl_aptsa.o so I modified the above statement to: [/COLOR][COLOR=red]sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta.o [/COLOR]
 
[COLOR=red]Then I did: [COLOR=red]sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o[/COLOR] [/COLOR]
 
[COLOR=#ff0000]The files were extracted and placed into my /lib/firmware directory.[/COLOR]
 
**[Step 4.]** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **b43** drivers can be activated for use. 
**Note:** A computer restart may be required before using the wifi card. 
 
[COLOR=red]I did not see an activation of the driver as stated above, but I restarted the system and voila', my wireless was recognized after the system restart! [/COLOR]

---

### Post by northd_tech on 2011-11-16
> **stevedude said:**
> 
**[Step 3.]** 
Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware: 
$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
$ sudo b43-fwcutter -w /lib/firmware **wl**_apsta-3.130.20.0.o
$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-**wl**-4.150.10.5/driver/**wl**_apsta_mimo.o
 
[COLOR=red]I did not have a **wl**_apsta-3.130.20.o file, mine was called just **wl**_aptsa.o so I modified the above statement to: [/COLOR][COLOR=red]sudo b43-fwcutter -w /lib/firmware broadcom-**wl**-4.150.10.5/driver/wl_apsta.o [/COLOR]
 
[COLOR=red]Then I did: [COLOR=red]sudo b43-fwcutter -w /lib/firmware broadcom-**wl**-4.150.10.5/driver/wl_apsta_mimo.o[/COLOR] [/COLOR]
 
[COLOR=#ff0000]The files were extracted and placed into my /lib/firmware directory.[/COLOR]
 
**[Step 4.]** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **b43** drivers can be activated for use. 
**Note:** A computer restart may be required before using the wifi card. 
 
[COLOR=red]I did not see an activation of the driver as stated above, but I restarted the system and voila', my wireless was recognized after the system restart! [/COLOR]

I'm  quite sure that "wl" part means you downloaded and installed Broadcom "STA" firmware instead of Broadcom "b43" firmware.  I'm actually a little surprised that your 4318 is working with STA files- I recall the 4318 wanting nothing to do with Broadcom's STA driver.

Those above are "broadcom-[COLOR=Red]**wl**[/COLOR]-[COLOR=Black]**4.150.10.5.tar.bz2**[/COLOR]" drivers. 

 According to Synaptic Package Manager, my **STA** drivers are version [COLOR=Red]**5.10.91.9.3-3**[/COLOR] for the "broadcom-sta-common" & "broadcom-sta-source" packages and version **5.60.48.36+bdcm-0ubuntu3** for the "bcmwl-kernel-source" for the STA drivers which are only claimed to work for the "BCM4311-, BCM4312-, BCM4321-, and BCM4322" Broadcom wireless hardware.

Of course there is a newer version at Broadcom's website than is apparently available in the Synaptic and Ubuntu apt repositories:

version [COLOR=Red]**5.100.82.112**[/COLOR] (in both 32-bit and 64-bit versions).

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

As I understand things, that Broadcom 4318 should NOT be working with STA drivers (which use the "wl.ko" kernel driver and associated hardware).

When I look in my "b43" firmware directory (which should be appropriate firmware for the Broadcom 4306, 4318, and a couple of other Broadcom wireless versions), I see this list:

> $ **ls -la /lib/firmware/[COLOR=Blue]b43[/COLOR]/**
total 300
drwxr-xr-x  2 root root  4096 2011-01-02 00:29 .
drwxr-xr-x 52 root root 12288 2011-11-12 22:05 ..
-rw-r--r--  1 root root   158 2011-01-02 00:29 a0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 a0g0bsinitvals9.fw
-rw-r--r--  1 root root  1840 2011-01-02 00:29 a0g0initvals5.fw
-rw-r--r--  1 root root  2002 2011-01-02 00:29 a0g0initvals9.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 a0g1bsinitvals13.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 a0g1bsinitvals5.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 a0g1bsinitvals9.fw
-rw-r--r--  1 root root  2080 2011-01-02 00:29 a0g1initvals13.fw
-rw-r--r--  1 root root  1840 2011-01-02 00:29 a0g1initvals5.fw
-rw-r--r--  1 root root  2002 2011-01-02 00:29 a0g1initvals9.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 b0g0bsinitvals13.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 b0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 b0g0bsinitvals9.fw
-rw-r--r--  1 root root  2080 2011-01-02 00:29 b0g0initvals13.fw
-rw-r--r--  1 root root  1840 2011-01-02 00:29 b0g0initvals5.fw
-rw-r--r--  1 root root  2002 2011-01-02 00:29 b0g0initvals9.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 lp0bsinitvals13.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 lp0bsinitvals14.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 lp0bsinitvals15.fw
-rw-r--r--  1 root root  3618 2011-01-02 00:29 lp0initvals13.fw
-rw-r--r--  1 root root  2064 2011-01-02 00:29 lp0initvals14.fw
-rw-r--r--  1 root root  2052 2011-01-02 00:29 lp0initvals15.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 n0absinitvals11.fw
-rw-r--r--  1 root root   158 2011-01-02 00:29 n0bsinitvals11.fw
-rw-r--r--  1 root root  2100 2011-01-02 00:29 n0initvals11.fw
-rw-r--r--  1 root root  1320 2011-01-02 00:29 pcm5.fw
-rw-r--r--  1 root root 29864 2011-01-02 00:29 ucode11.fw
-rw-r--r--  1 root root 32232 2011-01-02 00:29 ucode13.fw
-rw-r--r--  1 root root 31384 2011-01-02 00:29 ucode14.fw
-rw-r--r--  1 root root 30488 2011-01-02 00:29 ucode15.fw
-rw-r--r--  1 root root 22384 2011-01-02 00:29 ucode5.fw
-rw-r--r--  1 root root 25160 2011-01-02 00:29 ucode9.fw
For some strange reason, I'm not seeing where any Broadcom "wl" STA firmware is hiding on my 64bit Broadcom 4321AG/"4328" wireless Ubuntu system (unless it is packaged inside and as part of that "wl.ko" module:

> $ dmesg | egrep 'wl|oadcom|irmware'
[   32.564169] [COLOR=Red]**wl**[/COLOR] 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   32.564174] [COLOR=Red]**wl**[/COLOR] 0000:03:00.0: setting latency timer to 64
[   32.637455] eth1: **Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 **
[61698.973866] [COLOR=Red]**wl**[/COLOR] 0000:03:00.0: PCI INT A disabled
[61700.970082] wl 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[61700.970094] wl 0000:03:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xf200000c)
[61700.970099] wl 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf2200004)
[61700.970103] wl 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[61700.970108] wl 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[61702.149126] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[61702.149131] [COLOR=Red]**wl**[/COLOR] 0000:03:00.0: setting latency timer to 64
[61741.020072] Modules linked in: nls_iso8859_1 nls_cp437 btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs usb_storage binfmt_misc ppdev kvm_amd kvm dm_crypt joydev snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi lib80211_crypt_tkip snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 psmouse serio_raw wl(P) lib80211 snd k8temp edac_core edac_mce_amd nvidia(P) ricoh_mmc sdhci_pci sdhci led_class soundcore snd_page_alloc i2c_nforce2 lp parport dm_raid45 xor video ohci1394 fbcon tileblit font bitblit softcursor output ieee1394 ahci vga16fb vgastate forcedeth pata_amd ramzswap xvmalloc lzo_decompress lzo_compress
> $ modinfo [COLOR=Red]**wl**[/COLOR]
filename:       /lib/modules/2.6.32-35-generic/updates/dkms/[COLOR=Red]**wl.ko**[/COLOR]
license:        MIXED/Proprietary
srcversion:     74F8D9437CF7F1FCB427C79
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       2.6.32-35-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string
> $ **lsmod | egrep 'b4|ssb|wl'**
**[COLOR=Red]wl [/COLOR]**                  1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,[COLOR=Red]**wl**[/COLOR]
Strangely, I'm only finding broadcom firmware files in that "b43" and "b43legacy" directories though:

> $ **locate ucode1**
/lib/firmware/[COLOR=Blue]**b43**[/COLOR]/ucode11.fw
/lib/firmware/b43/ucode13.fw
/lib/firmware/b43/ucode14.fw
/lib/firmware/b43/ucode15.fw
/lib/firmware/b43legacy/ucode11.fw
> $ **locate initvals**
/lib/firmware/b43/a0g0bsinitvals5.fw
/lib/firmware/b43/a0g0bsinitvals9.fw
/lib/firmware/b43/a0g0initvals5.fw
/lib/firmware/b43/a0g0initvals9.fw
/lib/firmware/b43/a0g1bsinitvals13.fw
/lib/firmware/b43/a0g1bsinitvals5.fw
/lib/firmware/b43/a0g1bsinitvals9.fw
/lib/firmware/b43/a0g1initvals13.fw
/lib/firmware/b43/a0g1initvals5.fw
/lib/firmware/b43/a0g1initvals9.fw
/lib/firmware/b43/b0g0bsinitvals13.fw
/lib/firmware/b43/b0g0bsinitvals5.fw
/lib/firmware/b43/b0g0bsinitvals9.fw
/lib/firmware/b43/b0g0initvals13.fw
/lib/firmware/b43/b0g0initvals5.fw
/lib/firmware/b43/b0g0initvals9.fw
/lib/firmware/b43/lp0bsinitvals13.fw
/lib/firmware/b43/lp0bsinitvals14.fw
/lib/firmware/b43/lp0bsinitvals15.fw
/lib/firmware/b43/lp0initvals13.fw
/lib/firmware/b43/lp0initvals14.fw
/lib/firmware/b43/lp0initvals15.fw
/lib/firmware/b43/n0absinitvals11.fw
/lib/firmware/b43/n0bsinitvals11.fw
/lib/firmware/b43/n0initvals11.fw
/lib/firmware/b43legacy/a0g0bsinitvals2.fw
/lib/firmware/b43legacy/a0g0bsinitvals5.fw
/lib/firmware/b43legacy/a0g0initvals2.fw
/lib/firmware/b43legacy/a0g0initvals5.fw
/lib/firmware/b43legacy/a0g1bsinitvals5.fw
/lib/firmware/b43legacy/a0g1initvals5.fw
/lib/firmware/b43legacy/b0g0bsinitvals2.fw
/lib/firmware/b43legacy/b0g0bsinitvals5.fw
/lib/firmware/b43legacy/b0g0initvals2.fw
/lib/firmware/b43legacy/b0g0initvals5.fw
I do have a "b43-fwcutter" package installed with my ACTIVE "STA" Broadcom driver- maybe that is picking up the "b43" firmware directory:

> **dpkg -l b4***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  **b43-fwcutter   1:012-1build1**  Utility for extracting Broadcom 43xx firmwar

**dpkg -l bcm***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  **bcm[COLOR=Red]wl[/COLOR]-kernel-s 5.60.48.36+bdc** Broadcom 802.11 Linux STA wireless driver so
ii  **bcm[COLOR=Red]wl[/COLOR]-modalias 5.60.48.36+bdc** Modaliases for the Broadcom 802.11 Linux STA

dpkg -l broad*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  **broadcom-sta-c 5.10.91.9.3-3 ** Common files for the Broadcom STA Wireless d
ii  **broadcom-sta-s 5.10.91.9.3-3**  Source for the Broadcom STA Wireless driver
So your Broadcom 4318 apparently works with "wl"/STA firmware and my Broadcom STA driver is apparenly using "b43" firmware (of course the 4321 and 4322 series is supposed to be backwards-compatible with the "b43" drivers at the slower 802.11-b/g speeds).  I'm more surprised at the 4318 working with that "wl" firmware from the tarball file "broadcom-[COLOR=Red]**wl**[/COLOR]-4.150.10.5.tar.bz2." Perhaps the Broadcom STA** 4.xx** "[COLOR=Red]**wl**[/COLOR]" drivers are more compatible than the **5.1xx** STA "[COLOR=Red]**wl**[/COLOR]" Linux drivers. :confused:

Of course, Broadcom likes to keep all this 'proprietary' information tucked away firmly inside their corporate vaults somewhere so we can only guess what is going on with those firmware files with our "tainted" Ubuntu kernels...

Anyway, if your Broadcom 4318 strangely quits working in the future (like probably **immediately** following an Ubuntu kernel update/upgrade), I would suspect that "wl" firmware that is now installed on your Ubuntu system.  Maybe the newer Ubuntu 11.xx kernels are more forgiving of the old Broadcom "wl" vs. "b43" driver conflict that I have been watching, riding, and living so closely for about 3+ years now.

FYI- my Broadcom 4321AG/"4328" did NOT like the "b43" drivers the last couple of times I tried to install them under 10.04.2 LTS and 10.04.3 LTS Lucid Lynx (but they worked GREAT under 9.04 from what I remember).

---

### Post by northd_tech on 2011-11-16
> **northd_tech said:**
> 
For some strange reason, I'm not seeing where any Broadcom "wl" STA firmware is hiding on my 64bit Broadcom 4321AG/"4328" wireless Ubuntu system (unless it is packaged inside and as part of that "wl.ko" module:
[...]
Strangely, I'm only finding broadcom firmware files in that "b43" and "b43legacy" directories though:
That is a fairly large kernel driver object file "wl.ko" that my Broadcom 4321AG/"4328" wireless is currently using ( ~2.5 MB, and working very well with):

> $ ls -la /lib/modules/2.6.32-35-generic/updates/dkms/w*
-rw-r--r-- 1 root root **2439384** 2011-11-10 19:25 /lib/modules/2.6.32-35-generic/updates/dkms/[COLOR=Red]**wl.ko**[/COLOR]
Perhaps there is some firmware burrowed down somewhere inside that object file.

Edit:  Note that the 32 files in my **/lib/firmware/b43/** directory only total 195.7 KB.  So what **else** did Broadcom stick inside "[COLOR=Red]**wl.ko**[/COLOR]?"

---

