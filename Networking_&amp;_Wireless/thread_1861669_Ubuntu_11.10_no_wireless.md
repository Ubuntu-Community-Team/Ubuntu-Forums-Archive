---
title: "Ubuntu 11.10 no wireless"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by karma408 on 2011-10-15
When someone finds a fix to the no wireless problem with ubuntu 11.10 using Dell laptops and Broadcom please e-mail it to me at [email]cnelson@planetorange.com[/email]

I have a Dell Inspiron 1521. I did a fresh install of 11.10 and everything else id fine, but there is no wireless option.

---

### Post by wildmanne39 on 2011-10-15
Hi, if you want help we will need some information.

Please post the results of:
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by LostInTheSnow on 2011-10-16
$ sudo lshw -C network
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
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:7b:2f:9e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron E1405 [1028:01d8]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge
$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
b44                    31443  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505108  3 
psmouse                73673  0 
serio_raw              12990  0 
ssb                    50682  1 b44
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
r852                   17901  0 
sm_common              16737  1 r852
nand                   49707  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
wl                   2646601  0 
wmi                    18744  1 dell_wmi
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mtd                    35852  2 sm_common,nand
video                  18908  1 i915
lib80211               14570  1 wl
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
mmc_block              22393  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Oct 15 22:50:58 miramar kernel: [   18.647296] wl: module license 'MIXED/Proprietary' taints kernel.
Oct 15 22:50:58 miramar kernel: [   18.681012] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 15 22:50:58 miramar kernel: [   18.681022] wl 0000:0c:00.0: setting latency timer to 64
Oct 15 22:50:58 miramar kernel: [   18.749355] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
Oct 15 22:51:00 miramar NetworkManager[796]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 16 06:34:19 miramar kernel: [   22.843593] wl: module license 'MIXED/Proprietary' taints kernel.
Oct 16 06:34:19 miramar kernel: [   22.940430] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 16 06:34:19 miramar kernel: [   22.940440] wl 0000:0c:00.0: setting latency timer to 64
Oct 16 06:34:19 miramar kernel: [   23.652690] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
Oct 16 06:34:21 miramar NetworkManager[769]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 16 07:00:48 miramar kernel: [   22.553440] wl: module license 'MIXED/Proprietary' taints kernel.
Oct 16 07:00:48 miramar kernel: [   22.630706] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 16 07:00:48 miramar kernel: [   22.630717] wl 0000:0c:00.0: setting latency timer to 64
Oct 16 07:00:48 miramar kernel: [   22.691491] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
Oct 16 07:00:48 miramar NetworkManager[755]: <info> monitoring kernel firmware directory '/lib/firmware'.
$

---

### Post by wildmanne39 on 2011-10-16
Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

---

### Post by notoriousmic24 on 2011-10-16
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

I may not be the original poster, but this fixed my similar situation. Thanks so much!!!

---

### Post by garvinrick4 on 2011-10-16
From broadcom with 3.0 kernels

[http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)

---

### Post by Sofaires on 2011-10-16
i have a dell laptop and a broadcom wireless card, i will be giving this a try tommorow at work and let everyone knows, cause this problem seems to be with dell laptops

---

### Post by wildmanne39 on 2011-10-16
Hi notoriousmic24, I am glad it worked for you.
Enjoy

---

### Post by wildmanne39 on 2011-10-16
Hi Sofaires, whether is works or not depends on the wireless card you have not the brand of the computer.

Please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by La Noche on 2011-10-16
Hi I'm new to Linux and my wireless is not working it worked with 11.04 any how i thought i would save you some time by posting some information that you might ask for. tell me if you need anything else
Thanks.

```

  *-network              
       description: Ethernet interface
       product: 88E8042 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: //I took this out for this post.
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.106 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:d3100000-d3103fff ioport:3000(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d2000000-d2003fff

lspci -nnk | grep -ia2 net
    Kernel driver in use: radeon
    Kernel modules: radeon
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller [11ab:4357] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:308c]
    Kernel driver in use: sky2
    Kernel modules: sky2
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1507]
    Kernel modules: ssb

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod
Module                  Size  Used by
bnep                   17923  2
rfcomm                 38408  0
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0
ppdev                  12849  0
binfmt_misc            17292  1
snd_hda_codec_idt      60049  1
snd_hda_intel          28358  2
radeon                961723  3
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
joydev                 17393  0
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
ttm                    65224  1 radeon
snd_seq_midi           13132  0
drm_kms_helper         32889  1 radeon
drm                   196322  5 radeon,ttm,drm_kms_helper
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
sp5100_tco             13495  0
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                63474  0
hp_wmi                 13652  0
i2c_piix4              13093  0
i2c_algo_bit           13199  1 radeon
k10temp                12990  0
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     17455  0
video                  18908  0
sparse_keymap          13658  1 hp_wmi
serio_raw              12990  0
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
shpchp                 32356  0
parport                40930  3 parport_pc,ppdev,lp
sky2                   49304  0
ahci                   21634  2
libahci                25761  1 ahci

sudo cat /var/log/syslog |grep -e b43 -e wl -e firmware -e wlan0 |tail -n35

Oct 16 19:54:58 midnight-Compaq-515 kernel: [    0.000000] DMI: Hewlett-Packard Compaq 515/308C, BIOS 68GVV Ver. F.0F 12/17/2009
Oct 16 19:55:02 midnight-Compaq-515 NetworkManager[871]: <info> monitoring kernel firmware directory '/lib/firmware'.


```also i don't know if this will help but get the additional drivers pop up and when i click on the broadcom STA wireless driver (i thought that perhaps this would install the driver need) I get a message to check a log and the log has this

2011-10-16 20:32:38,582 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-16 20:32:38,657 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-16 20:32:38,657 DEBUG: fglrx is not the alternative in use

---

### Post by Matt 6:27 on 2011-10-17
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.


This did the trick for me as well, thanks!

One note: I tried these instructions while running off a usb drive, but firmware-b43-installer couldn't be found (b43-fwcutter was located and installed).  I then did a clean install of 11.10 on my Inspiron E1705, followed the instructions above, and voila! Moral to story: this might not work with a live CD or USB... you may have to do a full install.   Thanks so much!!

---

### Post by wildmanne39 on 2011-10-17
Hi La Noche, try this please:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Then disconnect your wired connection and restart your computer.
Thank you

---

### Post by LostInTheSnow on 2011-10-17
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.
Thanks wildemanne39.

A follow up question: Is there a way I can install these so the only way I can do the 'apt-get install' step without being connected on that laptop? My ethernet port is physically damaged, but I have other laptops at home. 

I downloaded some .deb files in a second laptop, and copied the files over using usb. However, I don't know how to install these, or even if these are sufficient.

---

### Post by LostInTheSnow on 2011-10-17
> **garvinrick4 said:**
> From broadcom with 3.0 kernels

[http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)
This sounds interesting; let me try it. If it doesn't work, I suppose I can manually edit blacklist.conf and undo the 'blacklisting' operation.

---

### Post by wildmanne39 on 2011-10-17
Hi LostInTheSnow, that will not work for your wireless card.

Download the b43zip file to your usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
The the code one line at a time.
Thank you

---

### Post by amishtrucker on 2011-10-17
> **notoriousmic24 said:**
> I may not be the original poster, but this fixed my similar situation. Thanks so much!!!
This solved the wireless on my Dell Inspiron 1720 when I upgraded from 11.04 to 11.10 (not a clean install, upgrade). 

Thanks for Posting the info!

---

### Post by wildmanne39 on 2011-10-17
Hi, your welcome!

---

### Post by LostInTheSnow on 2011-10-18
> **wildmanne39 said:**
> Hi LostInTheSnow, that will not work for your wireless card.

Download the b43zip file to your usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
The the code one line at a time.
Thank you
Yes, this worked for me too. And you were right, the broadcomm instructions didn't apply to me (sudo insmod wl.ko resulted in error message: can't read 'wl.ko': No such file or directory

thanks!

---

### Post by pro.gangster on 2011-10-18
hi
I'm using Ubuntu for the first time,but I saw the wifi problem for other users happening after upgrading to 11.10, so after my many searches,I'm going to downgrade if mmy problem doesn't solve
so,please help me on this
 
Lenovo-Ideapad U330
Intel Wifi Link 5100 AGN

I downloaded the .ucode driver (iwlwifi-5000-ucode-8.83.5.1) and copied it to /lib/firmware but it didn't work

I also tried Windows Wireless Driver app

what is the problem?
please help me

---

### Post by garvinrick4 on 2011-10-18
This thread has been broadcom cards and drivers.

> Lenovo-Ideapad U330
Intel Wifi Link 5100 AGNAs I understand if having iwlagn problem in oneiric, see post #42
[http://ubuntuforums.org/showthread.php?t=1862484&page=5](http://ubuntuforums.org/showthread.php?t=1862484&page=5)

---

### Post by garvinrick4 on 2011-10-18
Confirmed that kernel 2.6.38.8 will bring iwlagn driver for intel cards in working order for time being in 11.10.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38.8-natty/")

## Again this is not in all Intel cards with iwlagn driver just in some and have nothing confirmed as a
as to why only on select machines. But for now 2.6.38.8 does give connection until confirmed fix for 2.6.39 and 3.0 and up
is found or fixed.
Bugzilla report found.
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2312](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2312)

---

### Post by julio8a on 2011-10-18
Hi, I had the same problem three days ago, when I install xubuntu 11.10 my Dell laptop don't works with wirless connection.

As I am new with ubuntu, I don't know how to look for new hardware configuration (as in Windows), bu I connect my laptop directly to my router (lan cable) and it connects automatically to internet and, I supposse, it looks for the right driver.  After that, my laptop works fine.

I hope my simple answer helps!

---

### Post by wildmanne39 on 2011-10-18
Hi LostInTheSnow, I am glad it worked.
Enjoy

---

### Post by wildmanne39 on 2011-10-18
Hi pro.gangster, you should start your own thread, this one is for broadcom card issues.

Also do what garvinrick4 suggested.
Thank you

---

### Post by karma408 on 2011-10-18
My terminal gets stuck at the Configuring ttf-mscorefonts-installer screen. I push enter, but nothing happens. I can't get past this point so I can't fix my wireless problem.

When I run sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source is when it gets stuck. I disconnected the hard line, rebooted, but still no wireless.

---

### Post by karma408 on 2011-10-18
Ok after a fresh install my wireless shows up, but says: 

Wireless Networks
device not ready (firmware missing)

I know others have had the same issue, but I can't locate what the fix was for it. Any help would be appreciated.

---

### Post by wildmanne39 on 2011-10-18
Hi, it is not stuck it is waiting for you to type your password and when you do, the password will not be displayed on the screen after you are done typing it hit enter.
Thank you

---

### Post by karma408 on 2011-10-19
I figured it out, I think. 

sudo apt-get install b43-fwcutter firmware-b43-installer

seemed to do the trick. Now all my Wireless networks show up and I can connect. 

1 questions though: Should I add the additional driver for it, or will that mess it up again?

---

### Post by user_linux08 on 2011-10-19
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.


thank you kindly. Your "prescription" worked for me too.

I wish there would be a way for Ubuntu to have self diagnostic Ap to check itself for wireless, and correct it w/o user's involvement.

---

### Post by meconio on 2011-10-19
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

I'm on a Dell Inspiron 1720 with ubuntu 11.10 and this did work for me, Before that I installed the software recommended by the "additional drivers" app in ubuntu,  but your fix worked I'm using my wifi now.  Thank you Wildmanne

---

### Post by 69bambam on 2011-10-19
here is the basic info asked for 
barry@barry-MX6445:~$ sudo lshw -C network
[sudo] password for barry: 
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:b5:7e:10
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=10.34.5.181 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:d0200000-d0203fff ioport:a000(size=256)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0304000-d0305fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:bc:80:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg
barry@barry-MX6445:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
    Subsystem: Gateway 2000 Device [107b:0300]
    Kernel driver in use: sky2
--
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Broadcom Corporation Gateway 7510GX [14e4:0449]
    Kernel driver in use: b43-pci-bridge
barry@barry-MX6445:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
barry@barry-MX6445:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
barry@barry-MX6445:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
radeon                925020  3 
binfmt_misc            17292  1 
arc4                   12473  2 
tifm_7xx1              12937  0 
tifm_core              15040  1 tifm_7xx1
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
snd_atiixp             19337  2 
joydev                 17393  0 
b43                   318816  0 
drm                   192226  5 radeon,ttm,drm_kms_helper
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
psmouse                73673  0 
k8temp                 12905  0 
serio_raw              12990  0 
snd_atiixp_modem       18604  5 
mac80211              272785  1 b43
snd_ac97_codec        106082  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
i2c_algo_bit           13199  1 radeon
snd_pcm                80468  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
shpchp                 32356  0 
snd                    55902  20 snd_atiixp,snd_rawmidi,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  2 b43,mac80211
video                  18908  0 
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_atiixp,snd_atiixp_modem,snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_piix4              13093  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
crc_itu_t              12627  1 firewire_core
sdhci                  27360  1 sdhci_pci
ssb                    50682  1 b43
pata_atiixp            12967  2 
sky2                   49317  0 
barry@barry-MX6445:~$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Oct 19 14:15:42 barry-MX6445 avahi-daemon[804]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::3246:9aff:fe26:2310.
Oct 19 14:15:42 barry-MX6445 avahi-daemon[804]: Interface wlan1.IPv4 no longer relevant for mDNS.
Oct 19 14:15:42 barry-MX6445 avahi-daemon[804]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 10.34.5.123.
Oct 19 14:15:42 barry-MX6445 avahi-daemon[804]: Withdrawing address record for fe80::3246:9aff:fe26:2310 on wlan1.
Oct 19 14:15:42 barry-MX6445 avahi-daemon[804]: Withdrawing address record for 10.34.5.123 on wlan1.
Oct 19 14:15:42 barry-MX6445 avahi-daemon[804]: Withdrawing workstation service for wlan1.
Oct 19 14:15:42 barry-MX6445 kernel: [ 7066.302287] wlan1: deauthenticating from 00:a0:f8:a9:a3:bb by local choice (reason=3)
Oct 19 14:15:42 barry-MX6445 NetworkManager[818]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:13.2/usb1/1-1/1-1:1.0/net/wlan1, iface: wlan1)
Oct 19 14:15:42 barry-MX6445 NetworkManager[818]: <info> (wlan1): now unmanaged
Oct 19 14:15:42 barry-MX6445 NetworkManager[818]: <info> (wlan1): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Oct 19 14:15:42 barry-MX6445 NetworkManager[818]: <info> (wlan1): deactivating device (reason 'removed') [36]
Oct 19 14:15:42 barry-MX6445 NetworkManager[818]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 11917
Oct 19 14:15:42 barry-MX6445 NetworkManager[818]: <info> (wlan1): cleaning up...
Oct 19 14:15:42 barry-MX6445 wpa_supplicant[1672]: Could not read interface wlan1 flags: No such device
Oct 19 14:17:02 barry-MX6445 kernel: [    1.882346] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 19 14:17:02 barry-MX6445 kernel: [   12.018657] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Oct 19 14:17:02 barry-MX6445 kernel: [   13.425641] Registered led device: b43-phy0::tx
Oct 19 14:17:02 barry-MX6445 kernel: [   13.425667] Registered led device: b43-phy0::rx
Oct 19 14:17:02 barry-MX6445 kernel: [   13.425694] Registered led device: b43-phy0::radio
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:05:02.0/ssb0:0/net/wlan0, iface: wlan0)
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:05:02.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]: <info> (wlan0): now managed
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 19 14:17:11 barry-MX6445 NetworkManager[854]: <info> (wlan0): bringing up device.
Oct 19 14:17:12 barry-MX6445 kernel: [   26.984053] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Oct 19 14:17:12 barry-MX6445 NetworkManager[854]: <info> (wlan0): preparing device.
Oct 19 14:17:12 barry-MX6445 NetworkManager[854]: <info> (wlan0): deactivating device (reason 'managed') [2]
Oct 19 14:17:12 barry-MX6445 kernel: [   27.059769] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 19 14:17:13 barry-MX6445 NetworkManager[854]: <info> (wlan0): supplicant interface state: starting -> ready
Oct 19 14:17:13 barry-MX6445 NetworkManager[854]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 19 14:17:13 barry-MX6445 NetworkManager[854]: <info> (wlan0): supplicant interface state: ready -> inactive
barry@barry-MX6445:~$ 


Have tried about everything on the net to get wifi card working.     Help?

---

### Post by garvinrick4 on 2011-10-19
@69bambam
> Have tried about everything on the net to get wifi card working.     Help?Did you open a terminal and run the two lines of code (copy and paste them into a terminal and press enter, one at a time) that Wildmanne39 gave in Post #4.
Open a terminal (ctrl/alt/t)

---

### Post by 69bambam on 2011-10-19
> **garvinrick4 said:**
> @69bambam
Did you open a terminal and run the two lines of code (copy and paste them into a terminal and press enter, one at a time) that Wildmanne39 gave in Post #4.
Open a terminal (ctrl/alt/t)

Did That

---

### Post by 69bambam on 2011-10-19
did that again and it asked me to remove some file.   removed file and now the did that does work.
THANK YOU

---

### Post by garvinrick4 on 2011-10-19
>  that Wildmanne39 gave in Post #4.> did that again and it asked me to remove some file.   removed file and now the did that does work.
THANK YOU     I was just Wildmanne39's messenger in this Thread but I am sure he would say you are Welcome and enjoy you Ubuntu

---

### Post by wildmanne39 on 2011-10-19
> **karma408 said:**
> I figured it out, I think. 

sudo apt-get install b43-fwcutter firmware-b43-installer

seemed to do the trick. Now all my Wireless networks show up and I can connect. 

1 questions though: Should I add the additional driver for it, or will that mess it up again?

Hi, no do not add any more drivers that will break it again, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.
Thank you

---

### Post by wildmanne39 on 2011-10-19
Hi user_linux08 and meconio your welcome! I am glad it worked.
Enjoy

---

