---
title: "Webcam or bttv ?"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by mabovo on 2007-09-07
Hello,

I have a webcam (not detected on /dev/video0) and a bt878 installed and need to know if bttv can deal with both devices or do I have to config the Xorg.conf file ?.
 I got the following message from terminal:
marcos@linux-ubuntu:~$ sudo modprobe bttv
[sudo] password for marcos:
marcos@linux-ubuntu:~$ xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-10-386)
xinerama 0: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  67
  Current serial number in output stream:  67
marcos@linux-ubuntu:~$

---

### Post by mabovo on 2007-09-07
I did some tests and got the following messages:

[HTML]
marcos@linux-ubuntu:~$ lsusb
Bus 005 Device 008: ID 046d:08c5 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0566:3002 Monterey International Corp. 
Bus 002 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:4811 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
marcos@linux-ubuntu:~$  v4l-conf -c /dev/video0 -b 24 -2
v4l-conf: using X11 display :0.0
dga: version 2.0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
marcos@linux-ubuntu:~$ sudo mknod /dev/video0 c 81 0
mknod: `/dev/video0': O arquivo já existe
marcos@linux-ubuntu:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-10-386)
looking for available devices
port 73-73
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner 
*** glibc detected *** xawtv: free(): invalid pointer: 0xb778e740 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb79d9d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb79dd800]
/usr/lib/xawtv/drv0-v4l2.so[0xb778b1f6]
xawtv(grabber_scan+0x193)[0x805dcd3]
xawtv(main+0x1cf3)[0x8057b63]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7986050]
xawtv[0x8053c01]
======= Memory map: ========
08048000-0807f000 r-xp 00000000 16:41 822305     /usr/bin/xawtv
0807f000-08085000 rw-p 00037000 16:41 822305     /usr/bin/xawtv
08085000-080cd000 rw-p 08085000 00:00 0          [heap]
b7600000-b7621000 rw-p b7600000 00:00 0 
b7621000-b7700000 ---p b7621000 00:00 0 
b770f000-b7719000 r-xp 00000000 16:41 361824     /lib/libgcc_s.so.1
b7719000-b771a000 rw-p 0000a000 16:41 361824     /lib/libgcc_s.so.1
b772e000-b7747000 r-xp 00000000 16:41 820655     /usr/lib/libdv.so.4.0.3
b7747000-b7749000 rw-p 00019000 16:41 820655     /usr/lib/libdv.so.4.0.3
b7749000-b7755000 rw-p b7749000 00:00 0 
b7760000-b7761000 r-xp 00000000 16:41 18990      /usr/lib/xawtv/write-dv.so
b7761000-b7762000 rw-p 00000000 16:41 18990      /usr/lib/xawtv/write-dv.so
b7762000-b7764000 r-xp 00000000 16:41 18989      /usr/lib/xawtv/write-avi.so
b7764000-b7765000 rw-p 00002000 16:41 18989      /usr/lib/xawtv/write-avi.so
b7765000-b7768000 r-xp 00000000 16:41 18988      /usr/lib/xawtv/snd-oss.so
b7768000-b7769000 rw-p 00002000 16:41 18988      /usr/lib/xawtv/snd-oss.so
b7769000-b776b000 r-xp 00000000 16:41 18987      /usr/lib/xawtv/read-dv.so
b776b000-b776c000 rw-p 00001000 16:41 18987      /usr/lib/xawtv/read-dv.so
b776c000-b776e000 r-xp 00000000 16:41 18986      /usr/lib/xawtv/read-avi.so
b776e000-b776f000 rw-p 00001000 16:41 18986      /usr/lib/xawtv/read-avi.so
b776f000-b7770000 r-xp 00000000 16:41 18985      /usr/lib/xawtv/linedoubler.so
b7770000-b7771000 rw-p 00000000 16:41 18985      /usr/lib/xawtv/linedoubler.so
b7771000-b7772000 r-xp 00000000 16:41 18984      /usr/lib/xawtv/linear-blend.so
b7772000-b7773000 rw-p 00000000 16:41 18984      /usr/lib/xawtv/linear-blend.so
b7773000-b7775000 r-xp 00000000 16:41 18983      /usr/lib/xawtv/flt-smooth.so
b7775000-b7776000 rw-p 00001000 16:41 18983      /usr/lib/xawtv/flt-smooth.so
b7776000-b7777000 r-xp 00000000 16:41 18982      /usr/lib/xawtv/flt-invert.so
b7777000-b7778000 rw-p 00000000 16:41 18982      /usr/lib/xawtv/flt-invert.so
b7778000-b7779000 r-xp 00000000 16:41 18981      /usr/lib/xawtv/flt-gamma.so
b7779000-b777a000 rw-p 00000000 16:41 18981      /usr/lib/xawtv/flt-gamma.so
b777a000-b777b000 r-xp 00000000 16:41 18980      /usr/lib/xawtv/flt-disor.so
b777b000-b777c000 rw-p 00000000 16:41 18980      /usr/lib/xawtv/flt-disor.so
b777c000-b7782000 r-xp 00000000 16:41 18979      /usr/lib/xawtv/drv1-v4l.so
b7782000-b7787000 rw-p 00006000 16:41 18979      /usr/lib/xawtv/drv1-v4l.so
b7787000-b778e000 r-xp 00000000 16:41 18978      /usr/lib/xawtv/drv0-v4l2.so
b778e000-b779a000 rw-p 00006000 16:41 18978      /usr/lib/xawtv/drv0-v4l2.so
b779a000-b779f000 r-xp 00000000 16:41 18977      /usr/lib/xawtv/drv0-v4l2-old.so
b779f000-b77a0000 rw-p 00004000 16:41 18977      /usr/lib/xawtv/drv0-v4l2-old.so
b77a0000-b77a1000 r-xp 00000000 16:41 18976      /usr/lib/xawtv/cubic.so
b77a1000-b77a2000 rw-p 00000000 16:41 18976      /usr/lib/xawtv/cubic.so
b77a2000-b77a3000 r-xp 00000000 16:41 18974      /usr/lib/xawtv/bilinear.so
b77a3000-b77a4000 rw-p 00000000 16:41 18974      /usr/lib/xawtv/bilinear.so
b77a4000-b77e3000 r--p 00000000 16:41 884750     /usr/lib/locale/pt_BR.utf8/LC_CTYPE
b77e3000-b78c3000 r--p 00000000 16:41 884761     /usr/lib/locale/pt_BR.utf8/LC_COLLATE
b78c3000-b78c6000 rw-p b78c3000 00:00 0 
b78c6000-b78cf000 r-xp 00000000 16:41 820504     /usr/lib/libdrm.so.2.3.0
b78cf000-b78d0000 rw-p 00008000 16:41 820504     /usr/lib/libdrm.so.2.3.0
b78d0000-b78d4000 r-xp 00000000 16:41 820506     /usr/lib/libXfixes.so.3.1.0
b78d4000-b78d5000 rw-p 00003000 16:41 820506     /usr/lib/libXfixes.so.3.1.0
b78d5000-b78d7000 r-xp 00000000 16:41 820498     /usr/lib/libXdamage.so.1.1.0
b78d7000-b78d8000 rw-p 00001000 16:41 820498     /usr/lib/libXdamage.so.1.1.0
b78d8000-b78dc000 r-xp 00000000 16:41 820500     /usr/lib/libXdmcp.so.6.0.0
b78dc000-b78dd000 rw-p 00003000 16:41 820500     /usr/lib/libXdmcp.so.6.0.0
b78dd000-b78df000 r-xp 00000000 16:41 820489     /usr/lib/libXau.so.6.0.0
b78df000-b78e0000 rw-p 00001000 16:41 820489     /usr/lib/libXau.so.6.0.0
b78e0000-b78e1000 rw-p b78e0000 00:00 0 
b78e1000-b78ff000 r-xp 00000000 16:41 821089     /usr/lib/libexpat.so.1.0.0
b78ff000-b7901000 rw-p 0001e000 16:41 821089     /usr/lib/libexpat.so.1.0.0
b7901000-b796c000 r-xp 00000000 16:41 820703     /usr/lib/libfreetype.so.6.3.16
b796c000-b7970000 rw-p 0006a000 16:41 820703     /usr/lib/libfreetype.so.6.3.16
b7970000-b7ab4000 r-xp 00000000 16:41 294992     /lib/tls/i686/cmov/libc-2.6.1.so
b7ab4000-b7ab5000 r--p 00143000 16:41 294992     /lib/tls/i686/cmov/libc-2.6.1.so
b7ab5000-b7ab7000 rw-p 00144000 16:41 294992     /lib/tls/i686/cmov/libc-2.6.1.so
b7ab7000-b7aba000 rw-p b7ab7000 00:00 0 
b7aba000-b7ad8000 r-xp 00000000 16:41 820972     /usr/lib/libjpeg.so.62.0.0
b7ad8000-b7ad9000 rw-p 0001d000 16:41 820972     /usr/lib/libjpeg.so.62.0.0
b7ad9000-b7ada000 rw-p b7ad9000 00:00 0 
b7ada000-b7b38000 r-xp 00000000 16:41 884756     /usr/lib/libGL.so.1.2
b7b38000-b7b3a000 rw-p 0005d000 16:41 884756     /usr/lib/libGL.so.1.2
b7b3a000-b7b3b000 rw-p b7b3a000 00:00 0 
b7b3b000-b7b4f000 r-xp 00000000 16:41 819245     /usr/lib/libz.so.1.2.3.3
b7b4f000-b7b50000 rw-p 00013000 16:41 819245     /usr/lib/libz.so.1.2.3.3
b7b50000-b7b72000 r-xp 00000000 16:41 821111     /usr/lib/libpng12.so.0.15.0
b7b72000-b7b73000 rw-p 00021000 16:41 821111     /usr/lib/libpng12.so.0.15.0
b7b73000-b7b96000 r-xp 00000000 16:41 295160     /lib/tls/i686/cmov/libm-2.6.1.so
b7b96000-b7b98000 rw-p 00023000 16:41 295160     /lib/tls/i686/cmov/libm-2.6.1.so
b7b98000-b7bf3000 r-xp 00000000 16:41 822298     /usr/lib/libzvbi.so.0.10.0
b7bf3000-b7c02000 rw-p 0005a000 16:41 822298     /usr/lib/libzvbi.so.0.10.0
b7c02000-b7c03000 rw-p b7c02000 00:00 0 
b7c03000-b7cf0000 r-xp 00000000 16:41 820483     /usr/lib/libX11.so.6.2.0
b7cf0000-b7cf4000 rw-p 000ed000 16:41 820483     /usr/lib/libX11.so.6.2.0
b7cf4000-b7cf5000 rw-p b7cf4000 00:00 0 
b7cf5000-b7d02000 r-xp 00000000 16:41 820197     /usr/lib/libXext.so.6.4.0
b7d02000-b7d03000 rw-p 0000d000 16:41 820197     /usr/lib/libXext.so.6.4.0
b7d03000-b7d12000 r-xp 00000000 16:41 820522     /usr/lib/libXpm.so.4.11.0
b7d12000-b7d13000 rw-p 0000f000 16:41 820522     /usr/lib/libXpm.so.4.11.0
b7d13000-b7d28000 r-xp 00000000 16:41 819551     /usr/lib/libICE.so.6.3.0
b7d28000-b7d2a000 rw-p 00014000 16:41 819551     /usr/lib/libICE.so.6.3.0
b7d2a000-b7d2b000 rw-p b7d2a000 00:00 0 
b7d2b000-b7d32000 r-xp 00000000 16:41 820479     /usr/lib/libSM.so.6.0.0
b7d32000-b7d33000 rw-p 00006000 16:41 820479     /usr/lib/libSM.so.6.0.0
b7d33000-b7d80000 r-xp 00000000 16:41 820530     /usr/lib/libXt.so.6.0.0
b7d80000-b7d84000 rw-p 0004c000 16:41 820530     /usr/lib/libXt.so.6.0.0
b7d84000-b7d99000 r-xp 00000000 16:41 819705     /usr/lib/libXmu.so.6.2.0
b7d99000-b7d9a000 rw-p 00015000 16:41 819705     /usr/lib/libXmu.so.6.2.0
b7d9a000-b7d9b000 rw-p b7d9a000 00:00 0 
b7d9b000-b7dee000 r-xp 00000000 16:41 820134     /usr/lib/libXaw7.so.7.0.0
b7dee000-b7df5000 rw-p 00053000 16:41 820134     /usr/lib/libXaw7.so.7.0.0
b7df5000-b7df9000 r-xp 00000000 16:41 820536     /usr/lib/libXxf86dga.so.1.0.0
b7df9000-b7dfa000 rw-p 00004000 16:41 820536     /usr/lib/libXxf86dga.so.1.0.0
b7dfa000-b7dfe000 r-xp 00000000 16:41 820540     /usr/lib/libXxf86vm.so.1.0.0
b7dfe000-b7dff000 rw-p 00003000 16:41 820540     /usr/lib/libXxf86vm.so.1.0.0
b7dff000-b7e01000 r-xp 00000000 16:41 820745     /usr/lib/libXinerama.so.1.0.0
b7e01000-b7e02000 rw-p 00001000 16:41 820745     /usr/lib/libXinerama.so.1.0.0
b7e02000-b7e09000 r-xp 00000000 16:41 820526     /usr/lib/libXrender.so.1.3.0
b7e09000-b7e0a000 rw-p 00006000 16:41 820526     /usr/lib/libXrender.so.1.3.0
b7e0a000-b7e0f000 r-xp 00000000 16:41 820524     /usr/lib/libXrandr.so.2.1.0
b7e0f000-b7e10000 rw-p 00005000 16:41 820524     /usr/lib/libXrandr.so.2.1.0
b7e10000-b7e11000 rw-p b7e10000 00:00 0 
b7e11000-b7e15000 r-xp 00000000 16:41 820517     /usr/lib/libXv.so.1.0.0
b7e15000-b7e16000 rw-p 00003000 16:41 820517     /usr/lib/libXv.so.1.0.0
b7e16000-b7e39000 r-xp 00000000 16:41 820695     /usr/lib/libfontconfig.so.1.2.0
b7e39000-b7e41000 rw-p 00023000 16:41 820695     /usr/lib/libfontconfig.so.1.2.0
b7e41000-b7e52000 r-xp 00000000 16:41 820510     /usr/lib/libXft.so.2.1.2
b7e52000-b7e53000 rw-p 00010000 16:41 820510     /usr/lib/libXft.so.2.1.2
b7e53000-b7f14000 r-xp 00000000 16:41 819899     /usr/lib/libasound.so.2.0.0
b7f14000-b7f19000 rw-p 000c0000 16:41 819899     /usr/lib/libasound.so.2.0.0
b7f19000-b7f1e000 r-xp 00000000 16:41 820975     /usr/lib/liblirc_client.so.0.2.0
b7f1e000-b7f1f000 rw-p 00004000 16:41 820975     /usr/lib/liblirc_client.so.0.2.0
b7f1f000-b7f5b000 r-xp 00000000 16:41 262251     /lib/libncurses.so.5.6
b7f5b000-b7f63000 rw-p 0003b000 16:41 262251     /lib/libncurses.so.5.6
b7f63000-b7f64000 rw-p b7f63000 00:00 0 
b7f64000-b7f78000 r-xp 00000000 16:41 295170     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f78000-b7f7a000 rw-p 00013000 16:41 295170     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f7a000-b7f7c000 rw-p b7f7a000 00:00 0 
b7f7c000-b7f7e000 r-xp 00000000 16:41 295159     /lib/tls/i686/cmov/libdl-2.6.1.so
b7f7e000-b7f80000 rw-p 00001000 16:41 295159     /lib/tls/i686/cmov/libdl-2.6.1.so
b7f80000-b7f82000 r-xp 00000000 16:41 18975      /usr/lib/xawtv/conv-mjpeg.so
b7f82000-b7f83000 rw-p 00002000 16:41 18975      /usr/lib/xawtv/conv-mjpeg.so
b7f83000-b7f84000 r--p 00000000 16:41 885235     /usr/lib/locale/pt_BR.utf8/LC_NUMERIC
b7f84000-b7f85000 r--p 00000000 16:41 884931     /usr/lib/locale/pt_BR.utf8/LC_TIME
b7f85000-b7f86000 r--p 00000000 16:41 884930     /usr/lib/locale/pt_BR.utf8/LC_MONETARY
b7f86000-b7f87000 r--p 00000000 16:41 901152     /usr/lib/locale/pt_BR.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f87000-b7f88000 r--p 00000000 16:41 885119     /usr/lib/locale/pt_BR.utf8/LC_PAPER
b7f88000-b7f89000 r--p 00000000 16:41 885195     /usr/lib/locale/pt_BR.utf8/LC_NAME
b7f89000-b7f8a000 r--p 00000000 16:41 884937     /usr/lib/locale/pt_BR.utf8/LC_ADDRESS
b7f8a000-b7f8b000 r--p 00000000 16:41 885057     /usr/lib/locale/pt_BR.utf8/LC_TELEPHONE
b7f8b000-b7f8c000 r--p 00000000 16:41 885115     /usr/lib/locale/pt_BR.utf8/LC_MEASUREMENT
b7f8c000-b7f93000 r--s 00000000 16:41 836014     /usr/lib/gconv/gconv-modules.cache
b7f93000-b7f94000 r--p 00000000 16:41 884933     /usr/lib/locale/pt_BR.utf8/LC_IDENTIFICATION
b7f94000-b7f96000 rw-p b7f94000 00:00 0 
b7f96000-b7fb0000 r-xp 00000000 16:41 361826     /lib/ld-2.6.1.so
b7fb0000-b7fb2000 rw-p 00019000 16:41 361826     /lib/ld-2.6.1.so
bff37000-bff4c000 rw-p bff37000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Cancelado (core dumped)
marcos@linux-ubuntu:~$  xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-10-386)
xinerama 0: 1280x1024+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  67
  Current serial number in output stream:  67
marcos@linux-ubuntu:~$ 

[/HTML]

---

### Post by mabovo on 2007-09-07
A few more tests: 

[HTML]
marcos@linux-ubuntu:~$ lsmod | grep usb
usb_storage            71616  0 
snd_usb_audio          80896  0 
snd_usb_lib            16896  1 snd_usb_audio
snd_hwdep               9604  3 snd_emux_synth,snd_emu10k1,snd_usb_audio
libusual               17296  1 usb_storage
usbhid                 28384  0 
hid                    27008  1 usbhid
usblp                  14080  0 
snd_pcm                77960  6 snd_via82xx,snd_emu10k1,snd_via82xx_modem,snd_usb_audio,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            25088  5 snd_seq_virmidi,snd_mpu401_uart,snd_emu10k1,snd_usb_lib,snd_seq_midi
snd                    54148  21 snd_emux_synth,snd_seq_virmidi,snd_via82xx,snd_mpu401_uart,snd_emu10k1,snd_via82xx_modem,snd_usb_audio,snd_usb_lib,snd_seq_dummy,snd_ac97_codec,snd_hwdep,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
usbcore               135192  11 xpad,usb_storage,snd_usb_audio,snd_usb_lib,uvcvideo,libusual,usbhid,usblp,ehci_hcd,uhci_hcd
ide_core              114516  4 usb_storage,ide_cd,ide_disk,via82cxxx
scsi_mod              146572  4 sg,sd_mod,usb_storage,libata
marcos@linux-ubuntu:~$ dmesg | grep usb
[   37.208107] usbcore: registered new interface driver usbfs
[   37.208129] usbcore: registered new interface driver hub
[   37.208145] usbcore: registered new device driver usb
[   39.245938] usb usb1: configuration #1 chosen from 1 choice
[   39.347952] usb usb2: configuration #1 chosen from 1 choice
[   39.451780] usb usb3: configuration #1 chosen from 1 choice
[   39.555619] usb usb4: configuration #1 chosen from 1 choice
[   39.587290] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   39.659623] usb usb5: configuration #1 chosen from 1 choice
[   40.114469] usb 1-1: device not accepting address 2, error -71
[   41.304687] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   41.601108] usb 5-1: configuration #1 chosen from 1 choice
[   42.870294] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   43.046255] usb 4-1: configuration #1 chosen from 1 choice
[   43.285662] usb 4-2: new low speed USB device using uhci_hcd and address 3
[   43.439585] usb 4-2: configuration #1 chosen from 1 choice
[   43.681064] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   43.885637] usb 1-2: configuration #1 chosen from 1 choice
[   44.128388] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   44.295831] usb 2-1: configuration #1 chosen from 1 choice
[   44.535771] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   44.693175] usb 2-2: configuration #1 chosen from 1 choice
[   59.310449] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4811
[   59.310475] usbcore: registered new interface driver usblp
[   59.310479] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   59.454803] usbcore: registered new interface driver hiddev
[   59.509260] bttv0: i2c: checking for TDA9887 @ 0x86... <6>usb 4-1: USB disconnect, address 2
[   59.573236] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:10.3-2
[   59.656886] usb 4-1: new full speed USB device using uhci_hcd and address 4
[   59.833638] usb 4-1: configuration #1 chosen from 1 choice
[   59.836812] usbcore: registered new interface driver libusual
[   59.962428] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:10.1-1
[   60.028311] input: USB HID v1.10 Keyboard [HID 0566:3002] on usb-0000:00:10.1-2
[   60.074108] input,hiddev96: USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:10.1-2
[   60.074128] usbcore: registered new interface driver usbhid
[   60.074132] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   60.074149] usbcore: registered new interface driver uvcvideo
[   60.165298] usbcore: registered new interface driver snd-usb-audio
[   60.165436] usb-storage: device found at 4
[   60.165438] usb-storage: waiting for device to settle before scanning
[   60.165507] usb-storage: device found at 4
[   60.165509] usb-storage: waiting for device to settle before scanning
[   60.165520] usbcore: registered new interface driver usb-storage
[   60.356071] usbcore: registered new interface driver xpad
[   65.158486] usb-storage: device scan complete
[   65.158602] usb-storage: device scan complete
[  194.094539] usb 4-1: USB disconnect, address 4
[  207.423828] usb 5-1: USB disconnect, address 2
[  215.893473] usb 5-7: new high speed USB device using ehci_hcd and address 8
[  216.189639] usb 5-7: configuration #1 chosen from 1 choice
marcos@linux-ubuntu:~$ 

[/HTML]

---

### Post by AusIV4 on 2007-09-07
I have a Webcam, bttv tuner, and USB tuner all connected to my box, and I haven't had to modify Xorg.conf at all. I'd just recommend making sure each thing works independently (if you can). If you have the proper drivers, one item should show up as /dev/video0 and the next /dev/video1.

Part of your problem may just be xawtv. I've never gotten that program to work right.

---

### Post by mabovo on 2007-09-07
And my lspci and xorg.conf file:

lspci
[HTML]
marcos@linux-ubuntu:~$ lspci -nnn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:0282]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:1282]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:2282]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:3282]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:4282]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:7282]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:0b.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
00:0b.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
00:0d.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 74)
00:0e.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 05)
00:0e.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 05)
00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AR [Radeon 9600] [1002:4152]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) [1002:4172]
[/HTML]

xorg.conf
[HTML]
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
[/HTML]

---

### Post by mabovo on 2007-09-07
> **AusIV4 said:**
> I have a Webcam, bttv tuner, and USB tuner all connected to my box, and I haven't had to modify Xorg.conf at all. I'd just recommend making sure each thing works independently (if you can). If you have the proper drivers, one item should show up as /dev/video0 and the next /dev/video1.

Part of your problem may just be xawtv. I've never gotten that program to work right.

I also have TVTime Television viewr and Zapping TV Viewr installed but they don't work too.
I couldn't find the proper Logitech Quickcam PRO 5000 module to install on Gusty and wouldn't like to recompile kernel only to add webcam device. I know there is a dkms package that do this job but I think is too risk.

How can I do to make each device working independently ?
Should I configure /dev/video0 for bt878 and /dev/video1 for webcam ?

---

### Post by mabovo on 2007-09-07
> **AusIV4 said:**
> I have a Webcam, bttv tuner, and USB tuner all connected to my box, and I haven't had to modify Xorg.conf at all. 
Part of your problem may just be xawtv. I've never gotten that program to work right.

I just remove xawtv and give up to make webcam works. Now with kernel 2.6.22.14 on Gusty it seems that Logitech Quickcam Pro 5000 gave a breath of live but without sound.

Thanks anyway.

---

