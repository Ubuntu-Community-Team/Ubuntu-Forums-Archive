---
title: "lirc_mceusb2 and itvt module conflict"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by clalor on 2007-04-14
I've searched and searched, but haven't found a solution to my issue, so here goes. By the way, thanks to everyone involved in writing the community docs and HOWTOs on the forum. They've been a tremendous help. Ubuntu has actually made me want to start using Linux again (I started with RH 5.1). :)

I've spent some time over the last few weeks setting up MythTV (combined backend/frontend per the community MythTV setup docs) on a spare computer and have run into an issue with the lirc_mceusb2 and ivtv modules. For background, I'm running on Edgy (current updates as of last weekend) with the versions of lirc (0.8.2-CVS) and ivtv (0.7.4) that installed from the repositories in the respective wikis. The capture card is a Hauppauge PVR-150 MCE 1042 and the remote/receiver is a Microsoft MCE v2 alt (purchased separately from the tuner card, no colored buttons at the bottom).

During the installation, both the lirc and ivtv modules built without error and they functioned well until the system was rebooted. After a reboot, ivtv functions normally, but the MCE receiver doesn't work at all (no red light when a button is pressed on the remote). The lirc_mcesub2 module is shown as loaded by lsmod, lircd is running, irw runs but doesn't return any input, and MythTV doesn't respond to the remote at all. I've run some of the checks that have been recommended in other lirc threads and this is what I get:

_dmesg | grep lirc_
[17179582.928000] lirc_dev: IR Remote Control driver registered, at major 61
[17179582.932000] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[17179582.932000] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.25 $
[17179582.932000] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[17179583.200000] lirc_dev: lirc_register_plugin: sample_rate: 0
[17179583.204000] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb1:2
[17179583.204000] usbcore: registered new driver lirc_mceusb2

_dmesg | grep ivtv_
[17179584.120000] ivtv:  ==================== START INIT IVTV ====================
[17179584.120000] ivtv:  version 0.7.4 (tagged release) loading
[17179584.120000] ivtv:  Linux version: 2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179584.120000] ivtv:  In case of problems please include the debug info between
[17179584.120000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179584.120000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179584.120000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179584.120000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179584.272000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179584.444000] tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179584.532000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179588.056000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179588.812000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[17179589.028000] ivtv0: Encoder revision: 0x02060039
[17179589.028000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179589.028000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179589.028000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179589.028000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179589.028000] ivtv0: Create encoder radio stream
[17179589.144000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17179589.196000] ivtv:  ====================  END INIT IVTV  ====================

_lsusb_
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0471:0815 Philips
Bus 001 Device 001: ID 0000:0000

_cat /dev/bus/usb/devices_
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0471 ProdID=0815 Rev= 0.00
S:  Manufacturer=Philips
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=PH00QtPV
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=lirc_mceusb2
E:  Ad=01(O) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms

_lsmod | grep lirc_
lirc_mceusb2           14596  0
lirc_dev               16500  1 lirc_mceusb2
usbcore               134912  3 lirc_mceusb2,uhci_hcd

_lsmod | grep ivtv_
ivtv                  199056  0
i2c_algo_bit           10376  1 ivtv
v4l1_compat            15108  1 ivtv
tveeprom               16144  1 ivtv
i2c_core               23424  8 i2c_ec,wm8775,cx25840,tda9887,tuner,ivtv,i2c_algo_bit,tveeprom
videodev               10752  1 ivtv

Other than the PCI latency message for ivtv, which I just haven't taken the time to fix yet, everything appears to be normal from what I've read.

I did some experimentation on a clean install and lirc ran normally after a reboot (lirc was the only thing installed other than updates). It was only after ivtv was installed that it stopped working after a reboot. Now I am able to work around this problem by stopping lircd, rmmod'ing lirc_mceusb2, modprobe'ing lirc_mceusb2, restarting lircd, and restarting MythTV, however I'd like to try and find a solution to the problem since I've done some ugly things in the sudoers file to get this work around to run without having to login from another box. :-$ Any suggestions on what to do next?

Christian

---

