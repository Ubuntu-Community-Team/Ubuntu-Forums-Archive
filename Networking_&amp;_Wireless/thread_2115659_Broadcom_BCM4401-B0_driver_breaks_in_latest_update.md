---
title: "Broadcom BCM4401-B0 driver breaks in latest update"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by Camilo Cienfuegos on 2013-02-13
I have a Dell Vostro 1500 laptop and installed Ubuntu 12.04.1 LTS i386 from a CD

After the installation I used the update manager to install all (>300) pending updates (now running 12.04.2) 

After a restart the wireless connection showed "**Network cable unplugged**" while the cable was plugged in and the light was on. Booting from CD and the network was fine. Hmm.

I'm new to Ubuntu so this took me 2 days straight and a re-install of the entire operating system in order to partially solve the issue. I thought I'd post my findings if anyone else has the same problem (I saw many threads with people having similar problems)

My hardware: ```
Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44
    Kernel modules: b44
```When broken the ifconfig -a command came back with no eth0 and eth1 displaying mostly zeros in all the fields. Indicating that this was probably a driver issue.

[SIZE=3]SOLUTION 1[/SIZE]
 Install new drivers. There are various drivers available, B43 fwcutter drivers, STA drivers. I tried all the guides for those and **no success**.

[SIZE=3]SOLUTION 2[/SIZE]
 Find old driver and reinstall it. First I look for the list of all the old .deb files that have been superseded by more recent versions: 
```
ls -r /var/cache/apt/archives
``` The file I was looking for started "bcmwl". Now I found it I need to unpack it:
```
sudo dpkg -i /var/cache/apt/archives/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_i386.deb
```This reinstalls previous version of driver. Terminal crashes after installation. Wait until finished and close terminal and reboot. Ethernet connection now works! Hooray!

Problem: It stopped working after I restarted a few times . Reinstalling the driver and rebooting fixed it again. I think next I need to tell my computer to not update this driver because the newer version bricks my network card! Any suggestions how to do this?

Many thanks,

Camilo

---

### Post by Hadaka on 2013-02-13
Hi, brcm 4401 is your ethernet driver, that is the driver for the wired connection
b43,bcmwl are wireless drivers
this should start your brcm4401 ethernet driver

```
sudo modprobe b44 
```

please post 
```
lspci -nn | egrep '0200|0280'
```
thanks

---

### Post by Camilo Cienfuegos on 2013-02-14
> **Hadaka said:**
> Hi, brcm 4401 is your ethernet driver, that is the driver for the wired connection
b43,bcmwl are wireless drivers
this should start your brcm4401 ethernet driver


Yes I think you might be right. But for some reason the update makes the whole network stop working. If it breaks again would it be helpful for me to post the 'ifconfig -a'?

As requested: ```
$ lspci -nn | egrep '0200|0200'
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

```

---

### Post by chili555 on 2013-02-14
Just to help my friend Hadaka along in the right direction, bcmwl-kernel-source blacklists b43 and ssb. Unfortunately, ssb is also required by b44, the ethernet driver. You have a situation that works with wireless but not ethernet or vice-versa.

We now return you to your regularly scheduled guru. Have fun!

---

### Post by Camilo Cienfuegos on 2013-02-14
> **chili555 said:**
> Just to help my friend Hadaka along in the right direction, bcmwl-kernel-source blacklists b43 and ssb. Unfortunately, ssb is also required by b44, the ethernet driver. You have a situation that works with wireless but not ethernet or vice-versa.

We now return you to your regularly scheduled guru. Have fun!

This is ok, I only need to use ethernet as this is on my office computer and it just sits on my desk all the time.

Is this a known problem? Is there some documentation on it? Might be useful for me to read up on the issue so I know how to stay on top of it!

Many thanks.

---

### Post by Hadaka on 2013-02-14
Hi, please post the output of..

```
lspci -nnk | grep -iA2 net 
```
thanks

---

### Post by Camilo Cienfuegos on 2013-02-14
> **Hadaka said:**
> Hi, please post the output of..

```
lspci -nnk | grep -iA2 net 
```thanks

```
$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
```

---

### Post by Hadaka on 2013-02-14
Hi, it looks like you have what is needed for the b44 driver, your wireless
card brcm4311 might do better with the linux-firmware-nonfree driver, but
since you don't use wireless, the regular b43 diver has the ssb module needed
for your wired b44 dirver *(thanks for that info chili555)* so bottom line is..
all looks well for your needs.  I have no idea if the next kernel update will hose
your 4311 card or not,seems you werent alone with the last update. May as well
mark this SOLVED. and post again after the next update if you have problems.

