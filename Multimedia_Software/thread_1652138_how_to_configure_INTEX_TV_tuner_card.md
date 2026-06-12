---
title: "how to configure INTEX TV tuner card"
date: 2010-12-24
forum: Multimedia Software
---

### Post by Pramoda_84 on 2010-12-24
I have INTEX TV tuner card. i'm trying to configure in ubuntu for tvtime. The card has the saa7130 or saa7134 philipse chipset.

lspci | grep -i saa713
output:

```
00:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01) 
```

after the installation, the card was detected and /dev/video0 was created but dmesg indicated that the card is not among the ones listed as supported and since card did not have EEPROM, the card was not up and running right away.

i have edited /etc/modprobe.d/tvcard.conf and added options saa7134 card=3 tuner=14

```
$sudo nano /etc/modprobe.d/tvcard.conf
```
added:
```
options saa7134 card=3 tuner=14
```
Then CTRL+X to exit 

still it did not work. tvtime would always say no signal and tvtime-scanner never picked up any channels. 

then i followed instruction given by rsramkee ( [http://ubuntuforums.org/showthread.php?t=626780]("http://ubuntuforums.org/showthread.php?t=626780") ). edited saa7134-cards.c and deployed new kernel linux-2.6.36.2 with changes.

i rebooted machine to windows selected one channel in tv tuner software of windows,  again rebooted machine to ubuntu (i have dual boot windows XP and ubuntu 2.6.35.23). tvtime able display video of channel that is selected in windows OS (No sound), but not be able to tune any other stations.

In mplayer able display video of channel that is selected in windows OS with sound.

command:
```
mplayer tv:// -tv driver=v4l2:chanlist=us-cable:alsa:adevice=hw.0,1:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=PAL
```

i followed instruction given by [http://linuxtv.org/wiki/index.php/Saa7134-alsa]("http://linuxtv.org/wiki/index.php/Saa7134-alsa") to set up sound. 
loading the loopback module with the command:  

$ pactl load-module module-loopback

Now tvtime able display video of channel that is selected in windows OS with sound, but not be able to tune any other stations.

Problem:
 Not be able to tune any stations.

dmesg output:

```
[ 1320.568603] saa7130/34: v4l2 driver version 0.2.16 loaded
[ 1320.568697] saa7130[0]: found at 0000:00:0a.0, rev: 1, irq: 18, latency: 32, mmio: 0xdffff800
[ 1320.568737] saa7130[0]: subsystem: 1131:0000, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[ 1320.568976] saa7130[0]: board init: gpio is c08000
[ 1320.568981] saa7130[0]: there are different flyvideo cards with different tuners
[ 1320.568983] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[ 1320.568985] saa7130[0]: option to override the default value.
[ 1320.569026] Registered IR keymap rc-flyvideo
[ 1320.574929] input: saa7134 IR (LifeView FlyVIDEO30 as /devices/pci0000:00/0000:00:0a.0/rc/rc0/input6
[ 1320.575326] rc0: saa7134 IR (LifeView FlyVIDEO30 as /devices/pci0000:00/0000:00:0a.0/rc/rc0
[ 1320.676317] saa7130[0]: Huh, no eeprom present (err=-5)?
[ 1320.712350] tuner 1-0043: chip found @ 0x86 (saa7130[0])
[ 1320.712487] tda9887 1-0043: creating new instance
[ 1320.712491] tda9887 1-0043: tda988[5/6/7] found
[ 1320.729265] saa7130[0]: registered device video0 [v4l2]
[ 1320.731891] saa7130[0]: registered device vbi0
[ 1320.733748] saa7130[0]: registered device radio0
[ 1320.779244] saa7134 ALSA driver for DMA sound loaded
[ 1320.779256] saa7130[0]/alsa: LifeView FlyVIDEO3000 doesn't support digital audio
```


dmesg showing "tuner 1-0043: chip found @ 0x86 (saa7130[0])", but it is not displaying message as tuner number set like "tuner 1-0043: type set to 14" 
i tried with different tuner number value (1-127), but dmesg showing same massage.

commands change tuner number:
```
sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo rmmod tuner
sudo  modprobe saa7134 card=2 tuner=14 
```
tried with different tuner number value (1-127).

tvtime-scanner output:

```
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/pramoda/.tvtime/tvtime.xml
Scanning using TV standard PAL.
Scanning from  44.00 MHz to 958.00 MHz.
Checking  64.50 MHz: signal detected
```
sound played channel that is selected in windows OS.

please help me, i'm not be able to tune any stations using tvtime and xawtv. if channel  is not selected in windows OS for more then 1 hour then tvtime displays message no signal, same message in tvtime-scaner (No sound).

---

### Post by jeevas.v on 2011-03-02
press Alt+F2 and execute:

gksudo gedit /etc/modpobe.d/intex-tvtuner.conf

and paste the following line:

options saa7134 card=121

Save the file and restart.

---

### Post by Pramoda_84 on 2012-02-06
Thank you soo much jeevas.v for your help:D.

Now it is working fine!!!.. i'm trying this from last 2 years!!

as you suggested 

solution:

i have edited /etc/modprobe.d/tvcard.conf and added options saa7134 card=121

command:

```
$sudo nano /etc/modprobe.d/tvcard.conf
```

added

```
options saa7134 card=121
```

Then CTRL+X to exit 


rebooted machine 
then open tvtime select menu
 input configuration->  change video source
select television 

run tvtime-scanner to scan channel 

```
$tvtime-scanner
```

wait for scan channel to complete
then run tvtime


sound problem ?

solution:

run tvtime using below command 

command:
```
$tvtime --mixer=hw:0/Line
```

once again thanks to jeevas for help:D

---

### Post by sbnwl on 2012-02-19
I have a INTEX GRAVITY IT-200USB TV Tuner card. It is not even showing what chipset it contains?

With lsusb I get the following:

Bus 002 Device 007: ID 6000:0001 Beholder International Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x6000 Beholder International Ltd.
  idProduct          0x0001 
  bcdDevice            0.01
  iManufacturer          16 Trident
  iProduct               32 TVBOX
  iSerial                64 2004090820040908
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           78
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         48 2.0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA


I further did dmesg to get 

csc@csc-desktop:~/Desktop$ dmesg | grep usb
[    1.082632] usbcore: registered new interface driver usbfs
[    1.082639] usbcore: registered new interface driver hub
[    1.082659] usbcore: registered new device driver usb
[    2.072760] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.316145] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.519807] usb 1-1.2: new high speed USB device number 3 using ehci_hcd
[    2.719331] usb 1-1.5: new full speed USB device number 4 using ehci_hcd
[    2.921450] usbcore: registered new interface driver usbhid
[    2.921453] usbhid: USB HID core driver
[    2.990619] usb 1-1.6: new full speed USB device number 5 using ehci_hcd
[    3.162209] usb 2-1.4: new high speed USB device number 3 using ehci_hcd
[    3.337781] usb 2-1.6: new full speed USB device number 4 using ehci_hcd
[    3.434488] input: Sony RF Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input3
[    3.434586] generic-usb 0003:054C:04B8.0002: input,hidraw0: USB HID v1.11 Keyboard [Sony RF Receiver] on usb-0000:00:1d.0-1.6/input0
[    3.437123] input: Sony RF Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input4
[    3.437273] generic-usb 0003:054C:04B8.0003: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Sony RF Receiver] on usb-0000:00:1d.0-1.6/input1
[    9.557697] usbcore: registered new interface driver btusb
[   10.529444] input: QUANTA OpticalTouchScreen as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7
[   10.529577] quanta-touch 0003:0408:3001.0001: input,hidraw2: USB HID v1.10 Device [QUANTA OpticalTouchScreen] on usb-0000:00:1a.0-1.5/input0
[   10.635183] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input8
[   10.635249] usbcore: registered new interface driver uvcvideo


