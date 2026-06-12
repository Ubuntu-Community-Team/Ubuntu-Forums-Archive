---
title: "Wireless on a netbook with Karmic"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by damitch on 2009-12-31
Got the netbook for Christmas; thought it would be cool to get it working with Linux, and stop worrying so much about viruses.  Having troubles.

Ubuntu is working, the netbook mix version (took some effort, but it's past).  So the next thing is to get the wireless pci card working with a driver, right?  The netbook is a Dell Inspiron 1011 with a 1545 card.  No, there doesn't seem to be a Linux driver for the card, so what I have to do is install ndiswrapper and use that along with the Windows driver files - right?  The notes by others say that it will probably work, so I'll have to go with that, I guess.

The only way to get the module file for ndiswrapper is to compile it from source - right?  For that, I need dh-make and build-essential package - right?  Okay, I got the Debian package for dh-make installed, after installing its various dependency files. The build-essential package is not installed yet.  I've tried to install its dependencies g++-4.3_4.3.2-1.1.i386.deb and libstdc++6-4.3-dev_4.3.2-1.1_i386.deb, but each says that it needs the other one installed first (or at least says the other one is a dependency that 'can't be satisfied').  WTH?

Please help.  Thanks.

---

### Post by bkratz on 2009-12-31
> **damitch said:**
> Got the netbook for Christmas; thought it would be cool to get it working with Linux, and stop worrying so much about viruses.  Having troubles.

Ubuntu is working, the netbook mix version (took some effort, but it's past).  So the next thing is to get the wireless pci card working with a driver, right?  The netbook is a Dell Inspiron 1011 with a 1545 card.  No, there doesn't seem to be a Linux driver for the card, so what I have to do is install ndiswrapper and use that along with the Windows driver files - right?  The notes by others say that it will probably work, so I'll have to go with that, I guess.

The only way to get the module file for ndiswrapper is to compile it from source - right?  For that, I need dh-make and build-essential package - right?  Okay, I got the Debian package for dh-make installed, after installing its various dependency files. The build-essential package is not installed yet.  I've tried to install its dependencies g++-4.3_4.3.2-1.1.i386.deb and libstdc++6-4.3-dev_4.3.2-1.1_i386.deb, but each says that it needs the other one installed first (or at least says the other one is a dependency that 'can't be satisfied').  WTH?

Please help.  Thanks.




