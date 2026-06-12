---
title: "BCM4311 firmware not working in ubuntu 11.04"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by theintrepid1 on 2011-04-28
Hey all.

This is coming off of a clean install of Ubuntu 11.04. After activating the STA driver, wireless completly disappears off of the network applet in the top right. If i deactivate the STA driver and reboot, it reappears. Although, i can not activate the wireless connection, which says "wireless is disabled by hardware switch." I have a Dell E1705 and the hardware switch is activated by fn + F2. Doing that has no effect on the problem, with or without the STA driver installed and activated. Ive done rfkill list all and confirmed that it is hardware blocked. Any ideas on how to get this working

---

### Post by Kevdunleavy on 2011-04-28
I've been battling with the STA driver after upgrading to Natty all day and I eventually decided to give up and install the open source driver instead.

Just remove the STA driver then run **sudo apt-get install firmware-b43-installer** and then restart and you should be fine.

---

### Post by theintrepid1 on 2011-04-28
that seems to have installed the firmware, but im still hard blocked on the wifi, with my default wifi hotkey not turning on wifi like it did in 10.10

edit: i did rfkill unblock all which seemed to remove the hard block, but now its showing my wifi soft blocked. and the wireless network applet is still greyed out.

---

### Post by josephmills on 2011-04-28
```
rfkill list all 
``` please

---

### Post by theintrepid1 on 2011-04-28
cameron@cameron-MP061:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
this is after reactivating the STA driver b/c the b43 firmware installer wouldnt work. now the wireless option in the network applet is completely gone.


cameron@cameron-MP061:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
this was before I reactivated the STA driver.

---

### Post by josephmills on 2011-04-28
```
rfkill unblock all 
```
please take out all ip and hw address thanks 
```
sudo lshw -C network
```

please

---

### Post by theintrepid1 on 2011-04-28
Sorry, i don't know exactly what you refering to on removing the hardware id's. after running rfkill unblock all, im getting this on a rfkill list all.

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

This is the result of the sudo lshw -C network.

*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:ecffc000-ecffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:c7:36:ab
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ecbfe000-ecbfffff


but the wireless internet part of the network applet is still missing.

---

### Post by josephmills on 2011-04-28
```
lsmod 
```
and 
```
dmesg | grep b43 
```
thanks

---

### Post by theintrepid1 on 2011-04-28
lsmod:

Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
vesafb                 13449  1 
ppdev                  12849  0 
binfmt_misc            13213  1 
nvidia               9766978  42 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
b44                    35301  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ssb                    45942  1 b44
wl                   2642531  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
r852                   17878  0 
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
snd_timer              28659  2 snd_pcm,snd_seq
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18951  0 
lib80211               14570  1 wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci

and dmesg

[   16.056119] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64

---

### Post by josephmills on 2011-04-28
> **theintrepid1 said:**
> lsmod:

Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
vesafb                 13449  1 
ppdev                  12849  0 
binfmt_misc            13213  1 
nvidia               9766978  42 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
b44                    35301  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ssb                    45942  1 b44
wl                   2642531  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
r852                   17878  0 
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
snd_timer              28659  2 snd_pcm,snd_seq
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18951  0 
lib80211               14570  1 wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci

I dont see the mods listed are you sure you have the right diver installed? 
```
lspci -nn
```
thanks 
> 
and dmesg

[   16.056119] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64

I also don't see the firmware are you sure that you got it please go to synaptic and type in bcm and then take a scrren shot and show us thanks again

---

### Post by theintrepid1 on 2011-04-28
Im fairly sure i do have the right driver installed.

lspci -nn:


00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce Go 7900 GS] [10de:0298] (rev a1)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

1st image is the one you requested. 2nd is the absence of wireless connections from the network applet.
Thanks bro

---

### Post by theintrepid1 on 2011-04-28
Sorry, did the images wrong in prior post.

---

### Post by josephmills on 2011-04-28
all right install the b43fcutter and the firmware b43 installer the reboot then ```
sudo apt-get update 
```then ```
sudo apt-get upgrade 
``` then reboot again. Are you all set?

---

### Post by pdebruic on 2011-04-28
I'm having the same problem and have installed the open source firmware but am waiting for a Debian ISO CD to burn  to reboot.  This is whats available in Synaptic.  Also there is no bcm-modaliases

---

### Post by josephmills on 2011-04-28
> **pdebruic said:**
> I'm having the same problem and have installed the open source firmware but am waiting for a Debian ISO CD to burn  to reboot.  This is whats available in Synaptic.  Also there is no bcm-modaliases

please start a new thread

---

### Post by josephmills on 2011-04-28
I have to go to work guy I will be back in 2 to 4 hours sorry but I have to eat :popcorn:

---

### Post by theintrepid1 on 2011-04-28
np bro. did the stuff you said, but still missing the wireless connections in the network applet as in my last screen shot. thanks for the help man

---

