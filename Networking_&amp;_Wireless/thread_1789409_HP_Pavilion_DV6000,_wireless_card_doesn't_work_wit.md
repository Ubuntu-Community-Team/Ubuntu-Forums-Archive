---
title: "HP Pavilion DV6000, wireless card doesn't work with Ubuntu"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by arendell on 2011-06-23
Hi, all.  Newbie here.  Please forgive me if I'm asking for help on something covered elsewhere.  But I've been searching and coming up short.  I'm brand new to Ubuntu, also never having worked with Linux before.  PC user all my life.  So this is like looking at a computer for the first time for me.

Anyway, I installed Ubuntu on an older HP Pavilion DV6000 laptop.  The wireless card worked fine before when I was using Windows 7.  But as soon as Ubuntu installed, I couldn't get it to work.  When I go to System Settings and "Additional Drivers", it tells me my Broadcom STA wireless driver "is activated and currently in use."  But the light is amber, the switch (slide on/off) doesn't do anything, and [obviously] no wireless networks can be detected.

Can anyone help this Ubuntu dummy?

Thanks,
Randy

---

### Post by josephmills on 2011-06-23
hi there could you open your terminal (ctrl+alt+t) and enter in ```
lsmod 
``` and ```
rfkill list all 
``` and ```
lspci -nn
``` and ```
sudo lshw -C network 
``` then paste all that here

---

### Post by arendell on 2011-06-23
Here it is...


randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
wl                   2642531  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
i915                  450944  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
drm                   180037  4 i915,drm_kms_helper
lp                     13349  0 
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
parport                36746  3 parport_pc,ppdev,lp
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
video                  18951  1 i915
mtd                    26720  2 sm_common,nand
serio_raw              12990  0 
ahci                   21591  2 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
libahci                25548  1 ahci
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ sudo lshw -C network
[sudo] password for randy: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:be:aa:63
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.27 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ ^C
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$

---

### Post by josephmills on 2011-06-23
hp_wmi 13418 0 


 lets remove that 
```
sudo rmmod -f hp_wmi 
```

---

### Post by arendell on 2011-06-23
Done.  What did that command do?

Thanks for your time and your help, by the way, Joseph.

---

### Post by josephmills on 2011-06-23
oh after that do a ```
rfkill unblock all 
``` then let us see a ```
rfkill list all 
``` thanks
Oh and Welcome to Ubuntu Forums We will get you fixed up

---

### Post by arendell on 2011-06-23
I appreciate that.

When I do both of those commands, it doesn't list anything.  All I get is...


randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ sudo rmmod -f hp_wmi
[sudo] password for randy: 
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ cat/etc/issue
bash: cat/etc/issue: No such file or directory
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ rfkill unblock all
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ rfkill list all
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ rfkill unblock all
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ rfkill list all
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ ^C
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ 



I'm running out on a date with my wife.  Will be back later.  

Thanks again, Joseph.

Randy

---

### Post by arendell on 2011-06-24
I'm back briefly.  Will check in later to see any insights.  But that last command didn't produce anything other than another command prompt.  Maybe I missed something...

---

### Post by nm_geo on 2011-06-24
> **arendell said:**
> I'm back briefly.  Will check in later to see any insights.  But that last command didn't produce anything other than another command prompt.  Maybe I missed something...

Can you go to Synaptic and search for rfkill..
We could install from the terminal but I am curios here too.
The rfkill program monitors your wireless switch and other settings.

```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```Above are my results with wifi switch on:

```
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```Then with my switch off

The rfkill small program is very handy and I thought it came with the installed Natty?  Have you updated & upgraded your install yet?

First time you ran rfkill list all  when Joseph asked:
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    [COLOR=Red][B]Hard blocked: yes  [COLOR=Black]generally points to wifi switch is off[/COLOR]
[/B][/COLOR]

---

### Post by arendell on 2011-06-24
Hi, nm_geo.

I'm not sure if you're suggesting a particular command for me to enter.  Regardless, the switch isn't working in either position.  I'm not sure if slid-to-the-right is ON or OFF.  But the light is amber either way I slide it and it's acting disabled either way. 

Is it possible that the switch has gone bad?  It would be an interesting coincidence, if so, considering that it worked up until the moment that I changed to Ubuntu.

And by the way, I'm running 11.0.4.

Thanks for your input.  Sounds like you and Joseph know your stuff.   

Thanks,
Randy

---

### Post by nm_geo on 2011-06-24
> **arendell said:**
> Hi, nm_geo.

