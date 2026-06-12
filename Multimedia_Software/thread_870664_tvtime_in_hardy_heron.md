---
title: "tvtime in hardy heron"
date: 2008-07-26
forum: Multimedia Software
---

### Post by fishbulb1022 on 2008-07-26
hey, i just did a fresh install of hardy heron and its fantastic...except that i can't get tvtime to work. it worked 7.10 fine, but now when i try to start it it pops up as if its going to start and then closes. Any tips?

I figured out it doesn't work with the proprietary drivers

---

### Post by kpaden on 2008-07-27
Hi,

I am getting a black screen from Tvtime under Ubuntu Hardy. I have applied all of the patches, and I have spent the last couple of days trying to make this work. 

I built this one with Ubuntu and AMD64 processors. Tvtime gives me a black screen.  I am on comcast cable in Illinois, USA. I have attached a splitter for the lower two cable inputs. 

The tvtime-scanner seems to work. I am using the Nvidia drivers. I can play all other kinds of video except from the Tvtime application. I am including output from "tvtime -v", "lspci -v", hwinfo, dmesg, lsmod, and uname, lsmod, and uname.

[email]kpaden1@engineer.com[/email]

uname -a
Linux VGER-PRIME 2.6.25.11-custom #1 SMP Sun Jul 27 00:35:39 CDT 2008 x86_64 GNU/Linux
==========================================================================


tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/khalid/.tvtime/tvtime.xml
cpuinfo: CPU Quad-Core AMD Opteron(tm) Processor 2350, family 15, model 2, stepping 3.
cpuinfo: CPU measured at 2000.156MHz.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10400090
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1280x1024.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is compiz and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 280: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/khalid/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'cx23885', card 'Hauppauge WinTV-HVR1800' (bus PCIe:0000:04:00.0).
videoinput: Version is 1, capabilities 5010011.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (55).
tvtime: Cleaning up.
Thank you for using tvtime.


===========================================================================
lspci -v
  21: udi = '/org/freedesktop/Hal/devices/pci_14f1_8880_video4linux'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/video4linux/video0'
  video4linux.device = '/dev/video0'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.parent = '/org/freedesktop/Hal/devices/pci_14f1_8880'
  info.product = 'Hauppauge WinTV-HVR1800'
  video4linux.version = '2'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8880_video4linux'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'video4linux'
  info.category = 'video4linux'
  info.capabilities = { 'video4linux', 'video4linux.video_capture', 'video4linux.tuner', 'access_control' }
  linux.device_file = '/dev/video0'
  access_control.file = '/dev/video0'
  access_control.type = 'video4linux'

===============================================================================

lsmod
Module                  Size  Used by
nls_iso8859_1           6272  1 
nls_cp437               8000  1 
l2cap                  28608  13 rfcomm
video                  24084  0 
output                  5376  1 video
sbs                    17296  0 
sbshc                   8512  1 sbs
bttv                  209620  0 
ir_common              41796  1 bttv
i2c_algo_bit            8132  1 bttv
sbp2                   27084  0 
tuner                  41140  0 
tea5767                 8132  1 tuner
tda8290                15428  1 tuner
tda18271               34248  1 tda8290
tda827x                12292  1 tda8290
tuner_xc2028           22224  1 tuner
xc5000                 12740  1 tuner
tda9887                11524  1 tuner
tuner_simple           10504  1 tuner
mt20xx                 14408  1 tuner
snd_oxygen              9476  3 
snd_oxygen_lib         33344  1 snd_oxygen
snd_mpu401_uart        11072  1 snd_oxygen_lib
snd_pcm_oss            55040  0 
snd_mixer_oss          20416  1 snd_pcm_oss
snd_pcm                98632  3 snd_oxygen,snd_oxygen_lib,snd_pcm_oss
snd_seq_dummy           5316  0 
snd_seq_oss            38336  0 
mt2131                  7620  1 
snd_seq_midi           11776  0 
s5h1409                11460  1 
snd_rawmidi            31040  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
ipv6                  300392  28 
snd_seq                66144  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx23885                77040  0 
joydev                 15104  0 
v4l2_common            14144  3 bttv,tuner,cx23885
serio_raw               8516  0 
evdev                  14848  12 
nvidia               8114160  34 
btcx_risc               6472  2 bttv,cx23885
tveeprom               20368  2 bttv,cx23885
snd_timer              28816  2 snd_pcm,snd_seq
pcspkr                  4480  0 
snd_seq_device         10324  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dvb            8452  1 cx23885
i2c_nforce2             8768  0 
dvb_core               92212  1 videobuf_dvb
snd                    75912  19 snd_oxygen,snd_oxygen_lib,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        16580  3 bttv,cx23885,videobuf_dvb
videobuf_core          22148  4 bttv,cx23885,videobuf_dvb,videobuf_dma_sg
soundcore              10016  1 snd
button                 10400  0 
i2c_core               29152  19 bttv,i2c_algo_bit,tuner,tea5767,tda8290,tda18271,tda827x,tuner_xc2028,xc5000,tda9887,tuner_simple,mt20xx,mt2131,s5h1409,cx23885,v4l2_common,nvidia,tveeprom,i2c_nforce2
snd_page_alloc         12560  1 snd_pcm

================================================================================


04:00.0 Multimedia video controller: Conexant Unknown device 8880 (rev 0f)
	Subsystem: Hauppauge computer works Inc. Unknown device 7801
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at bfc00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>

---