### Post by fhulette on 2011-10-19
> **wildmanne39 said:**
> Hi La Noche, try this please:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Then disconnect your wired connection and restart your computer.
Thank you

:P This worked for me... I am new to Linux/Ubuntu but REALLY like the 11.04 version I had... that was until I updated and hit this problem.  Glad there are people out there helping like you to make this stuff manageable for us newbies :)

Thanks again!!

---

### Post by zoogTHOMzoog on 2011-10-20
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

Worked for me!:guitar:

---

### Post by takai on 2011-10-20
Im having a similar issue, Ubuntu thinks that the network is disabled by a hardware switch.

rfkill gives:
0: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: yes

Broadcom 4311 (i think) in a Dell Vostro 1520.

Back to 10.10 it is for now.

---

### Post by wildmanne39 on 2011-10-20
Hi fhulette and zoogTHOMzoog, your welcome! 
Enjoy

---

### Post by wildmanne39 on 2011-10-20
Hi takai, please post the results of:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by harryhaler on 2011-10-20
Hello everyone,

thank you all for your help. I had the same problem that started this thread. As I also have a Dell with a Broadcom card, I tried the same solution proposed by [B]wildmanne39. 

[/B]After that I rebooted my laptop, and I was glad to see that, at least,  it recognised my Broadcom card. However, still no network found :sad: :sad:.
Any idea of how could I do to find my wifi?

Thank you all!

---

### Post by wildmanne39 on 2011-10-20
Hi, welcome to the forum! please post the results of:
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n35
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by takai on 2011-10-20
> **wildmanne39 said:**
> Hi takai, please post the results of:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

My problem was this bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259)

Been documented since the 10th of Jan with no progress on it at all.

---

### Post by wildmanne39 on 2011-10-20
Hi takai, most of the time we can get the wireless to work even when blocked but I will need to see the information I asked for.
Thank you

---

### Post by takai on 2011-10-20
> **wildmanne39 said:**
> Hi takai, most of the time we can get the wireless to work even when blocked but I will need to see the information I asked for.
Thank you

As per the bug report the problem lies within dell_laptop. Removing that kernel module (and blacklisting it) re-enables wireless.

This combined with the Kernel 3.0 bug with the Broadcom B43 driver was causing the issues.

---

### Post by wildmanne39 on 2011-10-20
Hi, yes exactly so your issue is resolved the correct? Many people have to do it and not just in 11.10.

Yep have noticed that there are some bugs that do not get fixed form one release to another.
Thank you

---

### Post by the_hawk22 on 2011-10-21
Having trouble getting wireless to work as well. It shows me available networks, but I can't connect to any. When I click the name of my network, nothing happens. Here is all the information and thank you for your help!

**nm-tool**
```

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:1D:09:4E:49:28

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.76
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:1F:3A:9B:29:35

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NoorMohammed:    Infra, C0:3F:0E:14:7E:6E, Freq 2452 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    Mohammed:        Infra, 00:11:50:3B:76:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WEP
    2WIRE273:        Infra, B0:E7:54:DF:E7:69, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WEP
    Bar:             Infra, C0:83:0A:D2:EE:71, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    2WIRE586:        Infra, 00:24:56:5F:08:E1, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA
    sys0190:         Infra, 00:90:4C:7E:00:10, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WPA
    Jay:             Infra, 00:22:75:5C:20:36, Freq 2417 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    which internet:  Infra, 00:1B:2F:D6:70:4E, Freq 2417 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    2WIRE577:        Infra, 00:24:56:2E:53:D9, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA
    2WIRE171:        Infra, 64:0F:28:96:C0:D1, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    2WIRE996:        Infra, 00:23:51:CD:1E:19, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

```

**lspci -nnk | grep -iA2 net**
```

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
	Subsystem: Dell Device [1028:022f]
	Kernel driver in use: sky2
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
	Kernel driver in use: b43-pci-bridge

```

**lsmod**
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_idt      60049  1 
snd_hda_codec_hdmi     31426  1 
ppdev                  12849  0 
parport_pc             32114  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
binfmt_misc            17292  1 
snd_hda_intel          24262  0 
snd_hda_codec          91754  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
b43                   318816  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              272785  1 b43
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
r852                   17901  0 
sm_common              16737  1 r852
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              172392  2 b43,mac80211
wmi                    18744  1 dell_wmi
nand                   49707  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mtd                    35852  2 sm_common,nand
snd                    55902  10 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
i915                  505108  2 
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
serio_raw              12990  0 
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
coretemp               13188  0 
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49317  0 
ahci                   21634  2 
libahci                25727  1 ahci
ssb                    50682  1 b43

```

**sudo iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 64:0F:28:96:C0:D1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"2WIRE171"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d137ff6181
                    Extra: Last beacon: 1244ms ago
                    IE: Unknown: 00083257495245313731
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 02 - Address: B0:E7:54:DF:E7:69
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"2WIRE273"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000031f7c0c5181
                    Extra: Last beacon: 1200ms ago
                    IE: Unknown: 00083257495245323733
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 00:24:56:2E:53:D9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"2WIRE577"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ddd1ae6181
                    Extra: Last beacon: 1188ms ago
                    IE: Unknown: 00083257495245353737
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 00:1B:2F:D6:70:4E
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"which internet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000031f7a7ac177
                    Extra: Last beacon: 4876ms ago
                    IE: Unknown: 000E776869636820696E7465726E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6E1803FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602050000000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E1803FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050000000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:22:75:5C:20:36
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Jay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fafa915152
                    Extra: Last beacon: 4820ms ago
                    IE: Unknown: 00034A6179
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010775B6680BFDE11D38D2F0022755C2036103C000101
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502001E127A
                    IE: Unknown: DD1E00904C33EE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 06 - Address: 00:23:51:CD:1E:19
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"2WIRE996"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bba8fd6181
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 00083257495245393936
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 07 - Address: C0:83:0A:D2:EE:71
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Bar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f7390fa181
                    Extra: Last beacon: 4272ms ago
                    IE: Unknown: 0003426172
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
          Cell 08 - Address: 00:90:4C:7E:00:10
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"sys0190"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000568a975ad5
                    Extra: Last beacon: 716ms ago
                    IE: Unknown: 000773797330313930
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD06001018020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:11:50:3B:76:85
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Mohammed"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005bc5eee184
                    Extra: Last beacon: 840ms ago
                    IE: Unknown: 00084D6F68616D6D6564
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010500

```

**iwlist chan**
```
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

```

**sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n35**
```
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Auto-activating connection 'Wired connection 1'.
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) starting connection 'Wired connection 1'
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> dhclient started with pid 2003
Oct 21 02:07:39 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Oct 21 02:07:40 ilya-PC NetworkManager[856]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct 21 02:07:40 ilya-PC NetworkManager[856]: <info> (eth0): carrier now OFF (device state 70, deferring action for 4 seconds)
Oct 21 02:07:41 ilya-PC NetworkManager[856]: <info> (eth0): carrier now ON (device state 70)
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info>   address 192.168.1.76
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info>   prefix 24 (255.255.255.0)
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info>   gateway 192.168.1.254
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info>   nameserver '192.168.1.254'
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info>   domain name 'gateway.2wire.net'
Oct 21 02:07:44 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Oct 21 02:07:45 ilya-PC NetworkManager[856]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 21 02:07:45 ilya-PC NetworkManager[856]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Oct 21 02:07:45 ilya-PC NetworkManager[856]: <info> Activation (eth0) successful, device activated.
Oct 21 02:07:45 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 21 02:07:45 ilya-PC NetworkManager[856]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.

```

---

### Post by the_hawk22 on 2011-10-22
I take it this simply won't work on 11.10? Volume isn't working either btw. Everything was fine in 11.04. Great release!

---

### Post by Borunco on 2011-10-22
-desktop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan2  [Auto MiFi2372 8050] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        00:0F:11:21:07:D1

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *MiFi2372 8050:  Infra, 00:26:E8:0B:36:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:50:70:D6:84:FD

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


jose@jose-desktop:~$ lspci -nnk | grep -iA2 net
01:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
    Kernel driver in use: 8139too
jose@jose-desktop:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
vesafb                 13489  1 
arc4                   12473  2 
ppdev                  12849  0 
nvidia               4708682  22 
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
snd_wavefront          34737  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_cs4236             29294  0 
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236
snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib
snd_pcm                80468  4 snd_intel8x0,snd_ac97_codec,snd_cs4236,snd_wss_lib
psmouse                73673  0 
serio_raw              12990  0 
snd_mpu401             13847  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25241  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
ns558                  12654  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
gameport               15060  2 ns558
snd_timer              28932  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  18 snd_wavefront,snd_intel8x0,snd_ac97_codec,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_intel8x0,snd_wss_lib,snd_pcm
shpchp                 32356  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
pata_amd               13753  2 
8139too                23283  0 
8139cp                 22636  0 
sata_nv                23379  0 
floppy                 60310  0 
jose@jose-desktop:~$ sudo iwlist scan
[sudo] password for jose: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan2     Scan completed :
          Cell 01 - Address: 00:26:E8:0B:36:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"MiFi2372 8050"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a85186179
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 000D4D694669323337322038303530
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

jose@jose-desktop:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan2     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.437 GHz (Channel 6)

jose@jose-desktop:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n35
Oct 22 16:27:16 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 22 16:27:16 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 3 of 5 (IP Configure Start) started...
Oct 22 16:27:16 jose-desktop NetworkManager[847]: <info> (wlan2): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 22 16:27:16 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 22 16:27:16 jose-desktop NetworkManager[847]: <info> dhclient started with pid 1626
Oct 22 16:27:16 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 3 of 5 (IP Configure Start) complete.
Oct 22 16:27:16 jose-desktop dhclient: Listening on LPF/wlan2/00:0f:11:21:07:d1
Oct 22 16:27:16 jose-desktop dhclient: Sending on   LPF/wlan2/00:0f:11:21:07:d1
Oct 22 16:27:16 jose-desktop dhclient: DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 3
Oct 22 16:27:16 jose-desktop NetworkManager[847]: <info> (wlan2): DHCPv4 state changed nbi -> preinit
Oct 22 16:27:17 jose-desktop dhclient: DHCPREQUEST of 192.168.1.10 on wlan2 to 255.255.255.255 port 67
Oct 22 16:27:17 jose-desktop avahi-daemon[846]: Joining mDNS multicast group on interface wlan2.IPv6 with address fe80::20f:11ff:fe21:7d1.
Oct 22 16:27:17 jose-desktop avahi-daemon[846]: New relevant interface wlan2.IPv6 for mDNS.
Oct 22 16:27:17 jose-desktop avahi-daemon[846]: Registering new address record for fe80::20f:11ff:fe21:7d1 on wlan2.*.
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info> (wlan2): DHCPv4 state changed preinit -> bound
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) started...
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info>   address 192.168.1.10
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info>   prefix 24 (255.255.255.0)
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info>   gateway 192.168.1.1
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info>   nameserver '192.168.1.1'
Oct 22 16:27:17 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) started...
Oct 22 16:27:17 jose-desktop avahi-daemon[846]: Joining mDNS multicast group on interface wlan2.IPv4 with address 192.168.1.10.
Oct 22 16:27:17 jose-desktop avahi-daemon[846]: New relevant interface wlan2.IPv4 for mDNS.
Oct 22 16:27:17 jose-desktop avahi-daemon[846]: Registering new address record for 192.168.1.10 on wlan2.IPv4.
Oct 22 16:27:18 jose-desktop avahi-daemon[846]: Withdrawing address record for 192.168.1.10 on wlan2.
Oct 22 16:27:18 jose-desktop avahi-daemon[846]: Withdrawing workstation service for wlan2.
Oct 22 16:27:18 jose-desktop avahi-daemon[846]: Registering new address record for fe80::20f:11ff:fe21:7d1 on wlan2.*.
Oct 22 16:27:18 jose-desktop avahi-daemon[846]: Registering new address record for 192.168.1.10 on wlan2.IPv4.
Oct 22 16:27:18 jose-desktop NetworkManager[847]: <info> (wlan2): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 22 16:27:19 jose-desktop NetworkManager[847]: <info> Policy set 'Auto MiFi2372 8050' (wlan2) as default for IPv4 routing and DNS.
Oct 22 16:27:19 jose-desktop NetworkManager[847]: <info> Activation (wlan2) successful, device activated.
Oct 22 16:27:19 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 5 of 5 (IP Configure Commit) complete.
Oct 22 16:27:19 jose-desktop NetworkManager[847]: <info> Activation (wlan2) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 22 16:27:26 jose-desktop kernel: [   94.848024] wlan2: no IPv6 routers present
jose@jose-desktop:~$ 
I would greatly appreciate some one looking at my info and see, why my connection only works one at of four to five re-starts. I can allways see my network, but when i click on it, it does nothing, and also this is the second time I have been able to see my connection icon on the drop down menu (top right).
Thank you for the awsome work you all are doing in this forum:razz:

---

### Post by Borunco on 2011-10-22
PS I think wildmanne 39 Ubuntu ninja training is going very well:guitar:

---

### Post by Bubb2112 on 2011-10-22
Brand new Asus laptop, fresh install of Ubuntu 11.10 (love erasing windows immediately out of box!)

Wireless doesn't work, although it detects wireless networks. Keeps popping up & asking me for password. Password works great on 3 other computers. Here's the info you've been asking everyone else for:


```

bubb2115@bubb-2115:~$ sudo lshw -C network
[sudo] password for bubb2115: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:65:96:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:50 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:c8:7e:f4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.15.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128)
bubb2115@bubb-2115:~$ ^C
bubb2115@bubb-2115:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
    Kernel driver in use: iwlagn
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c
bubb2115@bubb-2115:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"belkin.6ba"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
bubb2115@bubb-2115:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bubb2115@bubb-2115:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
joydev                 17693  0 
arc4                   12529  2 
i915                  566711  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
iwlagn                314213  0 
mac80211              310872  1 iwlagn
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              199587  2 iwlagn,mac80211
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73882  0 
serio_raw              13166  0 
wmi                    19256  1 asus_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 
xhci_hcd               78641  0 
bubb2115@bubb-2115:~$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
[sudo] password for bubb2115: 
Oct 22 22:03:16 bubb-2115 kernel: [ 1444.428348] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 22 22:03:21 bubb-2115 kernel: [ 1450.015566] wlan0: direct probe to 94:44:52:fa:a6:ba (try 1/3)
Oct 22 22:03:22 bubb-2115 kernel: [ 1450.211716] wlan0: direct probe to 94:44:52:fa:a6:ba (try 2/3)
Oct 22 22:03:22 bubb-2115 kernel: [ 1450.411432] wlan0: direct probe to 94:44:52:fa:a6:ba (try 3/3)
Oct 22 22:03:22 bubb-2115 kernel: [ 1450.611126] wlan0: direct probe to 94:44:52:fa:a6:ba timed out
Oct 22 22:03:24 bubb-2115 kernel: [ 1452.616150] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 22 22:03:30 bubb-2115 kernel: [ 1458.183753] wlan0: direct probe to 94:44:52:fa:a6:ba (try 1/3)
Oct 22 22:03:30 bubb-2115 kernel: [ 1458.379550] wlan0: direct probe to 94:44:52:fa:a6:ba (try 2/3)
Oct 22 22:03:30 bubb-2115 kernel: [ 1458.579262] wlan0: direct probe to 94:44:52:fa:a6:ba (try 3/3)
Oct 22 22:03:30 bubb-2115 kernel: [ 1458.778964] wlan0: direct probe to 94:44:52:fa:a6:ba timed out
Oct 22 22:03:32 bubb-2115 kernel: [ 1460.783984] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 22 22:03:38 bubb-2115 kernel: [ 1466.376151] wlan0: direct probe to 94:44:52:fa:a6:ba (try 1/3)
Oct 22 22:03:38 bubb-2115 kernel: [ 1466.575348] wlan0: direct probe to 94:44:52:fa:a6:ba (try 2/3)
Oct 22 22:03:38 bubb-2115 kernel: [ 1466.775060] wlan0: direct probe to 94:44:52:fa:a6:ba (try 3/3)
Oct 22 22:03:38 bubb-2115 kernel: [ 1466.974773] wlan0: direct probe to 94:44:52:fa:a6:ba timed out
Oct 22 22:03:40 bubb-2115 kernel: [ 1468.979780] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 22 22:03:46 bubb-2115 kernel: [ 1474.543540] wlan0: direct probe to 94:44:52:fa:a6:ba (try 1/3)
Oct 22 22:03:46 bubb-2115 kernel: [ 1474.743167] wlan0: direct probe to 94:44:52:fa:a6:ba (try 2/3)
Oct 22 22:03:46 bubb-2115 kernel: [ 1474.942875] wlan0: direct probe to 94:44:52:fa:a6:ba (try 3/3)
Oct 22 22:03:47 bubb-2115 kernel: [ 1475.142633] wlan0: direct probe to 94:44:52:fa:a6:ba timed out
Oct 22 22:03:49 bubb-2115 kernel: [ 1477.203519] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
Oct 22 22:03:54 bubb-2115 kernel: [ 1482.826908] wlan0: direct probe to 94:44:52:fa:a6:ba (try 1/3)
Oct 22 22:03:54 bubb-2115 kernel: [ 1483.022852] wlan0: direct probe to 94:44:52:fa:a6:ba (try 2/3)
Oct 22 22:03:55 bubb-2115 kernel: [ 1483.222559] wlan0: direct probe to 94:44:52:fa:a6:ba (try 3/3)
Oct 22 22:03:55 bubb-2115 kernel: [ 1483.422260] wlan0: direct probe to 94:44:52:fa:a6:ba timed out
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <warn> Activation (wlan0/wireless): association took too long.
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <warn> Activation (wlan0) failed for access point (belkin.6ba)
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <warn> Activation (wlan0) failed.
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <info> (wlan0): deactivating device (reason 'none') [0]
Oct 22 22:03:56 bubb-2115 NetworkManager[882]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Oct 22 22:03:57 bubb-2115 kernel: [ 1485.423290] iwlagn 0000:02:00.0: fail to flush all tx fifo queues

```

