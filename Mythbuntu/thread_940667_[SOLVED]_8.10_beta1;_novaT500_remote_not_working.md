---
title: "[SOLVED] 8.10 beta1; novaT500 remote not working"
date: 2008-10-07
forum: Mythbuntu
---

### Post by jb5 on 2008-10-07
<Preamble> - Running under Hardy I had an intermittent problem whereby
the machine would occasionally fail to power_down properly. see [Bug](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42160) & [JB5 Bug report](https://bugs.launchpad.net/ubuntu/+bug/227844) 
After testing the Intrepid alpha six live CD and not experiencing this problem I decided
to ```
alt-F2
update-manager -d
``` and upgrade to Intrepid Beta one.
<end of Preamble>

Ok So running mythTv version 
```
jb@eric:~/v4l-dvb$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 0.21.0+fixes18528-0ubuntu0+mythbuntu1
  Candidate: 0.21.0+fixes18528-0ubuntu0+mythbuntu1
  Version table:
 *** 0.21.0+fixes18528-0ubuntu0+mythbuntu1 0
        100 /var/lib/dpkg/status
     0.21.0+fixes18379-0ubuntu1 0
        500 http://archive.ubuntu.com intrepid/multiverse Packages
     0.20.2-0ubuntu10.1 0
        500 http://gb.archive.ubuntu.com gutsy-updates/multiverse Packages
jb@eric:~/v4l-dvb$ 

```
However, I now have two problems :-
A) irw will not recognise any keys other than those supported by the kernal(Nova-T-500)
b) Wake times formally sent to /proc/acpi/alarm are no longer written as alarm no longer exists.

I will concentrate on the remote in this thread.

The number buttons are recognised as are the arrow keys!
I have tried the trick```

sudo dpkg-reconfigure lirc
```
First selecting none and then running the command again and selecting nova-t-500, also tried this trick from within MCC, all to no avail!!

dmesg | grep -i dvb```
jb@eric:~$ dmesg | grep -i dvb
[   21.567388] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   21.567395] firmware: requesting dvb-usb-dib0700-1.20.fw
[   21.616767] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   22.324042] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   22.324147] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   22.324325] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   22.444659] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   22.983349] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   22.983533] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   22.990234] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   23.553972] input: IR-receiver inside an USB DVB receiver as /class/input/input6
[   23.576642] dvb-usb: schedule remote query interval to 150 msecs.
[   23.576646] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   23.576851] usbcore: registered new interface driver dvb_usb_dib0700
jb@eric:~$ 

```
```
jb@eric:~$ ls -la /dev/input/by-path
total 0
drwxr-xr-x 2 root root 140 2008-10-07 13:08 .
drwxr-xr-x 4 root root 300 2008-10-07 13:08 ..
lrwxrwxrwx 1 root root   9 2008-10-07 13:08 pci-0000:00:1d.1-usb-0:1:1.0-event-kbd -> ../event1
lrwxrwxrwx 1 root root   9 2008-10-07 13:08 pci-0000:00:1d.1-usb-0:1:1.1-event-mouse -> ../event2
lrwxrwxrwx 1 root root   9 2008-10-07 13:08 pci-0000:00:1d.1-usb-0:1:1.1-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2008-10-07 13:08 pci-0000:00:1d.1-usb-0:1:1.2-event- -> ../event3
lrwxrwxrwx 1 root root   9 2008-10-07 13:08 pci-8-1--event-ir -> ../event6
jb@eric:~$ 

```
/etc/lirc/hardware.conf```
jb@eric:/etc/lirc$ cat hardware.conf
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
jb@eric:/etc/lirc$ 

```
/etc/lirc/lircd.conf```
jb@eric:/etc/lirc$ cat lircd.conf
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge Nova-T 500 remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge_novat500

jb@eric:/etc/lirc$ 

```
/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge_novat500```
jb@eric:/usr/share/lirc/remotes/hauppauge$ cat lircd.conf.hauppauge_novat500
#
# brand:                       Hauppauge NOVA-T-500
# model no. of remote control: Hauppage Nova-T-500 Snowboard Shape Silver over Black
#

begin remote

 name  NOVA-T500
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x1
 gap          199999
 toggle_bit      0


     begin codes
         Go                       0x0162
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         OK                       0x0160
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x009E
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         star                     0x0037
         0                        0x000B
         #                        0x0029
         one                      0x004F
         two                      0x0050
         three                    0x0051
         four                     0x004B
         five                     0x004C
         six                      0x004D
         seven                    0x0047
         eight                    0x0048
         nine                     0x0049
         ten                      0x0052
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191
     end codes

end remote


jb@eric:/usr/share/lirc/remotes/hauppauge$ 

```
~/.lirc/mythtv```
jb@eric:~/.lirc$ cat mythtv
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = NOVA-T500
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowRight
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = SkipBack
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = BackExit
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Fwdwind
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeDown
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeUp
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowLeft
    config = Left
    repeat = 0
    delay = 0
end
```