I'm not sure if you're suggesting a particular command for me to enter.  Regardless, the switch isn't working in either position.  I'm not sure if slid-to-the-right is ON or OFF.  But the light is amber either way I slide it and it's acting disabled either way. 

Is it possible that the switch has gone bad?  It would be an interesting coincidence, if so, considering that it worked up until the moment that I changed to Ubuntu.

And by the way, I'm running 11.0.4.

Thanks for your input.  Sounds like you and Joseph know your stuff.   

Thanks,
Randy

Let do this first... 
Disable the STA driver in Additional Drivers
Then install b43-fwcutter and the firmware-b43-installer in Synaptic
you can get to them by search on b43

Try the switch on way do 
```
rfkill list all
```then do it the other way 
```
rfkill list all
```If all goes well do 
```

sudo lshw -C network
```and 

```
lsmod
```

---

### Post by superduperlinuxperson on 2011-06-24
post #3 tells me two things: 1, that hp's wireless is hardblocked; rfkill unblock all should fix that, 2, that your firmware is not installed; [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by arendell on 2011-06-25
Okay, everyone.  I *THINK* I've done what you've said.  Still an amber light, in either switch position.  Here's some output...

randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
i915                  450944  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
wl                   2642531  0 
drm                   180037  4 i915,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
r852                   17878  0 
sm_common              16737  1 r852
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
i2c_algo_bit           13184  1 i915
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
firewire_ohci          31504  0 
libahci                25548  1 ahci
sdhci_pci              13623  0 
e100                   40108  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ sudo lshw -C network
[sudo] password for randy: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:be:aa:63
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.27 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ 






I think I now know that slid-to-the-right is the ON position, since when I do do that, it says "Hard Blocked:  No" under Wireless LAN.  But it doesn't matter:  still no connectivity.  I even went in and Activated the Broadcom STA Wireless Driver after killing it and reinstalling it.  I also rebooted.  Still stuck.


Randy

---

### Post by arendell on 2011-06-25
By the way, I'm here for a while today.  So I'll be able to reply to any other replies fairly quickly in-between other things I'm doing around the house today.

Thanks again for your help.

Randy

---

### Post by nm_geo on 2011-06-25
> **arendell said:**
> By the way, I'm here for a while today.  So I'll be able to reply to any other replies fairly quickly in-between other things I'm doing around the house today.

Thanks again for your help.

Randy

Randy according to the lsmod command you still have the STA driver installed and active.  It has been my experience that the b43-fwcutter   and the firmware-b43-installer work better with your wireless chip-set [COLOR=Red]Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) [/COLOR]in Natty 11.04.  

Now that you have determined the wireless switch position with "rfkill list all" we should be able to move forward.

I would do the following.