Now how to find which chipset does the card contain, so as to try that sort of modprobe ?
I am stuck at this very initial stage.

---

### Post by sbnwl on 2012-02-20
Okay, I got atleast the video to appear on tvtime.

First I opened the casing of (No care for Warranty, though only 3 months back purchase) the USB INTEX TV tuner card. Found some useful information on the pcb. 
It is a "TVMaster TM5600 B HCC02" (Trident 04) chip, with other small, nearly unreadable, content on other components.  For more info, logo looks like (the TM5600 chip only) as shown [URL="http://www.mocom.ru/Component/tv/roverbook/pro_700wh/roverbook_pro_700wh_tv.html"]here[U].

[/U][/URL]By googling around for the TM5600 chipset, found the standard wiki instructions on how to build and compile on a standalone machine, here follow this [link.]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")

The build, make and make install processes completed successfully w/o errors.
After a reboot, checked for new devices :

```
csb@csb-desktop:~/Desktop$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2012-02-20 14:37 /dev/video0
crw-rw----+ 1 root video 81, 1 2012-02-20 14:37 /dev/video1
```video1 is the newly appeared device. video0 is my usbwebcam (of my sony-all-in one box).
Another looked like:

```
csb@csb-desktop:~/Desktop$ ls -l /dev/dvb/
ls: cannot access /dev/dvb/: No such file or directory
```Doing lsmod showed:

```
csb@csb-desktop:~/Desktop$ lsmod | grep tm6000
tm6000_alsa            13581  1 
tm6000                 67227  2 tm6000_alsa
videobuf_vmalloc       13589  1 tm6000
videobuf_core          26022  2 tm6000,videobuf_vmalloc
rc_core                26333  9 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,tm6000
v4l2_common            16454  2 tuner,tm6000
videodev              106715  5 tuner,tm6000,v4l2_common,uvcvideo
snd_pcm                96714  3 tm6000_alsa,snd_hda_intel,snd_hda_codec
snd                    68266  16 tm6000_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```It sees that the tm6000 and tm6000_alsa modules loaded automatically after reboot.

dmesg showed the following:

```
  [   18.100277] IR RC5(x) protocol handler initialized
[   18.181961] tm6000: alt 0, interface 0, class 255
[   18.181963] tm6000: alt 0, interface 0, class 255
[   18.181964] tm6000: Bulk IN endpoint: 0x82 (max size=512 bytes)
[   18.181966] tm6000: alt 1, interface 0, class 255
[   18.181967] tm6000: ISOC IN endpoint: 0x81 (max size=3072 bytes)
[   18.181968] tm6000: alt 1, interface 0, class 255
[   18.181969] tm6000: alt 2, interface 0, class 255
[   18.181970] tm6000: alt 2, interface 0, class 255
[   18.181972] tm6000: New video device @ 480 Mbps (6000:0001, ifnum 0)
[   18.181973] tm6000: Found Generic tm5600 board
[   18.196345] tm6000 #0: i2c eeprom 00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.396985] IR RC6 protocol handler initialized
[   18.406290] tm6000 #0: i2c eeprom 10: 00 00
[   18.427679] IR JVC protocol handler initialized
[   18.435292]  00
[   18.439886] IR Sony protocol handler initialized
[   18.447711]  00
[   18.457361] init: failsafe main process (1078) killed by TERM signal
[   18.462389]  00
[   18.465667] init: apport pre-start process (1197) terminated with status 1
[   18.474162]  00
[   18.484131] init: apport post-stop process (1252) terminated with status 1
[   18.487608]  00
[   18.487949] init: kdm main process (1219) killed by TERM signal
[   18.490972] init: gdm main process (1251) killed by TERM signal
[   18.499480]  00 00 00 00 00
[   18.562871] IR SANYO protocol handler initialized
[   18.565573]  00 00 00 00  ................
[   18.617562] tm6000 #0: i2c eeprom 20: 00 00 00 00 00 00 00
[   18.701677] IR MCE Keyboard/mouse protocol handler initialized
[   18.706978] lirc_dev: IR Remote Control driver registered, major 247 
[   18.707052]  00
[   18.707520] IR LIRC bridge handler initialized
[   18.721433]  00 00 00 00 00 00 00 00  ................
[   18.824922] tm6000 #0: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   19.032527] tm6000 #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00
[   19.188991] vboxdrv: Found 4 processor cores.
[   19.189692] vboxdrv: fAsync=0 offMin=0x246 offMax=0x11c7
[   19.189761] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.189763] vboxdrv: Successfully loaded version 4.1.8 (interface 0x00190000).
[   19.189804]  00 00 00 00  ................
[   19.241700] tm6000 #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00
[   19.396042] vboxpci: IOMMU not found (not registered)
[   19.407318]  00 00 00 00  ................
[   19.460549] Bluetooth: RFCOMM TTY layer initialized
[   19.460554] Bluetooth: RFCOMM socket layer initialized
[   19.460556] Bluetooth: RFCOMM ver 1.11
[   19.463016] tm6000 #0: i2c eeprom 60: 00
[   19.464987] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.464989] Bluetooth: BNEP filters: protocol multicast
[   19.474800]  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   19.672167] tm6000 #0: i2c eeprom 70: 00 00 00 00 00 00 00 00
[   19.764217] sky2 0000:04:00.0: eth2: Link is up at 100 Mbps, full duplex, flow control rx
[   19.764344] sky2 0000:04:00.0: eth2: Link is up at 100 Mbps, full duplex, flow control rx
[   19.764855] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   19.776364]  00 00 00 00 00 00 00 00  ................
[   19.880099] tm6000 #0: i2c eeprom 80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.087577] tm6000 #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.295059] tm6000 #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.502539] tm6000 #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.710016] tm6000 #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.917473] tm6000 #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   21.125572] tm6000 #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   21.334880] tm6000 #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   21.529999] Device has eeprom but is currently unknown
[   21.535913] Found tm6000
[   21.806396] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   22.128536] i2c-core: driver [tuner] using legacy suspend method
[   22.128540] i2c-core: driver [tuner] using legacy resume method
[   22.129292] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[   22.131466] init: plymouth-stop pre-start process (1758) terminated with status 1
[   22.155233] xc2028 0-0061: creating new instance
[   22.155236] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   22.155239] Setting firmware parameters for xc2028
[   22.216076] xc2028 0-0061: Error: firmware xc3028-v24.fw not found.
[   22.217604] xc2028 0-0061: Error: firmware xc3028-v24.fw not found.
[   22.217685] tm6000 #0: registered device video1
[   22.217687] Trident TVMaster TM5600/TM6000/TM6010 USB2 board (Load status: 0)
[   22.217717] usbcore: registered new interface driver tm6000
[   22.261341] tm6000 #0: Initialized (TM6000 Audio Extension) extension
[   22.319651] xc2028 0-0061: Error: firmware xc3028-v24.fw not found.
[   22.941085] ppdev: user-space parallel port driver
[   22.948197] audit_printk_skb: 33 callbacks suppressed
[   22.948200] type=1400 audit(1329674932.744:23): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=2001 comm="apparmor_parser"
[   22.948585] type=1400 audit(1329674932.748:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2001 comm="apparmor_parser"
[   24.674868] init: mythtv-backend main process (1961) terminated with status 1
[   24.674891] init: mythtv-backend main process ended, respawning
[   25.787917] init: mythtv-backend main process (2056) terminated with status 1
[   25.787946] init: mythtv-backend main process ended, respawning
[   29.578520] init: mythtv-backend main process (2065) terminated with status 1
[   29.578541] init: mythtv-backend respawning too fast, stopped
[   30.018631] eth2: no IPv6 routers present
[   30.788588] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[  149.222669] tvtime[2490]: segfault at 840 ip 0000000000407220 sp 00007fffb6fa12a8 error 4 in tvtime[400000+83000]  
```It shows that the firmware xc3028-v24.fw is missing. Morever the  "Device has eeprom but is currently unknown" is the another problem that it shows.