cat /var/log/daemon.log | grep lirc*```

$ cat /var/log/daemon.log | grep lirc*
Oct  7 11:35:10 eric lircd-0.8.3[6674]: caught signal
Oct  7 11:35:10 eric lircd-0.8.3[6674]: closing '/dev/input/event6'
Oct  7 11:36:35 eric lircd-0.8.3[6644]: lircd(userspace) ready
Oct  7 11:36:40 eric lircd-0.8.3[6644]: accepted new client on /dev/lircd
Oct  7 11:36:40 eric lircd-0.8.3[6644]: initializing '/dev/input/event6'
Oct  7 11:36:40 eric lircd-0.8.3[6644]: can't get exclusive access to events comming from `/dev/input/event6' interface
Oct  7 11:36:52 eric lircd-0.8.3[6644]: accepted new client on /dev/lircd
Oct  7 11:36:55 eric lircd-0.8.3[6644]: accepted new client on /dev/lircd
Oct  7 11:37:15 eric lircd-0.8.3[6644]: accepted new client on /dev/lircd
Oct  7 11:37:27 eric lircd-0.8.3[6644]: removed client
Oct  7 11:49:35 eric lircd-0.8.3[6644]: caught signal
Oct  7 11:49:35 eric lircd-0.8.3[6644]: closing '/dev/input/event6'
Oct  7 11:50:59 eric lircd-0.8.3[6738]: lircd(userspace) ready
Oct  7 11:51:04 eric lircd-0.8.3[6738]: accepted new client on /dev/lircd
Oct  7 11:51:04 eric lircd-0.8.3[6738]: initializing '/dev/input/event6'
Oct  7 11:51:04 eric lircd-0.8.3[6738]: can't get exclusive access to events comming from `/dev/input/event6' interface
Oct  7 11:51:16 eric lircd-0.8.3[6738]: accepted new client on /dev/lircd
Oct  7 11:51:20 eric lircd-0.8.3[6738]: accepted new client on /dev/lircd
Oct  7 11:53:09 eric lircd-0.8.3[6738]: accepted new client on /dev/lircd
Oct  7 11:53:14 eric lircd-0.8.3[6738]: removed client
Oct  7 12:27:28 eric lircd-0.8.3[6738]: accepted new client on /dev/lircd
Oct  7 13:07:05 eric lircd-0.8.3[6738]: removed client
Oct  7 13:07:30 eric lircd-0.8.3[6738]: caught signal
Oct  7 13:07:30 eric lircd-0.8.3[6738]: closing '/dev/input/event6'
Oct  7 13:08:52 eric lircd-0.8.3[6634]: lircd(userspace) ready
Oct  7 13:08:57 eric lircd-0.8.3[6634]: accepted new client on /dev/lircd
Oct  7 13:08:57 eric lircd-0.8.3[6634]: initializing '/dev/input/event6'
Oct  7 13:08:57 eric lircd-0.8.3[6634]: can't get exclusive access to events comming from `/dev/input/event6' interface
Oct  7 13:09:09 eric lircd-0.8.3[6634]: accepted new client on /dev/lircd
Oct  7 13:09:13 eric lircd-0.8.3[6634]: accepted new client on /dev/lircd
jb@eric:~/.lirc$ 

```

ps -ef |grep lirc*```
jb@eric:~/.lirc$ ps -ef |grep lirc*
root      6634     1  0 13:08 ?        00:00:00 /usr/sbin/lircd --driver=devinput --device=/dev/input/event6
jb        9145  7234  0 13:24 pts/1    00:00:00 grep lirc*
jb@eric:~/.lirc$ 

```

sudo irrecord lircd.conf```
jb@eric:/dev$ sudo irrecord lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)