1) Go to Additional Drivers and deactivate the STA (wl) driver.
2) Go to Synaptic and do a search on "bcm" without quotes.
3) Verify the  bcmwl-kernel-source is not installed (green box)
3) Install b43-fwcutter and firmware-b43-installer (both at same time is ok)
4) Now we need to check to see if b43 was blacklisted by the wl during the first activation. Run the following code it checks for blacklist problems.
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```5) Review results for blacklist b43 and/or blacklist ssb
6) If we find these and **I think we will ***run the following *
```
gksudo gedit /etc/modprobe.d/*
```search the listed files for one with the name "broadcom-*sta*-common.conf"
7) place a # symbol in front of the line example **# blacklist b43 and # blacklist ssb **save the file where you found these and exit.
8) Now we should be able to reboot and the wireless be running using the b43 driver and proper firmware.

Give it a try it can't hurt.

Run the ```
sudo lshw -C network 
``` and ```
rfkill list all
``` after you either connect or don't for information.

---

### Post by josephmills on 2011-06-25
try a ```
sudo apt-get remove --purge bcmwl-kernel-source && sudo reboot 
``` after reboot do a ```
sudo apt-get install firmware-b43-installer && sudo apt-get install bcmwl-kernel-source && sudo reboot 
```  do you have wireless ?same thing that nm_geo says just in the terminal 
if you dont have wireless do a ```
sudo modprobe b43 
``` then do you have wireless if so reboot did it go away ? 


to copy and in the terminal press shift+ctrl+c to paste into the terminal do shift+ctrl+v   
reboot after modprobe if you dont get wireless and show us a ```
dmesg | grep b43 
``` and a ```
lsmod
```

---

### Post by arendell on 2011-06-25
> **nm_geo said:**
> Randy according to the lsmod command you still have the STA driver installed and active.  It has been my experience that the b43-fwcutter   and the firmware-b43-installer work better with your wireless chip-set [COLOR=Red]Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) [/COLOR]in Natty 11.04.  

Now that you have determined the wireless switch position with "rfkill list all" we should be able to move forward.

I would do the following.

1) Go to Additional Drivers and deactivate the STA (wl) driver.
Okay.  Done.

> 2) Go to Synaptic and do a search on "bcm" without quotes.
3) Verify the  bcmwl-kernel-source is not installed (green box)Not installed.

> 3) Install b43-fwcutter and firmware-b43-installer (both at same time is ok)b43-fwcutter was already installed.  I installed firmware-b43-installer.

> 4) Now we need to check to see if b43 was blacklisted by the wl during the first activation. Run the following code it checks for blacklist problems.
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```5) Review results for blacklist b43 and/or blacklist ssbIt doesn't look like these are blacklisted, unless I'm not understanding what it says.  Here are the results:

randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist wl
blacklist uart6850
blacklist twl4030_wdt
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ 

Since it doesn't say "blacklist" before either of those, then I assume it means that they're not blacklisted.  Is that right?  I'll hold off on going to #6 until I hear back from you on this.


Thanks,
Randy

---

### Post by arendell on 2011-06-25
> **josephmills said:**
> try a ```
sudo apt-get remove --purge bcmwl-kernel-source && sudo reboot 
``` after reboot do a ```
sudo apt-get install firmware-b43-installer && sudo apt-get install bcmwl-kernel-source && sudo reboot 
```  do you have wireless ?same thing that nm_geo says just in the terminal 
if you dont have wireless do a ```
sudo modprobe b43 
``` then do you have wireless if so reboot did it go away ? 


to copy and in the terminal press shift+ctrl+c to paste into the terminal do shift+ctrl+hi
reboot after modprobe if you dont get wireless and show us a ```
dmesg | grep b43 
``` and a ```
lsmod
```

Hi, Joseph.
 
Should I try this or wait to continue on with what nm-geo is suggesting?  I don't know what messes with what.

Thanks,
Randy

---

### Post by josephmills on 2011-06-25
> **arendell said:**
> Hi, Joseph.
 
Should I try this or wait to continue on with what nm-geo is suggesting?  I don't know what messes with what.

Thanks,
Randy

try it the      put a # in front of the wl and it is  blacklisted

---

### Post by arendell on 2011-06-25
Wireless is up and running!  I wish I knew what all happened and what those commands did.  Nevertheless, thanks so much for your patience with me and for fixing my problems.  I'm sure I'll be back for other discussions later as I continue learning Ubuntu.

Have a great night!

Randy

---

### Post by josephmills on 2011-06-25
> **arendell said:**
> Wireless is up and running!  I wish I knew what all happened and what those commands did.  Nevertheless, thanks so much for your patience with me and for fixing my problems.  I'm sure I'll be back for other discussions later as I continue learning Ubuntu.

Have a great night!

Randy

reboot is it staill there ? if not do a modprobe b43 then a ```
sudo -s
``` then a ```
echo b43 >> /ect/modules 
``` then reboot and it should work for a while a real long while


OHH and WELCOME TO UBUNTUFORUMS

---

### Post by arendell on 2011-06-25
That last command didn't work, Joseph.  It says:

randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ modprobe b43
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ sudo -s
[sudo] password for randy: 
root@randy-HP-Pavilion-dv6000-RG383UA-ABA:~# echo b43 >> /ect/modules
bash: /ect/modules: No such file or directory
root@randy-HP-Pavilion-dv6000-RG383UA-ABA:~#

---

### Post by josephmills on 2011-06-25
> **arendell said:**
> That last command didn't work, Joseph.  It says:

randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ modprobe b43
randy@randy-HP-Pavilion-dv6000-RG383UA-ABA:~$ sudo -s
[sudo] password for randy: 
root@randy-HP-Pavilion-dv6000-RG383UA-ABA:~# echo b43 >> /ect/modules
bash: /ect/modules: No such file or directory
root@randy-HP-Pavilion-dv6000-RG383UA-ABA:~#

my bad try```
sudo su 
``` then  ```
echo b43 >> /etc/modules
```   if that wont work let us see a ```
ls /ect/
``` is modules in there ?

also let us see a ```
rfkill list all
```

---

### Post by arendell on 2011-06-25
Seems that worked fine.  I then rebooted, still have a blue light, and have some freedom now.  :guitar:

Thanks again!

Randy

---