Thank you in advance for your help :)

---

### Post by wildmanne39 on 2011-10-23
Hi the_hawk22, please post the results of:
```
iwconfig
```
```
rfkill list all
```
Unpug your wired connection then run this command please:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n35
```
Thank you

---

### Post by wildmanne39 on 2011-10-23
Hi Borunco, the answer you need is at this link and you should ask for help in that thread since it is about your wireless adapter in 11.10.
[http://ubuntuforums.org/showthread.php?p=11382127#post11382127](http://ubuntuforums.org/showthread.php?p=11382127#post11382127)

Solution is in post 55.
Thank you

---

### Post by wildmanne39 on 2011-10-23
Hi Bubb2112, the answer you need is at this link and you should ask for help in that thread since it is about your wireless adapter in 11.10.
[http://ubuntuforums.org/showthread.php?t=1862484&page=3](http://ubuntuforums.org/showthread.php?t=1862484&page=3)
Post 22 is the only answer right now until there is a fix.
Thank you

---

### Post by the_hawk22 on 2011-10-23
**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

**rfkill list all**
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

[B]Unpug your wired connection then run this command please:
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n35[/B]
```
Oct 23 15:04:36 ilya-PC NetworkManager[899]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Oct 23 15:04:40 ilya-PC NetworkManager[899]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Oct 23 15:04:40 ilya-PC NetworkManager[899]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Oct 23 15:04:40 ilya-PC NetworkManager[899]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1244

```

---

### Post by wildmanne39 on 2011-10-23
Hi, please try this:
Open synaptic or software center and install wicd then run this command:
```
sudo apt-get purge network-manager network-manager-gnome
```
Then reboot with wired connection unplugged.
Thank you

---

### Post by the_hawk22 on 2011-10-23
I did that and now neither wired nor wireless work. I'm on a phone now.

---

### Post by wildmanne39 on 2011-10-23
Hi, did you install wicd before you ran the command?
Thank you

---

### Post by the_hawk22 on 2011-10-23
Yes. I have a feeling something went really wrong during the update. Perhaps because I lost wireless somewhere along the line. There were a host of problems after the update:

-no wireless
-no volume
-upon booting, loads to shell each time, I.e. have to run startx everytime.

So rather than waste any more time, I'm just going to back up the data, format the hard drive and reinstall Windows, dual boot ubuntu and we'll see how it goes. 

Thanks for your help. I can clearly tell you know what you're doing, but my system seems too messed up at this point :-)

---

### Post by wildmanne39 on 2011-10-23
Hi, that sounds like a good idea people are having trouble with updating from an earlier version, I myself had to do a clean install.

Always do an upgrade with a wired connection if you do an upgrade, but it is best to back up data and do a clean install.
Thank you

---

### Post by pellefantus on 2011-10-24
Hello! 

I am having problems on my asus EEE laptop with the BCM 4313 card. 
At first I had 11.04, with no problems but when I upgraded to 11.10 the wireless stopped working, I then tried the tips from this thread but now my wireless works but disconnects after ~1-5 minutes of using internet...
This is my output from various commands:
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel driver in use: brcmsmac
wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:EB:C0:2A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Belkin_G_Plus_MIMO_785000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000108115534a8
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 001942656C6B696E5F475F506C75735F4D494D4F5F373835303030
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD07000C4301000000
          Cell 02 - Address: C0:3F:0E:CE:43:52
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MyPrivate-KeepOut"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000034fb6bf18e
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 00114D79507269766174652D4B6565704F7574
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602051700000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A00011010440001011041000100103B00010310470010888F1DC08309C08286555A7839FCD6391021000D4E4554474541522C20496E632E10230008574E52333530304C10240008574E52333530304C10420004333530301054000800060050F204000110110008574E52333530304C100800020084103C000101
                    IE: Unknown: DD090010180202F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051700000000000000000000000000000000000000
          Cell 03 - Address: D8:5D:4C:BB:30:E6
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"aaaaaa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000084427277
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0006616161616161
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1605001700000000000000000000000000000000000000
          Cell 04 - Address: 1C:AF:F7:7E:F5:EA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"de Laval"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020f939cf17f
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 00086465204C6176616C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700100A23FE0DBA07702BBD0D1CAFF77EF5EA10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D36313510080002008E
          Cell 05 - Address: 00:19:E3:FB:69:9C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"FK Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002985319468c
                    Extra: Last beacon: 308ms ago
                    IE: Unknown: 000A464B204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706534520010D1E
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
                    IE: Unknown: DD0700039301680120
                    IE: Unknown: DD070017F203020180
          Cell 06 - Address: 00:1C:F0:C5:A3:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Bananturken2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ebde462180
                    Extra: Last beacon: 276ms ago
                    IE: Unknown: 000C42616E616E7475726B656E32
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340600070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160600030000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 07 - Address: C0:C1:C0:49:E3:87
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"DuvaStor-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000322ec810f7
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000E4475766153746F722D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 08 - Address: C0:C1:C0:49:E3:85
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"DuvaStor"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000322ec80139
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00084475766153746F72
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B00010310470010A4111EE7C1EFF5B2FF423914E4B0FBB310210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 09 - Address: 00:1E:2A:62:3B:48
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NETGEARCHILLI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006a1a36e0f
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000D4E4554474541524348494C4C49
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:04:E2:C7:A9:4F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"SMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050c7b641ed
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 0003534D43
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010910400
          Cell 11 - Address: 00:0C:F6:85:92:62
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Sitecom859262"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a2a8d9d437
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000D53697465636F6D383539323632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AFE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000200000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706415420010D10
                    IE: Unknown: DD1E00904C33FE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000200000000000000000000000000000000000000
                    IE: Unknown: DDA10050F204104A0001101044000101103B00010310470010775B6680BFDE11D38D2F000CF68592621021000753697465636F6D1023001B576972656C6573732D4E2042726F616462616E6420526F757465721024000753697465636F6D1042002000000000000000000000000000000000000000000000000000000000000000001054000800060050F204000110110006574C5F333431100800020084103C000101
          Cell 12 - Address: 70:71:BC:48:05:D2
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Abbe1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c7e01a5e3
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 00054162626531
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: E4:CE:8F:69:91:2D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Hammarby"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000022506c1c177
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 000848616D6D61726279
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706534520010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001100000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0120
                    IE: Unknown: DD070017F203020180
          Cell 14 - Address: 00:1B:2F:8E:4B:D1
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Rumbero"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bdaef422f
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 000752756D6265726F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16070D1600000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34070D1600000000000000000000000000000000000000


```

---

### Post by karik_o on 2011-11-09
hi
I have a Dell Vostro 1500 and I have a similar problem. My wireless does not work. Could you please help me?
Thanks in advance

---

### Post by wildmanne39 on 2011-11-09
Hi karik_o, please post the results of:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Xeleno on 2011-11-10
Hello,
My wireless is not working on Ubuntu 11.10. What commands would you like reported so you can help me get this fixed? Thanks in advance

---

### Post by wildmanne39 on 2011-11-10
Hi Xeleno, welcome to the forum! please post the same commands that are in post 66 right above yours.
Thank you

---

### Post by Xeleno on 2011-11-10
```

john@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


john@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron E1405 [1028:01d8]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 01)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-Card [1028:0009]
	Kernel driver in use: wl


john@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:9  invalid misc:0

eth0      no wireless extensions.


john@ubuntu:~$ rfkill list all
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


john@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
usb_storage            57901  1 
uas                    18027  0 
rfcomm                 47946  8 
bnep                   18436  2 
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
b44                    36315  0 
ssb                    52752  1 b44
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
snd_hda_codec_idt      70553  1 
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
btusb                  18600  2 
i915                  566711  3 
psmouse                73882  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
serio_raw              13166  0 
bluetooth             166112  23 rfcomm,bnep,btusb
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
snd_seq_midi           13324  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54966  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
wmi                    19256  1 dell_wmi
mtd                    33181  2 sm_common,nand
snd_rawmidi            30547  1 snd_seq_midi
lib80211               14991  2 lib80211_crypt_tkip,wl
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci

```

---

### Post by wildmanne39 on 2011-11-10
Hi, let's try this please:
```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source

```
Then go to Additional Drivers, the STA driver activate it.
```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```
Then restart your computer after you unplug your wired connection.
Thank you

---

### Post by Xeleno on 2011-11-10
Followed the above steps, after restart it keeps trying to connect but never does.

---

### Post by wildmanne39 on 2011-11-10
Hi, 
Please blacklist this driver too and see if it works if not we will go from there.
```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
``` 
Reboot
Thank you

---

### Post by Xeleno on 2011-11-10
Didn't work, what's next?

---

### Post by wildmanne39 on 2011-11-10
Hi, does it try to connect?

Please post the results of after you disconnect your wired connection:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan -eth2 -e wpa -e etwork | tail -n55
```
```
lsmod | grep wl
```
```
dmesg | grep wl
```
Thank you

---

### Post by Xeleno on 2011-11-10
It just keeps trying to connect.

Here you go:
```
john@ubuntu:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan -eth2 -e wpa -e etwork | tail -n55
[sudo] password for john: 
Nov 10 18:23:32 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: 4-way handshake -> disconnected
Nov 10 18:23:32 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: disconnected -> scanning
Nov 10 18:23:41 ubuntu wpa_supplicant[810]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Nov 10 18:23:41 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: scanning -> disconnected
Nov 10 18:23:42 ubuntu wpa_supplicant[810]: Authentication with 00:00:00:00:00:00 timed out.
Nov 10 18:23:46 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: disconnected -> scanning
Nov 10 18:23:54 ubuntu wpa_supplicant[810]: Trying to associate with 00:1c:f0:f3:5d:8a (SSID='Croomville' freq=2437 MHz)
Nov 10 18:23:54 ubuntu wpa_supplicant[810]: Association request to the driver failed
Nov 10 18:23:54 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: scanning -> associating
Nov 10 18:23:59 ubuntu wpa_supplicant[810]: Authentication with 00:1c:f0:f3:5d:8a timed out.
Nov 10 18:23:59 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: associating -> scanning
Nov 10 18:24:28 ubuntu NetworkManager[798]: <warn> Activation (eth2/wireless): association took too long.
Nov 10 18:24:28 ubuntu NetworkManager[798]: <info> (eth2): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 10 18:24:28 ubuntu NetworkManager[798]: <warn> Activation (eth2/wireless): asking for new secrets
Nov 10 18:24:28 ubuntu NetworkManager[798]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 10 18:24:28 ubuntu NetworkManager[798]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 10 18:24:29 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: scanning -> inactive
Nov 10 18:24:32 ubuntu NetworkManager[798]: <warn> No agents were available for this request.
Nov 10 18:24:32 ubuntu NetworkManager[798]: <info> (eth2): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 10 18:24:32 ubuntu NetworkManager[798]: <warn> Activation (eth2) failed for access point (Croomville)
Nov 10 18:24:32 ubuntu NetworkManager[798]: <info> Marking connection 'Croomville' invalid.
Nov 10 18:24:32 ubuntu NetworkManager[798]: <warn> Activation (eth2) failed.
Nov 10 18:24:32 ubuntu NetworkManager[798]: <info> (eth2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 10 18:24:32 ubuntu NetworkManager[798]: <info> (eth2): deactivating device (reason 'none') [0]
Nov 10 18:25:14 ubuntu wpa_supplicant[810]: No network configuration found for the current AP
Nov 10 18:25:14 ubuntu wpa_supplicant[810]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Nov 10 18:25:14 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: inactive -> disconnected
Nov 10 18:25:28 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: disconnected -> inactive
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Auto-activating connection 'Croomville'.
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) starting connection 'Croomville'
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> (eth2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> (eth2): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2/wireless): access point 'Croomville' has security, but secrets are required.
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> (eth2): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> (eth2): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> (eth2): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2/wireless): connection 'Croomville' has security, and secrets exist.  No new secrets needed.
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Config: added 'ssid' value 'Croomville'
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Config: added 'scan_ssid' value '1'
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Config: added 'psk' value '<omitted>'
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> Config: set interface ap_scan to 1
Nov 10 18:34:28 ubuntu NetworkManager[798]: <info> (eth2): supplicant interface state: inactive -> scanning


john@ubuntu:~$ lsmod | grep wl
wl                   2568210  0 
lib80211               14991  2 lib80211_crypt_tkip,wl


john@ubuntu:~$ dmesg | grep wl
[   49.170700] wl: module license 'MIXED/Proprietary' taints kernel.
[   49.343687] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   49.343697] wl 0000:0c:00.0: setting latency timer to 64


```

Thanks

---

### Post by wildmanne39 on 2011-11-10
Hi, please post the results of:
```
nm-tool
```
```
sudo iwlist scan
```
I think it is a problem with how network manager handles encryption but we can also try the b43 driver that is suppose to work with your card in 11.10 so I am deciding which one to try first and the information will help me decide.
Thank you

---

### Post by Xeleno on 2011-11-10
Here you go:
```
john@ubuntu:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: eth2  [Croomville] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:16:CF:20:9E:7B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    qwest1360:       Infra, 00:23:75:0A:8E:10, Freq 2412 MHz, Rate 0 Mb/s, Strength 20 WPA WPA2
    Croomville:      Infra, 00:1C:F0:F3:5D:8A, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2
    Apple Dave:      Infra, 28:CF:DA:AF:82:94, Freq 5755 MHz, Rate 0 Mb/s, Strength 40 WPA2
    Apple Dave:      Infra, 28:CF:DA:AF:82:93, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Davo:            Infra, 00:18:39:82:68:C5, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:15:C5:63:1F:D2

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


john@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:18:39:82:68:C5
                    ESSID:"Davo"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1C:F0:F3:5D:8A
                    ESSID:"Croomville"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-46 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A0001101044000102103B000103104700102F76B6EEE7D63F82B5C37387A062C4991021000E442D4C696E6B2053797374656D73102300074449522D363535102400024133104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 28:CF:DA:AF:82:93
                    ESSID:"Apple Dave"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-62 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 28:CF:DA:AF:82:94
                    ESSID:"Apple Dave"
                    Mode:Managed
                    Frequency:5.755 GHz
                    Quality:2/5  Signal level:-78 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.

```

---

### Post by wildmanne39 on 2011-11-10
Hi, your encryption is set to wpa/wpa2 linux has trouble with mixed mode a lot of the time.

Go to network icon top right of the screen click edit connection wireless then set to wpa2 only, then type 192.168.0.1 into web browser go to wireless security and set encryption to wpa2 only if you have that option.
Thank you

---

### Post by Xeleno on 2011-11-10
Hello,
I don't have the option to set it to wpa2 only in edit connections. The only option is wpa & wpa2 personal.
Thanks for your help

---

### Post by wildmanne39 on 2011-11-10
Hi, ok then I recommend we try this.
[http://ubuntuforums.org/showthread.php?t=1865420&page=2](http://ubuntuforums.org/showthread.php?t=1865420&page=2)
Post 12.
Thank you

---

### Post by Xeleno on 2011-11-10
Ethernet and Wireless aren't showing up at all anymore. So definitely not connecting. Did I do something incorrectly?

---

### Post by wildmanne39 on 2011-11-10
Did you install wicd before you got rid of network manager?

Did you reboot and see if it came alive with wicd?
thank you

---

### Post by Xeleno on 2011-11-10
It showed wicd already installed.

I rebooted and same thing.

---

### Post by wildmanne39 on 2011-11-10
Hi, go to dash type wicd then click on wicd and see if your wired connection is turned on.

Then you can set up your wireless if it sees it.
Thank you

---

### Post by Xeleno on 2011-11-10
Nothing showed up when I typed wicd in the dash, must not be installed :( I'm not sure why.

How do I get it now?

---

### Post by wildmanne39 on 2011-11-10
Hi, ok you did run the command to get rid of network manager right? If so we have to get it installed again before we can install wicd.

Wicd has to be installed before network is removed or you will not be able to install wicd. 

You do have a livecd right?
Thank you

---

### Post by Xeleno on 2011-11-10
I did remove network manager. How do I get it installed again?

---

### Post by wildmanne39 on 2011-11-10
Hi, follow the directions here and you should get network manager installed, then just make sure you install wicd before removing network manager.
[http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection](http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection)

Wicd does not show up in the top panel you have to use dash to open it but once it is setup you have no need to open it again.
Thank you

---

### Post by d3v1150m471c on 2011-11-10
you could always try wicd but it might not fix your problem. it does however fix network-manager ^_^

---

### Post by Xeleno on 2011-11-11
Alright on wicd it gets stuck at validating authentication and pops up an error "bad password". The password is correct though.

---

### Post by wildmanne39 on 2011-11-11
Hi, reset your router please.

Did you run the command to get rid of network manager? 

Did you reboot?
Thank you

---

### Post by Xeleno on 2011-11-11
Yes I did those three things, same error.
Thanks

---

### Post by wildmanne39 on 2011-11-11
Hi, I am going to ask a friend to take a look.
Thank you

---

### Post by Xeleno on 2011-11-11
Alright thank you

---

### Post by praseodym on 2011-11-11
Hi there,

did the command

```
sudo apt-get install bcmwl-kernel-source
```
install all the dependencies (namely the packages dkms, patch, and fakeroot)?

Try to install all needed things again:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms patch fakeroot bcmwl-kernel-source
sudo depmod -a
```
De- and reactivate the Broadcom-STA driver. Any strange signs or blanks in the ESSID or the key?

---

### Post by Xeleno on 2011-11-11
Hi,
So during depmod a power loss turned my computer off and now it's not booting into ubuntu. It says:
```
error: couldn't read file.
 Press any key to continue . . ._
```

---

### Post by praseodym on 2011-11-11
Can you choose the "Recovery Mode" by pressing SHIFT during the first seconds of trying to boot? If yes, try this:

```
apt-get -f install
dpkg --configure -a
reboot
```

---

### Post by Xeleno on 2011-11-11
Same error occurs in recovery mode

---

### Post by praseodym on 2011-11-11
Ok, at least this works. Try there:

```
update-initramfs -u
reboot
```

---

### Post by Xeleno on 2011-11-11
I can't get into recovery mode because it says "error: couldn't read file"