jb@eric:/dev$ ls -l /dev/lir*
srw-rw-rw- 1 root root 0 2008-10-07 13:08 /dev/lircd
jb@eric:/dev$ 

```


NB With the latest v4l-dvb the firmware loaded is version 1.20, when running with this I found that the remote would issue one arrow press - pause and then repeat the key press until another remote button press was recieved. So I renamed the old firmware version 1.10 to version 1.20. Whichever firmwre used only the numeric buttons, mute and the arrow keys are recognised! 



I noticed that the most recent version of V4l-dvb (v4l-dvb-5ecdeaaa5171) - throws out a number of errors
make
```

jb@eric:~$ cd v4l-dvb
jb@eric:~/v4l-dvb$ make > ~/5ecd.make
/home/jb/v4l-dvb/v4l/cx18-driver.c: In function 'cx18_request_module':
/home/jb/v4l-dvb/v4l/cx18-driver.c:566: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/af9015.c: In function 'af9015_download_firmware':
/home/jb/v4l-dvb/v4l/af9015.c:665: warning: assignment discards qualifiers from pointer target type
/home/jb/v4l-dvb/v4l/m5602_core.c:43: warning: initialization from incompatible pointer type
/home/jb/v4l-dvb/v4l/ivtv-driver.c: In function 'ivtv_request_module':
/home/jb/v4l-dvb/v4l/ivtv-driver.c:866: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/pvrusb2-hdw.c: In function 'pvr2_hdw_setup_low':
/home/jb/v4l-dvb/v4l/pvrusb2-hdw.c:1993: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/pvrusb2-std.c: In function 'pvr2_std_id_to_str':
/home/jb/v4l-dvb/v4l/pvrusb2-std.c:220: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/zoran_card.c: In function 'find_zr36057':
/home/jb/v4l-dvb/v4l/zoran_card.c:1438: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/zoran_card.c:1458: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/zoran_card.c:1481: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/zoran_card.c:1491: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/v4l2-common.c: In function 'v4l2_ctrl_query_fill':
/home/jb/v4l-dvb/v4l/v4l2-common.c:496: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/v4l2-common.c: In function 'v4l2_ctrl_query_menu':
/home/jb/v4l-dvb/v4l/v4l2-common.c:661: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/v4l2-common.c: In function 'v4l2_ctrl_query_menu_valid_items':
/home/jb/v4l-dvb/v4l/v4l2-common.c:679: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/tvaudio.c: In function 'chip_probe':
/home/jb/v4l-dvb/v4l/tvaudio.c:1539: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/z0194a.h:85: warning: 'sharp_z0194a_config' defined but not used
/home/jb/v4l-dvb/v4l/cx2341x.c: In function 'cx2341x_ctrl_query_fill':
/home/jb/v4l-dvb/v4l/cx2341x.c:475: warning: format not a string literal and no format arguments
/home/jb/v4l-dvb/v4l/af9013.c: In function 'af9013_download_firmware':
/home/jb/v4l-dvb/v4l/af9013.c:1493: warning: assignment discards qualifiers from pointer target type
/home/jb/v4l-dvb/v4l/cx24116.c: In function 'cx24116_load_firmware':
/home/jb/v4l-dvb/v4l/cx24116.c:566: warning: passing argument 3 of 'cx24116_writeregN' discards 
```

on sudo make install - no apparent problems```