### Post by theintrepid1 on 2011-04-28
Figured out a solution after looking around at few forum posts about problems with the bcm 4311 firmware. If you uninstall the bcm firmware made for 11.04 and install the firmware from 10.10 and reboot, it works. then just lock the firmware so it wont update until a fixed firmware is released. thanks for your help.

---

### Post by Or'Enn on 2011-04-29
There is a bug in the b43-installer and b43-legacy packages, which inhibits the post-installation of it when you have 2 broadcom cards (e.g., one ethernet card and one wireless card).

I can't find the issue I read detailing why this happens (like I described above), but here is another issue to post at:
[package firmware-b43legacy-installer 4.178.10.4-5 failed to install/upgrade due to unsupported hardware]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397")

EDIT: Found it, the original issue that explains it and gives a patch for the post-installation script:

[Bug#599741: firmware-b43legacy-installer: fails when there are multiple devices with similar PCI id]("http://lists.debian.org/debian-qa-packages/2010/11/msg00022.html")

---

### Post by shagbag9 on 2011-04-29
Is this going to be fixed in the next update? I cant seem to get this fix to work... any guidence would be appreciated!

-thanks

---

### Post by magowiz on 2011-04-30
> **Kevdunleavy said:**
> I've been battling with the STA driver after upgrading to Natty all day and I eventually decided to give up and install the open source driver instead.

Just remove the STA driver then run **sudo apt-get install firmware-b43-installer** and then restart and you should be fine.

Thank you, just worked on an HP Pavillion dv6000 with BCM4311 after 2 whole days of attempts!:D

---

### Post by rmt689 on 2011-05-03
> **Kevdunleavy said:**
> I've been battling with the STA driver after upgrading to Natty all day and I eventually decided to give up and install the open source driver instead.

Just remove the STA driver then run **sudo apt-get install firmware-b43-installer** and then restart and you should be fine.

worked for me too! thanks.

---

### Post by canty978 on 2011-05-06
I installed 'firmware-b43-installer'  in ubuntu software center and it worked, i was able to enable wireless networking

---

### Post by M. Suleman on 2011-05-06
I am new to ubuntu.

I installed 11.04 today. I am also facing the same problem. In fact my wired networks are also not working so I am unable to install the missing firmware.

Wired network is detected but after trying to connect it say that you have been disconnected. What do I do?

Regards
Suleman

---

### Post by josephmills on 2011-05-06
> **M. Suleman said:**
> I am new to ubuntu.

I installed 11.04 today. I am also facing the same problem. In fact my wired networks are also not working so I am unable to install the missing firmware.

Wired network is detected but after trying to connect it say that you have been disconnected. What do I do?

Regards
Suleman

hi there click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move to your ubuntu box then move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``````

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```
then 
```
sudo reboot 
``` tell us how it works out

---

### Post by M. Suleman on 2011-05-07
> hi there click on this link it will download you firmware and driver [http://www.omattos.com/sites/default...all-fw.tar_.gz]("http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz")
 then after you downloaded it move to your ubuntu box then move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in  	Code:
 	sudo cp -r ~/wireless/* /lib/firmware/ 
 	Code:
 	cd /lib/firmware 
then 
 	Code:
 	sudo -s 
then 
 	Code:
 	tar -xzf b43-all-fw.tar_.gz 
 then 
 	Code:
 	exit 
then 
 	Code:
 	sudo reboot 
 tell us how it works out 	


Thanks. It is working now. immediately after reboot it detected my wireless connection and connected without any problems. Thanks once again.

Regards
Suleman

---

### Post by Jarvempaalainen on 2011-05-08
Yep, the above worked for me as well, just remember to disable/remove the STA driver using the "Additional Drivers" tool before rebooting.

---

### Post by dknife9 on 2011-05-21
> **magowiz said:**
> Thank you, just worked on an HP Pavillion dv6000 with BCM4311 after 2 whole days of attempts!:D

This also worked for me on an HP Compaq nc6400 with a broadcom card.

I am running Ubuntu 11.04 installed with the web installer from windows and the Ubuntu Studio packages installed after, but the Unity desktop activated after loading (Ubuntu Studio uses the regular Gnome desktop by default). Now,with this, everything is working perfectly! :D

---

### Post by fatpunk2 on 2011-05-27
installing firmware-b43-installer from the software center just worked fine on my old HP pavilion dv5000, after one whole minute of attempt ;)...
Thx a lot

---

### Post by roperp on 2011-05-27
> **josephmills said:**
> hi there click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move to your ubuntu box then move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``````

cd /lib/firmware

```then 
```

sudo -s 

```then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```then 
```
sudo reboot 
```

This should be flagged and marked as a solution; I just spent two days reading posts and getting totally lost in Linux -la -la land and finally found this solution to work.

Thanks.

---

### Post by Djeff28 on 2011-07-08
> **josephmills said:**
> hi there click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move to your ubuntu box then move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``````

cd /lib/firmware

```then 
```

sudo -s 

```then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```then 
```
sudo reboot 
``` tell us how it works out

Thank you... As a newbie... I spent 2 days reading, trying, rebooting and reinstalling... Finally I hit the Jackpot... Thanks

---

### Post by jeffallender on 2011-07-08
Beautiful, worked like a charm! Thanks from a re-newbie!

---

### Post by gainward on 2011-07-30
Dell inspiron 1501


#30 Also worked for me - Thank you guys.
As a new user of Ubuntu the only frustration
I had was in not realising that the sudo password
would not appear on the screen as I typed, but
was accepted into the process "silently"

Best wishes to all!

---

### Post by spikeyV on 2011-08-14
> **josephmills said:**
> hi there click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move to your ubuntu box then move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``````

cd /lib/firmware

``` 
```

sudo -s 

```
```

tar -xzf b43-all-fw.tar_.gz

``` 
```

exit

```
```
sudo reboot 
``` tell us how it works out

that ^^ worked after doing the following:
> **Jarvempaalainen said:**
> Yep, the above worked for me as well, just remember to disable/remove the STA driver using the "Additional Drivers" tool before rebooting.

thank you so much!!

---

### Post by WiEiW on 2011-08-17
> **magowiz said:**
> Thank you, just worked on an HP Pavillion dv6000 with BCM4311 after 2 whole days of attempts!:D

It also worked for me :D On a Dell Latitude D420. Once again thank You very much! :D

---

### Post by hstefl on 2011-09-27
Hi,
I am almost depesperated. I tried almost everything, but on my Dell Inpiron 6400 I have still described problem - my wifi (even wired) card does not working on ubuntu 11.04.

I have installed and enabled packages:
 - bcmwm-kernel-source 5.100.82.38+bdcom-0ubuntu3 (green in synaptic)
 - firmware-b43-installer 4.150.10.5-5 (green in synaptic)
 - b43-fwcutter 1:013-3 (green in synaptic)

In additional drivers is noting.
Fn+f2 does not work.


```

sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efcfc000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ba:9a:9d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffffs



rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes



lsmod
Module                  Size  Used by
usb_storage            43946  1 
uas                    17676  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
binfmt_misc            13213  1 
b44                    35301  0 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
radeon                896428  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ssb                    45942  1 b44
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
wl                   2642531  0 
dell_wmi               12601  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
ttm                    65184  1 radeon
sparse_keymap          13666  1 dell_wmi
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13515  0 
drm_kms_helper         40745  1 radeon
dcdbas                 14054  1 dell_laptop
drm                   180037  5 radeon,ttm,drm_kms_helper
mtd                    26720  2 sm_common,nand
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  1 wl
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core


dmesg | grep b43
[   12.254253] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X1400 [1002:7145]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

---

### Post by bkratz on 2011-09-27
[QUOTE=hstefl;11291616]Hi,
I am almost depesperated. I tried almost everything, but on my Dell Inpiron 6400 I have still described problem - my wifi (even wired) card does not working on ubuntu 11.04.

I have installed and enabled packages:
 - bcmwm-kernel-source 5.100.82.38+bdcom-0ubuntu3 (green in synaptic)
 - firmware-b43-installer 4.150.10.5-5 (green in synaptic)
 - b43-fwcutter 1:013-3 (green in synaptic)

In additional drivers is noting.
Fn+f2 does not work.




Here is the ultimate guide to the 4311.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by hstefl on 2011-09-28
You helped me a lot. Thank you.

I unistalled bcmwl-kernel-source and AFTER connecting WIRED network I found wifi.

---

### Post by bkratz on 2011-09-28
> **hstefl said:**
> You helped me a lot. Thank you.

I unistalled bcmwl-kernel-source and AFTER connecting WIRED network I found wifi.


figured Dr. Chili's document would take care of you. Glad you got it going!

---

### Post by FredO823 on 2011-11-14
> **magowiz said:**
> Thank you, just worked on an HP Pavillion dv6000 with BCM4311 after 2 whole days of attempts!:D
BCM43xx firmware not working in ubuntu 11.10

I have an HP Pavillion dv5000 running Ubuntu 11.10. My wireless was not working, firmware needed update. I opened up terminal and typed in sudo apt-get install firmware-b43-installer

Now my wifi works great! Thank you Kevdunleavy.

---

### Post by alexgo on 2012-08-31
> **Kevdunleavy said:**
> I've been battling with the STA driver after upgrading to Natty all day and I eventually decided to give up and install the open source driver instead.

Just remove the STA driver then run **sudo apt-get install firmware-b43-installer** and then restart and you should be fine.

Hello, I had to create an account to personally thank you for this. I have been trying to get the wireless driver to work for hours with no success. Your suggestion is the only thing that finally worked, huge thank you!

This whole wireless broadcom driver thing needs to be way more streamlined, I've read so many posts of people having all the same problems I was having and there is no reason it should be so difficult.

---

### Post by wildmanne39 on 2012-09-01
Old thread closed.

---