---

### Post by praseodym on 2011-11-11
Ok, now you can repair your system with a Live-CD (the one you used to install). Boot with it and show the outputs of:

```
sudo blkid
sudo fdisk -l
cd media/
ls -l
```

---

### Post by wildmanne39 on 2011-11-11
Hi, that happens a lot during a power loss, it may not even have anything to do with the commands you were running at the time, power loss causes file corruption and bad sectors on the hard drive.

Thank you praseodym.

---

### Post by achilles261 on 2011-12-16
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After it intalls disconnect your wired connection and restart your computer.
I may not  be the original poster too, but this fix my situation as well. i've been working on it for days trying everything i found in this forum and this simple two things fix my thing.

---

### Post by thegant on 2011-12-17
>  Hi everyone,
I [like a few people here] recently downloaded/installed ubuntu 10.11 and since I am having a few problems with my wireless connection.
I was hoping someone here mght be able help me or point me into the right direction to resolve this issue. I've attached a notepad with my results from the following commands:
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
```

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.


I have also downloaded the zip file [on page 2 of this thread] which consisted on the b43 file. I carried out the commands attached, but again no luck.
I've tried rebooting many times :)
Any help would be greatly appricated.
thanks,
thegant

---

### Post by praseodym on 2011-12-17
Hi thegant,

the module "wl" from the STA driver is still loaded:

```
sudo modprobe -rfv wl
sudo modprobe -v b43
```
Check:
```
iwconfig
dmesg | grep b43
sudo iwlist scan
rfkill list
iwlist chan
```
Is it a Dell laptop?

---

### Post by wildmanne39 on 2011-12-17
Hi, did you have a connection to the internet when you ran the purge command and the install command?

This should get you going but you will need to be hard wired to the internet first. 
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get purge firmware-b43-lpphy-installer
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Reboot and it should be working.
thank you

---

### Post by thegant on 2011-12-17
> **praseodym said:**
> Hi thegant,

the module "wl" from the STA driver is still loaded:

```
sudo modprobe -rfv wl
sudo modprobe -v b43
```
Check:
```
iwconfig
dmesg | grep b43
sudo iwlist scan
rfkill list
iwlist chan
```
Is it a Dell laptop?

Hi praseodym, 
thanks a million - it is a Dell laptop and the commands you supplied above worked!
Can't believe it - thanks for you quick reply and help.

> **wildmanne39 said:**
> Hi, did you have a connection to the internet when you ran the purge command and the install command?

This should get you going but you will need to be hard wired to the internet first. 
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get purge firmware-b43-lpphy-installer
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Reboot and it should be working.
thank you

Hi wildmanne39,
thanks for your quick reply also. You were right, I wasnt connected to the internet. But the command that praseodym supplied worked before I got to yours.
Thanks a million - youre both very good to help.
Best regards,
thegant

---

### Post by wildmanne39 on 2011-12-17
Hi, glad it is working.

---

### Post by comperocean on 2011-12-25
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```After it intalls disconnect your wired connection and restart your computer.

i use the method above, and that resolve my issue, but some update from above.
the package "firmware-b43-installer " changed to "firmware-b43-lpphy-installer", the "lpphy" is low power.
thanks again.

computer setting [Dell inspiron, broadcom 4312 wireless], for reference.

---

### Post by wildmanne39 on 2011-12-25
Hi, I am glad you got it working!
Enjoy

---

### Post by csuggs4 on 2011-12-27
My HP dv9000 worked with the b43 driver and not the bcmwl driver.  I have a Broadcom BCM4311 [14e4:4311].

Had to make sure I uninstalled the bcmwl driver for the wireless card to work.  

Thanks

---

### Post by wildmanne39 on 2011-12-27
Hi, I am glad it is working! 
Enjoy

---

### Post by a7x1123 on 2012-01-19
Hi I've been having the same problem.
I have a Dell Dimension Desktop with a brand new Netgear wireless adapter (Broadcom BCM4323) and am very new to linux.
I have tried every proposed solution in this thread with no luck.
If anyone can help it would be much appreciated, just let me know what commands you would like me to run and I'll post the results.

---

### Post by wildmanne39 on 2012-01-19
Hi a7x1123, from what I read you will have to use ndiswrapper for this device.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Here are instructions for using it please read carefully, if it looks to much for you I suggest you post in this thread.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

---

### Post by praseodym on 2012-01-19
Hi,

can you please show:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```
Check the device ID here ("No" or "partially" only is related to b43/b43legacy):

[http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices)

You may try to compile the latest Broadcom-STA-driver on your own. Download here
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Uninstall the STA driver if installed before after deactivating it:

```
sudo apt-get remove --purge bcmwl-kernel-source
```

But ndiswrapper could be the way, the README reads

```
	   BRCM		    PCI		  PCI		  Dell
	  Product Name	  Vendor ID	Device ID	Product ID
          -------------	 ----------	---------   	-----------
          4311 2.4 Ghz	    0x14e4	0x4311  	Dell 1390
          4311 Dualband	    0x14e4	0x4312  	Dell 1490
          4311 5 Ghz	    0x14e4    	0x4313  	
          4312 2.4 Ghz	    0x14e4	0x4315  	Dell 1395
          4313 2.4 Ghz	    0x14e4	0x4727 		Dell 1501
          4321 Dualband	    0x14e4	0x4328  	Dell 1505
          4321 Dualband	    0x14e4	0x4328  	Dell 1500
          4321 2.4 Ghz	    0x14e4	0x4329  	
          4321 5 Ghz        0x14e4	0x432a  	
          4322 	Dualband    0x14e4	0x432b  	Dell 1510
          4322 2.4 Ghz      0x14e4 	0x432c  	
          4322 5 Ghz        0x14e4 	0x432d  	
          43224 Dualband    0x14e4	0x4353  	Dell 1520
          43225 2.4 Ghz     0x14e4	0x4357  	
          43227 2.4 Ghz     0x14e4	0x4358
          43228 Dualband    0x14e4	0x4359  	Dell 1530
```
No 4323 listed

---

### Post by Padwick on 2012-01-31
Ok. I've read most of what has been available on internet about now, and i still haven't been able to get a wireless conn working. I've recently installed Ubuntu 11.10, my computer is a HP Pavillion ZD8000, my wireless card is a Broadcom Corp BCM4318. And yes, i'm a total newbie...

Ive been trying to install b43-fwcutter and it seems ok but nothing comes up i 'additional drivers'.

Please help me. I'm running a wired conn now.

What do you need?

---

### Post by BlueToBits on 2012-01-31
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After it intalls disconnect your wired connection and restart your computer.

This is great. Worked a treat for my Dell Latitude D620.
Had the additional driver but had av "unclaimed" Broadcom wireless network device 

Thanks Wildmanne39.

---

### Post by arvindg14 on 2012-02-01
Hi 
I have recently loaded ubuntu 11.10 on laptop. Broadcom wireless 4312. It doesn't work. I do not have any internet on this laptop. Can you suggest a way out without internet on this laptop?
 
I went into system settings>Additional Drivers. Tried to "activate" Broadcom STA Wireless Driver. At said "Installation of this driver failed. Please have a look at the log file for details:/var/log/jockey.log. I don't know where to look for this log file and can I do that without internet on this laptop?
 
Thanks for your help.
Arvindg14

---

### Post by wildmanne39 on 2012-02-03
Hi arvindg14, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by arvindg14 on 2012-02-03
Thanks for your reply wildmanne39. I have ubuntu and window vista on the same laptop. I have to boot up with ubuntu to run those commands. Then I will have to boot up with window vista to log-in in this forum to paste the results here. 
1. How to copy from ubutu system and then paste in vista system?
2. I dont have the the vertical bar after -nnk in the command "lspci -nnk | grep -iA2 net" is typed using what key in laptop. I do not have that on my keyboard of my laptop.
Sorry, I am absolute beginner.
Thanks
Arvind

---

### Post by arvindg14 on 2012-02-04
Hi Wildmanne

The results are given below:

cat / etc/ lsb-release; uname -a
{Cat: /: Is a directory
Cat: etc: No such file or directory
Cat: /: Is a directory
Cat: lsb-release: No such file or directory
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 07 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux}

lspci -nnk / grep -iA2 net

{usage: lspci [<switches>]

Basic Display Modes:
-mm      Produce machine-readable output (single -m for an obsolete format)
-t       Show bus tree

Display Options:
-v    Be verbose (-vv for every verbose)
-k    Show kernel drivers handling each device
-x    show hex-dump of the standard part of the config space
-xxx  show hex-dump of the whole config space (dengerous; root only)
-xxxx Show hex-dump of the 4096 byte extended config space (root only)
-b    Bus-centric view (addresses and IRQ's as seen by the bus)
-D    Always show domain numbers

Resolving of device ID's to names:
-n    Show numeric ID's
-nn   Show both textual and numeric ID's (name and numbers)
-q    Query the PCI ID database for unknown ID's via DNS
-qq   As above, but requery locally cached entries
-Q    Query the PCI ID database for all ID's via DNS

Selection of Devices:
-s [[[[<domain>]:][<slot>][.[<func>]] Show only devices in selected slots
-d [<vendor>]:[<device>]  show only devices with specified ID's

Other options:
-i <file>  use specified ID database instead of A2
-p <file>  Look up kernel modules in a given file instead of default module s.pcimap
-M      Enable 'bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>  Use the specified PCI access method (see '-A hep' for a list)
-O <par>=<val> Set PCI access parameter (see '-o help' for a list)
-G             Enable PCI access debugging
-H <mode>      Use direct hardware access (<mode>=1 or 2)
-F ,file>      Read PCI configuration dump from a given file}

iwconfig:

{lo    no wireless extensions
eth0   no wireless extensions
wlan0  IEEE 802.11bg ESSID:off/any
       Mode: Managed Access Point: Not associated Tx-Power=0 dbm
       Retry long limit: 7 RTS thr:off Fragment thr: off
       Power management: on}

rfkill list all:

{0:   phy0: Wireless LAN
           Soft blocked: no
           hard blocked: no
1:  hp-wifi: Wireless LAN
           Soft blocked: no
           hard blocked: no
2: hp-bluetooth: Bluetooth
           Soft blocked: yes
           hard blocked: no}

lsmod:

{
Module       Size      Used by
bnep         18436     2
rfcomm       47946     0
bluetooth    166112    10 bnep, rfcomm
parport_pc   36962     0
ppdev        17113     0
lp           17799     0
parport      46562     3  parport-pc, ppdev, lp
snd_hda_codec_conexant 62197   1
binfmt_misc   17540    1
arc4         12529     2
joydev       17693     0
snd_hda_intel  33390   2
snd_hda_codec  104802  2  snd_hda_codec_conexant, snd_hda_intel
snd_hwdep   13668  1  snd_hda_codec
hp_wmi   18092  0
sparse_keymap   13890  1  hp_wmi
snd_pcm         96755  2  snd_hda_intel, snd_hda_codec
snd_seq_midi    13324  1  snd_seq_midi
snd_seq_midi_event  14899  1  snd_seq_midi
uvcvideo    72711   0
videodev   93004   1  uvcvideo
snd_seq    61896  2  snd_seq_midi, snd_seq_midi_event
v4l2_compat_ioctl32   17083   1   videodev
i915   566711   3
b43    341198   0
snd_timer   29991   2  snd_pcm, snd_seq
r852    18277   0
snd-seq_device   14540   3  snd_seq_midi, snd-rawmidi, snd_seq
sm_common    16865   1  r852
nand    54966   2  r852, sm_common
nand_ids    12723  1  nand
nand_bch    13147  1  nand_bch
nand_ecc   13230   1   nand
psmouse    73882   0
serio_raw   13166  0
snd    68266  13  snd_hda_codec_conexant, snd_hda_intel, snd_hda_codec, snd_hwdep, snd_pcm, snd_rawmidi, snd_seq, snd_timer, sm_common, nand
mac80211    310872   1  b43
drm_kms_helper   42558   1 i915
drm   236330   4  i915, drm_kms_helper
cfg80211   199587  2  b43,mac80211
soundcore   12680  1  snd
snd_page-alloc   18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit   13423   1  i915
wmi   19256   1  hp_wmi
video   19412  1 i915
firewire_ohci   40722  0
sdhci_pci  14032  0
sdhci   32166   1  sdhci_pci
firewire_core   63626   1  firewire_ohci
crc_itu_t   12707   1   firewire_core
ahci   26002   1
ibahci   26861   1   ahci
ssb    52752   1   b43
skyz   58674   0
}

I hope this help.
Thanks
Arvindg14

---

### Post by Padwick on 2012-02-04
> **Padwick said:**
> Ok. I've read most of what has been available on internet about now, and i still haven't been able to get a wireless conn working. I've recently installed Ubuntu 11.10, my computer is a HP Pavillion ZD8000, my wireless card is a Broadcom Corp BCM4318. And yes, i'm a total newbie...

Ive been trying to install b43-fwcutter and it seems ok but nothing comes up i 'additional drivers'.

Please help me. I'm running a wired conn now.

What do you need?

Noone? Im kinda stuck. Pleeease?

---

### Post by wildmanne39 on 2012-02-05
Hi arvindg14, looks like you figured out how to post the information here, also refer to my previous post and it will tell you how to put the commands into the terminal and you will not have to worry about typing the commands that way you will have no typos.
Thanks

---

### Post by wildmanne39 on 2012-02-05
> **Padwick said:**
> Noone? Im kinda stuck. Pleeease?Hi, please post the output of the commands in post 119.
Thanks

---

### Post by arvindg14 on 2012-02-05
Hello Wildmanne39,
I have posted the results in post 121. Could you suggest what should i do next?
Thanks
Arvind

---

### Post by praseodym on 2012-02-05
Hi,

you had typos there. You can c/p the commands, if neccessary.

"Tx-Power = off" means, there is a button, switch, key, or key combination to activate the wireless. Also check you BIOS if it can be activated there. Maybe resetting the BIOS?!

---

### Post by wildmanne39 on 2012-02-05
Hi arvindg14, yes I saw what you posted but not all commands were typed into the terminal correctly and my reference to my previous post was to get you to go back and read where I wrote copy and paste the commands into the terminal that makes it easier on you and usually insures accuracy.

This is the command that did not come out right:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by Padwick on 2012-02-05
Thanks. Ok, here goes.

```
                                   
**cat /etc/lsb-release; uname -a **
DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=11.10 
 DISTRIB_CODENAME=oneiric 
 DISTRIB_DESCRIPTION="Ubuntu 11.10" 
 Linux biffen-Pavilion-zd8000-EL026EA-AK8 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux 

**lspci -nnk | grep -iA2 net **
0b:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
     Subsystem: Hewlett-Packard Company Device [103c:3082] 
     Kernel driver in use: 8139too 
 -- 
 0b:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
     Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1356] 
     Kernel driver in use: b43-pci-bridge 

**iwconfig **
lo        no wireless extensions. 
eth0      no wireless extensions. 

**rfkill list all** 
0: hci
0: Bluetooth 
Soft blocked: no 
Hard blocked: no 
1: hp-wifi: Wireless LAN 
Soft blocked: no 
Hard blocked: no 
2: hp-bluetooth: Bluetooth 
Soft blocked: no 
Hard blocked: no
 
[B]lsmod 
[/B]Module                  Size  Used by 
 bnep                   17923  2  
 rfcomm                 38408  8  
 parport_pc             32114  0  
 ppdev                  12849  0  
 joydev                 17393  0  
 hp_wmi                 13652  0  
 sparse_keymap          13658  1 hp_wmi 
 binfmt_misc            17292  1  
 snd_intel8x0           33318  2  
 snd_ac97_codec        106082  1 snd_intel8x0 
 ac97_bus               12642  1 snd_ac97_codec 
 snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec 
 snd_seq_midi           13132  0  
 snd_rawmidi            25241  1 snd_seq_midi 
 snd_seq_midi_event     14475  1 snd_seq_midi 
 pcmcia                 39822  0  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
 btusb                  18160  2  
 bluetooth             148839  23 bnep,rfcomm,btusb 
 snd_timer              28932  2 snd_pcm,snd_seq 
 psmouse                73673  0  
 serio_raw              12990  0  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
 video                  18908  0  
 tifm_7xx1              12937  0  
 tifm_core              15040  1 tifm_7xx1 
 wmi                    18744  1 hp_wmi 
 yenta_socket           27428  0  
 pcmcia_rsrc            18367  1 yenta_socket 
 snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc 
 radeon                925178  3  
 ttm                    65224  1 radeon 
 drm_kms_helper         32889  1 radeon 
 soundcore              12600  1 snd 
 drm                   192194  5 radeon,ttm,drm_kms_helper 
 snd_page_alloc         14115  2 snd_intel8x0,snd_pcm 
 i2c_algo_bit           13199  1 radeon 
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp 
 8139too                23283  0  
 8139cp                 22636  0  
 firewire_ohci          35854  0  
 sdhci_pci              13658  0  
 ssb                    50682  0  
 firewire_core          56937  1 firewire_ohci 
 sdhci                  27360  1 sdhci_pci 
 crc_itu_t              12627  1 firewire_core
  
```

---

### Post by wildmanne39 on 2012-02-05
Hi, if you have an internet connection run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
then reboot and it should be working.
Thanks

---

### Post by Chasmo on 2012-02-05
charlie@charlie-laptop:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
[sudo] password for charlie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer
charlie@charlie-laptop:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-33-generic fakeroot diffstat debhelper module-assistant
  linux-headers-2.6.32-33 intltool-debian g++-4.4 quilt po-debconf
  libstdc++6-4.4-dev g++ libmail-sendmail-perl gettext cvs dpkg-dev xz-utils
  html2text patch libsys-hostname-long-perl build-essential
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
charlie@charlie-laptop:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
E: Couldn't find package firmware-b43-installer
charlie@charlie-laptop:~$ 


So why wont it find... E: Couldn't find package firmware-b43-installer

---

### Post by wildmanne39 on 2012-02-05
Hi Chasmo, did you have an internet connection when you tried that command? please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by praseodym on 2012-02-06
Hi,

the firmware packages dont work properly in 11.10. Try this firmware by hand:

```
wget [http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz](http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz) 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
```

---

### Post by Padwick on 2012-02-06
> **wildmanne39 said:**
> Hi, if you have an internet connection run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```then reboot and it should be working.
Thanks