For firmware, first installed linux-firmware-nonfree_1.11_all.deb package using synaptic. But it didn't contain the required firmware. (Actually it supplied xc3028-v27.fw). Had to extract it as suggested by the 'extract_xc3028.pl' script from [here.]("http://git.linuxtv.org/linux-2.6.git?a=blob;f=Documentation/video4linux/extract_xc3028.pl;h=47877deae6d7f60fe790bb4873df8f649162b691;hb=HEAD")
    
The script runs only on 32 bit *.sys driver files and generates xc3028-v24.fw file. And it shows md5 size mismatch error when run on 64 bit *.sys files, then terminates. Copied the generated xc3028-v24.fw file to /lib/firmware location.

Did a reboot and and finally dmesg shows following:

```
[   17.376666] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[   17.390099] Linux media interface: v0.10
[   17.395354] udevd[428]: renamed network interface wlan0 to wlan1
[   17.411273] input: QUANTA OpticalTouchScreen as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input9
[   17.411401] quanta-touch 0003:0408:3001.0001: input,hidraw2: USB HID v1.10 Device [QUANTA OpticalTouchScreen] on usb-0000:00:1a.0-1.5/input0
[   17.461788] Linux video capture interface: v2.00
[   17.461791] WARNING: You are using an experimental version of the media stack.
[   17.461792]     As the driver is backported to an older kernel, it doesn't offer
[   17.461793]     enough quality for its usage in production.
[   17.461793]     Use it with care.
[   17.461794] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   17.461794]     a3db60bcf7671cc011ab4f848cbc40ff7ab52c1e [media] xc5000: declare firmware configuration structures as static const
[   17.461796]     6fab81dfdc7b48c2e30ab05e9b30afb0c418bbbe [media] xc5000: drivers should specify chip revision rather than firmware
[   17.461797]     ddea427fb3e64d817d4432e5efd2abbfc4ddb02e [media] xc5000: remove static dependencies on xc5000 created by previous changesets
[   17.580373] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:64b1)
[   17.588167] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input10
[   17.588264] usbcore: registered new interface driver uvcvideo
[   17.588266] USB Video Class driver (1.1.1)
[   17.612510] WARNING: You are using an experimental version of the media stack.
[   17.612511]     As the driver is backported to an older kernel, it doesn't offer
[   17.612512]     enough quality for its usage in production.
[   17.612513]     Use it with care.
[   17.612514] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   17.612515]     a3db60bcf7671cc011ab4f848cbc40ff7ab52c1e [media] xc5000: declare firmware configuration structures as static const
[   17.612516]     6fab81dfdc7b48c2e30ab05e9b30afb0c418bbbe [media] xc5000: drivers should specify chip revision rather than firmware
[   17.612517]     ddea427fb3e64d817d4432e5efd2abbfc4ddb02e [media] xc5000: remove static dependencies on xc5000 created by previous changesets
[   17.642660] tm6000: alt 0, interface 0, class 255
[   17.642662] tm6000: alt 0, interface 0, class 255
[   17.642663] tm6000: Bulk IN endpoint: 0x82 (max size=512 bytes)
[   17.642665] tm6000: alt 1, interface 0, class 255
[   17.642666] tm6000: ISOC IN endpoint: 0x81 (max size=3072 bytes)
[   17.642667] tm6000: alt 1, interface 0, class 255
[   17.642668] tm6000: alt 2, interface 0, class 255
[   17.642669] tm6000: alt 2, interface 0, class 255
[   17.642671] tm6000: New video device @ 480 Mbps (6000:0001, ifnum 0)
[   17.642672] tm6000: Found Generic tm5600 board
[   17.657195] tm6000 #0: i2c eeprom 00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   17.867637] tm6000 #0: i2c eeprom 10: 00 00
[   17.880987] IR NEC protocol handler initialized
[   17.895180]  00 00 00 00 00 00 00 00 00
[   18.014456] IR RC5(x) protocol handler initialized
[   18.014992]  00 00 00 00 00  ................
[   18.073360] type=1400 audit(1329678605.855:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1139 comm="apparmor_parser"
[   18.073600] type=1400 audit(1329678605.855:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1140 comm="apparmor_parser"
[   18.074052] type=1400 audit(1329678605.855:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1140 comm="apparmor_parser"
[   18.074343] type=1400 audit(1329678605.855:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1140 comm="apparmor_parser"
[   18.074633] type=1400 audit(1329678605.855:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1143 comm="apparmor_parser"
[   18.075011] type=1400 audit(1329678605.855:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1143 comm="apparmor_parser"
[   18.080796] tm6000 #0: i2c eeprom 20: 00 00 00 00 00 00 00
[   18.161663] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   18.169102] sky2 0000:04:00.0: eth2: enabling interface
[   18.169523] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   18.170708]  00 00 00 00 00 00 00 00 00  ................
[   18.288289] tm6000 #0: i2c eeprom 30: 00 00
[   18.306148] IR RC6 protocol handler initialized
[   18.314670]  00 00 00 00
[   18.353235] IR JVC protocol handler initialized
[   18.366562]  00 00 00 00
[   18.414089] IR Sony protocol handler initialized
[   18.418414]  00 00 00 00 00
[   18.478980] IR SANYO protocol handler initialized
[   18.482269]  00  ................
[   18.490265] IR MCE Keyboard/mouse protocol handler initialized
[   18.495747] tm6000 #0: i2c eeprom 40: 00
[   18.500019] lirc_dev: IR Remote Control driver registered, major 247 
[   18.500642] IR LIRC bridge handler initialized
[   18.507855]  00 00 00
[   18.538552] init: failsafe main process (1084) killed by TERM signal
[   18.545046] init: apport pre-start process (1210) terminated with status 1
[   18.550116]  00 00
[   18.569001] init: apport post-stop process (1269) terminated with status 1
[   18.576226] init: kdm main process (1226) killed by TERM signal
[   18.578052]  00
[   18.581043] init: gdm main process (1265) killed by TERM signal
[   18.589921]  00 00 00 00 00 00 00 00 00  ................
[   18.707227] tm6000 #0: i2c eeprom 50: 00 00 00
[   18.744051] vboxdrv: Found 4 processor cores.
[   18.744814] vboxdrv: fAsync=0 offMin=0x242 offMax=0x23ed
[   18.744880] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   18.744882] vboxdrv: Successfully loaded version 4.1.8 (interface 0x00190000).
[   18.745264]  00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   18.914715] tm6000 #0: i2c eeprom 60: 00 00 00
[   18.951354] vboxpci: IOMMU not found (not registered)
[   18.952854]  00 00 00 00 00
[   19.014465] Bluetooth: RFCOMM TTY layer initialized
[   19.014470] Bluetooth: RFCOMM socket layer initialized
[   19.014471] Bluetooth: RFCOMM ver 1.11
[   19.016524] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.016527] Bluetooth: BNEP filters: protocol multicast
[   19.019722]  00 00 00 00 00 00 00 00  ................
[   19.124444] tm6000 #0: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   19.331964] tm6000 #0: i2c eeprom 80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   19.550131] tm6000 #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   19.754477] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   19.758858] tm6000 #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00
[   19.904423] sky2 0000:04:00.0: eth2: Link is up at 100 Mbps, full duplex, flow control rx
[   19.904558] sky2 0000:04:00.0: eth2: Link is up at 100 Mbps, full duplex, flow control rx
[   19.905023] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   19.914614]  00 00 00 00  ................
[   19.966507] tm6000 #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.173994] tm6000 #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.381461] tm6000 #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.588786] tm6000 #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.796414] tm6000 #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   20.990894] Device has eeprom but is currently unknown
[   20.997472] Found tm6000
[   21.531122] i2c-core: driver [tuner] using legacy suspend method
[   21.531126] i2c-core: driver [tuner] using legacy resume method
[   21.531355] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[   21.549894] xc2028 0-0061: creating new instance
[   21.549898] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   21.549901] Setting firmware parameters for xc2028
[   21.592346] xc2028 0-0061: Loading 77 firmware images from xc3028-v24.fw, type: xc2028 firmware, ver 2.4
[   21.871378] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   22.871457] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   29.063070] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   29.497450] SCODE (20000000), id 000000000000b700:
[   29.497457] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   29.579738] xc2028 0-0061: Incorrect readback of firmware version.
[   29.911152] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   30.489663] eth2: no IPv6 routers present
[   37.109525] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   37.544733] SCODE (20000000), id 000000000000b700:
[   37.544741] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   37.627763] xc2028 0-0061: Incorrect readback of firmware version.
[   37.966911] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   45.167646] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   45.606954] SCODE (20000000), id 000000000000b700:
[   45.606961] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   45.689881] xc2028 0-0061: Incorrect readback of firmware version.
[   46.022740] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   53.225074] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   53.661369] SCODE (20000000), id 000000000000b700:
[   53.661380] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   53.743178] xc2028 0-0061: Incorrect readback of firmware version.
[   54.074537] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   61.277933] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   61.721556] SCODE (20000000), id 000000000000b700: 
```No luck! 
Firmware not accepted. Tvtime freezed on first launch on video1 output. (configured the lines in settings,xml for 'video1' as hte video option)
```
 <option name="V4LDevice" value="/dev/video1"/> 
```Deleted the file:
```
csb@csb-desktop:~/Desktop$ sudo rm '/lib/firmware/xc3028-v24.fw' 
```Did a reboot, only to see that tvtime was working on first launch.(No Freeze)
This is the first launch:
```
csb@csb-desktop:~/Desktop$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/csb/.tvtime/tvtime.xml
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
Thank you for using tvtime. 
```Easily configured:
setup => input configuration => television standard => PAL => restart with new settings.
**It worked and the video appeared !**
I am able to switch between the channels by the SETUP BOX remote. 
BUT NO SOUND APPEARS.
What can be done now?

lsusb shows nothing change, surprisingly enough! Though video is fine there in tvtime.
```
Bus 002 Device 003: ID 6000:0001 Beholder International Ltd. 
```It was the output at very beginning of my start (The moment I first plugged the USB TV tuner).

Morever I searched through many threads, but none of the solutions worked for me.
For example see [here]("http://ubuntuforums.org/showthread.php?t=1814991") and [here]("https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770") and also [here]("https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/340769") .

I think the firmware problem behind missing noise, or may be tuner card number is not being properly detected in automatic mode. (I didn't try modprobe tm6000 card=xx tuner=xx ) Still using the default way.

What can be done further to get sound out of it?  Any suggestions are welcome.
Thanks in Advance.

---

### Post by sbnwl on 2012-02-25
Seems that this thread was old enough for most of us to see.
Sould I start a new thread on the matter?
Anybody watching should suggest....Please...

---

### Post by taherk on 2012-03-12
please help 
I Have intex tv tuner card and i m getting this massage

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/.tvtime/tvtime.xml: Permission denied.

please help to configure tvtuner.
i am new.

---