---

### Post by Camilo Cienfuegos on 2013-02-21
Well, it broke again after a restart. While it was not working I ran some commands in terminal to try and get some data:

I also found that "sudo modprobe b44" didn't do anything, just crashed terminal.

```
     $ lspci -nnk  
 00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: agpgart-intel  
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: i915  
     Kernel modules: intelfb, i915  
 00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)  
     Subsystem: Dell Device [1028:0228]  
 00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: uhci_hcd  
 00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: uhci_hcd  
 00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: ehci_hcd  
 00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: snd_hda_intel  
     Kernel modules: snd-hda-intel  
 00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp 
 00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp 
 00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp 
 00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: uhci_hcd  
 00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: uhci_hcd  
 00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: uhci_hcd  
 00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: ehci_hcd  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel modules: iTCO_wdt  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: ata_piix  
 00:1f.2 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] [8086:2828] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: ata_piix  
 00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel modules: i2c-i801  
 03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel modules: b44  
 03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: firewire_ohci  
     Kernel modules: firewire-ohci  
 03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: sdhci-pci  
     Kernel modules: sdhci-pci  
 03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: r592  
     Kernel modules: r592  
 03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)  
     Subsystem: Dell Device [1028:0228]  
     Kernel driver in use: r852  
     Kernel modules: r852  
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)  
     Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]  
     Kernel driver in use: wl  
     Kernel modules: wl, ssb  
  
``````
                      P { margin-bottom: 0.21cm; }P.western {  }   lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17308  1  
 fat                    55605  1 vfat  
 snd_hda_codec_idt      60251  1  
 snd_hda_intel          32765  3  
 snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel  
 rfcomm                 38139  0  
 bnep                   17830  2  
 parport_pc             32114  0  
 bluetooth             158479  10 rfcomm,bnep  
 ppdev                  12849  0  
 snd_hwdep              13276  1 snd_hda_codec  
 snd_pcm                80916  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi           13132  0  
 r852                   17901  0  
 sm_common              16772  1 r852  
 snd_rawmidi            25424  1 snd_seq_midi  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 ssb                    69106  1  
 wl                   3032542  1  
 snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event  
 i915                  423451  3  
 nand                   49667  2 r852,sm_common  
 nand_ids                8547  1 nand  
 mtd                    35584  2 sm_common,nand  
 snd_timer              28931  2 snd_pcm,snd_seq  
 nand_bch               13003  1 nand  
 r592                   17808  0  
 psmouse                86520  0  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq  
 bch                    21784  1 nand_bch  
 memstick               15857  1 r592  
 drm_kms_helper         45466  1 i915  
 dell_wmi               12601  0  
 nand_ecc               13105  1 nand  
 serio_raw              13027  0  
 drm                   197641  4 i915,drm_kms_helper  
 dell_laptop            17767  0  
 sparse_keymap          13658  1 dell_wmi  
 wacom                  51812  0  
 dcdbas                 14098  1 dell_laptop  
 snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              14635  1 snd  
 snd_page_alloc         14108  2 snd_hda_intel,snd_pcm  
 joydev                 17393  0  
 cfg80211              178877  1 wl  
 i2c_algo_bit           13199  1 i915  
 mac_hid                13077  0  
 lib80211               14040  1 wl  
 video                  19115  1 i915  
 wmi                    18744  1 dell_wmi  
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp  
 mmc_block              22618  2  
 firewire_ohci          40172  0  
 firewire_core          56940  1 firewire_ohci  
 crc_itu_t              12627  1 firewire_core  
 usbhid                 41937  0  
 sdhci_pci              18324  0  
 sdhci                  28241  1 sdhci_pci  
 hid                    77428  1 usbhid  
  
``````
                      P { margin-bottom: 0.21cm; }P.western {  }   $ ifconfig -a  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:512 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:512 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:44016 (44.0 KB)  TX bytes:44016 (44.0 KB)  
  
``````
                      P { margin-bottom: 0.21cm; }P.western {  }   $ cat /etc/network/interfaces  
 auto lo  
 iface lo inet loopback
  
``````
                      P { margin-bottom: 0.21cm; }P.western {  }   $ cat /etc/resolv.conf  
 # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)  
 #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
  
``````
                      P { margin-bottom: 0.21cm; }P.western {  }   $ lspci -nn | egrep '0200|0280'  
 03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)  
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
  
``````
                      P { margin-bottom: 0.21cm; }P.western {  }   $ lspci -nnk | grep -iA2 net  
 03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)  
     Subsystem: Dell Device [1028:0228]  
     Kernel modules: b44  
 --  
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)  
     Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]  
     Kernel driver in use: wl  
  
```Any ideas why the issue comes back after restart/update?

