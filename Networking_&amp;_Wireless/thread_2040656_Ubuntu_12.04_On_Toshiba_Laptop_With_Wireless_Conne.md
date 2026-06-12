---
title: "Ubuntu 12.04 On Toshiba Laptop With Wireless Connection Issues To Belkin N Wireless"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by NoobDroob on 2012-08-11
Hi Guys,

I have another laptop with no wireless connection for you to look at - I have done a heap of research but can't find anything that has helped for my specific problem. The laptop came with Win 7 Pro, which I completed the initial installation of before burning recovery discs and removing it - as part of the Win 7 install the laptop hooked up fine to my wireless network, so I know the hardware is OK.

No matter what I try the system says... Network - Disconnected - you are now offline

Have posted details below according to the HOWTO for wireless issues...


**Laptop Details**
```

Toshiba Satellite Pro C850 PSKC9A-00T019
Intel i5 2450M / 4GB DDR3 / 640 GB SATA / Intel HD 3000 / USB 3 / HDMI / Win 7 Pro (boooo!)
Purchased 11 Aug 2012 in Australia

```**Wireless Modem Router**
```

Belkin N Wireless Modem Router - F5D8636-4 v1

```**Ubuntu Details**
```

12.04 LTS  32 bit  downloaded and installed from CD - clean install removing previous OS's and partitions

```[FONT=Courier New]**lsb_release -d**[/FONT]
```

Description:    Ubuntu 12.04 LTS

```[FONT=Courier New]**uname -mr**[/FONT]
```

3.2.0-23-generic-pae i686

```[FONT=Courier New]**sudo /etc/init.d/networking restart**[/FONT]
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                   [ OK ] 

```[FONT=Courier New]**lspci**[/FONT]
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

```[FONT=Courier New]**lsusb**[/FONT]
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0930:021d Toshiba Corp. 
Bus 001 Device 004: ID 04ca:7008 Lite-On Technology Corp. 

```[FONT=Courier New]**ifconfig**[/FONT]
```

eth0      Link encap:Ethernet  HWaddr e8:40:f2:de:ed:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60064 (60.0 KB)  TX bytes:60064 (60.0 KB)

```[FONT=Courier New]**iwconfig**[/FONT]
```

lo        no wireless extensions.

eth0      no wireless extensions.


```[FONT=Courier New]**lsmod**[/FONT]
```

Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174055  1 
joydev                 17393  0 
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
sparse_keymap          13658  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
toshiba_bluetooth      12711  0 
wmi                    18744  0 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                72846  0 
btusb                  17912  2 
serio_raw              13027  0 
bluetooth             158438  23 rfcomm,bnep,btusb
i915                  414603  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17699  0 
r8169                  56321  0 
usb_storage            39646  1 ums_realtek

```[FONT=Courier New]**sudo lshw -C network**[/FONT]
```

  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:c2400000-c2403fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: e8:40:f2:de:ed:8d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0004000-c0004fff memory:c0000000-c0003fff

```[FONT=Courier New]**iwlist scan**[/FONT]
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```I haven't posted **[FONT=Courier New]dmesg [/FONT]**but can if you think it will help

Kindest Regards to you legends out there who took the time to read and respond - you make the world a better place

Cheers
Drew

---

### Post by chili555 on 2012-08-11
You'll need to download and compile a driver for this relatively new device. Here is a thread that describes the process and even gives a download link. Please post back if you need additional guidance.

