---
title: "Lost wireless on upgrade to 11.10"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by MarkJBrader on 2011-10-23
Last summer, I upgraded my PC, and had a difficult time finding a card that worked for both Ubuntu 10.10 and Windows, but finally found one.  Yesterday I decided to go through the pain of upgrading through 11.04 and up to 11.10.

The wireless disappeared.  I have gone through the other threads and done what I could to no avail.  Here are the particulars:

When I do: 

lspci -nn

The relevant line is:
  04:00.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]



lsmod
 gives:

Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  4 
snd_hda_codec_realtek   254125  1 
psmouse                63474  0 
nvidia              10390874  40 
mxm_wmi                12859  0 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 mxm_wmi
snd_timer              28932  2 snd_pcm,snd_seq
shpchp                 32356  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    36466  0 
lp                     17455  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  47200  0 
xhci_hcd               72957  0 


rfkill list all gives:
<nothing>

lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: RT3060 Wireless 802.11n 1T/1R
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:fa200000-fa20ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 8c:89:a5:13:85:ee
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.0.0.12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:49 ioport:d000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff


At the end of the blacklist.conf I have
blacklist rt2800pci

I had done that for 10.10.

I ran
apt-get install build-essential linux-headers-generic
and the system said I already had it all.

I went to ralinktech.com and downloaded the driver which said it was for the 3062.

edited the config.mk to set HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT to 'y'

I ran the make:

make

make -C tools
make[1]: Entering directory `/home/mbrader/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
In file included from /usr/include/stdio.h:28:0,
                 from bin2h.c:28:
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
compilation terminated.
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/mbrader/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
make: *** [build_tools] Error 2


Now, looking around, I found someone on with a build problem, and did an  export C_INCLUDE_PATH=/usr/include/i386-linux-gnu

then make gives:
make -C tools
make[1]: Entering directory `/home/mbrader/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
/usr/bin/ld: cannot find crt1.o: No such file or directory
/usr/bin/ld: cannot find crti.o: No such file or directory
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/mbrader/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
make: *** [build_tools] Error 2

I cannot figure out how to change this.  I hope that if I could get this driver to build, it would work.  Apparently it will on longer build on 11.10 64-bit system.

---

### Post by praseodym on 2011-10-23
Hi,

check this driver:

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz)
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install
```
After a kernel upgrade you need to compile again:

```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean 
sudo make
sudo make install 
```

---

### Post by henry83 on 2011-10-26
Hello there, I'm having the same problem, but in Ubuntu 11.10 32 bits... I was using the DWA-525 PCI Wireless without problems in Ubuntu 11.04, but after upgrading I found the same problem. It seems the driver was planned for 2.6.x linux kernel, as I am using now 3.0.0-13 when running make && make install, I get a /lib/modules/3.0.0-13-generic-pae/build: No such file or directory. Stop. Do you know how can I solve this issue? Thanks.

---

### Post by praseodym on 2011-10-26
You need to install the kernel headers and the compilation tools first:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-pae build-essential dkms
```

---