Eeeh, well.. not quite. After running the command, the comp installed and extracted something. So far so good, but after rebooting still no wireless. When i enter system/network there's no wireless conn.

---

### Post by praseodym on 2012-02-06
Tried that other firmware package?

---

### Post by wildmanne39 on 2012-02-06
Hi Padwick, did you watch the terminal to make sure there were no errors?

Also praseodym solution may fix the issue.

You can post the output of:
```
sudo iwlist scan
lsmod | grep b43
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e etork | tail -n45
```
and it will tell us more.
Thanks

---

### Post by Padwick on 2012-02-06
Ok, ive tried both solutions now but no success.. im almost sure there was no errors the first time, with the second solution im sure.

About the outcome of the last codes; 
```

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning

sudo ca /var/log/syslog | grep -e b43 -e firmware -e etork | tail -n45
sudo: ca: command not found


```

"lsmod | grep b43" didnt generate anything but a new line, so to speak.

---

### Post by wildmanne39 on 2012-02-06
Hi Padwick, please try:
```
sudo modprobe b43
```
if that does not work copy and paste this command into the terminal:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e etork | tail -n45
```
for accuracy and paste the output here.
Thanks

---

### Post by Padwick on 2012-02-06
```
sudo modprobe b43
```

generated 
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.

```


```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e etork | tail -n45
```

generated
```
Feb  6 22:29:45 biffen-Pavilion-zd8000-EL026EA-AK8 NetworkManager[568]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb  6 23:53:52 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5068.496921] b43-pci-bridge 0000:0b:03.0: enabling device (0000 -> 0002)
Feb  6 23:53:52 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5068.496936] b43-pci-bridge 0000:0b:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb  6 23:53:52 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5068.870826] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Feb  6 23:53:53 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5069.548816] Registered led device: b43-phy0::radio
Feb  6 23:53:54 biffen-Pavilion-zd8000-EL026EA-AK8 NetworkManager[568]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Feb  6 23:53:54 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5071.088051] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

---

### Post by wildmanne39 on 2012-02-06
Hi Padwick, post the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
this command:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e etork | tail -n45
```
should have had 45 lines, is that all it showed?
thanks

---

### Post by vhradice on 2012-02-06
I am having a similar problem.  I am trying to connect to a WPA/2 secured network.   I have a Netgear WNA3100 usb adapter.  I have tried everything listed here and other places but I cannot connect to the secure network.  If I remove the security I can connect.  I have tried the bcmwlhigh5 drivers and the bcmn43xx32 drivers.  Neither worked.  I downloaded and tried to install the Broabcom-STA drivers but I cannot figure out how to connect these drivers with my usb adapter.  I tried to copy the wl.ko file to the place that the Broadcom README file indicates the file should be.  I followed the rest of the install commands.  Now iwconfig does not even show the wireless adapter.  If I use ndiswrapper with either of the 2 drivers, iwconfig shows the wireless adapter.  If I try to connect to a secure network, i keep getting asked to supply the password.  I enter it correctly but I still do no get connected.  Right now I am using a wired connection to get in.  I need to get the wireless working.  I will gladly supply any debugging info requested.
Thanks in advance.
lsusb
\Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

---

### Post by arvindg14 on 2012-02-06
Hi Wildmanne39
 
I do not have vertical bar on my laptop. vertical bar as in this command after -nnk; "lspci -nnk | grep -iA2 net
". How to yepe that?
 
Secondly, can you suggest a way to copy and paste from this screen which I am seeing on Windows Vista to a terminal on Ubuntu?
 
Thanks
Arvind

---

### Post by wildmanne39 on 2012-02-06
Hi arvindg14, if you copy and paste the command into the terminal you do not need the bar on your key board.

This key | is located just above the enter key on most key boards.

Copy the output of the commands to a flash drive and then use vista to paste here and vice versa.
Thanks

---

### Post by wildmanne39 on 2012-02-06
Hi vhradice, you need to use ndiswrapper with the usb adapter from what I can tell, I am going to give you a link to the ndiswrapper thread so you can get the help you need and to keep this thread just wireless devices that do not need ndiswrapper.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Also here are directions for that device.
[http://ubuntuforums.org/showthread.php?t=1549190&highlight=BCM43231&page=9](http://ubuntuforums.org/showthread.php?t=1549190&highlight=BCM43231&page=9)
Thanks

---

### Post by vhradice on 2012-02-06
I have the latest ndiswrapper.

 ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.0.0-15-generic/misc/ndiswrapper.ko
version:        1.57
vermagic:       3.0.0-15-generic SMP mod_unload modversions 686 


How do I connect the Broadcom-STA drivers to my Netgear usb adapter?

---

### Post by wildmanne39 on 2012-02-07
Hi vhradice, I gave you links to get the help you need in my last post because I have never worked with ndiswrapper and this thread is not for ndiswrapper issues, please ask for help at the first link I posted.
Thanks

---

### Post by Padwick on 2012-02-07
"cat /etc/modprobe.d/blacklist.conf" resulted in
```

# This file lists those modules which we don't want to be loaded by
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

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```
This is all that shows when I type "sudo cat /var/log/syslog | grep -e b43 -e firmware -e etork | tail -n45"
```

Feb  6 22:29:45 biffen-Pavilion-zd8000-EL026EA-AK8 NetworkManager[568]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb  6 23:53:52 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5068.496921] b43-pci-bridge 0000:0b:03.0: enabling device (0000 -> 0002)
Feb  6 23:53:52 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5068.496936] b43-pci-bridge 0000:0b:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb  6 23:53:52 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5068.870826] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Feb  6 23:53:53 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5069.548816] Registered led device: b43-phy0::radio
Feb  6 23:53:54 biffen-Pavilion-zd8000-EL026EA-AK8 NetworkManager[568]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Feb  6 23:53:54 biffen-Pavilion-zd8000-EL026EA-AK8 kernel: [ 5071.088051] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Feb  6 23:58:25 biffen-Pavilion-zd8000-EL026EA-AK8 NetworkManager[702]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb  7 20:59:31 biffen-Pavilion-zd8000-EL026EA-AK8 NetworkManager[573]: <info> monitoring kernel firmware directory '/lib/firmware'.

```

---

### Post by wildmanne39 on 2012-02-07
Hi Padwick, after you downloaded the file in post 132 did you run the second command that started with sudo?  You do have a wired connection on your ubuntu computer right?

I have older firmware you can use but the one for post 132 should be better.
Thanks

---

### Post by arvindg14 on 2012-02-08
Hi Wildmanne

The results are given below:

$ lspci -nnk | grep -iA2 net 
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14) 
	Subsystem: Hewlett-Packard Company Device [103c:30cd] 
	Kernel driver in use: sky2 
-- 
07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d] 
	Kernel driver in use: b43-pci-bridge 

cat / etc/ lsb-release; uname -a
{Cat: /: Is a directory
Cat: etc: No such file or directory
Cat: /: Is a directory
Cat: lsb-release: No such file or directory
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 07 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux}

iwconfig:

{lo no wireless extensions
eth0 no wireless extensions
wlan0 IEEE 802.11bg ESSIDff/any
Mode: Managed Access Point: Not associated Tx-Power=0 dbm
Retry long limit: 7 RTS thrff Fragment thr: off
Power management: on}

rfkill list all:

{0: phy0: Wireless LAN
Soft blocked: no
hard blocked: no
1: hp-wifi: Wireless LAN
Soft blocked: no
hard blocked: no
2: hp-bluetooth: Bluetooth
Soft blocked: yes
hard blocked: no}

lsmod:

{
Module Size Used by
bnep 18436 2
rfcomm 47946 0
bluetooth 166112 10 bnep, rfcomm
parport_pc 36962 0
ppdev 17113 0
lp 17799 0
parport 46562 3 parport-pc, ppdev, lp
snd_hda_codec_conexant 62197 1
binfmt_misc 17540 1
arc4 12529 2
joydev 17693 0
snd_hda_intel 33390 2
snd_hda_codec 104802 2 snd_hda_codec_conexant, snd_hda_intel
snd_hwdep 13668 1 snd_hda_codec
hp_wmi 18092 0
sparse_keymap 13890 1 hp_wmi
snd_pcm 96755 2 snd_hda_intel, snd_hda_codec
snd_seq_midi 13324 1 snd_seq_midi
snd_seq_midi_event 14899 1 snd_seq_midi
uvcvideo 72711 0
videodev 93004 1 uvcvideo
snd_seq 61896 2 snd_seq_midi, snd_seq_midi_event
v4l2_compat_ioctl32 17083 1 videodev
i915 566711 3
b43 341198 0
snd_timer 29991 2 snd_pcm, snd_seq
r852 18277 0
snd-seq_device 14540 3 snd_seq_midi, snd-rawmidi, snd_seq
sm_common 16865 1 r852
nand 54966 2 r852, sm_common
nand_ids 12723 1 nand
nand_bch 13147 1 nand_bch
nand_ecc 13230 1 nand
psmouse 73882 0
serio_raw 13166 0
snd 68266 13 snd_hda_codec_conexant, snd_hda_intel, snd_hda_codec, snd_hwdep, snd_pcm, snd_rawmidi, snd_seq, snd_timer, sm_common, nand
mac80211 310872 1 b43
drm_kms_helper 42558 1 i915
drm 236330 4 i915, drm_kms_helper
cfg80211 199587 2 b43,mac80211
soundcore 12680 1 snd
snd_page-alloc 18529 2 snd_hda_intel,snd_pcm
i2c_algo_bit 13423 1 i915
wmi 19256 1 hp_wmi
video 19412 1 i915
firewire_ohci 40722 0
sdhci_pci 14032 0
sdhci 32166 1 sdhci_pci
firewire_core 63626 1 firewire_ohci
crc_itu_t 12707 1 firewire_core
ahci 26002 1
ibahci 26861 1 ahci
ssb 52752 1 b43
skyz 58674 0
}

I hope this help.
Thanks
Arvindg14

---

### Post by wildmanne39 on 2012-02-08
Hi arvindg14, please post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
```
nm-tool
```
> Tx-Power=0 dbm
means that the switch may be off so check your switch or it may be a key combination that turns it on or possibly turned off in your bios.

Also please do:
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
save and close gedit then reboot.
Thanks

---

### Post by Padwick on 2012-02-08
> **wildmanne39 said:**
> Hi Padwick, after you downloaded the file in post 132 did you run the second command that started with sudo?  You do have a wired connection on your ubuntu computer right?

I have older firmware you can use but the one for post 132 should be better.
Thanks

Yes, i think so at least.

---

### Post by Padwick on 2012-02-08
> **Padwick said:**
> Yes, i think so at least.

I redid it now, with the same results.

---

### Post by arvindg14 on 2012-02-09
Hi Wildmanne

It did not work. Here are the results:


Code:
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55

Feb  8 01:53:12 ubuntu kernel: [    2.102482] b43-pci-bridge 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
Feb  8 01:53:12 ubuntu kernel: [    2.102498] b43-pci-bridge 0000:07:00.0: setting latency timer to 64 
Feb  8 01:53:12 ubuntu kernel: [   23.538128] b43-phy0: Broadcom 4312 WLAN found (core revision 15) 
Feb  8 01:53:12 ubuntu kernel: [   23.688340] Registered led device: b43-phy0::tx 
Feb  8 01:53:12 ubuntu kernel: [   23.688409] Registered led device: b43-phy0::rx 
Feb  8 01:53:12 ubuntu kernel: [   23.688465] Registered led device: b43-phy0::radio 
Feb  8 01:53:13 ubuntu NetworkManager[791]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/ssb0:0/net/wlan0, iface: wlan0) 
Feb  8 01:53:13 ubuntu NetworkManager[791]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found. 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> monitoring kernel firmware directory '/lib/firmware'. 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01). 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3) 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> (wlan0): now managed 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2] 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> (wlan0): bringing up device. 
Feb  8 01:53:13 ubuntu NetworkManager[791]: <info> (wlan0): deactivating device (reason 'managed') [2] 
Feb  9 00:44:31 ubuntu kernel: [    2.101512] b43-pci-bridge 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
Feb  9 00:44:31 ubuntu kernel: [    2.101528] b43-pci-bridge 0000:07:00.0: setting latency timer to 64 
Feb  9 00:44:31 ubuntu kernel: [   23.233307] b43-phy0: Broadcom 4312 WLAN found (core revision 15) 
Feb  9 00:44:31 ubuntu kernel: [   23.406917] Registered led device: b43-phy0::tx 
Feb  9 00:44:31 ubuntu kernel: [   23.407090] Registered led device: b43-phy0::rx 
Feb  9 00:44:31 ubuntu kernel: [   23.407244] Registered led device: b43-phy0::radio 
Feb  9 00:44:31 ubuntu NetworkManager[791]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/ssb0:0/net/wlan0, iface: wlan0) 
Feb  9 00:44:31 ubuntu NetworkManager[791]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found. 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> monitoring kernel firmware directory '/lib/firmware'. 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01). 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3) 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> (wlan0): now managed 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2] 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> (wlan0): bringing up device. 
Feb  9 00:44:31 ubuntu NetworkManager[791]: <info> (wlan0): deactivating device (reason 'managed') [2] 


Code:
nm-too

NetworkManager Tool 

State: disconnected 

- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            sky2 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1D:72:45:A6:C4 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 


- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            b43 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1A:73:F3:10:D8 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points l
Quote:
Tx-Power=0 dbm
means that the switch may be off so check your switch or it may be a key combination that turns it on or possibly turned off in your bios.

Also please do:
Code:
gksudo gedit /etc/pm/power.d/wireless

(gksudo:1846): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1846): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1846): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1846): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following:*
Code:
#!/bin/sh

/sbin/iwconfig wlan0 power off

Error for wireless request "Set Power Management" (8B2C) : 
    SET failed on device wlan0 ; Operation not permitted.

---

### Post by wildmanne39 on 2012-02-09
Hi Padwick, try this please:

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do on line at a time:
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by wildmanne39 on 2012-02-09
Hi arvindg14, on the power management command did you enter your password when the window opened for you to type it? 

I think it is at least one of the problems if not the complete problem so we need to get the power management to off.

Try the it again and add the content before the exit 0.
Thanks

---

### Post by arvindg14 on 2012-02-09
Hi WIldmann
 
Yes, I typed my password.
 
Which command should I try again?
 
Thanks
Arvind

---

### Post by wildmanne39 on 2012-02-09
Hi arvindg14, this one:
```
gksudo gedit /etc/pm/power.d/wireless
```
then add the lines to the file above the exit that are stated in the same post as the above command.
Thanks

---

### Post by slvjerome on 2012-02-10
This worked for me too for my Inspiron 1521.  Thanks Wildmanne!

> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

---

### Post by wildmanne39 on 2012-02-10
Hi slvjerome, your welcome!

---

### Post by neilrizo on 2012-02-11
I installed Ubuntu 11.10 the other day and, so far, I have been unable to activate my wireless connection. I've tried several of the suggestions posted here and in other sites to no avail. This is driving me crazy since I've never had this problem with the past Ubuntu releases.

My wireless device is a Broadcom BCM4312 802.11b/g LP-PHY. If anyone needs anymore information, just let me know what to do and I'll post it ASAP.

---

### Post by praseodym on 2012-02-11
Hi neilrizo,

did you install the firmware package as decribed? Rebooted after that?

Please show:
```
lsmod
rfkill list
iwconfig
sudo iwlist scan
dmesg | egrep 'b43|wl'
```

Alternatively try the Broadcom-STA driver from "additional drivers" instead.

---

### Post by arvindg14 on 2012-02-11
Hi Wildmanne

I performed this command and the output is pasted here. 

gksudo gedit /etc/pm/power.d/wireless

 gksudo gedit /etc/pm/power.d/wireless 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gedit:1812): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3U0J9V': No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 

(gedit:1812): Gtk-WARNING **: Unable to retrieve the file info for `file:///root/Untitled%20Document%201': Error stating file '/root/Untitled Document 1': No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.OSBM9V': No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 

What do you suggest?

Thanks
Arvind

---

### Post by neilrizo on 2012-02-11
> **praseodym said:**
> Hi neilrizo,

did you install the firmware package as decribed? Rebooted after that?

Please show:
```
lsmod
rfkill list
iwconfig
sudo iwlist scan
dmesg | egrep 'b43|wl'
```

Alternatively try the Broadcom-STA driver from "additional drivers" instead.


Thanks for the reply.

The first thing I did after installing 11.10 was go to 'Additional Drivers' and activate the Broadcom STA wireless driver. I then detached the cable and rebooted. That didn't work.

So I removed the Broadcom STA drivers and installed the b43 drivers via Synaptic. Detached and rebooted again to failed results.

Anyway, here is what you were asking for...

**lsmod**
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
acer_wmi               23302  0 
snd_seq_midi           13132  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
b43                   318816  0 
btusb                  18160  2 
psmouse                73673  0 
mac80211              393459  1 b43
ideapad_laptop         13575  0 
serio_raw              12990  0 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_timer              28932  2 snd_pcm,snd_seq
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
cfg80211              172427  2 b43,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  509487  3 
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
wmi                    18744  1 acer_wmi
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ssb                    50682  1 b43
ahci                   21634  3 
libahci                25727  1 ahci
tg3                   132972  0 

```

**rfkill list**
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

**sudo iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