[http://ubuntuforums.org/showthread.php?t=2017622&highlight=8723](http://ubuntuforums.org/showthread.php?t=2017622&highlight=8723)

---

### Post by NoobDroob on 2012-08-11
Thanks very much Chili - I'll try and wade through all that... wow!

I didn't bother searching on Realtek 8723 because I thought 8723 was an internal address or something assigned by Ubuntu - never imagined that was the device/driver name - should try all possibilities next time - I'll let you know how I go

cheers
Drew

---

### Post by chili555 on 2012-08-11
> **NoobDroob said:**
> Thanks very much Chili - I'll try and wade through all that... wow!

I didn't bother searching on Realtek 8723 because I thought 8723 was an internal address or something assigned by Ubuntu - never imagined that was the device/driver name - should try all possibilities next time - I'll let you know how I go

cheers
DrewAlthough I am pretty confident, you might verify the pci.id:```
lspci -nn | grep 0280
```Is it the same as in the linked thread?> [0280]: Realtek Semiconductor Co., Ltd. Device [[COLOR="Red"]10ec:8723[/COLOR]]If so, please proceed. If not, post and we'll see what we need to do.

---

### Post by NoobDroob on 2012-08-11
yep - one and the same thanks mate... I'll give it a go

is this something that would one day be rectified through an Ubuntu update? ie if I just keep updating my system it would eventually recognise the wireless device and connect? if so how far away do you think that would be?

or would we have to wait until 12.10 for this to be part of core Ubuntu?

dropbox source site makes me nervous... but it looks like I'm not the first!

---

### Post by NoobDroob on 2012-08-11
Hi Chili,

Mate, thanks very much for your help... its all working well here now... for those who come after me these are the steps I took to resolve the issue...

1. Establish an ethernet connection

2. Run the following...
```

sudo apt-get update
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
sudo dpkg -s build-essential
sudo su
wget -O- http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz | tar -xz
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
make
sudo make install
sudo modprobe rtl8723e

```3. Reboot and thank Chili !

Cheers mate
Drew

---

### Post by chili555 on 2012-08-11
> is this something that would one day be rectified through an Ubuntu update? ie if I just keep updating my system it would eventually recognise the wireless device and connect? if so how far away do you think that would be?Yes it will, but it's hard to know. I'd guess it might be at least six months.

Don't forget to rebuild the driver when Update Manager installs a newer kernel, also known as linux-image:```
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe rtl8723e
```Have fun and great job, by the way!

---

### Post by NoobDroob on 2012-08-11
> 
Don't forget to rebuild the driver when Update Manager installs a newer kernel
ha ha... of *course *I'll forget!

thanks mate
Drew

---

### Post by NoobDroob on 2012-12-05
As follow up (and more for my own future reference for when it happens again)

As predicted...
a) Update Manager installed a new kernel
b) I forgot to do a 'make clean'

The steps I took to make and install the driver again...

```

cd /home/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
sudo su
make clean
make
sudo make install
sudo modprobe rtl8723e

```

And hey presto... my wireless connects again immediately!

Cheers
Drew

---

### Post by joch3n on 2013-01-18
Hi there,

i bought today a Toshiba satellite c870-19R and the Wireless card Realtek is not recognized :(

i tryed to fix it with:
(with the file from: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized))
cd /home/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.201 (work)
sudo su (work?)
make clean
**make: *** No rule to make target `clean'.  Stop.**

make
**make: *** No targets specified and no makefile found.  Stop.**

sudo make install
**make: *** No targets specified and no makefile found.  Stop.**

sudo modprobe rtl8723e
**FATAL: Module rtl8723e not found.**

did i something wrong or is the file defect?

thanks in advance for your help!

cheers, Jo

---

### Post by chili555 on 2013-01-18
> **joch3n said:**
> Hi there,

i bought today a Toshiba satellite c870-19R and the Wireless card Realtek is not recognized :(

i tryed to fix it with:
(with the file from: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized))
cd /home/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.201 (work)
sudo su (work?)
make clean
**make: *** No rule to make target `clean'.  Stop.**

make
**make: *** No targets specified and no makefile found.  Stop.**

sudo make install
**make: *** No targets specified and no makefile found.  Stop.**

sudo modprobe rtl8723e
**FATAL: Module rtl8723e not found.**

did i something wrong or is the file defect?

thanks in advance for your help!

cheers, JoDid you install linux-headers-generic and build-essential first?

---

### Post by joch3n on 2013-01-18
Hi Chili555,

i think yes

```
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
[sudo] password for xxx:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
build-essential ist schon die neueste Version.
linux-headers-3.2.0-36-generic-pae ist schon die neueste Version.
linux-headers-generic ist schon die neueste Version.
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
```the text says that build-essentialand and linux-headers-generic are the newest....

i dont know whats going wrong :/

---

### Post by chili555 on 2013-01-18
> cd /home/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514 .201rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.201[COLOR="Red"]2[/COLOR]. List the contents of the directory:```
ls
```It ought to look like:```
chili@Think60:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ ls
base.c                              core.c    Kconfig         rc.c          rtl8192se
base.h                              core.h    ***Makefile***        rc.h          rtl8723e
base.o                              core.o    modules.order   rc.o          rtlwifi.ko
cam.c                               debug.c   Module.symvers  readme        rtlwifi.mod.c
cam.h                               debug.h   pci.c           regd.c        rtlwifi.mod.o
cam.o                               debug.o   pci.h           regd.h        rtlwifi.o
compat                              efuse.c   pci.o           regd.o        stats.c
compat.h                            efuse.h   ps.c            release_note  stats.h
compat-wireless-3.0-2-mesh.tar.bz2  efuse.o   ps.h            rtl8192ce     stats.o
compat-wireless-3.0-2.tar.bz2       firmware  ps.o            rtl8192de     wifi.h
```When you are in the correct directory and ls shows the Makefile, then you are all ready to proceed.

---

### Post by joch3n on 2013-01-19
the problem is resolved :D

thanks for your help, love ubuntu :)

---

### Post by mackrackit on 2013-02-27
Thank you Chili !!!
This thread fixed my problem.

---

### Post by jaber426 on 2013-03-03
thank

---

### Post by redboots on 2013-03-07
Hi all, noob to Ubunto here... Used to be in OS/390 & z/OS in a previous life:). Little to no dealings with Unix:(

I am trying to install the RTL8723 driver on a new Toshiba laptop that reports having this wifi unit.
I have followed this thread and read all the various links to other threads, but keep coming upwith the same problem.
From the term log;
 > make
make -C /lib/modules/3.5.0-23-generic/build M=/home/pookie/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/pookie/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/pookie/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/pookie/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/pookie/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/pookie/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/pookie/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [all] Error 2

Any help on how to solve this would be really appreciated!!
Please be gentle!

Cheers,
John

---

### Post by chili555 on 2013-03-07
@GentleJohn--

Here is a slightly newer version that avoids the well-known IEEE80211_HW_BEACON_FILTER issue. The link is my own Dropbox. I just ran 'make' and it succeeds, albeit with a few warnings.

It looks like you are doing well so far. Keep up the good work.

[https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)

---

### Post by redboots on 2013-03-08
> **chili555 said:**
> @GentleJohn--

Here is a slightly newer version that avoids the well-known IEEE80211_HW_BEACON_FILTER issue. The link is my own Dropbox. I just ran 'make' and it succeeds, albeit with a few warnings.

Sir, you ar a star!
All working AOK. Many thanks.

Now to teach this old dog some new tricks... UB wise.:)


Thanks again.

John

---

### Post by megajuan88 on 2013-04-06
it didn't work for me, root@jennifer-Satellite-Pro-C840:/home/jennifer# cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
root@jennifer-Satellite-Pro-C840:/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# ~sudo su
No se ha encontrado la orden «~sudo», quizás quiso decir:
 La orden «sudo» del paquete «sudo» (main)
 La orden «sudo» del paquete «sudo-ldap» (universe)
~sudo: no se encontró la orden
root@jennifer-Satellite-Pro-C840:/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo su
root@jennifer-Satellite-Pro-C840:/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: se ingresa al directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce»
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: se sale del directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce»
make[1]: se ingresa al directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se»
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: se sale del directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se»
make[1]: se ingresa al directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de»
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: se sale del directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de»
make[1]: se ingresa al directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e»
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: se sale del directorio «/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e»
root@jennifer-Satellite-Pro-C840:/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.5.0-26-generic/build M=/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.5.0-26-generic»
  CC [M]  /home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: En la función ‘_rtl_init_mac80211’:
/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ no se declaró aquí (primer uso en esta función)
/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: nota: cada identificador sin declarar se reporta sólo una vez para cada función en el que aparece
make[2]: *** [/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.5.0-26-generic»
make: *** [all] Error 2
root@jennifer-Satellite-Pro-C840:/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo make install
make -C /lib/modules/3.5.0-26-generic/build M=/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.5.0-26-generic»
  CC [M]  /home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: En la función ‘_rtl_init_mac80211’:
/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ no se declaró aquí (primer uso en esta función)
/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: nota: cada identificador sin declarar se reporta sólo una vez para cada función en el que aparece
make[2]: *** [/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.5.0-26-generic»
make: *** [all] Error 2

---

### Post by megajuan88 on 2013-04-06
how can I get it to work?

---

### Post by megajuan88 on 2013-04-06
> **chili555 said:**
> @GentleJohn--

Here is a slightly newer version that avoids the well-known IEEE80211_HW_BEACON_FILTER issue. The link is my own Dropbox. I just ran 'make' and it succeeds, albeit with a few warnings.

It looks like you are doing well so far. Keep up the good work.

[https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)

How can I get it to work?

---

### Post by chili555 on 2013-04-06
> it didn't work for me, root@jennifer-Satellite-Pro-C840:/home/jennifer# cd rtl_92ce_92se_92de_8723ae_linux_mac80211_000[COLOR="#FF0000"]6.0514 .2012[/COLOR]
<snip>
/home/jennifer/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514 .2012/base.c:320:6: error: ‘[COLOR="#FF0000"]IEEE80211_HW_BEACON_FILTER[/COLOR]’ no se declaró aquí (primer uso en esta función)You are not using the newer version I linked and recommended just a few posts above. Please try it.

---

### Post by chili555 on 2013-04-06
> **megajuan88 said:**
> How can I get it to work?Get the package I linked just above and place it on your desktop. Right-click it and select 'Extract Here.' Get a temporary wired ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
sudo su
make
make install
modprobe rtl8723e
exit
```Post back if you get stuck.

---

