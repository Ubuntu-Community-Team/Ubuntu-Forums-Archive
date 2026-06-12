---
title: "Can't get &quot;HauppaugeHVR-1600&quot; and &quot;Nvidia Restricted Driver&quot; to work at the same time"
date: 2008-09-23
forum: Multimedia Software
---

### Post by jgedutis on 2008-09-23
This is my first post to the Ubuntu forums.  I am new to Ubunto/Debian but quite familiar with Red Hat based distros from a system administration standpoint, as well as AIX.  We didn't even have the X Server installed.  I had been using Fedora, but ran into issues with the wireless and other things.  I had heard ubuntu was great and tried out 8.04.  Fixed my network issue and others.  It did take me almost a week to get dual monitors working with the nvidia card though.  I have this computer connected to a HDTV with a DVI cable and stereo and use it to watch digital movies and listen to my music collection.  I wanted to get MythTV installed and to do so wanted to use my Hauppauge HVR-1600 card.  I can get either the Hauppauge card or the nvidia driver, but not both at the same time.  Any help would be greatly appreciated.

Research So Far Follows
__________________________________________________________________________________________________________________________
Nvidia 6200 256MB 

root@Fusion:/home/taco# lspci | grep -i geforce
02:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

root@Fusion:/home/taco# dmesg | grep -i nv
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000F7550, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF30C0, 48F4 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: APIC 3FFF79C0, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[   33.276908] agpgart: Detected NVIDIA nForce2 chipset
[   35.542347] nvidia: module license 'NVIDIA' taints kernel.
[   37.604500] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008



Hauppauge HVR-1600 - cx23418

I followed the instructions at [http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600) to install the driver and firmware.

root@Fusion:/home/taco# lspci | grep -i cx
01:06.0 Multimedia video controller: Conexant CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

root@Fusion:/home/taco# dmesg | grep -i cx
[   35.049767] cx18:  Start initialization, version 1.0.0
[   35.309936] cx18-0: Initializing card #0
[   35.309940] cx18-0: Autodetected Hauppauge card
[   35.309975] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   35.310180] cx18-0: cx23418 revision 01010000 (B)
[   35.562268] tveeprom 2-0050: audio processor is CX23418 (idx 38)
[   35.562270] tveeprom 2-0050: decoder processor is CX23418 (idx 31)
[   35.562276] cx18-0: Autodetected Hauppauge HVR-1600
[   35.562278] cx18-0: VBI is not yet supported
[   36.448213] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   36.448241] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   36.608822] cx18-0: Disabled encoder IDX device
[   36.608878] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   36.608882] DVB: registering new adapter (cx18)
[   37.003617] cx18-0: DVB Frontend registered
[   37.003641] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   37.003660] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   37.003663] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   37.003682] cx18:  End initialization
[   43.594029] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   44.168606] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   44.174917] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   45.392068] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)

System --> Administration --> Hardware Drivers
Component
  NVIDIA accelerated graphics driver (latest cards) 
Enabled 
  Checked
Status
  In Use

root@Fusion:/home/taco# dpkg --status nvidia-glx-new
Package: nvidia-glx-new
Status: install ok installed
Priority: optional
Section: restricted/misc
Installed-Size: 15256
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.24 (2.6.24.13-19.45)
Version: 169.12+2.6.24.13-19.45
Replaces: nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video-2
Depends: libc6 (>= 2.1.3), libgl1-mesa | libgl1, libglu1-mesa | libglu1, libx11-6, libxext6, linux-restricted-modules-common, xserver-xorg-core (>= 1:0.99.0-1)
Suggests: nvidia-new-kernel-source (>= 169.12), nvidia-settings
Conflicts: nvidia-glx, nvidia-glx-legacy, nvidia-glx-src, nvidia-xconfig
Description: NVIDIA binary XFree86 4.x/X.Org 'new' driver
 These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
 of OpenGL applications via a direct-rendering X Server and supports the  newer
 GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
 flat panel displays are also supported.
 .
 If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
 package instead of this one. If you have a GeForce4, you may need the nvidia-glx
 package.