**dmesg | egrep 'b43|wl'**
```
[    4.862222] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.862236] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   16.979088] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   17.084661] Registered led device: b43-phy0::tx
[   17.084687] Registered led device: b43-phy0::rx
[   17.084712] Registered led device: b43-phy0::radio
[   18.996052] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   24.584700] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.876041] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   30.553902] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.932038] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   67.492622] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  164.584049] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  170.121611] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  170.376032] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  175.924501] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  236.852062] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  242.396937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  242.656057] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  248.205628] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  579.012062] b43-phy0: Radio hardware status changed to DISABLED
[  594.020069] b43-phy0: Radio hardware status changed to ENABLED
[  614.024055] b43-phy0: Radio hardware status changed to DISABLED
[  619.012073] b43-phy0: Radio hardware status changed to ENABLED
[  621.928066] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  627.485111] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  627.736066] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  633.284905] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  639.028085] b43-phy0: Radio hardware status changed to DISABLED
[  644.020078] b43-phy0: Radio hardware status changed to ENABLED
[  659.012058] b43-phy0: Radio hardware status changed to DISABLED
[  664.021571] b43-phy0: Radio hardware status changed to ENABLED
[12282.944406] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[12284.361066] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[12284.362253] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[12304.423714] Modules linked in: bnep rfcomm parport_pc ppdev binfmt_misc joydev snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm acer_wmi snd_seq_midi uvcvideo videodev snd_rawmidi snd_seq_midi_event arc4 snd_seq b43 btusb psmouse mac80211 ideapad_laptop serio_raw bluetooth snd_timer sparse_keymap cfg80211 snd_seq_device i915 snd drm_kms_helper drm soundcore wmi snd_page_alloc i2c_algo_bit video lp parport ums_realtek usb_storage uas ssb ahci libahci tg3
[12304.433501] b43-phy0: Radio hardware status changed to DISABLED
[16265.853380] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[16267.337041] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[16267.338206] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[16287.400016] Modules linked in: bnep rfcomm parport_pc ppdev binfmt_misc joydev snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm acer_wmi snd_seq_midi uvcvideo videodev snd_rawmidi snd_seq_midi_event arc4 snd_seq b43 btusb psmouse mac80211 ideapad_laptop serio_raw bluetooth snd_timer sparse_keymap cfg80211 snd_seq_device i915 snd drm_kms_helper drm soundcore wmi snd_page_alloc i2c_algo_bit video lp parport ums_realtek usb_storage uas ssb ahci libahci tg3
[18383.012057] b43-phy0: Radio hardware status changed to ENABLED

```

---

### Post by praseodym on 2012-02-12
The module acer_wmi is wrong on an ideapad:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot needed

---

### Post by neilrizo on 2012-02-12
> **praseodym said:**
> The module acer_wmi is wrong on an ideapad:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot needed

That totally worked! Thanks a lot!

Using this same laptop, do you think the same problem will arise for future Ubuntu releases?

---

### Post by praseodym on 2012-02-12
Just check

> rfkill list
lsmod

in that case ;-)

---

### Post by neilrizo on 2012-02-12
> **praseodym said:**
> Just check

in that case ;-)


Thanks again!

---

### Post by wulinxjj on 2012-02-12
> **karma408 said:**
> When someone finds a fix to the no wireless problem with ubuntu 11.10 using Dell laptops and Broadcom please e-mail it to me at [email]cnelson@planetorange.com[/email]

I have a Dell Inspiron 1521. I did a fresh install of 11.10 and everything else id fine, but there is no wireless option.

So anybody know how to solve this problem with an acer aspire 4710g?

---

### Post by wildmanne39 on 2012-02-12
> **arvindg14 said:**
> Hi Wildmanne

I performed this command and the output is pasted here. 

gksudo gedit /etc/pm/power.d/wireless

 gksudo gedit /etc/pm/power.d/wireless 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:1810): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gedit:1812): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3U0J9V': No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 

(gedit:1812): Gtk-WARNING **: Unable to retrieve the file info for `file:///root/Untitled%20Document%201': Error stating file '/root/Untitled Document 1': No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.OSBM9V': No such file or directory 

(gedit:1812): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 

What do you suggest?

Thanks
ArvindHi, please do:
```
sudo mkdir /root/.local/share
```
Thanks

---

### Post by arvindg14 on 2012-02-14
Hi Wildmanne
The output of this command is:

arvnindgupta@ubuntu:~$ sudo mkdir /root/.local/share 
[sudo] password for arvnindgupta: 
mkdir: cannot create directory `/root/.local/share': No such file or directory

---

### Post by wildmanne39 on 2012-02-15
Hi arvindg14, this > mkdir: cannot create directory `/root/.local/share': No such file or directory should not stop gedit from opening to let you add the lines.

Did gedit open and were you able to add the lines?
Thanks

---

### Post by dockalek on 2012-02-16
Hi,I think I have a similar problem. Ubuntu 11.10 Dell labtop, wifi doesn't work. but the solution doesn't work with my computer. I coppied the commands that you said, the result is below. I have broadcom sta wireless driver in additional drivers. If anyone could help.

 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 01
       serial: 00:23:4d:70:88:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:6d:bb:71
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb v2.17 ip=192.168.2.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fc500000-fc50ffff
georgi@georgi-Studio-1537:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: wl
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Dell Device [1028:029f]
	Kernel driver in use: tg3

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
georgi@georgi-Studio-1537:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
btusb                  18600  2 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bluetooth             166112  23 bnep,rfcomm,btusb
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
dell_laptop            13831  0 
v4l2_compat_ioctl32    17083  1 videodev
r852                   18277  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sm_common              16865  1 r852
dcdbas                 14490  1 dell_laptop
nand                   54965  2 r852,sm_common
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  571221  2 
joydev                 17693  0 
nand_ids               12723  1 nand
lib80211_crypt_tkip    17390  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2568210  0 
nand_bch               13147  1 nand
ir_lirc_codec          12898  0 
bch                    22061  1 nand_bch
lirc_dev               19204  1 ir_lirc_codec
psmouse                73882  0 
ir_sony_decoder        12549  0 
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
drm_kms_helper         42558  1 i915
soundcore              12680  1 snd
serio_raw              13166  0 
r592                   18144  0 
ir_jvc_decoder         12546  0 
memstick               16569  1 r592
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ir_rc6_decoder         12546  0 
drm                   236290  3 i915,drm_kms_helper
lib80211               14991  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13423  1 i915
ir_rc5_decoder         12546  0 
wmi                    19256  1 dell_wmi
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
ite_cir                25775  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ite_cir
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
tg3                   147729  0 
ahci                   26002  3 
libahci                26861  1 ahci

---

### Post by peartruck on 2012-02-16
Hi there,

I've been working on this for a week or so now but no luck fixing my lack of wireless connection (i'm a complete linux newbie). Any help would be appreciated!

Here are the results of 

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```

**cat /etc/lsb-release; uname -a**

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Impermanence 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 athlon i386 GNU/Linux

```

**lspci -nnk | grep -iA2 net**

```
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
	Kernel modules: ssb

```

**iwconfig**

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

**rfkill list all**

```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

**lsmod**

```
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
snd_hda_codec_conexant    52418  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
nvidia               7098131  47 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12905  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
nv_tco                 13399  0 
i2c_nforce2            12906  0 
wmi                    18744  1 hp_wmi
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
forcedeth              58103  0 
sata_nv                23379  2 
pata_amd               13753  0 
```

---

### Post by wildmanne39 on 2012-02-17
Hi dockalek, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmwl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
unplug wired connection and reboot.
Thanks

---

### Post by gruns on 2012-02-20
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After it intalls disconnect your wired connection and restart your computer.

Thanks for this
I have finally found the Little trick to make my wireless work.:D

---

### Post by wildmanne39 on 2012-02-20
Hi, your welcome! 
Enjoy

---

### Post by peartruck on 2012-02-22
> **wildmanne39 said:**
> Hi dockalek, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmwl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
unplug wired connection and reboot.
Thanks

I tried this. All went fine until:

```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```

I got:

```
No supported card found.
Use proper b43 or b43legacy firmware.
Aborting.
```

Can anyone advise on this? I'm a bit lost now...

---

### Post by pkinztho on 2012-02-22
Hey guys, this is literally my first time messing with Ubuntu and I'm hopelessly lost.
Just Installed 11.10 on a Macbookpro, and I can't figure out the wireless. 
It won't pick up any networks, but then again I can't even tell if I have the right drivers.
Just looking for a push in the right direction.

Results of suggested commands:
sudo lshw -c network

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: c8:2a:14:17:73:05
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=57765-v1.37 ip=192.168.0.12 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff

lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3
    Kernel modules: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Broadcom Corporation Device [14e4:0000]
    Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Computer Inc. AirPort Extreme [106b:00d6]
    Kernel driver in use: bcma-pci-bridge

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

rfkill list all

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

lsmod

Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
usb_storage            57901  1 
uas                    18027  0 
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfsplus                88963  0 
hfs                    54782  0 
minix                  36322  0 
ntfs                  101885  0 
vfat                   17585  1 
msdos                  17332  0 
fat                    61475  2 vfat,msdos
jfs                   186662  0 
xfs                   831526  0 
reiserfs              248828  0 
rfcomm                 47946  8 
bnep                   18436  2 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_cirrus    18601  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
btusb                  18600  2 
bluetooth             166112  23 rfcomm,bnep,btusb
snd_seq_midi           13324  0 
bcm5974                17399  0 
v4l2_compat_ioctl32    17083  1 videodev
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  566711  3 
drm_kms_helper         42558  1 i915
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
drm                   236330  4 i915,drm_kms_helper
snd_timer              29991  2 snd_pcm,snd_seq
bcma                   20219  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13423  1 i915
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
apple_bl               13225  0 
mei                    41480  0 
soundcore              12680  1 snd
joydev                 17693  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 i915
applesmc               19554  0 
input_polldev          13896  1 applesmc
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_apple              13375  0 
usbhid                 47198  0 
hid                    95463  2 hid_apple,usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   147729  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci

sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35

Nothing

Thanks for takin' the time.

---

### Post by wildmanne39 on 2012-02-22
Hi peartruck, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2012-02-22
Hi pkinztho, this device is not supported in ubuntu yet, it shows there is partial support with this kernel (3.2-rc3+) so you can try that kernel or a newer one but you will need to get help to install it in general section of the forum or you cold try ndiswrapper here is a link to get help with that.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

---

### Post by peartruck on 2012-02-23
Hey wildmanne39

Result as requested - thanks

```
patrick@Impermanence:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Impermanence 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 athlon i386 GNU/Linux
patrick@Impermanence:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
	Kernel driver in use: b43-pci-bridge
patrick@Impermanence:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
patrick@Impermanence:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
patrick@Impermanence:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
nvidia               7098131  47 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
b43                   318816  0 
binfmt_misc            17292  1 
mac80211              393459  1 b43
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
cfg80211              172427  2 b43,mac80211
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
k8temp                 12905  0 
nv_tco                 13399  0 
i2c_nforce2            12906  0 
wmi                    18744  1 hp_wmi
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
forcedeth              58103  0 
pata_amd               13753  0 
ssb                    50682  1 b43
sata_nv                23379  2 

```

---

### Post by praseodym on 2012-02-23
Hi pkinztho,

install the Broadcom-STA driver via additional drivers, blacklist the wrong ones via:

```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

@peartruck:

Install the missing firmware of the driver:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot, too

---

### Post by kdbannon on 2012-02-23
My comp had the exact problem but this thread basically helped fix it :)

---

### Post by peartruck on 2012-02-24
Thanks praseodym and wildmanne39 - I'm finally wireless!

---

### Post by wildmanne39 on 2012-02-24
Hi peartruck, I am glad it is working and the reason the first commands you tried did not work is because you have a different broadcom card then the one those commands are for.
Thanks

---

### Post by mapr on 2012-02-25
I can not get my wifi to work and hope someone can help me. What information is needed to help me?

---

### Post by praseodym on 2012-02-25
Please show

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
```

---

### Post by mapr on 2012-02-25
> **praseodym said:**
> Please show

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
```

uname -a:
Linux Martin-Laptop 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net:
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Hewlett-Packard Company Device [103c:1453]
	Kernel driver in use: rt2860
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:149c]
	Kernel driver in use: r8169

lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 148f:1000 Ralink Technology, Corp. 
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 004: ID 0408:03b2 Quanta Computer, Inc. HP Webcam

lsmod:
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
uvcvideo               67271  0 
hp_accel               21632  0 
radeon                929507  2 
videodev               85626  1 uvcvideo
usbhid                 41905  0 
hid                    77367  1 usbhid
ttm                    65224  1 radeon
lis3lv02d              19280  1 hp_accel
snd_hda_codec_hdmi     31426  1 
mei                    36466  0 
snd_hda_codec_idt      60049  1 
drm_kms_helper         32889  1 radeon
hp_wmi                 13652  0 
snd_hda_intel          24262  3 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
drm                   192194  4 radeon,ttm,drm_kms_helper
snd_seq_midi           13132  0 
sparse_keymap          13658  1 hp_wmi
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
i7core_edac            23254  0 
edac_core              46858  3 i7core_edac
input_polldev          13648  1 lis3lv02d
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
psmouse                73673  0 
serio_raw              12990  0 
i2c_algo_bit           13199  1 radeon
video                  18908  0 
rt3090sta             794403  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  3 
libahci                25727  1 ahci
r8169                  43104  0 

rfkill list:
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2012-02-25
Try the module rt2800pci:

```
sudo modprobe -rfv rt3090sta
sudo modprobe -v rt2800pci
```
Check:

```
iwconfig
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by mapr on 2012-02-26
> **praseodym said:**
> Try the module rt2800pci:

```
sudo modprobe -rfv rt3090sta
sudo modprobe -v rt2800pci
```
Check:

```
iwconfig
sudo iwlist scan
dmesg | grep rt2
```

sudo modprobe -rfv rt3090sta:
rmmod /lib/modules/3.0.0-16-generic/updates/dkms/rt3090sta.ko

sudo modprobe -v rt2800pci:
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

sudo iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

dmesg | grep rt2:
[   26.118164] rt2860 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.118190] rt2860 0000:02:00.0: setting latency timer to 64
[  736.813565] rt2800pci 0000:02:00.0: setting latency timer to 64
[  736.849299] Registered led device: rt2800pci-phy0::radio
[  736.849349] Registered led device: rt2800pci-phy0::assoc
[  736.849401] Registered led device: rt2800pci-phy0::quality



Now the wifi works. What was it that made it work? It's good to know if it happens again. Thanks for the help.

Edit:
Sadly, it didn't solve the problem. When I restarted the computer, the wifi wasn't working again. I have uninstalled the network manager and now I only have wicd network manager.

---

### Post by praseodym on 2012-02-26
Please show:

> lsmod
egrep 'rt2|rt3' /etc/modprobe.d/*
cat /etc/modules

---

### Post by mapr on 2012-02-26
> **praseodym said:**
> Please show:

lsmod:
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
radeon                929507  2 
binfmt_misc            17292  1 
joydev                 17393  0 
hp_accel               21632  0 
hp_wmi                 13652  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  3 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
ttm                    65224  1 radeon
lis3lv02d              19280  1 hp_accel
snd_seq_midi           13132  0 
sparse_keymap          13658  1 hp_wmi
snd_rawmidi            25241  1 snd_seq_midi
drm_kms_helper         32889  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hwdep              13276  1 snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   192194  4 radeon,ttm,drm_kms_helper
snd_timer              28932  2 snd_seq,snd_pcm
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i7core_edac            23254  0 
edac_core              46858  3 i7core_edac
mei                    36466  0 
input_polldev          13648  1 lis3lv02d
psmouse                73673  0 
serio_raw              12990  0 
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
wmi                    18744  1 hp_wmi
video                  18908  0 
i2c_algo_bit           13199  1 radeon
rt3090sta             794403  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci

egrep 'rt2|rt3' /etc/modprobe.d/*:
/etc/modprobe.d/blacklist.conf:blacklist rt2800pci
/etc/modprobe.d/blacklist.conf~:blackli0st rt2800pci
/etc/modprobe.d/blacklist.conf~:blacklist rt2800pci

cat /etc/modules:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3090sta
rt3390sta

---

### Post by praseodym on 2012-02-26
Solution should be:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Replace

```
blacklist rt2800pci
```

with

```
blacklist rt3090sta
blacklist rt3390sta
```
save and close. Remove rt3090sta and rt3390sta from /etc/modules and reboot. Wireless should work now with the module rt2800pci

---

### Post by mapr on 2012-02-27
> **praseodym said:**
> Solution should be:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Replace

```
blacklist rt2800pci
```

with

```
blacklist rt3090sta
blacklist rt3390sta
```
save and close. Remove rt3090sta and rt3390sta from /etc/modules and reboot. Wireless should work now with the module rt2800pci

Great, now it works. Thanks for the help. The only thing now is that when ubuntu boots it says "boot without network configurations" or something like that and it takes a few minutes and that is quite frustrating.

---

### Post by praseodym on 2012-02-27
Thats the "60 seconds" bug, see here:

[http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/](http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/)

---

### Post by hhhpsycho on 2012-03-01
Hello

I installed ubuntu 11.10 on a Lenovo ideapad and followed the instructions regarding the wireless drives as posted on the first page. The system says i have my version is updated but still the wireless won't work. 

Anybody any suggestions?

I'm using ubuntu for quit a while but i am still a bit of a noob:-\"

---

### Post by praseodym on 2012-03-01
Hi hhhpsycho,

same hardware? Please show the outputs of #186

---

### Post by hhhpsycho on 2012-03-01
Linux laptop 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo Device [17aa:38fb]
	Kernel driver in use: tg3
--
07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Kernel driver in use: b43-pci-bridge

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0241 Acer, Inc BisonCam, NB Pro

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  0 
snd_hda_codec_hdmi     31426  1 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
acer_wmi               23302  0 
arc4                   12473  2 
b43                   318816  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              393421  1 b43
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nvidia              10390874  32 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172427  2 b43,mac80211
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32356  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
wmi                    18744  1 acer_wmi
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13489  1 
tg3                   132972  0 
ssb                    50682  1 b43
ahci                   21634  2 
libahci                25727  1 ahci
video                  18908  0 

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  0 
snd_hda_codec_hdmi     31426  1 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
acer_wmi               23302  0 
arc4                   12473  2 
b43                   318816  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              393421  1 b43
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nvidia              10390874  32 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172427  2 b43,mac80211
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32356  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
wmi                    18744  1 acer_wmi
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13489  1 
tg3                   132972  0 
ssb                    50682  1 b43
ahci                   21634  2 
libahci                25727  1 ahci
video                  18908  0 
evelien@laptop:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by praseodym on 2012-03-02
On an Ideapad the module "acer_wmi" is wrong. Blacklist it via:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

---

### Post by hhhpsycho on 2012-03-02
thx, it worked like a charm. Super

---

### Post by cespinal on 2012-03-02
This thread is solved my problem with Precise Beta 1

---

### Post by SanraS on 2012-03-21
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

Thanks a lot, this worked for me inspiron-1525, Now I just need to find info as easy as this for my graphics card to install the drivers!:lolflag::guitar:

---

### Post by wildmanne39 on 2012-03-21
Your welcome!

---

### Post by alainyd58 on 2012-04-11
Thank you so much. This worked like a charm for my Dell D630.

---

### Post by jimenez.edward on 2012-04-12
I own a dell xps m1530 which was running 10.10, after I updated to Natty, my wireless was not working.  I followed the upon steps and then ran sudo modprobe b43 to rescan the bus.  After doing that, my wireless was working.  Thanks.

---

### Post by eliterucks on 2012-04-15
> **wildmanne39 said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After it intalls disconnect your wired connection and restart your computer.
I would like to say thanks this work for me in my Dell 1501 thank you so much.

---

### Post by wildmanne39 on 2012-04-15
Hi eliterucks, your welcome!

---

### Post by whatitakes on 2012-04-21
Thanks alot wildmanne39, your post on page2 solved my "wireless missing firmware" issue. ubuntu 11.10 dell inspiron E1505.

---

### Post by wildmanne39 on 2012-04-21
Hi, your welcome!

---

### Post by Farbror on 2012-07-04
Thanks for your patient work!

Followed the removal and installation process. Did not work. Then I used Ubuntu "add-proprietary driver", unplugged the wired connection, restarted and: "woala!". Worked. I had added the proprietary driver before and restarted without solving anything. So it seed that [INDENT]**sudo apt-get purge broadcom-sta-common broadcom-sta-source bcmwl-kernel-source**
[/INDENT]*Install the correct one:*[INDENT]**sudo apt-get install b43-fwcutter firmware-b43-installer**
[/INDENT]followed by ubuntus easy-install-proprietarythings-by-GUI did the job for me.

---

### Post by oldmaxonian on 2012-08-28
Hi,

I'm struggling to get Ubuntu 11.10 running from a Live USB on my Inspiron 1501 Laptop with Broadcom wireless adapter.

I have seen lots of posts relating to this common problem, but I can't find any set of instructions which works for me. Can anyone help? Otherwise I'm probably just going to give up.

Thanks!

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth3
       version: 02
       serial: 00:15:c5:c5:c9:63
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.70 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:c0300000-c0301fff
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f5]
    Kernel driver in use: b44
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth3      no wireless extensions.

ubuntu@ubuntu:~$ rfkill list all
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
mac80211              272785  0 
cfg80211              172392  1 mac80211
b44                    31443  0 
ssb                    50682  1 b44
wl                   2646601  0 
lib80211               14570  1 wl
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
joydev                 17393  0 
dell_wmi               12601  0 
snd_seq_midi           13132  0 
sparse_keymap          13658  1 dell_wmi
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            13519  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  1 dell_laptop
arc4                   12473  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
k8temp                 12905  0 
i2c_piix4              13093  0 
shpchp                 32356  0 
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
radeon                925020  1 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  4 radeon,ttm,drm_kms_helper
usb_storage            44173  1 
uas                    17699  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
video                  18908  0 
pata_atiixp            12967  0 
i2c_algo_bit           13199  1 radeon
wmi                    18744  1 dell_wmi
ahci                   21634  0 
libahci                25727  1 ahci
ati_agp                13242  0 
ubuntu@ubuntu:~$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Aug 28 19:37:52 ubuntu NetworkManager[4361]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 28 19:37:52 ubuntu NetworkManager[4361]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Aug 28 19:37:52 ubuntu NetworkManager[4361]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 28 19:37:52 ubuntu NetworkManager[4361]: <info> (wlan0): now managed
Aug 28 19:37:52 ubuntu NetworkManager[4361]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 28 19:37:52 ubuntu NetworkManager[4361]: <info> (wlan0): bringing up device.
Aug 28 19:37:52 ubuntu NetworkManager[4361]: <info> (wlan0): deactivating device (reason 'managed') [2]
Aug 28 19:37:52 ubuntu NetworkManager[4361]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0)
Aug 28 19:37:52 ubuntu NetworkManager[4361]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 28 18:42:27 ubuntu avahi-daemon[4343]: Withdrawing workstation service for wlan0.
Aug 28 18:42:27 ubuntu NetworkManager[4361]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0)
Aug 28 18:42:27 ubuntu NetworkManager[4361]: <info> (wlan0): now unmanaged
Aug 28 18:42:27 ubuntu NetworkManager[4361]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Aug 28 18:45:42 ubuntu kernel: [  623.134555] b43-pci-bridge 0000:05:00.0: PCI INT A disabled
Aug 28 18:45:42 ubuntu kernel: [  623.206350] wl: module license 'MIXED/Proprietary' taints kernel.
Aug 28 18:45:42 ubuntu kernel: [  623.262186] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 28 18:45:42 ubuntu kernel: [  623.262214] wl 0000:05:00.0: setting latency timer to 64
Aug 28 18:45:42 ubuntu kernel: [  623.273623] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Aug 28 18:58:48 ubuntu kernel: [ 1408.827318] wl 0000:05:00.0: setting latency timer to 64
Aug 28 18:58:48 ubuntu kernel: [ 1408.838296] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Aug 28 18:59:53 ubuntu kernel: [ 1474.631419] wl 0000:05:00.0: setting latency timer to 64
Aug 28 18:59:53 ubuntu kernel: [ 1474.642591] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Aug 28 19:24:19 ubuntu kernel: [ 2940.358950] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Aug 28 19:24:19 ubuntu kernel: [ 2940.434174] Registered led device: b43-phy0::tx
Aug 28 19:24:19 ubuntu kernel: [ 2940.434251] Registered led device: b43-phy0::rx
Aug 28 19:24:19 ubuntu kernel: [ 2940.434315] Registered led device: b43-phy0::radio
Aug 28 19:24:19 ubuntu NetworkManager[4361]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan1, iface: wlan1)
Aug 28 19:24:19 ubuntu NetworkManager[4361]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Aug 28 19:24:19 ubuntu NetworkManager[4361]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Aug 28 19:24:19 ubuntu NetworkManager[4361]: <info> (wlan1): new 802.11 WiFi device (driver: 'b43' ifindex: 7)
Aug 28 19:24:19 ubuntu NetworkManager[4361]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/5
Aug 28 19:24:19 ubuntu NetworkManager[4361]: <info> (wlan1): now managed
Aug 28 19:24:19 ubuntu NetworkManager[4361]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 28 19:24:19 ubuntu NetworkManager[4361]: <info> (wlan1): bringing up device.
Aug 28 19:26:31 ubuntu avahi-daemon[4343]: Withdrawing workstation service for wlan1.
ubuntu@ubuntu:~$ 

```

---

### Post by praseodym on 2012-08-28
Hi,

uninstall the Broadcom-STA driver and install the firmware for the native b43 driver:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```


Reboot your system.

---

### Post by oldmaxonian on 2012-08-30
Thanks for your help. I'm switching to Precise, so will try the above suggestion if I still have problems.

---

### Post by michtrio on 2012-08-30
@Wild Man:

I have the same problem as everyone here. This is the info on my wireless card, I would be endlessly grateful if you could help me out!

```
michael@michael-System-Product-Name:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device [1043:83a4]
    Kernel driver in use: forcedeth
michael@michael-System-Product-Name:~$ lsmod
Module                  Size  Used by
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  2 iptable_filter,ip_tables
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148869  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91888  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nvidia              10394970  50 
snd_rawmidi            25241  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
k10temp                12990  0 
psmouse                63474  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
i2c_nforce2            12906  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_atk0110           17742  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm)

```

---

### Post by oldmaxonian on 2012-08-31
How do I point to the correct repository?

ubuntu@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
ubuntu@ubuntu:~$

---

### Post by stephen14 on 2012-10-04
Hi I have a new dell inspiron 7720 and the wireless card is from Intel. I tried previous broadcom driver but it didn't work. can you help me?

[FONT=Courier New]uname -a
Linux london 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Device [8086:0887] (rev c4)
        Subsystem: Intel Corporation Device [8086:4462]
        Kernel modules: iwlagn
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Dell Device [1028:0578]
        Kernel driver in use: r8169

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp.
Bus 001 Device 004: ID 1bcf:2897 Sunplus Innovation Technology Inc.

lsmod
Module                  Size  Used by
parport_pc             36962  0
ppdev                  17113  0
rfcomm                 47946  0
bnep                   18436  2
bluetooth             166112  10 rfcomm,bnep
snd_hda_codec_hdmi     32040  1
snd_hda_codec_idt      70553  1
binfmt_misc            17540  1
rts5139               351143  0
uvcvideo               72711  0
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
nouveau               728662  0
ttm                    76805  1 nouveau
mxm_wmi                12979  1 nouveau
snd_hda_intel          33390  2
dell_wmi               12681  0
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
sparse_keymap          13890  1 dell_wmi
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30547  1 snd_seq_midi
dell_laptop            13831  0
dcdbas                 14490  1 dell_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0
serio_raw              13166  0
iwlagn                314213  0
i915                  566711  3
mac80211              310872  1 iwlagn
drm_kms_helper         42558  2 nouveau,i915
mei                    41480  0
drm                   236330  6 nouveau,ttm,i915,drm_kms_helper
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  2 nouveau,i915
wmi                    19256  2 mxm_wmi,dell_wmi
video                  19412  2 nouveau,i915
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0
hid                    95463  1 usbhid
ahci                   26002  1
libahci                26861  1 ahci
xhci_hcd               78641  0
r8169                  52788  0

rfkill list
0: dell-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: dell-bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: yes
[/FONT]

---

### Post by kishoreavi on 2012-10-12
am using DEll inspiron 15R with intel centrino wifi card ... am also facing the same problem ..what should i do? ... pls help me .. i am struggling for long time ...

---

### Post by wildmanne39 on 2012-10-12
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by stephen14 on 2012-10-12
Thank you Wild Man.

netinfo.txt file is attached here.

---

### Post by wildmanne39 on 2012-10-12
Hi, first make sure your wireless is turned on by the physical switch right now it is off.
Then do:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then:
```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
Then reboot if it does not connect delete the text info file and run it again and attach it here.
Thanks

---

### Post by stephen14 on 2012-10-12
Still doesn't work. I attached two files here:

netinfo2.txt: after I turned on wireless hard switch;
netinfo3.txt: after executing your commands and rebooting

Thanks!

---

### Post by wildmanne39 on 2012-10-12
It looks like you are having a firmware issue, I will look at it more later I have to leave for a little while.
Thanks

---

### Post by wildmanne39 on 2012-10-12
Hi, let's try this please:
```
sudo apt-get install linux-firmware-nonfree
```
Then reboot if it does not work post a new text info file.
Thanks

---

### Post by stephen14 on 2012-10-12
Still doesn't work: no suitable firmware found. 
netinfo4.txt attached

---

### Post by wildmanne39 on 2012-10-12
Hi, please show the output of:
```
ls -al /lib/firmware/
```
Thanks

---

### Post by stephen14 on 2012-10-12
total 28608
drwxr-xr-x 63 root root   20480 2012-10-12 15:36 ./
drwxr-xr-x 20 root root    4096 2012-10-09 16:05 ../ 
drwxr-xr-x 32 root root    4096 2011-10-12 07:27 3.0.0-12-generic/
drwxr-xr-x 32 root root    4096 2012-10-09 16:06 3.0.0-26-generic/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 3com/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 acenic/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 adaptec/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 advansys/
-rw-r--r--  1 root root   50698 2012-01-23 09:20 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 2012-01-23 09:20 agere_sta_fw.bin
-rw-r--r--  1 root root   22622 2012-01-23 09:21 aic94xx-seq.fw
drwxr-xr-x  6 root root    4096 2012-10-09 16:12 ar3k/
-rw-r--r--  1 root root   70624 2012-01-23 09:20 ar7010_1_1.fw
-rw-r--r--  1 root root   70624 2012-01-24 10:10 ar7010.fw
-rw-r--r--  1 root root   83968 2012-01-23 09:20 ar9170-1.fw
-rw-r--r--  1 root root    3508 2012-01-23 09:20 ar9170-2.fw
-rw-r--r--  1 root root   15960 2012-01-23 09:21 ar9170.fw
-rw-r--r--  1 root root   51312 2012-01-24 10:10 ar9271.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 asihpi/
-rw-r--r--  1 root root  246804 2012-01-23 09:20 ath3k-1.fw
drwxr-xr-x  5 root root    4096 2011-10-12 07:27 ath6k/
-rw-r--r--  1 root root   30348 2012-01-23 09:21 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   31764 2012-01-23 09:21 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 2012-01-23 09:21 atmel_at76c502d.bin
-rw-r--r--  1 root root   31776 2012-01-23 09:21 atmel_at76c502e.bin
-rw-r--r--  1 root root   35180 2012-01-23 09:21 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 2012-01-23 09:21 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root   31748 2012-01-23 09:21 atmel_at76c504.bin
-rw-r--r--  1 root root   31824 2012-01-23 09:21 atmel_at76c506.bin
-rw-r--r--  1 root root    9726 2012-01-23 09:20 atmsar11.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 av7110/
drwxr-xr-x  2 root root   12288 2012-10-12 15:36 b43/
-rw-r--r--  1 root root  114688 2011-09-1drwxr-xr-x  2 root root    4096 2012-10-09 16:12 bnx2/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 bnx2x/
-rw-r--r--  1 root root  165768 2012-01-23 09:20 bnx2x-e1-4.8.53.0.fw
-rw-r--r--  1 root root  163000 2012-01-24 10:10 bnx2x-e1-5.2.13.0.fw
-rw-r--r--  1 root root  162800 2012-01-23 09:20 bnx2x-e1-5.2.7.0.fw
-rw-r--r--  1 root root  192400 2012-01-23 09:20 bnx2x-e1h-4.8.53.0.fw
-rw-r--r--  1 root root  205512 2012-01-24 10:10 bnx2x-e1h-5.2.13.0.fw
-rw-r--r--  1 root root  205488 2012-01-23 09:20 bnx2x-e1h-5.2.7.0.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 brcm/
-rw-r--r--  1 root root   12548 2012-01-23 09:21 carl9170-1.fw
drwxr-xr-x  3 root root    4096 2012-10-09 16:12 cis/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 cpia2/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 cxgb3/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 cxgb4/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 dabusb/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 dsp56k/
-rw-r--r--  1 root root      44 2011-09-16 15:21 dvb-cx18-mpc718-mt352.fw
-rw-r--r--  1 root root    9180 2011-09-16 15:21 dvb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root   32674 2011-09-16 15:21 dvb-fe-cx24116.fw
-rw-r--r--  1 root root    9584 2011-09-16 15:21 dvb-fe-nxt2004.fw
-rw-r--r--  1 root root   12772 2011-09-16 15:21 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root   17532 2011-09-16 15:21 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root    8518 2011-09-16 15:21 dvb-fe-or51211.fw
-rw-r--r--  1 root root   24602 2011-09-16 15:21 dvb-fe-tda10046.fw
-rw-r--r--  1 root root   24878 2011-09-16 15:21 dvb-fe-tda10048-1.0.fw
-rw-r--r--  1 root root   12401 2012-01-23 09:20 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root  231952 2011-09-16 15:21 dvb-ttpci-01.fw
-rw-r--r--  1 root root  430328 2011-09-16 15:21 dvb-ttusb-dec-2000t.fw
-rw-r--r--  1 root root  460448 2011-09-16 15:21 dvb-ttusb-dec-2540t.fw
-rw-r--r--  1 root root  465152 2011-09-16 15:21 dvb-ttusb-dec-3000s.fw
-rw-r--r--  1 root root   15913 2011-09-16 15:21 dvb-usb-af9015.fw
-rw-r--r--  1 root root   10757 2011-09-16 15:21 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root    9025 2011-09-16 15:21 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root   34306 2011-09-16 15:21 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root   33768 2012-01-23 09:20 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root    9180 2011-09-16 15:21 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root    7558 2011-09-16 15:21 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root    7431 2011-09-16 15:21 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root   50222 2012-01-24 10:10 dvb-usb-terratec-h5-drxk.fw
-rw-r--r--  1 root root    3360 2011-09-16 15:21 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root    4286 2011-09-16 15:21 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root   10752 2011-09-16 15:21 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root   10752 2011-09-16 15:21 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root    8480 2011-09-16 15:21 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root   12902 2011-09-16 15:21 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root    8518 2011-09-16 15:21 dvb-usb-wt220u-zl0353-01.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 e100/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 ea/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 edgeport/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 emi26/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 emi62/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 ene-ub6250/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 ess/
-rw-r--r--  1 root root  180776 2012-01-24 10:10 f2255usb.bin
-rw-r--r--  1 root root   35068 2012-01-24 10:10 GPL-3
drwxr-xr-x  2 root root    4096 2011-08-22 01:05 hp/
-rw-r--r--  1 root root   72992 2012-01-24 10:10 htc_7010.fw
-rw-r--r--  1 root root   51272 2012-01-24 10:10 htc_9271.fw
-rw-r--r--  1 root root 1251036 2012-01-23 09:20 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root 1334532 2012-01-24 10:10 i2400m-fw-usb-1.5.sbcf
-rw-r--r--  1 root root 1531932 2012-01-24 10:10 i6050-fw-usb-1.5.sbcf
-rw-r--r--  1 root root   34304 2012-01-23 09:20 intelliport2.bin
-rw-r--r--  1 root root  209190 2012-01-23 09:21 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 2012-01-23 09:21 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 2012-01-23 09:21 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 2012-01-23 09:21 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2012-01-23 09:21 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2012-01-23 09:21 ipw2200-sniffer.fw
-rw-r--r--  1 root root  112128 2011-09-16 15:21 isl3877
-rw-r--r--  1 root root   29036 2011-09-16 15:21 isl3886pci
-rw-r--r--  1 root root   29500 2011-09-16 15:21 isl3886usb
-rw-r--r--  1 root root   29736 2011-09-16 15:21 isl3887usb
-rw-r--r--  1 root root   93996 2011-09-16 15:21 isl3890
-rw-r--r--  1 root root  335056 2012-01-23 09:20 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  337520 2012-01-23 09:20 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root  337572 2012-01-24 10:10 iwlwifi-100-5.ucode
-rw-r--r--  1 root root  689680 2012-01-24 10:10 iwlwifi-105-6.ucode
-rw-r--r--  1 root root  701228 2012-01-24 10:10 iwlwifi-135-6.ucode
-rw-r--r--  1 root root  695876 2012-01-24 10:10 iwlwifi-2000-6.ucode
-rw-r--r--  1 root root  707392 2012-01-24 10:10 iwlwifi-2030-6.ucode
-rw-r--r--  1 root root  150100 2012-01-23 09:20 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2012-01-23 09:20 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2012-01-23 09:20 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2012-01-23 09:20 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  340696 2012-01-23 09:21 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 2012-01-23 09:20 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 2012-01-24 10:10 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2012-01-24 10:10 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460236 2012-01-24 10:10 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  679436 2012-01-24 10:10 iwlwifi-6000g2b-6.ucode
-rw-r--r--  1 root root  463692 2012-01-23 09:20 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2012-01-23 09:20 iwlwifi-6050-5.ucode
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 kaweth/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 keyspan/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 keyspan_pda/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 korg/
-rw-r--r--  1 root root     262 2012-01-24 10:10 lgs8g75.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 libertas/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 matrox/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 mrvl/
-rw-r--r--  1 root root   13847 2012-01-23 09:20 mts_cdma.fw
-rw-r--r--  1 root root   14067 2012-01-23 09:20 mts_edge.fw
-rw-r--r--  1 root root   13847 2012-01-23 09:20 mts_gsm.fw
-rw-r--r--  1 root root   13769 2012-01-24 10:10 mts_mt9234mu.fw
-rw-r--r--  1 root root   13769 2012-01-24 10:10 mts_mt9234zba.fw
-rw-r--r--  1 root root   51596 2012-01-24 10:10 mwl8335_duplex.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 mwl8k/
-rw-r--r--  1 root root  377784 2012-01-24 10:10 myri10ge_ethp_z8e.dat
-rw-r--r--  1 root root  367464 2012-01-24 10:10 myri10ge_eth_z8e.dat
-rw-r--r--  1 root root  563592 2012-01-24 10:10 myri10ge_rss_ethp_z8e.dat
-rw-r--r--  1 root root  553192 2012-01-24 10:10 myri10ge_rss_eth_z8e.dat
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 myricom/
-rw-r--r--  1 root root   23466 2011-09-16 15:21 ngene_15.fw
-rw-r--r--  1 root root   24446 2011-09-16 15:21 ngene_17.fw
-rw-r--r--  1 root root   15664 2012-01-23 09:21 NPE-B
-rw-r--r--  1 root root   15664 2012-01-23 09:21 NPE-C
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 ositech/
-rw-r--r--  1 root root 1793805 2012-01-24 10:10 phanfw.bin
-rw-r--r--  1 root root   76802 2012-01-23 09:20 ql2100_fw.bin
-rw-r--r--  1 root root   84566 2012-01-23 09:20 ql2200_fw.bin
-rw-r--r--  1 root root  123170 2012-01-23 09:20 ql2300_fw.bin
-rw-r--r--  1 root root  132978 2012-01-23 09:20 ql2322_fw.bin
-rw-r--r--  1 root root  228056 2012-01-23 09:20 ql2400_fw.bin
-rw-r--r--  1 root root  199776 2012-01-23 09:20 ql2500_fw.bin
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 qlogic/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 r128/
drwxr-xr-x  2 root root   12288 2012-10-09 16:12 radeon/
-rw-r--r--  1 root root    8192 2012-01-23 09:20 rt2561.bin
-rw-r--r--  1 root root    8192 2012-01-23 09:20 rt2561s.bin
-rw-r--r--  1 root root    8192 2012-01-23 09:20 rt2661.bin
-rw-r--r--  1 root root    8192 2012-01-24 10:10 rt2860.bin
-rw-r--r--  1 root root    8192 2012-01-24 10:10 rt2870.bin
lrwxrwxrwx  1 root root      10 2012-01-24 10:10 rt3070.bin -> rt2870.bin
-rw-r--r--  1 root root    4096 2012-01-24 10:10 rt3071.bin
lrwxrwxrwx  1 root root      10 2012-01-24 10:10 rt3090.bin -> rt2860.bin
-rw-r--r--  1 root root    2048 2012-01-23 09:20 rt73.bin
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 RTL8192E/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 RTL8192SE/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 rtl_nic/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 rtlwifi/
-rw-r--r--  1 root root    9508 2012-01-24 10:10 s2250.fw
-rw-r--r--  1 root root    1092 2012-01-24 10:10 s2250_loader.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 sb16/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 scripts/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 slicoss/
-rw-r--r--  1 root root  101056 2011-09-16 15:21 sms1xxx-hcw-55xxx-dvbt-02.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 sun/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 sxg/
-rw-r--r--  1 root root   37028 2012-01-24 10:10 TDA7706_OM_v2.5.1_boot.txt
-rw-r--r--  1 root root   10509 2012-01-24 10:10 TDA7706_OM_v3.0.2_boot.txt
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 tehuti/
-rw-r--r--  1 root root   13765 2012-01-23 09:20 ti_3410.fw
-rw-r--r--  1 root root   13764 2012-01-23 09:20 ti_5052.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 ti-connectivity/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 tigon/
-rw-r--r--  1 root root   51972 2012-01-24 10:10 tlg2300_firmware.bin
-rw-r--r--  1 root root    7614 2012-01-23 09:20 tr_smctr.bin
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 ttusb-budget/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 ueagle-atm/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 usbdux/
-rw-r--r--  1 root root     999 2012-01-23 09:20 usbduxfast_firmware.bin
-rw-r--r--  1 root root    1770 2012-01-23 09:20 usbdux_firmware.bin
-rw-r--r--  1 root root   16382 2012-01-23 09:20 v4l-cx231xx-avcore-01.fw
-rw-r--r--  1 root root  141200 2012-01-23 09:20 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 2012-01-23 09:20 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 2012-01-23 09:20 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 2012-01-23 09:21 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 2012-01-23 09:21 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 2012-01-23 09:21 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 2012-01-23 09:20 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root   16382 2012-01-23 09:20 v4l-cx23885-enc.fw
-rw-r--r--  1 root root   16382 2012-01-23 09:20 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 2012-01-23 09:21 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 2012-01-23 09:21 v4l-pvrusb2-29xxx-01.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 vicam/
-rw-r--r--  1 root root   11341 2012-01-24 10:10 vntwusb.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 vxge/
-rw-r--r--  1 root root    5208 2012-01-24 10:10 WHENCE.ubuntu
-rw-r--r--  1 root root   23554 2012-01-23 09:20 whiteheat.fw
-rw-r--r--  1 root root    5626 2012-01-23 09:20 whiteheat_loader.fw
-rw-r--r--  1 root root   66220 2011-09-16 15:21 xc3028-v27.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 yam/
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 yamaha/
-rw-r--r--  1 root root   62484 2012-01-23 09:21 zd1201-ap.fw
-rw-r--r--  1 root root   70612 2012-01-23 09:21 zd1201.fw
drwxr-xr-x  2 root root    4096 2012-10-09 16:12 zd1211/

-rw-r--r--  1 root root    3245 2011-09-16 15:21 bcm2033-md.hex
-rw-r--r--  1 root root 2786404 2011-09-16 15:21 bcm70012fw.bin
-rw-r--r--  1 root root  868372 2011-09-16 15:21 bcm70015fw.bin

---

### Post by wildmanne39 on 2012-10-12
Hi, please try:
```
linux-backports-modules-cw-3.1-oneiric-generic
```
Reboot
Thanks

---

### Post by stephen14 on 2012-10-12
I tried:
sudo apt-get install linux-backports-modules-cw-3.1-oneiric-generic

and reboot.

still doesn't work.

attached netinfo.txt and ls /lib/firmware result

---

### Post by stephen14 on 2012-10-21
Hi Wild Man, thank you for your help so far. Could you give it another try on the firmware? Thanks!

---

### Post by TwoKillerMockingbirds on 2012-12-01
Hey Wildman, I just feel like thanks is always warranted. I recently had to scrub my computer, and have a fresh install of 11.10, the only thing I could get running, and you post way back on page 2, #15 was enormously helpful. Got everything working, I'm much obliged. Need to figure out exactly what I did, but that comes later. Cheers!

---

### Post by joebwankenobi on 2012-12-17
> **Wild Man said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

THANK YOU SOOO MUCH. Got this inspiron 1521 w/ a 43xx card inside. light would not come on for wireless... tried many terminal fixes in past few day but this (gift from father in law virused vista revived with ubuntu 12.10) laptop would not let wireless work... thought card may be junk. bought netgear adapter and realized it would be same amount of terminal jockeying to make it work... so gave the internal card one more go... stumbled on this post and OMG thank you.... those 2 term line entries and a restart have enabled my internal card now... New to ubuntu world, was semi frustrated, but curiously intrigued. Now I'm wanting to learn more and will be spending alot of my time trying to do so. Thanx for the spark!

---

### Post by Dr Mahgoub on 2013-01-19
I am also  not be the original  person wo has the problem,,,,  but this fixed my similar situation. Thanks so much!!!

---

### Post by johnros on 2013-02-01
I am having the same trouble guys.
Any help appreciated.

```
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:0c:42:e4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=10.0.0.17 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:ce00(size=256) memory:f0204000-f0204fff memory:f0200000-f0203fff memory:f0220000-f023ffff
```

```
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Dell Device [1028:02d8]
	Kernel driver in use: r8169
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel modules: ssb
```

```
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```
Module                  Size  Used by
hidp                   21825  0 
dm_crypt               22402  0 
snd_hda_codec_conexant    52202  1 
snd_hda_intel          32515  2 
snd_hda_codec         111547  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
joydev                 17161  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
coretemp               13168  0 
uvcvideo               71277  0 
snd                    61991  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
kvm_intel             126745  0 
soundcore              14599  1 snd
videobuf2_core         32070  1 uvcvideo
btusb                  17986  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
kvm                   357806  1 kvm_intel
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
gpio_ich               13159  0 
dell_laptop            17161  0 
dell_wmi               12601  0 
psmouse                84843  0 
sparse_keymap          13658  1 dell_wmi
parport_pc             31968  0 
serio_raw              13031  0 
lpc_ich                16925  0 
rfcomm                 37276  12 
ppdev                  12817  0 
dcdbas                 14054  1 dell_laptop
microcode              18209  0 
bnep                   17707  2 
mac_hid                13037  0 
lp                     13299  0 
bluetooth             183228  23 hidp,btusb,rfcomm,bnep
parport                40753  3 parport_pc,ppdev,lp
binfmt_misc            17260  1 
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  3 hidp,hid_generic,usbhid
ums_realtek            17669  0 
r8169                  55976  0 
uas                    17556  0 
i915                  457181  3 
drm_kms_helper         47303  1 i915
drm                   238768  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
wmi                    18590  1 dell_wmi
video                  18847  1 i915
usb_storage            39350  1 ums_realtek
```

```
Jan 31 22:48:19 johnros-laptop NetworkManager[869]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 31 22:48:19 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 31 22:48:19 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 31 22:48:19 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 31 22:48:19 johnros-laptop NetworkManager[869]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 31 22:48:19 johnros-laptop NetworkManager[869]: <info> Activation (wlan0/wireless): connection 'john 1' has security, and secrets exist.  No new secrets needed.
Jan 31 22:48:19 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 31 22:48:21 johnros-laptop NetworkManager[869]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 31 22:48:31 johnros-laptop wpa_supplicant[960]: wlan0: Trying to associate with f0:7d:68:17:8a:70 (SSID='john' freq=2437 MHz)
Jan 31 22:48:31 johnros-laptop wpa_supplicant[960]: wlan0: Association request to the driver failed
Jan 31 22:48:31 johnros-laptop NetworkManager[869]: <info> (wlan0): supplicant interface state: scanning -> associating
Jan 31 22:48:32 johnros-laptop wpa_supplicant[960]: wlan0: Associated with f0:7d:68:17:8a:70
Jan 31 22:48:32 johnros-laptop wpa_supplicant[960]: wlan0: CTRL-EVENT-CONNECTED - Connection to f0:7d:68:17:8a:70 completed (reauth) [id=5 id_str=]
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> (wlan0): supplicant interface state: associating -> completed
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'john'.
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan 31 22:48:32 johnros-laptop avahi-daemon[540]: Withdrawing address record for fe80::924c:e5ff:fe09:5ae1 on wlan0.
Jan 31 22:48:32 johnros-laptop avahi-daemon[540]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::924c:e5ff:fe09:5ae1.
Jan 31 22:48:32 johnros-laptop avahi-daemon[540]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 31 22:48:32 johnros-laptop NetworkManager[869]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 31 22:48:32 johnros-laptop dhclient: Listening on LPF/wlan0/90:4c:e5:09:5a:e1
Jan 31 22:48:32 johnros-laptop dhclient: Sending on   LPF/wlan0/90:4c:e5:09:5a:e1
Jan 31 22:48:32 johnros-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan 31 22:48:33 johnros-laptop avahi-daemon[540]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::924c:e5ff:fe09:5ae1.
Jan 31 22:48:33 johnros-laptop avahi-daemon[540]: New relevant interface wlan0.IPv6 for mDNS.
Jan 31 22:48:33 johnros-laptop avahi-daemon[540]: Registering new address record for fe80::924c:e5ff:fe09:5ae1 on wlan0.*.
Jan 31 22:48:35 johnros-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan 31 22:48:41 johnros-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jan 31 22:48:42 johnros-laptop kernel: [  779.088024] wlan0: no IPv6 routers present
Feb  1 09:38:46 johnros-laptop NetworkManager[832]: <info> kernel firmware directory '/lib/firmware' changed
```

---

### Post by praseodym on 2013-02-01
@johnros: You have the low-power chipset (LP). You need this firmware:

```
sudo apt-get install firmware-b43-lpphy-installer 
```

---

### Post by WORKSdefaultITguy on 2013-05-08
Thanks for the help.  I'm so glad to have found this forum.  Your help of another user near the beginning of this thread fixed my wifi issue.  Thanks again, I'm looking forward to learning more as I explore Ubuntu.

---

### Post by wildmanne39 on 2013-05-08
Your welcome! and welcome to the forum.

---

### Post by TREESofRIGHTEOUSNESS on 2013-06-09
I would like to add something (I searched through about 11 pages and didn't find this answer, (man dpkg helped).
If for some reason you mistakenly install the driver from jockey *after* installing b43-fwcutter and firmware-b43-installer you will be stuck in a dpkg --configure -a crash loop.
to fix this simply run
```
sudo dpkg -P bcmwl-kernel-source
```
Which purges the bcmwl-kernel-source package (installed by jockey... the Additional Drivers program) from your computer much like apt-get does....
So if someone (such as myself) ever needs to find this command here it is.;)

---

### Post by wildmanne39 on 2013-06-09
Thanks TREESofRIGHTEOUSNESS I have never used that command before, we use this one.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

---

### Post by TREESofRIGHTEOUSNESS on 2013-06-09
Yeah when you install the propreitary drivers through jockey (Additional Drivers) *after* installing b43 packages, it got my computer stuck saying I needed to run [CODE}sudo dpk --configure -a[/CODE] which results in a serious locked up crashed computer (everytime).  So since I can run apt-get purge (remove, autoremove,etc....) I had to use dpkg.  If someone really screws up by installing drivers from jockey after already installing them.  I had to install windows to flash the BIOS on 2 computers and both have b43, so when reinstalling I accidentally took the "you need to install propreitary drivers" OSD bait.  So after fruitless internet searches, I came across this thread, and tried your solution (which resulted in the loop of crashing).  That didn't work so I looked at dpkg man pages and discovered the -P (purge) option. Voila!  So for users that are stuck like that I wanted to add my findings to your page.  I also deleted the "lock" file in /var/cache/apt  but I don't know if that is related to fixing it.  I tried everything I could think of....  having a newly installed borked OS is lame :(

---

### Post by wildmanne39 on 2013-06-09
Yes, now I understand why you used that command.

Nothing worse then a broken system.

---

### Post by olexander.halii on 2013-10-31
hi to everyone i am using Backtrackr on VmWare my Wireless network Adapter is Ralink RT3090 
after command 

root@bt:~# iwconfig
lo        no wireless extensions.


eth1      no wireless extensions.


root@bt:~# 
how to get my wifi work? 
and i am tryed another command
root@bt:~# airmon-ng start wlan0




Found 1 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!


PID	Name
999	dhclient3




Interface	Chipset		Driver




root@bt:~# 

i have no interface chipset and driver.

---

### Post by sasky84 on 2014-06-03
> **Wild Man said:**
> Hi, it looks like you installed the driver for this card in additional drivers if so please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After it intalls disconnect your wired connection and restart your computer.

This helped me also with Ubuntu 13.04 (Asus Eee). Thanks!

---

### Post by Edwin_Camero on 2014-06-03
Hi this is edwin I aslo have the same problem

---

### Post by slickymaster on 2014-06-03
> **Edwin_Camero said:**
> Hi this is edwin I aslo have the same problem

I'm closing this thread according to point 19 of the [Forum rules]("http://ubuntuforums.org/misc.php?do=showrules").

Not only this thread is more than three years old but it also addresses a version that reached its EOL on 9 May 2013. Please start a new thread of your own, following this [general guidelines]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811#post8920811").

---