make -C /home/jb/v4l-dvb/v4l install
make[1]: Entering directory `/home/jb/v4l-dvb/v4l'
Stripping debug info from files
-e 
Removing obsolete files from /lib/modules/2.6.27-5-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.27-5-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.27-5-generic/kernel/drivers/media/:
	video/gspca/m5602/: gspca_m5602.ko 
	dvb/dvb-usb/: dvb-usb-dtv5100.ko dvb-usb-opera.ko dvb-usb-cxusb.ko 
		dvb-usb-vp7045.ko dvb-usb-af9005-remote.ko dvb-usb-ttusb2.ko 
		dvb-usb-af9015.ko dvb-usb-dib0700.ko dvb-usb-a800.ko 
		dvb-usb-gp8psk.ko dvb-usb-dibusb-common.ko dvb-usb-au6610.ko 
		dvb-usb-digitv.ko dvb-usb.ko dvb-usb-dibusb-mc.ko 
		dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko dvb-usb-dtt200u.ko 
		dvb-usb-vp702x.ko dvb-usb-umt-010.ko dvb-usb-anysee.ko 
		dvb-usb-dibusb-mb.ko dvb-usb-dw2102.ko dvb-usb-gl861.ko 
		dvb-usb-m920x.ko 
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
		bt856.ko upd64083.ko stradis.ko 
		videobuf-core.ko tda9840.ko saa7191.ko 
		cx2341x.ko wm8775.ko meye.ko 
		w9968cf.ko saa7185.ko tuner.ko 
		zr364xx.ko ks0127.ko stv680.ko 
		videobuf-dvb.ko tvaudio.ko bt866.ko 
		tea6420.ko cafe_ccic.ko saa5246a.ko 
		msp3400.ko zr36016.ko tcm825x.ko 
		soc_camera.ko wm8739.ko stkwebcam.ko 
		saa5249.ko cpia_pp.ko tda7432.ko 
		w9966.ko mt9m001.ko upd64031a.ko 
		ir-kbd-i2c.ko ov511.ko tea6415c.ko 
		dabusb.ko bt819.ko cpia_usb.ko 
		videodev.ko zr36060.ko tda9875.ko 
		adv7175.ko mxb.ko vivi.ko 
		soc_camera_platform.ko cs53l32a.ko s2255drv.ko 
		btcx-risc.ko se401.ko saa7110.ko 
		saa7115.ko saa6588.ko saa7111.ko 
		tvmixer.ko v4l2-common.ko saa7114.ko 
		hexium_orion.ko hexium_gemini.ko tvp5150.ko 
		mt9m111.ko vp27smpx.ko adv7170.ko 
		videocodec.ko ov7670.ko saa7127.ko 
		zr36067.ko m52790.ko mt9v022.ko 
		v4l1-compat.ko videobuf-vmalloc.ko compat_ioctl32.ko 
		v4l2-int-device.ko zr36050.ko sh_mobile_ceu_camera.ko 
		c-qcam.ko tveeprom.ko cs5345.ko 
		saa717x.ko cpia.ko tlv320aic23b.ko 
		bw-qcam.ko 
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
		mt352.ko isl6405.ko s5h1409.ko 
		sp887x.ko dibx000_common.ko isl6421.ko 
		mt312.ko or51132.ko dib3000mb.ko 
		tda1004x.ko lgs8gl5.ko dib3000mc.ko 
		itd1000.ko sp8870.ko l64781.ko 
		dib7000p.ko ves1x93.ko tda8083.ko 
		dib0070.ko ves1820.ko stv0297.ko 
		tda10086.ko cx22700.ko zl10353.ko 
		cx24110.ko stv0299.ko dvb_dummy_fe.ko 
		dvb-pll.ko lgdt330x.ko cx24123.ko 
		lnbp21.ko cx22702.ko stb6000.ko 
		cx24116.ko tda10023.ko tua6100.ko 
		bcm3510.ko tda10021.ko tda10048.ko 
		or51211.ko tda826x.ko af9013.ko 
	video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko 
		cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko 
		cx88-dvb.ko 
	video/bt8xx/: bttv.ko 
	video/gspca/: gspca_pac207.ko gspca_stk014.ko gspca_spca501.ko 
		gspca_spca500.ko gspca_mars.ko gspca_spca508.ko 
		gspca_t613.ko gspca_vc032x.ko gspca_spca561.ko 
		gspca_spca505.ko gspca_spca506.ko gspca_sonixj.ko 
		gspca_zc3xx.ko gspca_main.ko gspca_conex.ko 
		gspca_pac7311.ko gspca_sonixb.ko gspca_ov519.ko 
		gspca_etoms.ko 
	dvb/pluto2/: pluto2.ko 
	video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko 
		ultracam.ko konicawc.ko quickcam_messenger.ko 
	video/usbvision/: usbvision.ko 
	common/: saa7146_vv.ko ir-common.ko saa7146.ko 
	video/em28xx/: em28xx-dvb.ko em28xx-alsa.ko em28xx.ko 
	video/pvrusb2/: pvrusb2.ko 
	radio/: dsbr100.ko radio-maestro.ko radio-maxiradio.ko 
		radio-si470x.ko radio-gemtek-pci.ko radio-mr800.ko 
	video/uvc/: uvcvideo.ko 
	dvb/ttusb-budget/: dvb-ttusb-budget.ko 
	video/pwc/: pwc.ko 
	video/zc0301/: zc0301.ko 
	video/ovcamchip/: ovcamchip.ko 
	video/au0828/: au0828.ko 
/sbin/depmod -a 2.6.27-5-generic 
make[1]: Leaving directory `/home/jb/v4l-dvb/v4l'
```

and on sudo make load```