after installing cx23418 reboot

Ubuntu is running in low-graphics mode
Your screen and graphics card could not be detected correctly.
To use higher resolutions, visual effects or multiple screens, 
you have to configure the display yourself

System --> Administration --> Hardware Drivers
Component
  NVIDIA accelerated graphics driver (latest cards) 
  CX23418
Enabled 
  Checked
  Checked
Status
  In Use
  In Use

System --> Administration --> Nvidia X Server Settings

I get the error 
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

System --> Preferences --> Screen Resolution

Says monitor is unknown
Only resolution options are 800x600 and 640x480

If I into Hardware Drivers and uncheck the CX23418 Driver and reboot it goes back to working correctly with the Nvidia driver.

Sorry for the long post but I wanted to make sure I posted everything I thought that might help.


Any help would be greatly appreciated

---

### Post by jgedutis on 2008-09-24
<crickets>

---

### Post by jgedutis on 2008-09-24
I did a little more poking around and found the following.

I uninstalled the nvidia restricted driver and rebooted.  I then installed envyng-core and envyng-gtk.  I used that to install the latest drivers and update what was needed.  After rebooting I now have the nvidia driver working and the enabled box check in Hardware Drivers, but the status shows as "Not in use".  At least it doesn't disable the graphics driver and make me use a 800x600 window anymore ;)

user@computer:~$ dmesg | grep -i cx
[   35.370525] cx18: disagrees about version of symbol dvb_dmxdev_init
[   35.370531] cx18: Unknown symbol dvb_dmxdev_init
[   35.370563] cx18: disagrees about version of symbol video_ioctl2
[   35.370565] cx18: Unknown symbol video_ioctl2
[   35.370666] cx18: disagrees about version of symbol v4l_compat_ioctl32
[   35.370668] cx18: Unknown symbol v4l_compat_ioctl32
[   35.370772] cx18: disagrees about version of symbol cx2341x_ext_ctrls
[   35.370774] cx18: Unknown symbol cx2341x_ext_ctrls
[   35.370926] cx18: disagrees about version of symbol dvb_register_adapter
[   35.370928] cx18: Unknown symbol dvb_register_adapter
[   35.370988] cx18: disagrees about version of symbol cx2341x_ctrl_query
[   35.370990] cx18: Unknown symbol cx2341x_ctrl_query
[   35.371030] cx18: disagrees about version of symbol video_devdata
[   35.371032] cx18: Unknown symbol video_devdata
[   35.371265] cx18: disagrees about version of symbol tveeprom_read
[   35.371267] cx18: Unknown symbol tveeprom_read
[   35.371407] cx18: disagrees about version of symbol dvb_net_init
[   35.371408] cx18: Unknown symbol dvb_net_init
[   35.371463] cx18: disagrees about version of symbol video_unregister_device
[   35.371465] cx18: Unknown symbol video_unregister_device
[   35.371498] cx18: disagrees about version of symbol dvb_dmxdev_release
[   35.371500] cx18: Unknown symbol dvb_dmxdev_release
[   35.371529] cx18: disagrees about version of symbol cx2341x_update
[   35.371531] cx18: Unknown symbol cx2341x_update
[   35.371558] cx18: disagrees about version of symbol video_device_alloc
[   35.371560] cx18: Unknown symbol video_device_alloc
[   35.371609] cx18: disagrees about version of symbol video_register_device
[   35.371611] cx18: Unknown symbol video_register_device
[   35.371667] cx18: disagrees about version of symbol cx2341x_ctrl_get_menu
[   35.371669] cx18: Unknown symbol cx2341x_ctrl_get_menu
[   35.371729] cx18: disagrees about version of symbol dvb_frontend_detach
[   35.371731] cx18: Unknown symbol dvb_frontend_detach
[   35.371771] cx18: disagrees about version of symbol dvb_net_release
[   35.371773] cx18: Unknown symbol dvb_net_release
[   35.371801] cx18: disagrees about version of symbol cx2341x_log_status
[   35.371803] cx18: Unknown symbol cx2341x_log_status
[   35.371894] cx18: disagrees about version of symbol cx2341x_fill_defaults
[   35.371896] cx18: Unknown symbol cx2341x_fill_defaults
[   35.371937] cx18: disagrees about version of symbol dvb_unregister_frontend
[   35.371939] cx18: Unknown symbol dvb_unregister_frontend
[   35.372024] cx18: disagrees about version of symbol dvb_register_frontend
[   35.372026] cx18: Unknown symbol dvb_register_frontend
[   35.372081] cx18: disagrees about version of symbol tveeprom_hauppauge_analog
[   35.372083] cx18: Unknown symbol tveeprom_hauppauge_analog
[   35.372111] cx18: disagrees about version of symbol video_device_release
[   35.372113] cx18: Unknown symbol video_device_release
user@computer:~$

