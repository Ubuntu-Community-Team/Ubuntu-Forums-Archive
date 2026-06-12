---
title: "Belkin F6D4050 not working using ralink rt2870 or ndisgtk windows drivers"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by malapradej on 2011-08-01
Hi,
I ma relatively new to ubuntu. I have reinstalled ubuntu 10.10 on my desktop and am trying to setup the Belkin usb wireless adapter to work. I have tried many, many forums and could not find and answer for why this is not working. The list is as follows:
[http://ubuntuforums.org/showthread.php?t=960642&highlight=maverick](http://ubuntuforums.org/showthread.php?t=960642&highlight=maverick)
[http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)
[http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage](http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage)
[http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870)
[http://ubuntuforums.org/showthread.php?t=1160551](http://ubuntuforums.org/showthread.php?t=1160551)
[http://ubuntugeek.com/forum/index.php?topic=77.0](http://ubuntugeek.com/forum/index.php?topic=77.0)
and many more.....

each time I run the make command I get the following:

make -C tools
make[1]: Entering directory `/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2

and each time I run the make install command:

make -C /home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/malapradej/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
make: *** [install] Error 2

dmesg | grep rt2 brings:

zeroo, nada.....

modprobe -l | grep rt2 brings:

kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/staging/rt2860/rt2860sta.ko
kernel/drivers/staging/rt2870/rt2870sta.ko

lsusb brings:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 043d:0078 Lexmark International, Inc. InkJet Color Printer
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 050d:935a Belkin Components 
Bus 001 Device 006: ID 0951:1601 Kingston Technology DataTraveler II+ Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod brings:

Module                  Size  Used by
ndiswrapper           184207  0 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
binfmt_misc             6599  1 
snd_via82xx            20140  2 
radeon                825934  3 
gameport                9327  1 snd_via82xx
snd_ac97_codec         99227  1 snd_via82xx
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_via82xx,snd_ac97_codec
snd_page_alloc          7120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5661  1 snd_via82xx
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  5 radeon,ttm,drm_kms_helper
ppdev                   5556  0 
usblp                  10651  0 
parport_pc             26058  1 
crc_ccitt               1351  0 
snd                    49006  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via_agp                 5322  1 
i2c_algo_bit            5168  1 radeon
i2c_viapro              5777  0 
shpchp                 29886  0 
soundcore                880  1 snd
agpgart                32011  3 ttm,drm,via_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
floppy                 54311  0 
via_rhine              19038  0 
pata_via                7300  4 
sata_via                7344  0 
dc395x                 32431  0 
mii                     4425  1 via_rhine

Back to ndisgtk. I have tried it numerous times and it even shows up that hardware is present it will not recognize the devise in the applet.


Short of giving up and buying a cable or another USB wireless I don't know what to do.....

Help will be very much appreciated.

Jacques

---