I believe most Dells just relabel Broadcom devices.  Go the the teminal (Application>>Accessories>>Terminal and type in 

lspci -nn   (that is LSPCI in lowercase)

and look for the wireless card  will probably say something like BCM43xx. If you copy and paste the output here someone will help decode what you need or you can just reply with the wireless card chip description.

---

### Post by FuManShu on 2009-12-31
You can do a:

sudo dpkg -i libstdc++6-4.3-dev_4.3.2-1.1_i386.deb --ignore-depends=g++-4.3

or perhaps it's 

sudo dpkg -i --ignore-depends=g++-4.3 libstdc++6-4.3-dev_4.3.2-1.1_i386.deb 

It's been a little while but that should get the first one installed.  The next one should install without any hiccups.  Had to do this on my desktop fairly recently.

---

### Post by Gramps on 2009-12-31
To get my wifi working on my Gateway netbook I installed Karmic from USB stick, then plugged it into ethernet opened a terminal and entered the following
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Reboot
System/Administration/Hardware Drivers
You should see 2 Broadcom drivers listed that need to be activated so highlight them starting with the top one and click Activate then repeat for the 2nd one.
Another reboot and your should be able to now see a list of the wifi networks in the area if you click the network icon in the panel.

---

### Post by damitch on 2009-12-31
Decided to try it this way:
> **FuManShu said:**
> ...
```
sudo dpkg -i --ignore-depends=g++-4.3 libstdc++6-4.3-dev_4.3.2-1.1_i386.deb 
```

Seemed to work, but when I went back to install the other one using the Package Installer, it said I had "broken dependencies" and said I needed to immediately fix them with

```
sudo apt-get install -f
or 
gksudo synaptic
```
I'm still a bit of a newbie with Linux, so I tried the first one - which uninstalled the package I had just installed.  Sigh.  So I tried it again, got the same error message, and this time tried the Synaptic Package Manager.  From looking around in that, I guess the issue really is that I already (unknowingly) had Ubuntu versions of the packages installed, and that's causing confusion.  Anyhow, I'll pick up tomorrow where I left off, with trying to build ndiswrapper.

Yes, I've found that the chip in the card is a Broadcomm chip, #14e4:4315.

I have already removed the previous installation of ndiswrapper, so that speaks to the need to build and install a new copy.

I'll report on progress tomorrow.  Many thanks.

---

### Post by FuManShu on 2009-12-31
If I'm not mistaken, there is a newer g++-4.4 package available.  Perhaps this package will solve your issues as I'm pretty sure Karmic ships with gcc-4.4 and that is probably causing your conflict.

---

### Post by bkratz on 2009-12-31
> **damitch said:**
> Decided to try it this way:

Seemed to work, but when I went back to install the other one using the Package Installer, it said I had "broken dependencies" and said I needed to immediately fix them with

```
sudo apt-get install -f
or 
gksudo synaptic
```
I'm still a bit of a newbie with Linux, so I tried the first one - which uninstalled the package I had just installed.  Sigh.  So I tried it again, got the same error message, and this time tried the Synaptic Package Manager.  From looking around in that, I guess the issue really is that I already (unknowingly) had Ubuntu versions of the packages installed, and that's causing confusion.  Anyhow, I'll pick up tomorrow where I left off, with trying to build ndiswrapper.

Yes, I've found that the chip in the card is a Broadcomm chip, #14e4:4315.

I have already removed the previous installation of ndiswrapper, so that speaks to the need to build and install a new copy.

I'll report on progress tomorrow.  Many thanks.

Other than for the learning experience I don't understand going though all this. The Broadcom STA driver should work perfectly well for you. See this thread--complete installation instructions in post #7.

[http://ubuntuforums.org/showthread.php?t=1317801](http://ubuntuforums.org/showthread.php?t=1317801)

---

### Post by damitch on 2010-01-01
**bkratz**, I followed the instructions given, rebooted, and now have a 'wl' module loaded - but the Network Manager still says no wireless connections are found.

This thread [http://ubuntuforums.org/showthread.php?t=1266620]("http://ubuntuforums.org/showthread.php?t=1266620") seems to suggest that the b43 driver should work, if it's the latest build version.  But it doesn't seem all that assured.

Getting more confused all the time.

---

### Post by damitch on 2010-01-01
Okay, current status:

```
david@david-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

david@david-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:f1:88:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

david@david-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

david@david-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
joydev                 10272  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
dell_wmi                2564  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
compal_laptop           3728  0 
uvcvideo               59080  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0 
parport                35340  2 ppdev,lp
dcdbas                  7292  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
serio_raw               5280  0 
soundcore               7264  1 snd
iptable_filter          3100  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
ndiswrapper           185404  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
usb_storage            52544  1 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
r8169                  32064  0 
mii                     5212  1 r8169
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
```

So somehow, some part of ndiswrapper *is* running (?), but there's nothing to show that wl is running.  What have I got myself into?

---

### Post by bkratz on 2010-01-01
Well we are probably going to have to use synaptic and remove the ndiswrapper stuff. Here is a really good thread to look at while I spend a little time reviewing where we are.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by damitch on 2010-01-01
**bkratz**, for what it's worth:

I checked System -> Admin -> Synaptic Package Manager and there are listings for ndiswrapper-common, ndis-wrapper-utils-1.9, and ndisgtk.  I'll hold off on doing anything with them until I hear further.

I checked System -> Admin -> Hardware Drivers, and it shows the listing for the Broadcomm STA wireless driver.  It says the driver is active, but not in use.

At the top, there's an icon that gives the mouse-over message "No network connection," but there's none I can find for strictly wireless connections.

I'll get some late lunch, now.

---

### Post by bkratz on 2010-01-01
I believe that if you remove the 3 ndis files with synaptic and reboot it will probably find the STA driver unless you blacklisted it earlier.  When you bring it back up go to the terminal and copy and paste the output of 

sudo lshw -C network

( that is LSHW in lowercase and C in upper case)

back here so we can see what shows up for wireless.

---

### Post by damitch on 2010-01-01
```
david@david-laptop:~$ sudo lshw -C network
[sudo] password for david: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:f1:88:5a
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)
david@david-laptop:~$ 
```

---

### Post by damitch on 2010-01-01
Found another piece to the puzzle:

It seems that I had not successfully removed the old pieces of ndiswrapper, after all.

This is what happened:

```
david@david-laptop:~$ sudo modprobe -r ndiswrapper
[sudo] password for david: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```
I hadn't understood the warning message - still don't - but I shouldn't have ignored it either.

I should have re-checked, like this:
```

david@david-laptop:~$ modprobe -l *ndis*
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/ubuntu/ndiswrapper/ndiswrapper.ko
david@david-laptop:~$ 
```

So.  How do I get rid of the interfering ndiswrapper once and for all?  Again, many thanks for any help.

---

### Post by bkratz on 2010-01-01
Well we will soon be getting in over my head, but I do know that they are two or three files related to ndiswrapper and ndisgtk (my usb dongle requires them). Did you try to remove them through synaptic and reboot (power down)? All those files would show up there. It is probably the most direct method.  Just search for ndis.

---