---

### Post by dotnick on 2008-11-12
I don't know if this will help you or not but I put a series of commands in a script and run it if things start acting up.

I put these two scripts in their own directory.

The first (download and install new v4l-dvb code):

update_v4l.sh
```
#bash
sudo /etc/init.d/mythtv-backend stop
cd v4l* && sudo make unload && cd ..
rm -r v4l* && rm tip.tar.bz2
wget http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2
tar jxvf tip.tar.bz2
cd v4l*
make && sudo make install
sudo modprobe cx18
sudo /etc/init.d/mythtv-backend start
```

The second (when I get those nasty cx18 disagrees with v4l_compat_ioctl32 errors and won't load):

forceReload.sh
```
#bash
sudo /etc/init.d/mythtv-backend stop
cd v4l* && sudo make unload
sudo make install
sudo make load
sudo /etc/init.d/mythtv-backend start
```

I get mixed success with both.  Sometimes they work and cx18 loads and sometimes they don't.

Good luck.

---

### Post by redboy33 on 2009-01-24
First, I am completely new to the wonderful world of Linux and Mythtv.  I am a seasoned Microsoft Systems Engineer that is completely lost when it comes to the command line (windows has made me soft)  I could use some help with this same problem.

In short I cannot get my HVR-1600 to work AT ALL with mythbuntu.

I've tried 8.04, 8.10 and 9.04 beta.

I follow the directions on 
[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) exactly (with the exception of a few sudo's infront of some of the commands, seems unbuntu is a little more secure than other distros??)  

Here are the errors.  Sorry if this is too much info, like I said I'm flying blind here... :p

vb936@mythtvbe:~$ uname -r
2.6.27-7-generic

vb936@mythtvbe:~$ sudo apt-get install mercurial linux-headers-$KERNEL_VERSION build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
mercurial is already the newest version.
Package linux-headers is not installed, so not removed
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 455 not upgraded.

vb936@mythtvbe:~$ sudo hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
destination directory: v4l-dvb
requesting all changes
adding changesets
adding manifests
adding file changes
added 10306 changesets with 26558 changes to 1695 files
updating working directory
1226 files updated, 0 files merged, 0 files removed, 0 files unresolved

vb936@mythtvbe:~/v4l-dvb$ sudo make

(this took about 5 minutes to complete and I guess the buffer wasn't set high enough to capture all the output?) 

--This was the last few lines--

  LD [M]  /home/vb936/v4l-dvb/v4l/zr36060.ko
  CC      /home/vb936/v4l-dvb/v4l/zr36067.mod.o
  LD [M]  /home/vb936/v4l-dvb/v4l/zr36067.ko
  CC      /home/vb936/v4l-dvb/v4l/zr364xx.mod.o
  LD [M]  /home/vb936/v4l-dvb/v4l/zr364xx.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
./scripts/rmmod.pl check
found 294 modules
make[1]: Leaving directory `/home/vb936/v4l-dvb/v4l'

vb936@mythtvbe:~/v4l-dvb$ sudo make install
make -C /home/vb936/v4l-dvb/v4l install
make[1]: Entering directory `/home/vb936/v4l-dvb/v4l'
Stripping debug info from files
-e
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/video:

-e
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/cinergyT2:

-e
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.27-7-generic/kernel/drivers/media/:
        video/gspca/m5602/: gspca_m5602.ko
        dvb/dvb-usb/: dvb-usb-dtv5100.ko dvb-usb-opera.ko dvb-usb-cxusb.ko
                dvb-usb-vp7045.ko dvb-usb-af9005-remote.ko dvb-usb-ttusb2.ko
                dvb-usb-af9015.ko dvb-usb-dib0700.ko dvb-usb-a800.ko
                dvb-usb-gp8psk.ko dvb-usb-dibusb-common.ko dvb-usb-au6610.ko
                dvb-usb-digitv.ko dvb-usb.ko dvb-usb-dibusb-mc.ko
                dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko dvb-usb-dtt200u.ko
                dvb-usb-cinergyT2.ko dvb-usb-vp702x.ko dvb-usb-umt-010.ko
                dvb-usb-anysee.ko dvb-usb-dibusb-mb.ko dvb-usb-dw2102.ko
                dvb-usb-gl861.ko dvb-usb-m920x.ko
        video/zoran/: videocodec.ko zr36050.ko zr36016.ko
                zr36060.ko zr36067.ko
        video/cx18/: cx18.ko
        video/cpia2/: cpia2.ko
        dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko
        video/ivtv/: ivtvfb.ko ivtv.ko
        common/tuners/: tuner-xc2028.ko mt2060.ko tda9887.ko
                mt2131.ko qt1010.ko mt20xx.ko
                tda827x.ko tda18271.ko xc5000.ko
                mxl5007t.ko tea5761.ko tuner-types.ko
                tda8290.ko tuner-simple.ko mt2266.ko
                tea5767.ko mxl5005s.ko
        video/sn9c102/: sn9c102.ko
        dvb/dvb-core/: dvb-core.ko
        video/: videobuf-dma-contig.ko vpx3220.ko videobuf-dma-sg.ko
                pms.ko bt856.ko upd64083.ko
                stradis.ko videobuf-core.ko tda9840.ko
                saa7191.ko cx2341x.ko wm8775.ko
                meye.ko w9968cf.ko saa7185.ko
                tuner.ko mt9t031.ko zr364xx.ko
                ks0127.ko stv680.ko videobuf-dvb.ko
                tvaudio.ko bt866.ko tea6420.ko
                cafe_ccic.ko saa5246a.ko msp3400.ko
                tvp514x.ko tcm825x.ko soc_camera.ko
                wm8739.ko stkwebcam.ko saa5249.ko
                cpia_pp.ko tda7432.ko w9966.ko
                mt9m001.ko upd64031a.ko ir-kbd-i2c.ko
                ov511.ko tea6415c.ko dabusb.ko
                bt819.ko cpia_usb.ko videodev.ko
                tda9875.ko adv7175.ko mxb.ko
                vivi.ko soc_camera_platform.ko cs53l32a.ko
                s2255drv.ko btcx-risc.ko se401.ko
                saa7110.ko saa7115.ko saa6588.ko
                saa7111.ko tvmixer.ko v4l2-common.ko
                saa7114.ko tw9910.ko hexium_orion.ko
                hexium_gemini.ko tvp5150.ko mt9m111.ko
                vp27smpx.ko adv7170.ko ov772x.ko
                ov7670.ko saa7127.ko m52790.ko
                mt9v022.ko v4l1-compat.ko videobuf-vmalloc.ko
                v4l2-int-device.ko c-qcam.ko tveeprom.ko
                cs5345.ko saa717x.ko cpia.ko
                tlv320aic23b.ko bw-qcam.ko
        video/cx23885/: cx23885.ko
        dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko
                dst.ko
        dvb/siano/: sms1xxx.ko
        video/cx25840/: cx25840.ko
        dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko
        dvb/dm1105/: dm1105.ko
        video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-alsa.ko
                saa7134-dvb.ko saa7134.ko
        dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko
                budget-av.ko budget.ko budget-core.ko
                budget-ci.ko
        video/et61x251/: et61x251.ko
        dvb/frontends/: nxt6000.ko dib7000m.ko drx397xD.ko
                s5h1411.ko si21xx.ko au8522.ko
                s5h1420.ko stv0288.ko nxt200x.ko
                mt352.ko s921.ko isl6405.ko
                s5h1409.ko sp887x.ko dibx000_common.ko
                isl6421.ko mt312.ko or51132.ko
                tda1004x.ko dib3000mb.ko lgs8gl5.ko
                dib3000mc.ko itd1000.ko sp8870.ko
                l64781.ko dib7000p.ko ves1x93.ko
                tda8083.ko stb6100.ko dib0070.ko
                ves1820.ko stv0297.ko tda10086.ko
                cx22700.ko zl10353.ko cx24110.ko
                stv0299.ko dvb_dummy_fe.ko cx24123.ko
                lgdt330x.ko dvb-pll.ko lnbp21.ko
                cx22702.ko stb6000.ko lgdt3304.ko
                cx24116.ko tda8261.ko tda10023.ko
                tua6100.ko bcm3510.ko tda10021.ko
                tda10048.ko stb0899.ko or51211.ko
                cx24113.ko tda826x.ko af9013.ko
        video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko
                cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko
                cx88-dvb.ko
        video/bt8xx/: bttv.ko
        video/gspca/: gspca_pac207.ko gspca_stk014.ko gspca_spca501.ko
                gspca_spca500.ko gspca_mars.ko gspca_spca508.ko
                gspca_t613.ko gspca_sunplus.ko gspca_vc032x.ko
                gspca_spca561.ko gspca_ov534.ko gspca_tv8532.ko
                gspca_spca505.ko gspca_spca506.ko gspca_sonixj.ko
                gspca_zc3xx.ko gspca_main.ko gspca_conex.ko
                gspca_pac7311.ko gspca_sonixb.ko gspca_ov519.ko
                gspca_finepix.ko gspca_etoms.ko
        dvb/pluto2/: pluto2.ko
        video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko
                ultracam.ko konicawc.ko quickcam_messenger.ko
        video/usbvision/: usbvision.ko
        common/: saa7146_vv.ko ir-common.ko saa7146.ko
        video/em28xx/: em28xx-dvb.ko em28xx-alsa.ko em28xx.ko
        video/pvrusb2/: pvrusb2.ko
        radio/: dsbr100.ko radio-maestro.ko radio-zoltrix.ko
                radio-terratec.ko radio-aimslab.ko radio-maxiradio.ko
                radio-gemtek.ko radio-trust.ko radio-sf16fmr2.ko
                radio-tea5764.ko radio-typhoon.ko radio-cadet.ko
                radio-aztech.ko radio-si470x.ko radio-sf16fmi.ko
                radio-rtrack2.ko radio-gemtek-pci.ko radio-mr800.ko
        video/uvc/: uvcvideo.ko
        dvb/ttusb-budget/: dvb-ttusb-budget.ko
        video/pwc/: pwc.ko
        video/zc0301/: zc0301.ko
        video/ovcamchip/: ovcamchip.ko
        video/au0828/: au0828.ko
/sbin/depmod -a 2.6.27-7-generic
make[1]: Leaving directory `/home/vb936/v4l-dvb/v4l'

vb936@mythtvbe:~/v4l-dvb$ sudo make unload
make -C /home/vb936/v4l-dvb/v4l unload
make[1]: Entering directory `/home/vb936/v4l-dvb/v4l'
scripts/rmmod.pl unload
found 294 modules
/sbin/rmmod tuner_types
ERROR: Module tuner_types is in use by tuner_simple
/sbin/rmmod tuner_simple
ERROR: Module tuner_simple is in use
/sbin/rmmod cx18
/sbin/rmmod ivtv
/sbin/rmmod cx8800
/sbin/rmmod tuner
/sbin/rmmod cx2341x
/sbin/rmmod cs5345
/sbin/rmmod bttv
/sbin/rmmod v4l2_common
/sbin/rmmod cx88xx
/sbin/rmmod videodev
/sbin/rmmod tuner_simple
/sbin/rmmod videobuf_dma_sg
/sbin/rmmod s5h1409
/sbin/rmmod tuner_types
/sbin/rmmod btcx_risc
/sbin/rmmod ir_common
/sbin/rmmod v4l1_compat
/sbin/rmmod dvb_core
/sbin/rmmod mxl5005s
/sbin/rmmod videobuf_core
/sbin/rmmod tveeprom
/sbin/rmmod tuner_types
ERROR: Module tuner_types does not exist in /proc/modules
/sbin/rmmod tuner_simple
ERROR: Module tuner_simple does not exist in /proc/modules
Couldn't unload: tuner_simple tuner_types
make[1]: Leaving directory `/home/vb936/v4l-dvb/v4l'

vb936@mythtvbe:~/v4l-dvb$ sudo modprobe cx18
vb936@mythtvbe:~/v4l-dvb$

vb936@mythtvbe:~/v4l-dvb$ sudo wget [http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz)
--2009-01-24 11:09:25--  [http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz)
Resolving dl.ivtvdriver.org... 130.133.35.29
Connecting to dl.ivtvdriver.org|130.133.35.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230740 (225K) [application/x-gzip]
Saving to: `cx18-firmware.tar.gz'

100%[======================================>] 230,740      193K/s   in 1.2s

2009-01-24 11:09:27 (193 KB/s) - `cx18-firmware.tar.gz' saved [230740/230740]

vb936@mythtvbe:~/v4l-dvb$ sudo tar -xzvf cx18-firmware.tar.gz
cx18-firmware/
cx18-firmware/v4l-cx23418-dig.fw
cx18-firmware/v4l-cx23418-cpu.fw
cx18-firmware/LICENSE
cx18-firmware/v4l-cx23418-apu.fw
cx18-firmware/CX23418 Firmware Video Firmware Release Notes.pdf

vb936@mythtvbe:~/v4l-dvb$ sudo cp cx18-firmware/*.fw /lib/firmware/$KERNEL_VERSION/

******(no output??  was anything supposed to happen here)******

vb936@mythtvbe:~/v4l-dvb$ sudo shutdown -r now

Broadcast message from vb936@mythtvbe
        (/dev/pts/0) at 11:12 ...

The system is going down for reboot NOW!

vb936@mythtvbe:~$ dmesg | grep cx18
[   11.765282] cx18:  Start initialization, version 1.0.4
[   11.774726] cx18-0: Initializing card #0
[   11.774733] cx18-0: Autodetected Hauppauge card
[   11.797269] cx18 0000:03:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.799487] cx18-0: cx23418 revision 01010000 (B)
[   12.123882] cx18-0: Autodetected Hauppauge HVR-1600
[   12.123884] cx18-0: Raw VBI supported; Sliced VBI is not yet supported
[   12.309255] tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   12.309278] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   12.515141] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   12.515145] DVB: registering new adapter (cx18)
[   12.630584] cx18-0: DVB Frontend registered
[   12.630586] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   12.630632] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   12.630674] cx18-0: Registered device vbi0 for encoder VBI (60 x 17328 bytes)
[   12.630716] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   12.630719] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   12.630747] cx18:  End initialization
[   26.557777] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   26.841936] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   26.848328] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   27.874225] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
vb936@mythtvbe:~$

******(Does this look correct?)******

Now to go and see if I get any kind of video.

FYI, I have Comcast Digital Cable.  Moving to FIOS next month..

---

### Post by 67GTA on 2009-02-21
[http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia](http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia)

---

