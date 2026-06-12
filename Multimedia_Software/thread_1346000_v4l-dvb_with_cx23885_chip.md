---
title: "v4l-dvb with cx23885 chip"
date: 2009-12-04
forum: Multimedia Software
---

### Post by Zsoltika66 on 2009-12-04
Hi,

I need help. Sorry my english is terrible, bu i try to tel you about my problem.
I have Ubuntu 9.10 on a  PC, PC has Hauppauge WinTV 1200. I think it has a cx3885 chip on it. I tried tu install the driver, but I have no /dev/video file after the installation. The tvtime can't find the /dev/video or any similar thing to receive a TV channel.

You can see what I did, it is my .bash_history:

lspci
dmesg
modprobe cx23885
dmesg
apt-get install mercurial
cd ..
mkdir v4l_source
cd v4l_source/
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb/
make
make install
modprobe cx23885
dmesg
MAKEDEV video


the make sent me many errors:
make -C /v4l_source/v4l-dvb/v4l 
make[1]: Entering directory `/v4l_source/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/v4l_source/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/v4l_source/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/v4l_source/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/v4l_source/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-15-generic/build
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/v4l_source/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /v4l_source/v4l-dvb/v4l/firedtv-1394.o
/v4l_source/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/v4l_source/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/v4l_source/v4l-dvb/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/v4l_source/v4l-dvb/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/v4l_source/v4l-dvb/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory

... and so on

I send an attached TXT file, with the output of lspci, dmesg and make.

Does anybody know what I should do?

Thanks for your help

---

### Post by markackerman8@gmail.com on 2009-12-09
I am pulling my hair out as we3ll, after revisiting this HP pcmcia rebranded HVR-1500, and coded as hauppauge cx-23885, arghhhh tuner card, and at least after 1 year it at leaast is seen in my dmesg, and i will show it, but i have tried so many ways ... tv-time, kaffeine, mplayer, xbmc,MythTV etc...... and nothing, ANY HELP would be much appreciated


Mark

Dmesg

[   28.365472] tveeprom 0-0050: Hauppauge model 77041, rev E2F0, serial# 3746385
[   28.365476] tveeprom 0-0050: MAC address is 00-0D-FE-39-2A-51
[   28.365480] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   28.365482] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   28.365486] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[   28.365488] tveeprom 0-0050: decoder processor is CX23885 (idx 33)
[   28.365490] tveeprom 0-0050: has no radio
[   28.365493] cx23885[0]: hauppauge eeprom: model=77041
[   28.365496] cx23885_dvb_register() allocating 1 frontend(s)
[   28.365645] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[   28.365663] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   28.367768] Registered led device: mmc0::
[   28.368827] mmc0: SDHCI controller on PCI [0000:09:09.1] using PIO
[   28.368861] cx23885[0]: cx23885 based dvb card
[   28.369763] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input9
[   28.369832] usbcore: registered new interface driver uvcvideo
[   28.369835] USB Video Class driver (v0.1.0)
[   28.438100] xc5000 1-0061: creating new instance
[   28.438818] xc5000: Successfully identified at address 0x61
[   28.438820] xc5000: Firmware has not been loaded previously
[   28.438824] DVB: registering new adapter (cx23885[0])
[   28.438828] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   28.439177] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   28.439188] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xf6000000
[   28.439196] cx23885 0000:04:00.0: setting latency timer to 64
,,,,
....
[   57.092876] r8169: eth0: link up
[   67.710056] eth0: no IPv6 routers present
[  130.249004] CE: hpet increasing min_delta_ns to 15000 nsec
[  306.715197] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[  306.733681] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[  306.733688] cx88/2: registering cx8802 driver, type: dvb access: shared
[  509.863623] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[  509.863641] cx23885 0000:04:00.0: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[  509.903119] xc5000: firmware read 12401 bytes.
[  509.903124] xc5000: firmware uploading...
[  511.550164] xc5000: firmware upload complete...
[  893.467131] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[  893.467143] cx23885 0000:04:00.0: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[  893.474036] xc5000: firmware read 12401 bytes.
[  893.474041] xc5000: firmware uploading...
[  895.092661] xc5000: firmware upload complete...
[ 2383.697582] CE: hpet increasing min_delta_ns to 22500 nsec
[ 7402.031486] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 7402.031494] cx23885 0000:04:00.0: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 7402.038380] xc5000: firmware read 12401 bytes.
[ 7402.038383] xc5000: firmware uploading...
[ 7403.740054] xc5000: firmware upload complete...
[ 7612.184303] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 7612.184311] cx23885 0000:04:00.0: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 7612.189039] xc5000: firmware read 12401 bytes.
[ 7612.189042] xc5000: firmware uploading...
[ 7613.812555] xc5000: firmware upload complete...
[ 7850.622684] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[ 7850.622688] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 9244.857194] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 9244.857205] cx23885 0000:04:00.0: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 9244.869826] xc5000: firmware read 12401 bytes.
[ 9244.869831] xc5000: firmware uploading...
[ 9246.590107] xc5000: firmware upload complete...
[ 9644.816889] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 9644.816899] cx23885 0000:04:00.0: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 9644.824861] xc5000: firmware read 12401 bytes.
[ 9644.824864] xc5000: firmware uploading...
[ 9646.550158] xc5000: firmware upload complete...
[12309.109438] uvcvideo: Failed to resubmit video URB (-1).
ack@Titan:/lib/firmware$

HELP!!!

---

### Post by bmjenkins on 2010-02-21
Zsoltika66:

Your 'make' did not work and this stopped the module from being created.

You need to disable the firedtv module so that the rest can complete before you continue.

go to v4l-dvb/v4l/ directory and edit the .config file. Look for the line below and change it.

CONFIG_DVB_FIREDTV=m

change to:

CONFIG_DVB_FIREDTV=n

now redo your `make` and `sudo make install`

hope that helps.

---