jb@eric:~/v4l-dvb$ sudo make load > ~/5ecd.makeload
insmod: error inserting './dib0070.ko': -1 File exists
insmod: error inserting './dvb-core.ko': -1 File exists
insmod: error inserting './mt2060.ko': -1 File exists
insmod: error inserting './dibx000_common.ko': -1 File exists
insmod: error inserting './dvb-usb.ko': -1 File exists
insmod: error inserting './dib3000mc.ko': -1 File exists
insmod: error inserting './dib7000p.ko': -1 File exists
insmod: error inserting './dib7000m.ko': -1 File exists
insmod: error inserting './dvb-usb-dib0700.ko': -1 File exists
insmod: error inserting './zr36067.ko': -1 No such device
insmod: error inserting './cx88-dvb.ko': -1 No such device
insmod: error inserting './ivtvfb.ko': -1 No such device
insmod: error inserting './cx88-blackbird.ko': -1 No such device
jb@eric:~/v4l-dvb$ 
```


So if you've made it this far, thank you!!!
The only problems that I can see are the errors when installing v4l-dvb and when I try to generate my own lircd.conf file, it complains that there is no /dev/lirc file!

My searches so far lead me to think that the v4l-dvb errors, mean that /dev/lirc doesn't get created / loaded. 
I've tried a couple of earlier v4l-dvb releases to see if that helps but so far no joy.

Apologies for the VERY LONG post but I've exausted my meagre talents in this area and I hope that the info may lead someone to a solution.

---

### Post by SiHa on 2008-10-08
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=787218&highlight=can%27t+exclusive+access](http://ubuntuforums.org/showthread.php?t=787218&highlight=can%27t+exclusive+access)

There is a bug filed relating to lirc devices not getting exclusive access to the dev/input interface. There's a manual fix posted in the bug comments. I've been meaning to try it out, because I think it might cure my problem of the NovaT-500 card filtering out repeat keypresses.

OK, the bug & fix relates to Hardy, but the fix is only dated a couple of weeks ago, so it probably hasn't made it into the Intrepid release yet.

I'd be interested to know
a) if this cures the problem.
b) if you get repeat events generated

Cheers,

Simon

---

### Post by jb5 on 2008-10-09
Thanks for the link, it appears to have worked! :)

So, for anybody upgrading to Intrepid, this is the sequence of events I followed to get my novaT500 remote working again.

Download and install v4l-dvb, as directed [here](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI). 
**NB** I am still running the 1.10verion of the firmware, however as the new v4l-dvb tries to load the 1.20version you will need to overwrite that file if you wish to do likewise```
cd /lib/firmware 
sudo cp dvb-usb-dib0700-1.20.fw dvb-usb-dib0700-1.20.fw.current
sudo cp dvb-usb-dib0700-1.10.fw dvb-usb-dib0700-1.20.fw
```

After switching off the machine and then booting up again:-

Download the lirc.fdi file found on this [bug report](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627) to your home directory, then```
cd /usr/share/hal/fdi/preprobe/20thirdparty
sudo cp lirc.fdi lirc.fdi.back
sudo cp ~/lirc.fdi lirc.fdi.hack
sudo cp lirc.fdi.hack lirc.fdi
```

Now configure the remote```
ls -al /dev/input/by-path
```and note the the ir event number. Then```
sudo dpkg-reconfigure lirc
```Run this through twice, the first time select none, the second time select nova_t_500 and enter in the event number when asked. Reboot your machine & this time the remote **should** work!

ASIDE - It is also possible to reconfigure the remote via mythbuntu control centre. If you choose to do it this way it might be worth backing up your definition file.```
cp ~/.lirc/mythtv ~/.lirc/mythtv.mydefs
```I think MCC might make a backup for you anyway, but certainly if you've altered or added button mappings/definitions yourself it does no harm to have another backup!

BTW the remote now repeats commands sent to it for as long as the button is pressed.

Thanks again for the tip, SiHa!

---

### Post by SiHa on 2008-10-09
```
BTW the remote now repeats commands sent to it for as long as the button is pressed.

```

That's the bit I was interested in! Guess I'll have to give that fix a try...

---