I managed to fix it again by running the solution I gave in the first post but I don't want to have to reinstall the driver and reboot every time I install some updates!

---

### Post by Hadaka on 2013-02-21
Hi, please do
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree 
sudo modprobe ssb
sudo modprobe b43
```

---

### Post by xSCCMx on 2013-02-21
Permanent solution is to look up an Intel Wi-fi card compatible with your Vostro and use the driver provided by ubuntu.

I had a Broadcom card that wouldn't have it's firmware recognized no matter what I did so I looked up my Dell Model and got directed to 5 year old forum post that had the compatable wifi cards, looked it up on amazon and it came with no problems, hope this helps!

---

### Post by chili555 on 2013-02-21
> **xSCCMx said:**
> Permanent solution is to look up an Intel Wi-fi card compatible with your Vostro and use the driver provided by ubuntu.

I had a Broadcom card that wouldn't have it's firmware recognized no matter what I did so I looked up my Dell Model and got directed to 5 year old forum post that had the compatable wifi cards, looked it up on amazon and it came with no problems, hope this helps!With the correct driver and no conflicts, Broadcom drivers work well. Throwing money at a problem is seldom the best solution.

You were given the best answer here: [http://ubuntuforums.org/showthread.php?t=2114218](http://ubuntuforums.org/showthread.php?t=2114218) If you didn't return to say it wasn't working, then it's hard to fix it.

---

### Post by Hadaka on 2013-02-21
Hi,looks like we are now on page 2, please do the code
on post #10..this thread. Also the bcmwl-kernel-source
is getting loaded somehow when you boot. please also do

```
cat /etc/modules 
```

it should only have lp and you should add b43
*IF it has ... wl ...please remove it.
```
gksudo gedit /etc/modules
#delete wl
#replace wl with b43 
```
thanks

---

### Post by Camilo Cienfuegos on 2013-02-25
```
$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for ***: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,656 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 302824 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic-pae
``````
~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 3,947 kB of archives.
After this operation, 8,962 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu1 [3,947 kB]
Fetched 3,947 kB in 0s (4,184 kB/s)                 
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 302759 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu1_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu1) ...
```
The modprobe commands didn't seem to do anything...


```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```I then edited it with gedit, and it now reads:
```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43
```So now I will try restart and see if the connection stays working.

It seems to me like it keeps trying to update or use the latest drivers, but the latest drivers are not working and it is preventing all network connectivity. When I reinstall old drivers and restart it works fine. Is there a way to force it to use the old drivers?

Thank you so much for all the help so far!

---

### Post by Camilo Cienfuegos on 2013-02-25
I just restarted and connection was fine after login. Maybe it's fixed?! :)

---

### Post by Hadaka on 2013-02-25
Great !, yes you fixed it.
please use thread tools and mark this solved.

---

### Post by pleurastic on 2014-01-28
Fixed my Dell 5100.  Thank you.  Actually, this is the second computer I've fixed this way in two weeks.  I'm converting old XP equipment for friends.

---

### Post by Gabor_Bosze on 2014-04-29
Thanks! It worked on my Dell 1520, Ubuntu 14.04.

---

### Post by juan26 on 2014-06-12
This solution worked perfectly for my Dell Inspiron 6400. Thanks!

---

### Post by Pawel_Poplawski on 2014-10-19
Quick update, as of **linux-firmware-nonfree-1.14ubuntu2** firmware for b43 **is ****not included** in the package. Updating your system will make wifi defunct.
You need to follow [this guide]("http://wireless.kernel.org/en/users/Drivers/b43") to make b43 work again.

---

### Post by chili555 on 2014-10-19
> **Pawel_Poplawski said:**
> Quick update, as of **linux-firmware-nonfree-1.14ubuntu2** firmware for b43 **is ****not included** in the package. Updating your system will make wifi defunct.
You need to follow [this guide]("http://wireless.kernel.org/en/users/Drivers/b43") to make b43 work again.Or simply consult the sticky at the top.

---

### Post by theunsheydenrych on 2015-03-22
This solution work for me aswell, thank you.
hp compaq nx 7300.

---

